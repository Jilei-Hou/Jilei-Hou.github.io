---
title: Conv
date: 2022-07-09 14:26:09
categories:
  - 模型量化
  - 算子
tags:
  - Conv
  - ONNX
---





卷积作为深度学习的基础概念，入门深度学习，不可能绕过卷积。但你真的了解各种卷积吗？

2D / 3D / 1x1 /转置/扩张（Atrous）/空间可分/深度可分/平展/分组/混洗分组卷积

# 什么卷积？

![](C:\Users\HJL\Desktop\Hexo\source\img\Conv\R-C.gif)



卷积的过程如上图，简单来说，卷积其实就是通过某个卷积核不断地与输入进行内积，得到输出。

其中涉及到很多其他问题：

1. 卷积核（kernel）：用于对输入进行共享权值的遍历，上图中每次阴影部分3*3都会与卷积核内积
2. 步长（stride）：即每次内积后移动的幅度
3. 填充（padding）：为了保持输出的尺寸，需要在输入图像进行上填充，使用padding后的输出 = padding前的输出+2*padding

## 输入输出和卷积核、步长、填充间的关系

假设输入为C\*H\*W，padding = p，kernel size为k\*k，步长为s

输出：C\*H<sub>out</sub>\*W<sub>out</sub>

每个维度单独卷积，维度不会变，还是C

H<sub>out</sub> = (H + 2*p - k)/s + 1

W<sub>out</sub> = (W + 2*p - k)/s + 1

# 参考资料

[卷积有多少种？一文读懂深度学习中的各种卷积 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/57575810)
