LLVM 系统入门 falsetrue(Getting Started with the LLVM System) 
=============================================================

概述 falsetrue(Overview) 
------------------------

欢迎来到 LLVM 项目! falsetrue

*Welcome to the LLVM project!*

LLVM项目包含多个组件。 该项目的核心本身称为"LLVM"。
它包含处理中间表示层并将其转换为目标文件所需的所有工具，库和头文件。
工具包括汇编器，反汇编器，[bitcode]{acronym-label="bitcode"
acronym-form="singular+short"}[^1]分析器和[bitcode]{acronym-label="bitcode"
acronym-form="singular+short"}优化器。 它还包含基本的回归测试。
falsetrue

*The LLVM project has multiple components. The core of the project is
itself called "LLVM". This contains all of the tools, libraries, and
header files needed to process intermediate representations and converts
it into object files. Tools include an assembler, disassembler, bitcode
analyzer, and bitcode optimizer. It also contains basic regression
tests.*

类C语言使用Clang前端。 该组件将C，C ++，Objective C和Objective C
++代码编译为LLVM[bitcode]{acronym-label="bitcode"
acronym-form="singular+short"}，并使用LLVM将[bitcode]{acronym-label="bitcode"
acronym-form="singular+short"}编译为目标文件。 falsetrue

*C-like languages use the Clang front end. This component compiles C,
C++, Objective C, and Objective C++ code into LLVM bitcode -- and from
there into object files, using LLVM.*

其他组件包括：libc ++ C ++标准库，LLD链接器等。 falsetrue

*Other components include: the libc++ C++ standard library, the LLD
linker, and more.*

获取源代码并构建LLVM falsetrue

*Getting the Source Code and Building LLVM*

LLVM入门文档可能已过时。 Clang入门页可能包含更准确的信息。 falsetrue

*The LLVM Getting Started documentation may be out of date. The Clang
Getting Started page might have more accurate information.*

这是一个获取和构建llvm源码的工作流程和配置的例子： falsetrue

*This is an example workflow and configuration to get and build the LLVM
source:*

1.  签出LLVM（包括相关的子项目，如Clang）： falsetrue

    *Checkout LLVM (including related subprojects like Clang):*

The Second Chapter
==================

aaa [s2e]{acronym-label="s2e" acronym-form="singular+long"}
aaaaaaaaaaaaaaa [s2e]{acronym-label="s2e" acronym-form="singular+abbrv"}
aaaaaaaaaa [glsy]{acronym-label="glsy" acronym-form="singular+short"}

[^1]: [bitcode]{acronym-label="bitcode" acronym-form="singular+long"}
