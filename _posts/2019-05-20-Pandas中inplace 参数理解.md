---
layout:     post					# 使用的布局（不需要改）
title:      Pandas中inplace 参数理解		# 标题
subtitle:   inplace的取值只有False和True，如给定0或1，会报如下错误    			#副标题
date:       2019-05-20
author:     Valuebai
header-img: img/bg_common.jpg 	#这篇文章标题背景图片
catalog: true
tags:
    - Python
---



pandas 中 inplace 参数在很多函数中都会有，它的作用是：是否在原对象基础上进行修改

​ inplace = True：不创建新的对象，直接对原始对象进行修改；

​ inplace = False：对数据进行修改，创建并返回新的对象承载其修改结果。

默认是False，即创建新的对象进行修改，原对象不变，和深复制和浅复制有些类似。

例：

inplace=True情况：
```python
import pandas as pd
import numpy as np
df=pd.DataFrame(np.random.randn(4,3),columns=["A","B","C"])
data=df.drop(["A"],axis=1,inplace=True)
print(df)
print(data)

>> 
          B         C
0  0.472730 -0.626685
1  0.065358  0.031326
2 -0.318582  1.123308
3 -0.097687  0.018820
None
```

inplace=False情况：

```python
df=pd.DataFrame(np.random.randn(4,3),columns=["A","B","C"])
data=df.drop(["A"],axis=1,inplace=False)
print(df)
print(data)

>>
         A         B         C
0 -0.731578  0.226483  0.986656
1  0.075936  1.622889  1.767967
2 -1.477780 -0.164374 -1.025555
3 -0.645208 -0.847264 -0.744622
         B         C
0  0.226483  0.986656
1  1.622889  1.767967
2 -0.164374 -1.025555
3 -0.847264 -0.744622

```
另外，要注意的是，inplace的取值只有False和True，如给定0或1，会报如下错误：
```python
ValueError: For argument "inplace" expected type bool, received type int.
```

【Me】https://github.com/Valuebai/

【参考】
1、出处：地址