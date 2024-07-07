# ics_nju
## Plan it
框架代码看完，了解基础设施，写PA1
CS61B，，   
## Read it
**[book](https://riscv.org/technical/specifications/)**


## PA1 --
作为一个最简单的真实计算机需要满足哪些条件:

* 结构上, TRM有存储器, 有PC, 有寄存器, 有加法器
* 工作方式上, TRM不断地重复以下过程: 从PC指示的存储器位置取出指令, 执行指令, 然后更新PC

**程序是个状态机**
从两个互补的视角来看待同一个程序:

* 一个是以代码(或指令序列)为表现形式的静态视角, 大家经常说的"写程序"/"看代码", 其实说的都是这个静态视角. 这个视角的一个好处是描述精简, 分支, 循环和函数调用的组合使得我们可以通过少量代码实现出很复杂的功能. 但这也可能会使得我们对程序行为的理解造成困难.
* 另一个是以状态机的状态转移为运行效果的动态视角, 它直接刻画了"程序在计算机上运行"的本质. 但这一视角的状态数量非常巨大, 程序代码中的所有循环和函数调用都以指令的粒度被完全展开, 使得我们难以掌握程序的整体语义. 但对于程序的局部行为, 尤其是从静态视角来看难以理解的行为, 状态机视角可以让我们清楚地了解相应的细节.

## RTFSC
[readit!](https://nju-projectn.github.io/ics-pa-gitbook/ics2022/1.3.html)

### [配置系统和项目构建](https://nju-projectn.github.io/ics-pa-gitbook/ics2022/1.3.html#%E9%85%8D%E7%BD%AE%E7%B3%BB%E7%BB%9F%E5%92%8C%E9%A1%B9%E7%9B%AE%E6%9E%84%E5%BB%BA)
* 配置系统kconfig
* 项目构建和Makefile

### [准备第一个客户程序](https://nju-projectn.github.io/ics-pa-gitbook/ics2022/1.3.html#%E5%87%86%E5%A4%87%E7%AC%AC%E4%B8%80%E4%B8%AA%E5%AE%A2%E6%88%B7%E7%A8%8B%E5%BA%8F)

### [运行第一个客户程序](https://nju-projectn.github.io/ics-pa-gitbook/ics2022/1.3.html#%E8%BF%90%E8%A1%8C%E7%AC%AC%E4%B8%80%E4%B8%AA%E5%AE%A2%E6%88%B7%E7%A8%8B%E5%BA%8F)
**Summary**
* 存储器是个在nemu/src/memory/paddr.c中定义的大数组
* PC和通用寄存器都在nemu/src/isa/$ISA/include/isa-def.h中的结构体中定义
* 加法器在... 嗯, 这部分框架代码有点复杂, 不过它并不影响我们对TRM的理解, 我们还是在PA2里面再介绍它吧
* TRM的工作方式通过cpu_exec()和exec_once()体现