<!DOCTYPE html>
<head>
    <link rel="stylesheet" href="style.scss">
</head>

# Intro
My name is <a href="https://www.linkedin.com/in/alex-tauriainen/">Alex Tauriainen</a>, and I am a computer engineer by trade. My interests span a wide range of topics within computer engineering, from computer hardware architecture to computer systems design and the entire computing software stack.
This site holds documentation for my personal projects, as well as occasional reports or remarks on recent papers or developments in my fields of interest.

## Personal Projects
Personal projects listed here are all intended to be part of a cohesive toolchain, allowing me to convert high-level C programs to RISC-V assembly, to a bootable hex image, and then simulating the results of the program on a custom CPU design. Long-term goals include working with my partner, <a href="https://www.linkedin.com/in/arjun-siderys/">Arjun Siderys</a>, to synthesize the custom CPU on an FPGA and connect it with external peripherals, allowing us to develop an entirely custom computer system.

<a href="C2asm.html">
    <button>
        C2asm (C compiler) Project
    </button>
</a>

<a href="asm2hex.html">
    <button>
        asm2hex (RISC-V assembler) Project
    </button>
</a>

<a href="RISC-V_Processors.html">
    <button>
        Catalog of RISC-V Processor releases
    </button>
</a>


## Academic History
### MSECE, Purdue University, Aug 2025 - May 2027
Relevant Coursework:
* Computer Architecture (Fall 2026)
    * Extension of undergraduate computer architecture, including new topics of out-of-order processing, and pivoting project work from Verilog development to C simulation utilizing the Gem5 simulator.
* Algorithms and Complexity (Fall 2026)
    * Pure lecture course focused on more rigorous mathematical analysis of algorithms and the introduction of more specific algorithms, such as the Fast Fourier Transform and accelerated matrix multiplication algorithms.
* MOS VLSI Design (Fall 2026)
    * Project-based course focusing on the implementation and layout of larger digital circuits in Cadence Virtuoso.
* Compilers (Fall 2025)
    * Project-based course covering parsing, code generation and common optimizations, culminating in the development of a compiler from MicroC code to RISC-V Assembly. Written in Java.
* Artificial Intelligence (Fall 2025)
    * Lecture and Project-based course covering the mathematical foundations of modern artificial intelligence models, with an open-ended research and design project. Selected project was a neural network-based correlating branch predictor. Simulation written in Python.

### BSCmpE, Purdue University, Aug 2023 - May 2026
Relevant Coursework: 
* Processor Prototyping and Design/Undergraduate Computer Architecture
    * Lecture and project-based course. Project iteratively develops a RISC-V processor, progressing from simple single-cycle, to a standard 5-stage pipeline, adding instruction and data cache, and then finally implementing a two-core design with MSI cache coherency protocol. All processors implemented in Verilog, simulated with Vivado toolchain, and then finally verified on Xilinx FPGAs.
* Microprocessor Systems and Design
    * Lecture and Laboratory course culminating in a team project utilizing an STM32 embedded microcontroller. Team developed an implementation of the classic Google dinosaur game on an STM32 with a TFT screen and connected buttons.