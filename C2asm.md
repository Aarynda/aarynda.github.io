The C2asm project is a simple C compiler that converts from C to RISC-V assembly.

An endgoal of this project is to support the majority of C syntax features, as well as compiling to multiple different non-standard ISAs. The main ISA supported at the moment is RISC-V, due to the simplicity of the ISA itself and ability to more easily verify the correctness of the assembly code. In the future, however, this project may be expanded to support some microprocessor-specific ISAs, such as the 6502 processor's ISA, making it possible to use this tool to compile C programs for use on older hardware.

This project is still in very early stages, but the repository will be made public and progress updates posted here as the project continues.