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

类C语言使用[Clang](https://clang.llvm.org/)前端。 该组件将C，C
++，Objective C和Objective C
++代码编译为LLVM[bitcode]{acronym-label="bitcode"
acronym-form="singular+short"}，并使用LLVM将[bitcode]{acronym-label="bitcode"
acronym-form="singular+short"}编译为目标文件。 falsetrue

*C-like languages use the Clang front end. This component compiles C,
C++, Objective C, and Objective C++ code into LLVM bitcode -- and from
there into object files, using LLVM.*

其他组件包括：libc ++ C ++标准库，LLD链接器等。 falsetrue

*Other components include: the libc++ C++ standard library, the LLD
linker, and more.*

获取源代码并构建LLVM falsetrue(Getting the Source Code and Building LLVM) 
-------------------------------------------------------------------------

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

2.  配置并构建 LLVM 和 Clang: falsetrue

    *Configure and build LLVM and Clang:*

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

        一些常见的选项: falsetrue

        *Some Common options:*

        -   -DLLVM\_ENABLE\_PROJECTS='\...'
            你要额外构建的LLVM子项目的分号分隔列表,可以包含以下任意项:
            clang, clang-tools-extra, libcxx, libcxxabi, libunwind,
            lldb, compiler-rt, lld, polly, 或 debuginfo-tests。
            falsetrue

            *-DLLVM\_ENABLE\_PROJECTS='\...' --- semicolon-separated
            list of the LLVM subprojects you'd like to additionally
            build. Can include any of: clang, clang-tools-extra, libcxx,
            libcxxabi, libunwind, lldb, compiler-rt, lld, polly, or
            debuginfo-tests.*

            例如要构建LLVM,Clang,libcxx和libcxxabi,使用
            -DLLVM\_ENABLE\_PROJECTS=\"clang;libcxx;libcxxabi\"。
            falsetrue

            *For example, to build LLVM, Clang, libcxx, and libcxxabi,
            use -DLLVM\_ENABLE\_PROJECTS=\"clang;libcxx;libcxxabi\".*

        -   -DCMAKE\_INSTALL\_PREFIX=目录 --- 为目录指定要安装 LLVM
            工具和库的位置的完整路径名（默认为 /usr/local）。 falsetrue

            *-DCMAKE\_INSTALL\_PREFIX=directory --- Specify for
            directory the full pathname of where you want the LLVM tools
            and libraries to be installed (default /usr/local).*

        -   -DCMAKE\_BUILD\_TYPE=类型 --- 类型的有效选项为
            Debug、Release、RelWithDebInfo 和 MinSizeRel。 默认为Debug。
            falsetrue

            *-DCMAKE\_BUILD\_TYPE=type --- Valid options for type are
            Debug, Release, RelWithDebInfo, and MinSizeRel. Default is
            Debug.*

        -   -DLLVM\_ENABLE\_ASSERTIONS=开 ---
            启用断言检查进行编译（调试版本的默认值为
            Yes，所有其他版本类型的默认值为 No）。 Compile with
            assertion checks enabled (default is Yes for Debug builds,
            No for all other build types). falsetrue

            *-DLLVM\_ENABLE\_ASSERTIONS=On --- Compile with assertion
            checks enabled (default is Yes for Debug builds, No for all
            other build types).*

    -   cmake --build . \[--target \<目标\>\]或
        直接上面所指定的构建系统。 falsetrue

        *cmake --build . \[--target \<target\>\] or the build system
        specified above directly.*

        -   默认目标 (例如: cmake --build . 或 make)
            将构建所有的LLVM内容。 falsetrue

            *The default target (i.e. cmake --build . or make) will
            build all of LLVM.*

        -   check-all 目标（例如 ninja
            check-all）将运行回归测试以确保一切正常。 falsetrue

            *The check-all target (i.e. ninja check-all) will run the
            regression tests to ensure everything is in working order.*

        -   CMake 会为每个工具和库生成构建目标，大多数 LLVM
            子项目会生成自己的 check-\<project\> 目标 falsetrue

            *CMake will generate build targets for each tool and
            library, and most LLVM sub-projects generate their own
            check-\<project\> target.*

        -   运行串行构建会很慢。 要提高速度，请尝试运行并行构建。 这是在
            Ninja 中默认完成的； 对于 make，使用选项 -j NN，其中 NN
            是并行作业的数量，例如 可用 CPU 的数量。 falsetrue

            *Running a serial build will be slow. To improve speed, try
            running a parallel build. That's done by default in Ninja;
            for make, use the option -j NN, where NN is the number of
            parallel jobs, e.g. the number of available CPUs.*

    -   更多信息参见CMake。 falsetrue

        *For more information see CMake*

    -   如果你遇到\"内部编译错误\"或者测试失败，参见下文。 falsetrue

        *If you get an "internal compiler error (ICE)" or test failures,
        see below.*

欲知入门指南关于配置和编译LLVM详细信息,请转到目录布局去了解源码树的布局
falsetrue

*Consult the Getting Started with LLVM section for detailed information
on configuring and compiling LLVM. Go to Directory Layout to learn about
the layout of the source code tree.*

要求 falsetrue(Requirements) 
----------------------------

在开始使用 LLVM 系统之前，请查看下面给出的要求。
通过提前了解您需要哪些硬件和软件，这可能会为您省去一些麻烦。 falsetrue

*Before you begin to use the LLVM system, review the requirements given
below. This may save you some trouble by knowing ahead of time what
hardware and software you will need.*

硬件 falsetrue(Hardware) 
------------------------

已经知道LLVM在可以在以下主机平台运行: falsetrue

*LLVM is known to work on the following host platforms:*

  **OS**         **Arch**          **Compilers**
  -------------- ----------------- ---------------
  Linux          x86$^{1}$         GCC, Clang
  Linux          amd64             GCC, Clang
  Linux          ARM               GCC, Clang
  Linux          Mips              GCC, Clang
  Linux          PowerPC           GCC, Clang
  Linux          SystemZ           GCC, Clang
  Solaris        V9 (Ultrasparc)   GCC
  FreeBSD        x86$^{1}$         GCC, Clang
  FreeBSD        amd64             GCC, Clang
  NetBSD         x86$^{1}$         GCC, Clang
  NetBSD         amd64             GCC, Clang
  macOS2         PowerPC           GCC
  macOS          x86               GCC, Clang
  Cygwin/Win32   x86$^{1,3}$       GCC
  Windows        x86$^{1}$         Visual Studio
  Windows x64    x86-64            Visual Studio

+----------------------------------------------------------------------+
| 注解 falsetrue                                                       |
|                                                                      |
| *note*                                                               |
+:=====================================================================+
| 1.  代码生成支持奔腾及以上处理器 falsetrue                           |
|                                                                      |
|     *Code generation supported for Pentium processors and up*        |
|                                                                      |
| 2.  代码生成仅支持 32位 ABI falsetrue                                |
|                                                                      |
|     *Code generation supported for 32-bit ABI only*                  |
|                                                                      |
| 3.  要在基于 Win32 的系统上使用 LLVM 模块，您可以使用                |
|     -DBUILD\_SHARED\_LIBS=On 配置 LLVM。 falsetrue                   |
|                                                                      |
|     *To use LLVM modules on Win32-based system, you may configure    |
|     LLVM with -DBUILD\_SHARED\_LIBS=On.*                             |
+----------------------------------------------------------------------+

The Second Chapter
==================

aaa [s2e]{acronym-label="s2e" acronym-form="singular+long"}
aaaaaaaaaaaaaaa [s2e]{acronym-label="s2e" acronym-form="singular+abbrv"}
aaaaaaaaaa [glsy]{acronym-label="glsy" acronym-form="singular+short"}

[^1]: [bitcode]{acronym-label="bitcode" acronym-form="singular+long"}

[^2]: 在git或者svn等版本管理软件中，一次提交就会形成一次修订

[^3]: [ninja]{acronym-label="ninja" acronym-form="singular+long"}
