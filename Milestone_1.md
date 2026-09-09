#### Milestone 1: 9/9/2026
First full pipeline completed - converted C code to valid RISC-V assembly (albeit without register allocation). Manual tweaks made to convert "temporary" registers into actual ones valid for use in assembly. Assembly code was then converted to raw hex via asm2hex2, with a minimalistic memory map configuration. Hex file was then finally run as the boot image for the custom RISC-V processor, completing the pipeline and giving the final output. There are still some errors to be resolved, as the outputs are not entirely what was expected, but this is truly the first and roughest proof-of-concept run possible.


C code
```C
int a = 5 + 7; //Expected value: 12
int b = a - 5; //Expected value: 7
int c = b + b; //Expected value: 14
int d = a - b - c; //Expected value: -9
```

RISC-V Assembly (with manual register modifications)
```RISC-V
addi x1, x0, 7
addi x2, x1, 5
sw x2, 0(x0)
lw x3, 0(x0)
addi x4, x3, 5  #Error in compilation here - sign of immediate value changed
                #causing cascading effects on the value of outputs
sw x4, 4(x0)
lw x5, 4(x0)
lw x6, 4(x0)
add x7, x5, x6
sw x7, 8(x0)
lw x8, 0(x0)
lw x9, 4(x0)
sub x10, x8, x9
lw x11, 8(x0)
sub x12, x10, x11
sw x12, 12(x0)
```

Pure Hex Input
```
00700093
00508113
00200023
00002183
00518213
00400223
00402283
00402303
006283b3
00700423
00002403
00402483
00940533
00802583
00b50633
00c00623
```

Pure Hex Output
```
0000000c #Address used for variable a -> value of 12, as expected
00000011 #Address used for variable b -> value of 17, expected due to compilation error
00000022 #Address used for variable c -> value of 34, expected due to compilation error
0000003f #Address used for variable d -> value of 63, unexpected and unknown (as of yet) error cause
00518213
00400223
00402283
00402303
006283b3
00700423
00002403
00402483
00940533
00802583
00b50633
00c00623
```