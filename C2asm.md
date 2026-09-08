## Abstract
This compiler is intended to compile from a subset of C features to the RISC-V ISA supported by my partner and I's <a href="RISC-V_Processors.html">custom CPU</a>, allowing us to run high-level C programs on our own hardware.

Additionally, due to personal interest in front-end parsing of compilers, I have chosen to forgo utilizing ANTLR or other front-end parsing tools, and am instead writing my own parser. However, I recognize the significant value offered by ANTLR's ease of reconfiguring grammar and adding semantic actions, and have effectively chosen to re-implement a subset of ANTLR's functionality for personal understanding.

Repo link for <a href="https://github.com/Aarynda/Compiler">compiler</a>.