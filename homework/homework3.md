---
date: 2020-09-21T11:00:59-04:00
description: "The third homework"
featured_image: ""
tags: []
title: "Data Representation"
---

# H3-Data Representation

## 第一题-计算

* (2)`int8_t x = 0xd3 = 1101 0011`出现溢出错误
* (4)`int9_t z = y - x`出现溢出错误，因为`y`是负数，`x`是正数，那么`z`应该是负数，但最后的结果是`z = 0111 1010`是正数
* (7)`float x = 0.45`存在精度误差

## 第二题-名词解释

### Method of complements

In mathematics and computing, the method of complements is a technique to encode a symmetric range of positive and negative integers in a way that they can use the same algorithm (hardware) for addition throughout the whole range. For a given number of places half of the possible representations of numbers encode the positive numbers, the other half represents their respective additive inverses. The pairs of mutually additive inverse numbers are called complements. Thus subtraction of any number is implemented by adding its complement. Changing the sign of any number is encoded by generating its complement, which can be done by a very simple and efficient algorithm. 

在数学和计算中，补数方法是一种对正整数和负整数的对称范围进行编码的技术，使它们可以在整个范围内使用相同的算法（硬件）进行加法运算。 对于给定的位置数，可能的数字表示形式中的一半编码为正数，另一半表示其相应的加法逆。 成对的相互加反数称为补数。 因此，任何数字的减法都通过添加其补码来实现。 更改任何数字的符号都是通过生成其补码来编码的，这可以通过非常简单且有效的算法来完成。

### Byte

The byte is a unit of digital information that most commonly consists of eight bits. Historically, the byte was the number of bits used to encode a single character of text in a computer[1][2] and for this reason it is the smallest addressable unit of memory in many computer architectures. 

字节是数字信息的单位，通常由八位组成。 从历史上看，字节是计算机[1] [2]中用于编码文本的单个字符的位数，因此，它是许多计算机体系结构中最小的可寻址存储单元。

### Integer (Computer science)

In computer science, an integer is a datum of integral data type, a data type that represents some range of mathematical integers. Integral data types may be of different sizes and may or may not be allowed to contain negative values. Integers are commonly represented in a computer as a group of binary digits (bits). 

在计算机科学中，整数是整数数据类型的数据，该数据类型表示一定范围的数学整数。 整数数据类型可能具有不同的大小，并且可能允许也可能不允许包含负值。 整数通常在计算机中表示为一组二进制数字（位）。

### Floating point

In computing, floating-point arithmetic (FP) is arithmetic using formulaic representation of real numbers as an approximation to support a trade-off between range and precision. For this reason, floating-point computation is often found in systems which include very small and very large real numbers, which require fast processing times. A number is, in general, represented approximately to a fixed number of significant digits (the significand) and scaled using an exponent in some fixed base; the base for the scaling is normally two, ten, or sixteen. A number that can be represented exactly is of the following form:
$$
    significand \times base^{exponent}
$$

在计算中，浮点算术（FP）是使用实数的公式表示作为近似值以支持范围和精度之间折衷的算术。 因此，在包含非常小和非常大的实数的系统中经常会发现浮点计算，这需要快速的处理时间。 通常，数字大约代表固定数量的有效数字（有效数字），并使用某个固定基数中的指数进行缩放； 缩放的基数通常为2、10或16。 可以精确表示的数字具有以下形式：

$$
    significand \times base^{exponent}
$$

## 第三题-反码和补码

### 证明二进制数的负数（补码）等于它的反码加一

$$
    -X = 2^k - X = 2^k - 1 - X + 1 = (111....111 - X) + 1 
$$
在这里$k$可以任意大，则$(111...111 - X)$相当于$X$取反，则$X$的负数等于它的反码加一

### 用八进制描述$X = -017$

$$
    X = (11110001)_2 = (0361)_8
$$

## 第四题

### 用16进制描述$int8_t x = -0x1f$和$int y = 8$并说明后者的计算过程

$x = 0xE1$，然后$y$在前面补符号位，为$y = 0xFFE1$

### 用数学证明为什么可以这么算

因为负数在计算机中的存储方式是补码，转换为正数计算时需要取反加一，因为补$1$之后转换为正数都会变成0

## 第五题

### NaN是什么

IEEE 754 specifies a special value called "Not a Number" (NaN) to be returned as the result of certain "invalid" operations, such as 0/0, ∞×0, or sqrt(−1). In general, NaNs will be propagated i.e. most operations involving a NaN will result in a NaN, although functions that would give some defined result for any given floating-point value will do so for NaNs as well, e.g. NaN ^ 0 = 1. There are two kinds of NaNs: the default quiet NaNs and, optionally, signaling NaNs. A signaling NaN in any arithmetic operation (including numerical comparisons) will cause an "invalid operation" exception to be signaled.

IEEE 754指定一个特殊值“ Not a Number”（NaN）作为某些“无效”操作（例如$0/0$，$∞×0$或$sqrt（-1）$）的结果返回。 通常，将传播NaN，即，大多数涉及NaN的操作都将生成NaN，尽管对于任何给定的浮点值都会给出某些定义结果的函数也将对NaN进行传播。 $NaN ^ 0 =1$。有两种NaN：默认静默NaN和可选地发送信号NaN。 任何算术运算（包括数值比较）中的信号NaN都会导致发出“无效运算”异常的信号。
