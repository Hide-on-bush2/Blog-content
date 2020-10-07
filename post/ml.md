---
date: 2020-09-15T22:30:49+08:00
description: "Machine Learning"
featured_image: ""
tags: []
title: "ML-Perceptron Model"
markup: mmark
---

# 机器学习之朴素贝叶斯法
## 简介
朴素贝叶斯法是一种分类方法，主要是从训练集中根据统计规律学得分类方法。对于给定的输入x，利用贝叶斯定理求出后验概率最高的类别y

## 基本方法和推导
* Input:$x = (x^{(1)}, x^{(2)}, ..., x^{n})$，为输入变量的特征向量
* Output:类别$y\in \{c_1, c_2, ..., c_k\}$

定义$X$为输入空间上的随机变量，$Y$是输出空间中的随机变量，我们要求的便是$max_{k}(p(Y = c_k|X=x))$，具体的方法是求出每一个$P_k(Y=c_k|X=x)$，然后选择概率最大的那个分类。

这个概率是后验概率，没办法直接通过统计数据得来（[关于先验概率和后验概率](https://zhuanlan.zhihu.com/p/26464206)），所以需要利用到贝叶斯定理：
$$P(Y=c_k|X=x) = \frac{P(Y=c, X=x)}{P(X=x)} = \\\frac{P(X=x|Y=c_k)P(Y=c_k))}{\sum_kP(X=x|Y=c_k)P(Y=c_k)} \tag{1}$$
这里为了降低计算的复杂度做了一个合理的假设：输入空间中的特征都是不相关的，则：
$$P(X=x|Y=c_k) = P(X^{(1)} = x^{(1)}, X^{(2)} \\= x^{(2)}, ..., X^{(n)} = x^{(n)}|Y=c_k) \\= \Pi_{j=1}^nP(X^{(j)}=x^{(k)}|Y=c_k) \tag{2}$$
这也是为什么叫“朴素贝叶斯法”（naive bayes），是通过合理性假设简化了运算的缘故。
则将（2）式代入到（1）式可以得到：
$$P(Y=c_k|X=x) \\= \frac{P(Y=c_k)\Pi_{j}P(X^{(j)} \\= x^{(j)}|Y=c_k)}{\sum_kP(Y=c_k)\Pi_{j}P(X^{(j)} = x^{(j)}|Y=c_k)} \tag{3}$$
这里令$P^{'}_k = P(Y=c_k)\Pi_{j}P(X^{(j)} = x^{(j)}|Y=c_k)$，则（3）式可变为：
$$P(Y=c_k|X=x) = \frac{P^{'}_k}{\sum_kP^{'}_k}\tag{4}$$
很明（4）分母对于一个训练集来说是一个定植，那么我们的朴素贝叶斯分类器便可以表示为：
$$y = argmaxP^{'}_k \\= argmaxP(Y=c_k)\Pi_{j}P(X^{(j)} = x^{(j)}|Y=c_k)\tag{5}$$

## 参数估计
我们已经得到了朴素贝叶斯分类器的模型表示，接下来就是要求这个模型的参数。对于朴素贝叶斯法来说，需要学习的参数就是$P(Y=c_k)$和$P(X^{(j)} = x^{(j)}|Y=c_k)$，这里有两种参数估计的方法：

### 极大似然估计
估计方法：
* 先验概率$P(Y=c_k)$的极大似然估计是：$P(Y=c_k) = \frac{\sum_{i=1}^NI(y_i = c_k)}{N}$，意思是在N训练实例中找出类别为$c_k$的个数，$I(y_i = c_k)$是一个指示函数，是指$y_i = c_k$为真的话返回1，否则返回0
* 假设第$j$个特征$x^{(j)}$可能取值的集合为${a_{j1}, a_{j2}, ..., a_{jS_j}}$，条件概率$P(X^{(j)} = a_{jl}|Y=c_k)$的极大似然估计是$$P(X^{(j)} = a_{jl}|Y=c_k) = \frac{\sum_{i=1}^NI(x_i^{(j)}=a_{jl}, y_i=c_k)}{\sum_{i=1}^NI(y_i=c_k)}$$意思是从分类$c_k$中求得特征是$a_{jl}$的先验概率

### 贝叶斯估计
用极大似然估计会有一个缺点：会出现所要估计的概率值为0的情况。假如某一项的数据为0，则$P(X^{(i)} = x^{(i)}|Y=c_k) = 0$，则整个概率都为0，这使得模型的泛化效果不太好。
估计方法：
* 先验概率$P\_{\lambda}(Y=c_k) = \frac{\sum_{i=1}^NI(y_i = c_k) + \lambda}{N + K\lambda}$
* 条件概率
	$$
	P\_{\lambda}(X^{(j)} = a\_{jl}|Y=c\_k) \\= \frac{\sum\_{i=1}^NI(x\_i^{(j)} = a\_{jl}, y\_i = c\_k) + \lambda}{\sum\_{i=1}^NI(y\_i=c\_k) + S\_j\lambda}
	$$
意思是在随机变量各个取值的频数上赋予一个正数$\lambda$，当$\lambda = 0$时便是最大似然估计。当$\lambda=1$时，称为拉普拉斯平滑(Laplace smoothing)。对于任何$l = 1, 2, ..., S_j, k = 1, 2, ..., K$有：
$$P_{\lambda}(X^{(j)} = a_{jl}|Y=c_k)>0, \\\sum_{l=1}^{S_j}P(X^(j) = a_{jl}|Y=c_k) = 1$$

## 学习与分类算法
* 计算先验概率$P(Y=c_k)$和条件概率$P(X^{(j)} = a_{jl}|Y=c_k)$
* 对于输入的实例$x=(x^{(1)}, x^{(2)}, ..., x^{(n)})$，计算$$P(Y=c_k)\Pi_{j=1}^n(X^{(j)} = x^{(j)}|Y=c_k)$$
* 根据后验概率的大小确定实例的分类：$$y = argmax_{c_k}P(Y=c_k)\Pi_{j=1}^n(X^{(j)} = x^{(j)}|Y=c_k)$$


## 代码实现
```
class Bayes_classifier:
	def __init__(self, data_set, num_class, num_eigen):
		self.data_set = data_set
		self.num_node = data_set.shape[0]
		self.num_class = num_class
		self.num_eigen = num_eigen
		self.prior_probability = np.zeros(self.num_class)
		self.conditional_probability = np.zeros((self.num_class, self.num_eigen, 3))

	def learn(self):
		for node in self.data_set:
			t_class = node[self.num_eigen]
			self.prior_probability[t_class] += 1
		self.prior_probability = self.prior_probability / self.num_node

		for c in range(self.num_class):
			for node in self.data_set:
				if node[self.num_eigen] == c:
					for j in range(self.num_eigen):
						self.conditional_probability[node[self.num_eigen], j, node[j]] += 1

			self.conditional_probability[c, :, :] = self.conditional_probability[c, :, :] / (self.prior_probability[c] * self.num_node)

	def classify(self, node):
		l = []
		for c in range(self.num_class):
			p_ck = self.prior_probability[c]
			p_con = 1
			for i in range(self.num_eigen):
				p_con *= self.conditional_probability[c, i, node[i]]
			l.append(p_ck * p_con)
		idx = np.argsort(l)
		return idx[len(idx)-1]

	def get_model(self):
		return self.prior_probability, self.conditional_probability

```
[github](https://github.com/Hide-on-bush2/machine_learning/tree/master/naive_bayes)