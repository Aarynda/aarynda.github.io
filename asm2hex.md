This page contains a running blog of my asm2hex project, which uses regex parsing to convert RISC-V assembly into a raw hex file format that could be used in computer simulation.

## Abstract
This is intended to function as one small part of a larger toolchain that will eventually allow C programs to be compiled into RISC-V asssembly, converted to a hex file, and then run on a simulated or FPGA-based custom processor.

There are currently two different versions of asm2hex present in the main repo. asm2hex.py is the original version of the program, which was for the most part deprecated due to a) being spaghetti code, and b) only supporting singular .asm files, which would be insufficient for larger assembly projects (such as a small OS kernel for my custom CPU). As such, the second version (asm2hex2.py), currently has support for a smaller subset of the RISC-V ISA, but also functions as a small linker with the ability to convert multiple .asm files into a singular memory image that can be loaded into either a simulation environment, or onto an FPGA memory block. Currently asm2hex2 has the ability to take in a .yml file representing the memory map of the target processor, allowing you to mark out what regions of memory should be reserved for kernel code, application code, or memory-mapped I/O. This also allows you to define specific memory-mapped I/O locations and reference them globally in your kernel or user-level assembly files.

Repo Link for <a href="https://github.com/Aarynda/asm2hex">asm2hex</a>.

## Archived Posts/Details
<a href="asm2hex_archive_june_2026">
    <button>
        June 2026
    </button>
</a>