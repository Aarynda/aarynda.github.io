This page contains a running blog of my asm2hex project, which uses regex parsing to convert RISC-V assembly into a raw hex file format that could be used in computer simulation.

This is intended to function as one small part of a larger toolchain that will eventually allow C programs to be compiled into RISC-V asssembly, converted to a hex file, and then run on a simulated or FPGA-based custom processor.

Development of this project started off quite simply as I started with the basic i-type and r-type instructions - this meant I just needed to use regexes to identify the opcode and operands for a line of code, and that could be converted directly to into the equivalent hex through simple bitshifting and addition. There were some minor complications, as I chose to implement the pseudo-instruction *li* and would need to convert this single instruction into an *lui* and *addi* if the immediate was too large. Some basic arithmetic solved this issue fairly easily though, and *li* instructions were able to work with minimal issues.
Issues began to arise, however, when I began to add basic branch instructions - for ease of developing assembly code, I would like asm2hex to be able to parse labels as immediate values, meaning the program now has to do some additional preprocessing on the file to identify the values for each of these labels. Unfortunately, due to the previous choice of implementing *li*, I could no longer simply use line numbers, or even number of non-comment, non-blank line instructions as the memory address for the label as it's possible that an *li* instruction would now be converted to two instructions, throwing off the count. This required me to make a slightly more complicated preprocessing function, and preemptively check whether *li* should be converted or not - in future iterations its possible that the split of *li* into *lui* and *addi* will actually be done in the preprocessing step in order to reduce the amount of double-checking being done, but that may depend on whether other instructions will cause further issues.

Future steps for this project will include finishing support for the rest of the basic RISC-V 32I ISA, as well as potentially adding support for additional extensions, including floating-point and atomic operations. The status of all ISA extensions will be reported in a table linked both here, and on the asm2hex repository README found <a href="https://github.com/Aarynda/asm2hex">here</a>.

| Extension | Level of Support |
|:---:|:---:|
|RV32I|In Progress|
|RV32M|No|
|RV32A|No|
|RV32F|No|
|RV32D|No|
|RV32C|No|
|RV32B|No|
|RV32V|No|
