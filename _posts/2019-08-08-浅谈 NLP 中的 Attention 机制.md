---
layout:     post					# 使用的布局（不需要改）
title:      浅谈 NLP 中的 Attention 机制		# 标题
subtitle:   Google 某种程度上体现了“大道至简”的理念，的确是 NLP 中不可多得的精品。    			#副标题
date:       2019-08-08
author:     Valuebai
header-img: img/bg_article_common.jpg 	#这篇文章标题背景图片
catalog: true
tags:
    - 深度学习
    - 自然语言处理
---


> 【原文地址】：https://xiaosheng.me/2018/01/13/article121/


## 背景

2017 年中，有两篇类似并且都算是 Seq2Seq 上的创新的论文，分别是 FaceBook 的《Convolutional Sequence to Sequence Learning》和 Google 的《Attention is All You Need》。本质上来说，它们都是抛弃了 RNN 结构来做 Seq2Seq 任务。

本文将首先对《Attention is All You Need》做一点简单的分析，然后再介绍一些 Attention 的变体。

## Hello Mr.Lucky


注意点：
1、复制图片过来，要先等一会！要先等一会！！要先等一会！！！让小书匠保存成github的图床图片，先不要保存到github上的文章，不然图片获取用的是：(./images/1561707358500.png)，会导致复制到CSDN上无法使用
2、复制图片过来先保存一遍，不然容易出现(./images/1561707358500.png)



【小书匠 常用快捷键及设置】https://www.cnblogs.com/wushuaishuai/p/9308094.html



【环境】win10_x64 + python3.6.5


【Me】https://github.com/Valuebai/


【参考】
1、出处：地址