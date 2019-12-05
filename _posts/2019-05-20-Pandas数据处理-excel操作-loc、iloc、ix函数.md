---
layout:     post					# 使用的布局（不需要改）
title:      Pandas数据处理-excel操作-loc、iloc、ix函数		# 标题
subtitle:   loc、iloc在数据处理，特征工程中经常用到    			#副标题
date:       2019-05-20
author:     Valuebai
header-img: img/bg_common.jpg 	#这篇文章标题背景图片
catalog: true
tags:
    - Python
---


loc中的数据是列名，是字符串，所以前后都要取；iloc中数据是int整型，所以是Python默认的前闭后开

**当用行号索引的时候, 尽量用 iloc 来进行索引; 而用标签索引的时候用 loc ,  ix 尽量别用。**

## 一、loc函数
构建数据集df


```python

import pandas as pd  
df = pd.DataFrame([  
            ['green', 'M', 10.1, 'class1'],   
            ['red', 'L', 13.5, 'class2'],   
            ['blue', 'XL', 15.3, 'class1']])  
print (df)    
# 数据集为以下内容，所有操作均对df进行
       0   1     2       3
0  green   M  10.1  class1
1    red   L  13.5  class2
2   blue  XL  15.3  class1
```

loc函数主要通过行标签索引行数据，划重点，标签！标签！标签！
loc[1] 选择行标签是1的（从0、1、2、3这几个行标签中）

```python
In[1]:    df.loc[1]
Out[1]: 
0       red
1         L
2      13.5
3    class2
```

loc[0:1] 和 loc[0,1]的区别，其实最重要的是loc[0:1]和iloc[0:1]

```python
In[10]: df.loc[0:1]  #取第一和第二行，loc[]中的数字其实是行索引，所以算是前闭加后闭
Out[10]: 
       0  1     2       3
0  green  M  10.1  class1
1    red  L  13.5  class2

In[12]:   df.iloc[0:1]
Out[12]: 
       0  1     2       3
0  green  M  10.1  class1

In[11]:   df.loc[0,1]
Out[11]: 'M'
```

索引某一列数据，loc[:,0:1]，还是标签，注意，如果列标签是个字符，比如'a'，loc['a']是不行的，必须为loc[:，'a']。
但如果行标签是'a',选取这一行，用loc['a']是可以的。

```python

n[13]: df.loc[:,0:1]
Out[13]: 
       0   1
0  green   M
1    red   L
2   blue  XL
```


## 二、iloc函数
iloc 主要是通过行号获取行数据，划重点，序号！序号！序号！
iloc[0:1]，由于Python默认是前闭后开，所以，这个选择的只有第一行！

```python
In[12]:   df.iloc[0:1]
Out[12]: 
       0  1     2       3
0  green  M  10.1  class1
```

## 三、ix函数
ix——结合前两种的混合索引，即可以是行序号，也可以是行标签。

另，一些筛选操作
如选择prize>10(prize为一个标签)的，即 df.loc[df.prize>10]
还有&并或等操作





　Pandas是作为Python数据分析著名的工具包，提供了多种数据选取的方法，方便实用。本文主要介绍Pandas的几种数据选取的方法。

　　Pandas中，数据主要保存为Dataframe和Series是数据结构，这两种数据结构数据选取的方式基本一致，本文主要以Dataframe为例进行介绍。

　　在Dataframe中选取数据大抵包括3中情况：

　　1）行（列）选取（单维度选取）：df[]。这种情况一次只能选取行或者列，即一次选取中，只能为行或者列设置筛选条件（只能为一个维度设置筛选条件）。

　　2）区域选取（多维选取）：df.loc[]，df.iloc[]，df.ix[]。这种方式可以同时为多个维度设置筛选条件。

　　3）单元格选取（点选取）：df.at[]，df.iat[]。准确定位一个单元格。

　　接下来，我们以下面的数据为例，分别通过实例介绍这三种情况。

 



【Me】https://github.com/Valuebai/

【参考】
1、出处：地址