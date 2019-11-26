---
layout:     post					# 使用的布局（不需要改）
title:      Python实用代码：用Pandas获取excel或csv表格的一列数据		# 标题
subtitle:   pandas神器，方便解决各种表格问题    			#副标题
date:       2019-05-05
author:     Valuebai
header-img: img/20191126common.jpg 	#这篇文章标题背景图片
catalog: true
tags:
    - Python
---

在实际应用中，我有时候需要从数据库导出的csv表格获取大量用户的userId，用1,2,3,4,5,6,7, ... , 9999类似的格式展示出来，或者写到sql中，故有了这段代码的帮助，就能很快解决

## 实用代码


```python
# 大家默认as pd, 都成规范了
import pandas as pd


# 如果遇到报错UnicodeDecodeError: 'utf-8' codec can't decode
# 用三种不同 GB2312、gbk、ISO-8859-1 编码进行尝试
# temp = pd.read_csv('temp.csv', encoding='utf-8')
# temp = pd.read_csv('temp.csv', encoding='gbk')
temp = pd.read_csv('temp.csv', encoding='ISO-8859-1') # 将temp.csv改为要读取的

result = temp['@']  # 将@改为你的列名

res = [i for i in result] # 将pandas格式的数据转为列表

print(res)
```



【环境】win10_x64 + python3.6.5


【Me】https://github.com/Valuebai/


【参考】
1、出处：地址