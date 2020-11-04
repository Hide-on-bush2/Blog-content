---
date: 2020-09-15T11:00:59-04:00
description: "FL_Week6"
featured_image: ""
tags: []
title: "每周论文分享-6"
---

<<<<<<< HEAD
# Client Selection in Federated Learning: Convergence Analysis and Power-of-Choice Selection Strategies

## 背景

现有的关于联邦学习的收敛性证明已经囊括了Full Participation和Partical Participation的收敛性证明，但是这些工作都是默认选择到的设备都是无偏差的情况(unbiased)，这里的偏差指的是相同的全局模型在不同的设备上的不同表现。现有的联邦学习收敛性证明工作都是用一个差值上界来统一这些差异。这篇文章指出，如果在每一轮选择训练的设备的时候偏向于选择具有较高损失的设备，可以得到更快的收敛速度

## 论文贡献

* 提出了考虑到设备偏差的第一个收敛性证明
* 提出POWER-OF-CHOICE设备选择机制

## 收敛性分析

### 假设

完成这篇文章的收敛性分析需要四个假设：

前两个条件是$L-smooth条件$和$\mu-strong convex$条件：

![](/images/week6/1.png)

第三个假设的意思是，虽然每次选择到的设备有偏差，但是在设备本地训练的时候进行mini-batch默认是没有偏差的：

![](/images/week6/2.png)

第四个假设的意思是，随机梯度的期望平方范数是一致有界的：

![](/images/week6/3.png)

### 相关定义

这片论文的核心在于如何定义设备选择的偏差，文章给出了两个定义：

第一个是局部-全局偏差，是系统误差：

![](/images/week6/4.png)

第二个是选择偏差，是选择设备策略导致的偏差与局部-全局偏差之比的相对误差

![](/images/week6/5.png)

其中这里$\pi$代表的是选择训练设备的策略，第一个$w$代表的是决定选择策略的模型参数，它可以是当前的全局模型的参数。第二个$w'$可以理解为是在选择策略$\pi$下它与选择到的设备模型之间的偏差与它与全局模型之间的偏差的一个比值

然后将选择机制$\pi$下的选择偏差最小值定义为$\overline{\rho}$，将选择机制$\pi$下与全局最优模型的偏差最大值定义为$\widetilde{\rho}$

![](/images/week6/6.png)

### 收敛性结果

![](/images/week6/7.png)

从上述结果中我们可以看出：

* Large $\overline{\rho}$ and Fast Convergence：如果选择策略偏向于选择那些偏差大的设备，那么系统会更快达到收敛
* Non-vanishing Bias Term：式子中的第二项由选择策略决定，如果$\overline{\rho}$比较大的话，那么收敛边界会更加接近最优值

## 选择策略：POWER-OF-CHOICE

核心步骤就是选择训练设备的时候倾向于选择那些局部损失高的

![](/images/week6/8.png)

与我们熟悉的联邦学习过程的唯一不同便是，中央服务器从参与的设备中随机抽样出一部分候选设备之后，还要根据它们的局部损失来进行选拔，最后选择局部损失最大的几个设备来进行训练

## 实验

![](/images/week6/9.png)

他们通过实验证明了确实这种选择机制可以加快系统的收敛速度

## 结论

这篇论文提出的POWER-OF-CHOICE机制算是比较自然的想法，但是这篇论文给出了不同的选择机制下的收敛性分析方法，我觉得是一个很不错的亮点，另外就是委员会机制下的选择策略跟这篇文章的选择策略有着异曲同工之妙，委员会是倾向于选择那些损失函数比较低的，而POWER-OF-CHOICE选择的是损失函数比较高的，虽然两者的训练目的不同，但是我觉得这篇文章的收敛性分析方法用到委员会机制下，也是完全可以的
=======
# FedPAQ: A Communication-Efficient Federated Learning Method with Periodic Averaging and Quantization

## 论文的贡献

这篇论文的贡献主要是在传统的联邦学习方法上做了3个改进：
* 定期更新(Periodic averaging)
* 部分节点参与(Partical node participation)
* 低精度量化(Low-precision quantizer)

其中第一和第二点在很多其他的论文中也出现过，第三点也许是一个不错的切入点

## FedPAQ算法

![](https://i.loli.net/2020/10/18/PRyIghoHL7YNkuB.png)

这个算法与我们熟悉的联邦学习方法的不同点在于：在每次进行全局更新的时候不是直接将$X_{k, r}^{(i)} - X_k$上传，而是先对它们进行一个量化$Q(X_{k, r}^{(i)} - X_k)$，再将这个参数进行上传

这种量化的方法可以有很多种，这篇论文用的是一种低精度量化

### 低精度量化(Low-precision quantizer)

![](https://i.loli.net/2020/10/18/PrhKDB2IXMO1C4Q.png)

在这里，$x_i$表示的是$X$矩阵中的元素，简单地理解，这个映射关系是将矩阵元素的绝对值要么变成$\frac{l+1}{s}$，要么变成$\frac{l}{s}$，这个会根据元素的绝对值与矩阵的二范数$||x||$所组成的一个概率$\frac{|x_i|}{||X||}s - l$来决定

## 收敛性

这篇文章给出了这种训练方式的一个收敛上界：
![](https://i.loli.net/2020/10/19/Su1QtOdgwXmCPMF.png)

证明过程就不在这里放出来了

## 实验

### 设置1

![](https://i.loli.net/2020/10/19/V54vjztFSk8ugsB.png)

可以看出三点：
* 使用量化方法要比不使用量化方法更快地收敛
* 量化方式中的一个超参数$s$的值越大，收敛速度会越快
* 最后训练出来的模型性能并没有什么参数

### 设置2

![](https://i.loli.net/2020/10/19/qM69yLGtJAZC5be.png)

可以看到这篇论文介绍的方法FedPAQ比FedAvg和SDG方法的收敛速度更快

## 结论

这篇文章整体上的亮点不多，但我觉得提供了一种新的切入角度：考虑设备发送给服务器的参数，可以设计一些合适的量化方式，来达到我们的一些目的：减少上传参数的大小、加快收敛速度、得到更好的收敛上界，甚至可以使得联邦训练的方式更加公平

目前为止，我了解到的对传统联邦学习进行改进的角度有：
* 改变Average的方式
* 改变全局的损失函数
* 对设备上传的参数进行量化
* 服务器进行Sample的方式

>>>>>>> 129d6cd94e10cc13a91abf81e5a59bc9b4e024a9
