---
date: 2020-09-21T11:00:59-04:00
description: "The 7th homework"
featured_image: ""
tags: []
title: "Programming Barely"
---

# H7-Programming Barely

## Program with machine language according to the following c

```
int_8 a = 1
int_8 c = a + 3
```

### Write your assembly code & machine code

汇编(x86)：
```
a db 0
c db 0
mov al, 1
mov a, al 
add al, 3
mov c, al 
```

机器语言：
```
00010100 00000001
00000101 10000001
00010100 10000001
00010000 00000011
00000100 10000002
00001111 00000000
```

### Explain machine code execution with the fetch-decode-execute cycle

* 取指令：首先将PC寄存器的内容装入MAR，并且将PC寄存器的值+1(因为我们完成当前这一条指令之后还需要继续进行下一条，就是通过这种方式来实现指令的顺序执行的)。然后将地址指向的内容装入MDR，最后控制单元将MDR中的内容送入IR，至此，我们完成了指令的读取
* 译码：在这个步骤中，指令由处理器解码。如果指令需要，处理器将获得任何操作数。例如，指令MOV AX, 0。将值0存储在Ax寄存器中。在执行指令之前，处理器将从内存中的下一个位置获取常数值0
* 执行：在最后一个阶段，处理器执行指令，它在寄存器AX中存储0。
处理器执行指令MOV AX, 0。最后，它调整指令指针指向存储在地址0102的下一条要执行的指令

### Explain functions about IR, PC, ACC registers in a CPU

* IR：指令寄存器，存放指令
* PC：程序计数器，指示下一条要执行的指令的地址
* ACC：累加器，在CPU执行某种运算前，两个操作数中的一个通常应放在累加器A中，运算完成后累加器A中便可得到运算结果

### Explain physical meaning about vars a & c in a machine

一个变量a或者c只是一个符号，代表着在一片内存地址。我们对变量进行操作，实际上是对它代表的这片内存地址进行重写，复制内容等操作

## 简答题

### What are stored in memory

代码和数据

### Can a data or a instruction stored in the same place

在有些OS里面可以，有些不可以

### Explain Instruction Format with example instructions

MIPS指令：
![](https://tva1.sinaimg.cn/large/007S8ZIlgy1gjokel171yj30yo08ajs7.jpg)

## 名词解释

### 汇编语言（Assembly Language）

In computer programming, assembly language (or assembler language),[1] often abbreviated asm, is any low-level programming language in which there is a very strong correspondence between the instructions in the language and the architecture's machine code instructions.[2] Because assembly depends on the machine code instructions, every assembly language is designed for exactly one specific computer architecture. Assembly language may also be called symbolic machine code.[3][4]

### 编译（Compiler）

In computing, a compiler is a computer program that translates computer code written in one programming language (the source language) into another language (the target language). The name "compiler" is primarily used for programs that translate source code from a high-level programming language to a lower level language (e.g., assembly language, object code, or machine code) to create an executable program.[1][2]:p1

### 命令式语言（Imperative programming）

In computer science, imperative programming is a programming paradigm that uses statements that change a program's state. In much the same way that the imperative mood in natural languages expresses commands, an imperative program consists of commands for the computer to perform. Imperative programming focuses on describing how a program operates.

### 函数编程语言（Functional programming）

In computer science, functional programming is a programming paradigm where programs are constructed by applying and composing functions. It is a declarative programming paradigm in which function definitions are trees of expressions that each return a value, rather than a sequence of imperative statements which change the state of the program.

### 过程式编程（Procedural programming）

Procedural programming is a programming paradigm, derived from structured programming,[citation needed] based on the concept of the procedure call. Procedures (a type of routine or subroutine) simply contain a series of computational steps to be carried out. Any given procedure might be called at any point during a program's execution, including by other procedures or itself. The first major procedural programming languages appeared circa 1957–1964, including Fortran, ALGOL, COBOL, PL/I and BASIC.[1] Pascal and C were published circa 1970–1972.






