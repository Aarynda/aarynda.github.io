#### Compiling Multiplication Instructions with RV32I

As I am adding features to my custom compiler, I have run into the first hurdle caused by my implementation plan of co-developing a compiler, assembler, and CPU. At the moment, my CPU core is a rather <a href="processor_specs/alpha_rev.md">simple single-cycle processor</a>, which only supports RV32I - notably, this lacks even integer multiply instructions. As such, this means my compiler must recreate multiplication functionality with simple adds and shifts. There are an incredible number of potential integer multiplication algorithms, each of which may be most useful for specific multiplication use cases, which my compiler must identify. For ease of compilation however, I am only considering two main algorithms - a naive addition loop (used when at least one operand is < 32), and a shift-and-add multiplication algorithm. 

The naive addition algorithm is incredibly easy to understand - simply add "B" to the output register "A" times. This algorithm is guaranteed to always work, but as the input operands grow larger, the loop will begin to run for an absurd amount of time, dramatically increasing the runtime of the entire program. 

The shift-and-add multiplication algorithm is slightly more complicated, but far more efficient as operands grow above values of 32. An outer loop checks the LSB of "A" - if it is 1, it will add an intermediate register that starts with a value of "B" to the output register, and if it is 0, it skips to the end of the loop iteration. At the end of each iteration, the register holding "A" is shifted to the right once so we can obtain the next LSB, and the intermediate register that started with a value of "B" is shifted to the left once to maintain the relative value of the bits in "A". 

There are still some minor issues with this implementation of multiplication - namely that it only returns the bottom 32 bits and may not always operate effectively with negative numbers. Future planned improvements to this small facet of the compiler will include alternative multiplication algorithms based on whether future instructions will need the top 32, bottom 32, or entire 64 bits of a product, as well as ensuring that signed integer multiplication works as expected. And of course, once the processor moves along to the stage of supporting RV32M, there will become some additional hardware-specific tradeoffs, as the compiler has to be aware whether using the single MUL instruction will be more or less efficient than a simple shift and add routine.

Algorithm 1: The basics
```
#using x10 & x11 as inputs
addi x12, x0, 0
addi x13, x0, 0
loop:
	add x12, x12, x10
	addi x13, x13, 1
	blt x13, x11, loop
```

Algorithm 2: Shift and Add
```
#using x10 and x11 as inputs
addi x12, x0, 0
addi x13, x0, 0
outer_loop:
	andi x14, x10, 1
	beq x14, x0, skip
	add x15, x0, x11
	sll x15, x15, x12
	add x13, x13, x15
	skip:
		srli x10, x10, 1
		addi x30, x0, 32
		addi x12, x12, 1
		blt x12, x30, outer_loop
```