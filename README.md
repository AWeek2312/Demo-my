![image](https://github.com/AWeek2312/Demo-my/assets/103011325/cdf82efd-e846-4666-9050-0e7f9bf913e1)![image](https://github.com/AWeek2312/Demo-my/assets/103011325/0fa375f1-2d60-4db1-8459-7465624f87ee)优化 intAbs工具,用于检测中断驱动程序可能存在的错误以及缺陷

◼ 开发、运行环境为 linux操作系统（ ubuntu 14.04 ）

◼ 使用到的关键工具和技术： llvm， cmake，  抽象解释技术，主要通过 apron 和 z3 实现支配树

    IntAbs工具使用LLVM IR来表示程序的中间表示形式，并使用LLVM Passes来分析和优化程序，例如数据流分析、指针分析、内存管理等；使用LLVM JIT来动态编译程序，并使用LLVM CodeGen将LLVM IR转换为目标平台的机器码。

    Apron是一个抽象解释工具，用于计算机程序的静态分析，其提供了一组数据结构和算法，可以用于计算程序中的抽象域（如多维区间、多项式等）和约束关系。在IntAbs工具中，Apron是一个基于抽象解释理论的抽象域库，可以用于静态分析和程序验证。Apron库提供了一组抽象域类型和操作，包括线性抽象域、区间抽象域、多项式抽象域等，以及对应的加、减、乘、除等算法，使我们可以方便地实现各种抽象解释算法。简而言之，intabs工具主要利用Apron来分析程序的安全性和正确性。

    build方法
    mkdir build
cd build
cmake ../
make
   其余具体细则在各个文件夹下的README文件可见。
   

