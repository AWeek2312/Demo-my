## README

该项目主要为优化 intAbs工具,用于检测中断驱动程序可能存在的错误以及缺陷。

◼ 开发、运行环境为 linux操作系统（ ubuntu 14.04 ）

◼ 使用到的关键工具和技术： llvm， cmake，  抽象解释技术，主要通过 apron 和 z3 实现支配树

​		 IntAbs工具使用LLVM IR来表示程序的中间表示形式，并使用LLVM Passes来分析和优化程序，例如数据流分析、指针分析、内存管理等；使用LLVM JIT来动态编译程序，并使用LLVM CodeGen将LLVM IR转换为目标平台的机器码。

​		Apron是一个抽象解释工具，用于计算机程序的静态分析，其提供了一组数据结构和算法，可以用于计算程序中的抽象域（如多维区间、多项式等）和约束关系。

​		在IntAbs工具中，Apron是一个基于抽象解释理论的抽象域库，可以用于静态分析和程序验证。Apron库提供了一组抽象域类型和操作，包括线性抽象域、区间抽象域、多项式抽象域等，以及对应的加、减、乘、除等算法，使我们可以方便地实现各种抽象解释算法。简而言之，intabs工具主要利用Apron来分析程序的安全性和正确性。

# Building

这个程序是一个 LLVM opt pass. 使用 CMake 进行构建. 
S由于使用CMake，t所需的 LLVM 版本为 3.7.0

修改CMakeLists文件变量APRON_PREFIX为Apron安装的位置

假设您的LLVM库文件位于标准位置 (以下是更多相关信息), 只需要执行:

    mkdir build
    cd build
    cmake ../
    make

构建过程的结果是一个   .so 文件, 即  libworklistAI.so

如果你需要告诉LLVM你的CMake的位置, 您需要添加选项 -DLLVM_DIR，

之后执行cmake -DLLVM_DIR=.../

传递给的目录 LLVM_DIR 应该是LLVM CMake files  的目录

你也需要设定 -DZ3_INC 和 -DZ3_LIB 在 include 目录, 和你的Z3库文件路径


# 目录描述

- icbmc: 该目录为用于测试icbmc中的二进制文件的目录.

- src: 它包含主要实现(worlist-ai, utils, CMakeLists.txt) 和一个测试目录 (test)

- src/test: 它包含运行测试和基准程序的脚本文件。 此外，结果文件包含在每个目录中。

