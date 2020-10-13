---
date: 2020-09-15T22:30:49+08:00
description: "Circuit"
featured_image: ""
tags: []
title: "用电路做加法"
markup: mmark
---

# 使用EveryCircuit来做电路实验

## 任务0：验证非门

电路图如下：

![](/images/circuit/1.png)

输入为1：

![](/images/circuit/2.png)

输入为0：

![](/images/circuit/3.png)

真值表为：

|INPUT|OUTPUT|
|:---:|:----:|
|0|1|
|1|0|

## 任务1：建立一个简单的电路

电路图如下：

![](/images/circuit/4.png)

测试结果如下：

![](/images/circuit/5.png)
![](/images/circuit/6.png)
![](/images/circuit/7.png)
![](/images/circuit/8.png)

真值表如下：

|In A|In B|OUTPUT|
|:--:|:--:|:----:|
|0|0|0|
|0|1|0|
|1|0|0|
|1|1|1|

## 任务2：验证电路等价

电路图：
![](/images/circuit/9.png)

测试结果如下：
![](/images/circuit/10.png)
![](/images/circuit/11.png)
![](/images/circuit/12.png)
![](/images/circuit/13.png)
![](/images/circuit/14.png)
![](/images/circuit/15.png)
![](/images/circuit/16.png)
![](/images/circuit/17.png)

真值表如下：

|In A|In B|In C|Q1|Q2|
|:--:|:--:|:--:|:-:|:-:|
|0|0|0|0|0|
|0|0|1|0|0|
|0|1|0|0|0|
|0|1|1|0|0|
|1|0|0|0|0|
|1|0|1|1|1|
|1|1|0|1|1|
|1|1|1|1|1|

## 任务3：理解存储电路

电路图如下：

![](/images/circuit/18.png)

测试结果：
![](/images/circuit/19.png)
![](/images/circuit/20.png)
![](/images/circuit/21.png)
![](/images/circuit/22.png)
![](/images/circuit/23.png)

真值表为：

|Set|Reset|Q|~Q|
|:-:|:---:|:-:|:-:|
|1|1||0|1|
|0|1|1|0|
|1|1|1|0|
|1|0|0|1|
|1|1|0|1|

## 任务4：设计全加电路

1位全加器电路：
![](/images/circuit/24.png)

测试结果：
![](/images/circuit/25.png)
![](/images/circuit/26.png)
![](/images/circuit/27.png)
![](/images/circuit/28.png)
![](/images/circuit/29.png)
![](/images/circuit/30.png)
![](/images/circuit/31.png)
![](/images/circuit/32.png)

真值表为：

|A|B|C_in|Sum|C_out|
|:-:|:-:|:-:|:-:|:-:|
|0|0|0|0|0|
|0|0|1|1|0|
|0|1|0|1|0|
|0|1|1|0|1|
|1|0|0|1|0|
|1|0|1|0|1|
|1|1|0|0|1|
|1|1|1|1|1|

2位全加器电路：
![](/images/circuit/33.png)

测试结果：
![](/images/circuit/34.png)

这里测例太多，就不全部贴上来，图中第一个灯泡表示第一位，第二个灯泡表示第二位，第三个灯泡表示进位。图中显示的是11+11且进位为1的加法，结果是11且进位也为1