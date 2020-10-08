---
date: 2020-09-15T11:00:59-04:00
description: "FL_Week3"
featured_image: ""
tags: []
title: "每周论文分享-3"
---

# Blockchain-Federated-Learning and Deep Learning Models for COVID-19 detection using CT Imaging

这是一篇很有意思的论文，讲如何利用胶囊网络/联邦学习/区块链来帮助医生诊断新冠患者

## 背景

一般来说，对一名疑似患者进行诊断是否真正患有新冠肺炎需要耗费大量的时间和医疗费用。在这种情况下，用CT图片来训练一个AI模型，然后用该模型来进行诊断则显得廉价得多。但是数据的收集是一个主要的问题，不同的医疗机构之间存在着严重的“数据孤岛“问题，将所有的CT图片集中在一个医疗机构显得不太现实，也很难实现。这时候利用联邦学习可以在各个医疗机构不需要暴露它们的数据的前提下训练出一个令人满意的AI模型，来提升诊断的准确率和降低诊断的成本

## 核心思想

AI模型用的是胶囊网络，用联邦学习保证数据的隐私性，将每一次全局更新看成是一项交易，共识算法用的是工作量证明(PoW)

## 胶囊网络

使用CapsNet而不是CNN的原因是前者的效果更好，并且能达到举一反三的效果

![](https://tva1.sinaimg.cn/large/007S8ZIlgy1gj31i688zyj31i40fs15a.jpg)

它和一般的ANN(Artificail Neural Network)也非常像，只不过将映射的方式和激活函数等换了一下：

![](https://tva1.sinaimg.cn/large/007S8ZIlgy1gj31ld4f5tj30pw0g4wgu.jpg)

## 联邦学习

使用的是一般的联邦学习架构：

![](https://tva1.sinaimg.cn/large/007S8ZIlgy1gj31n1bsanj30rc0imdlw.jpg)

在这篇论文中将联邦学习与区块链进行结合，训练方法为：

![](https://tva1.sinaimg.cn/large/007S8ZIlgy1gj33epfjv2j30sw11sgqm.jpg)

## 区块链

区块链还可以用来进行数据共享。由于将患者的数据放到区块链上花销过于巨大，因此将数据保存在医疗机构中，区块链用来帮助检索这些数据。当一个医院提供数据时，它会在区块链中发起一项交易。每一个数据共享和检索过程的交易过程如下图所示：

![](https://tva1.sinaimg.cn/large/007S8ZIlgy1gj333j12m3j30qo0p20vx.jpg)

多家医院可以协作共享数据并训练模型以预测最佳的结果，并且这种数据共享和数据检索的过程可以通过区块链的技术来保证数据的隐私性，数据共享的过程如下图所示：

![](https://tva1.sinaimg.cn/large/007S8ZIlgy1gj33bulz9hj30ru0v07a5.jpg)

## 总结

个人觉得这篇文章非常有意思，也非常地有意义。这篇文章提供了一种将联邦学习和区块链技术结合起来的思路（这件事并不是很简单，因为联邦学习需要一个中心服务器，而区块链是去中心化的）。此外，我觉得新冠诊断这个场景与联邦学习非常契合，在医疗这方面联邦学习确实有着广泛的应用。