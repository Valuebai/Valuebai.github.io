---
layout:     post					# 使用的布局（不需要改）
title:      Temp-临时文件，不展示出来		# 标题
subtitle:   Temp-临时文件，不展示出来    			#副标题
date:       2009-09-09
author:     Valuebai
header-img: img/bg_common.jpg 	#这篇文章标题背景图片
catalog: true
tags:
    - 
---



## Hello Mr.Lucky


## 过拟合

什么是过拟合，就是在训练集的结果很好，但是在测试集的表现很差（训练时准确率大于测试集准确率的现象）
解决方法：
（1）在神经网络中，如果参数过多，就容易出现过拟合，可以通过简化模型来解决。比如GRU对于LSTM来说就简化了网络结构，减少了参数，因而可以减轻过拟合。
（2）在训练过程中随机丢弃一部分数据，采用dropout的方法也可避免神经网络过度学习训练集的特征。
（3）在每一轮epoch结束后测一下测试集的准确率，如果accuracy不再提升，则停止训练（early stopping）。
（4）在loss函数上附加一个正则化项，可以使得模型参数变得稀疏，从而减轻过拟合。



## 用numpy实现softmax

```python
import numpy as np 
y1, y2, y3 = 3.0, 1.0, 0.2
logits = np.array([y1, y2, y3])
softmax = np.exp(logits) / np.sum(np.exp(logits))
print(softmax)

# 或者结合lambda

# 使用Numpy
import numpy as np

z = [3.0, 1.0, 0.2]

# 输出阵列
softmax = lambda x: np.exp(x) / np.sum(np.exp(x), axis=0)
print(softmax(z))


# softmax(x) = softmax(x +c)


# 写成函数
def softmax(vec):
    """Compute the softmax in a numerically stable way."""
    vec = vec - np.max(vec)  # softmax(x) = softmax(x+c)
    exp_x = np.exp(vec)
    softmax_x = exp_x / np.sum(exp_x)
    return softmax_x


print(softmax([3.0, 1.0, 0.2]))

```



注意点：
1、复制图片过来，要先等一会！要先等一会！！要先等一会！！！让小书匠保存成github的图床图片，先不要保存到github上的文章，不然图片获取用的是：(./images/1561707358500.png)，会导致复制到CSDN上无法使用
2、复制图片过来先保存一遍，不然容易出现(./images/1561707358500.png)



【小书匠 常用快捷键及设置】https://www.cnblogs.com/wushuaishuai/p/9308094.html



【环境】win10_x64 + python3.6.5


【Me】https://github.com/Valuebai/


【参考】
1、出处：地址