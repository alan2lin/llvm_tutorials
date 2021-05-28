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

1.  检出LLVM（包括相关的子项目，如Clang）： falsetrue

    *Checkout LLVM (including related subprojects like Clang):*

    -   git clone https://github.com/llvm/llvm-project.git

    -   或者在windows上 git clone --config core.autocrlf=false
        https://github.com/llvm/llvm-project.git falsetrue

        *or, on windows, git clone --config core.autocrlf=false
        https://github.com/llvm/llvm-project.git*

    -   为了节省存储和加快检出时间,你可能想要一个浅拷贝。例如，要获取LLVM项目的最后一次修订[^2],使用
        git clone --depth 1 https://github.com/llvm/llvm-project.git
        falsetrue

        *To save storage and speed-up the checkout time, you may want to
        do a shallow clone. For example, to get the latest revision of
        the LLVM project, use git clone --depth 1
        https://github.com/llvm/llvm-project.git*

2.  falsetrue

    -   cd llvm-project

    -   mkdir build

    -   cd build

    -   cmake -G \<生成器\> \[选项\] ../llvm falsetrue

        *cmake -G \<generator\> \[options\] ../llvm*

        一些常见的构建系统生成器: falsetrue

        *Some common build system generators are:*

        -   Ninja --- 用于生成Ninja [^3] 构建文件. 大多数的 llvm
            开发者使用 Ninja。 falsetrue

            *Ninja --- for generating Ninja build files. Most llvm
            developers use Ninja.*

        -   Unix Makefiles --- 用于生成与make兼容的并行编译makeflies。
            falsetrue

            *Unix Makefiles --- for generating make-compatible parallel
            makefiles.*

        -   Visual Studio --- 用于生成 Visual Studio 项目和解决方案。
            falsetrue

            *Visual Studio --- for generating Visual Studio projects and
            solutions.*

        -   Xcode --- 用于生成 Xcode 项目。 falsetrue

            *Xcode --- for generating Xcode projects.*

The Second Chapter
==================

aaa [s2e]{acronym-label="s2e" acronym-form="singular+long"}
aaaaaaaaaaaaaaa [s2e]{acronym-label="s2e" acronym-form="singular+abbrv"}
aaaaaaaaaa [glsy]{acronym-label="glsy" acronym-form="singular+short"}

[^1]: [bitcode]{acronym-label="bitcode" acronym-form="singular+long"}

[^2]: 在git或者svn等版本管理软件中，一次提交就会形成一次修订

[^3]: [ninja]{acronym-label="ninja" acronym-form="singular+long"}
