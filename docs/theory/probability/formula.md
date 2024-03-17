---
title: Formula
tags: [formula]
sidebar_label: Formula
sidebar_position: 2
---

# 概率公式

## 期望和方差

### 数学期望

$$
\begin{align}
{E}[X]=\sum _{i}x_{i}p(x_i) \\
{E}[X]=\int _{-\infty }^{\infty }xf(x)\,\mathrm{d}x
\end{align}
$$

### 方差

$$
\begin{align}
{Var}(X)&=E[{(X-E[X])}^2] \\
~&=E[X^2-2XE[X]+E[X]^2] \nonumber \\
~&=E[X^2]-2E[X]E[X]+E[X]^2 \nonumber \\
~&=E[X]^2-E[X^2]
\end{align}
$$

## 估计

### 最大似然估计（MLE）

优化 $\theta$ 使得 $P(X|\theta)$ 最大，也就是在最优 $\theta_{MLE}$ 参数下， $X$ 出现的概率最大。

$$
\begin{align}
L(\theta) = P(X|\theta) \\
\end{align}
$$

$$
\begin{align}
\theta_{MLE}&=\argmax _\theta L(\theta) \nonumber \\
~&=\argmax _\theta \log{L(\theta)} \nonumber \\
~&=\argmax _\theta \sum _{i=1}^n\log{P(x_i|\theta)}
\end{align}
$$

### 最大后验估计

我们有先验知识 $P(\theta)$ ，并且已知 $X$ ，然后来优化 $\theta$ 使得 $P(\theta|X)$ 最大。

$$
\begin{align}
\theta_{MAP}&=\argmax _\theta P(\theta|X) \\
~&=\argmax _\theta \frac{P(X|\theta)P(\theta)}{P(X)} \nonumber \\
~&=\argmax _\theta P(X|\theta)P(\theta) \nonumber \\
~&=\argmax _\theta P(\theta) \prod _i P(x_i|\theta) \nonumber \\
~&=\argmax _\theta (\log{P(\theta)} + \sum _i \log{P(x_i|\theta)}) \\
\end{align}
$$

MAP中两个值得注意的地方：

1. 若假设先验分布 $\theta$ 服从均匀分布，则 $P(\theta)$ 为常数。此时 $\theta_{MLE}=\theta_{MAP}$ ，即 MAP 等价于 MLE 。
2. 从机器学习的角度来看，MAP 可以看作是 MLE 增加了一个关于参数的先验分布的正则项 $\log{P(\theta)}$。


## 熵

### 信息量

概率越大的事件，其信息量越少，反之，概率越小的事件，信息量越大。

$$
\begin{align}
I(x)=-\log{p(x)}
\end{align}
$$

### 信息熵

$$
\begin{align}
H_p(X)=-\sum_x p(x)\log p(x) \\
H_p(X)=-\int p(x)\log p(x)\mathrm{d}x
\end{align}
$$

### 交叉熵

带着某个主观认知去接触某个客观随机现象的时候，会产生的平均惊喜度。

$$
\begin{align}
H_{p_o,p_s}(X)=-\int p_o(x)\log{p_s(x)}
\end{align}
$$

$p_o(x)$是客观（objective）上$x$会发生的概率，$p_s(x)$是客观（subjective）上$x$会发生的概率。

### 相对熵（KL散度）

$$
\begin{align}
D_{KL}(p_o||p_s)&=H_{p_o,p_s}(X)-H_{p_o}(X) \\
~&=-\int p_o(x)\log{p_s(x)} - (-\int p_o(x)\log{p_o(x)}) \nonumber \\
~&=\int p_o(x)\log\frac{{p_o(x)}}{{p_s(x)}} \nonumber
\end{align}
$$

# 参考资料

* [一篇文章讲清楚交叉熵和KL散度 - 康斯坦丁的文章 - 知乎](https://zhuanlan.zhihu.com/p/573385147)
* [机器学习方法—统计：MLE与MAP - 苗思奇的文章 - 知乎](https://zhuanlan.zhihu.com/p/345024301)
