---
layout:     post					# 使用的布局（不需要改）
title:      Python代码实现：softmax函数		# 标题
subtitle:   一种归一化的方式，将数据转换到[0, 1]之间，将数据变得更加平均    			#副标题
date:       2019-05-05
author:     Valuebai
header-img: img/bg_common.jpg 	#这篇文章标题背景图片
catalog: true
tags:
    - Python
---

## 神经网络的softmax如何理解：

 softmax是一种数据归一化的方式，可以将数据转换到[0,1]之间的概率分布；也可以将数据变得更加平均，使反向传播初始最大最小的数据的影响变小；softmax常用来解决多分类问题。

- softmax在标准化之前对数据进行了指数转换
- softmax函数可以将数据变得更加平均
- softmax的优势：可以处理output中同时存在正负数的情况，数据间评分的概率分布不会在计算时抵消

## softmax的学习及实现

softmax函数将任意n维的实值向量转换为取值范围在(0,1)之间的n维实值向量，并且总和为1。
例如：向量softmax([1.0, 2.0, 3.0]) ------> [0.09003057, 0.24472847, 0.66524096]

性质：

1. 因为softmax是单调递增函数，因此不改变原始数据的大小顺序。
2. 将原始输入映射到(0,1)区间，并且总和为1，常用于表征概率。
3. softmax(x) = softmax(x+c), 这个性质用于保证数值的稳定性。

softmax的实现及数值稳定性

```md
import numpy as np


def softmax(x):
    """Compute the softmax of vector x."""
    exp_x = np.exp(x)
    softmax_x = exp_x / np.sum(exp_x)
    return softmax_x


# 让我们来测试一下上面的代码：

print(softmax([1, 2, 3]))
# result: array([0.09003057, 0.24472847, 0.66524096])

# 但是，当我们尝试输入一个比较大的数值向量时，就会出错：

print(softmax([1000, 2000, 3000]))
# result: array([nan, nan, nan])

这是由numpy中的浮点型数值范围限制所导致的。
当输入一个较大的数值时，sofmax函数将会超出限制，导致出错。
为了解决这一问题，这时我们就能用到sofmax的第三个性质，
即：softmax(x) = softmax(x+c)，

一般在实际运用中，通常设定c = - max(x)。
接下来，我们重新定义softmax函数：

# 写成函数
def softmax(vec):
    """Compute the softmax in a numerically stable way."""
    vec = vec - np.max(vec)  # softmax(x) = softmax(x+c)
    exp_x = np.exp(vec)
    softmax_x = exp_x / np.sum(exp_x)
    return softmax_x


print(softmax([3.0, 1.0, 0.2]))
```

## 另外2种用numpy实现softmax

```python
import numpy as np 
y1, y2, y3 = 3.0, 1.0, 0.2
logits = np.array([y1, y2, y3])
softmax = np.exp(logits) / np.sum(np.exp(logits))
print(softmax)

# 或者结合lambda
import numpy as np

z = [3.0, 1.0, 0.2]

# 输出阵列
softmax = lambda x: np.exp(x) / np.sum(np.exp(x), axis=0)
print(softmax(z))


# softmax(x) = softmax(x +c)




```


## 写出crossentropy的函数表达式，说明该函数的作用和意义
回答：交叉熵代表两个概率分布之间的差异性。在分类时，一般用Softmax来预测一个样本落在每一类中的概率分布，用one-hot编码代表真实的分类（严格某类为1，其余全是0的概率分布），这样两者的交叉熵就可以作为损失函数，用来衡量预测分类与真实分类label之间的差异大小，在神经网络中通过反向传播不断将其缩小，预测值也就逐渐接近真实值。


【环境】win10_x64 + python3.6.5


【Me】https://github.com/Valuebai/


【参考】
1、出处：地址