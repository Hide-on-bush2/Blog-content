---
date: 2020-09-21T11:00:59-04:00
description: "The 5th homework"
featured_image: ""
tags: []
title: "Gates and Circuits"
---

# H5-Gates and Circuits

## 回答问题

* Give the three representations of an AND gate and say in your words what AND means
  * 布尔表达式：$X = AB$
  * 真值表：
  
    |A|B|X|
    |:-:|:-:|:-:|
    |0|0|0|
    |0|1|0|
    |1|0|0|
    |1|1|1|
  * 逻辑图：
    ![](https://tva1.sinaimg.cn/large/007S8ZIlgy1gjg0niyz3wj3076042a9x.jpg)
* Give the three representations of an XOR gate and say in your words what XOR means
  * 布尔表达式：$X = A \bigoplus B$
  * 真值表
    |A|B|X|
    |:-:|:-:|:-:|
    |0|0|0|
    |0|1|1|
    |1|0|1|
    |1|1|0|
  * 逻辑图：
    ![](https://tva1.sinaimg.cn/large/007S8ZIlgy1gjg0s73d4lj3078043jrc.jpg)
* Draw a circuit diagram corresponding to the following Boolean expression: $(A + B)(B + C)$
  * ![](https://tva1.sinaimg.cn/large/007S8ZIlgy1gjg0tgu0zij30ej0a80sz.jpg)
* Show the behavior of the following circuit with a truth table
  * |A|B|$\overline{A}\bigoplus (AB)$|
    |:-:|:-:|:-:|
    |0|0|1|
    |0|1|1|
    |1|0|0|
    |1|1|1|
* What is circuit equivalence? Use truth table to prove the following formula.
$(AB)’ = A’ + B’$
    * |A|B|$\overline{(AB)}$|$\overline{A} + \overline{B}$|
      |:-:|:-:|:-:|:-:|
      |0|0|1|1|
      |0|1|1|1|
      |1|0|1|1|
      |1|1|0|0|
* There are eight 1bit full adder integrated circuits. Combine them to 8bit adder circuit using the following box diagram.
  * ![](https://tva1.sinaimg.cn/large/007S8ZIlgy1gjg130wbi1j30t30jygm5.jpg)

* Logical binary operations can be used to modify bit pattern. Such as (X8X7X6X5X4X3X2X1)2 and (00001111)2 = (0000X4X3X2X1)2
We called that (00001111)2 is a mask which only makes low 4 bits to work.
Fill the follow expression
    * (X8X7X6X5X4X3X2X1)2 or (00001111)2 = (X8X7X6X50000)2
    * (X8X7X6X5X4X3X2X1)2 xor (00001111)2 = (X8X7X6X5X4’X3’X2’X1’)2
    * ((X8X7X6X5X4X3X2X1)2 and (11110000)2 ) or (not (X8X7X6X5X4X3X2X1)2 and (00001111)2) = (00001111)2

## 名词解释

### Logic gate

A logic gate is an idealized or physical electronic device implementing a Boolean function, a logical operation performed on one or more binary inputs that produces a single binary output. Depending on the context, the term may refer to an ideal logic gate, one that has for instance zero rise time and unlimited fan-out, or it may refer to a non-ideal physical device[1] (see Ideal and real op-amps for comparison).

逻辑门是在集成电路上的基本组件。简单的逻辑门可由晶体管组成。这些晶体管的组合可以使代表两种信号的高低电平在通过它们之后产生高电平或者低电平的信号。高、低电平可以分别代表逻辑上的“真”与“假”或二进制当中的1和0，从而实现逻辑运算。常见的逻辑门包括“与”闸，“或”闸，“非”闸，“异或”闸（也称：异或）等等

### Boolean algebra

In mathematics and mathematical logic, Boolean algebra is the branch of algebra in which the values of the variables are the truth values true and false, usually denoted 1 and 0, respectively.[1] Instead of elementary algebra, where the values of the variables are numbers and the prime operations are addition and multiplication, the main operations of Boolean algebra are the conjunction (and) denoted as ∧, the disjunction (or) denoted as ∨, and the negation (not) denoted as ¬. It is thus a formalism for describing logical operations, in the same way that elementary algebra describes numerical operations.

在抽象代数中，布尔代数（英语：Boolean algebra）是捕获了集合运算和逻辑运算二者的根本性质的一个代数结构（就是说一组元素和服从定义的公理的在这些元素上运算）。特别是，它处理集合运算交集、并集、补集；和逻辑运算与、或、非。

### Filp-flop

#### 中文解释

触发器

#### How many bits information does a SR latch store?

One bit



