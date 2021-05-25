LLVM 系统入门 falsetrue(Getting Started with the LLVM System) 
=============================================================

概述 falsetrue(Overview) 
------------------------

欢迎来到 LLVM 项目! falsetrue

Welcome to the LLVM project!

LLVM项目包含多个组件。 该项目的核心本身称为"LLVM"。
它包含处理中间表示层并将其转换为目标文件所需的所有工具，库和头文件。
工具包括汇编器，反汇编器，位码分析器和位码优化器。
它还包含基本的回归测试。 falsetrue

The LLVM project has multiple components. The core of the project is
itself called "LLVM". This contains all of the tools, libraries, and
header files needed to process intermediate representations and converts
it into object files. Tools include an assembler, disassembler, bitcode
analyzer, and bitcode optimizer. It also contains basic regression
tests.

类C语言使用Clang前端。 该组件将C，C ++，Objective C和Objective C
++代码编译为LLVM位码，并使用LLVM将位码编译为目标文件。 falsetrue

C-like languages use the Clang front end. This component compiles C,
C++, Objective C, and Objective C++ code into LLVM bitcode -- and from
there into object files, using LLVM.

The Second Chapter
==================

aaa [s2e]{acronym-label="s2e" acronym-form="singular+long"}
aaaaaaaaaaaaaaa [s2e]{acronym-label="s2e" acronym-form="singular+abbrv"}
aaaaaaaaaa [glsy]{acronym-label="glsy" acronym-form="singular+short"}
