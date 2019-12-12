---
layout:     post					# 使用的布局（不需要改）
title:      安利神器-Jupyter Notebook-保存并可视化代码执行结果		# 标题
subtitle:    介绍在不同场景下的notebook使用，本地，远程，各大厂商提供的在线notebook服务等，对python，机器学习，深度学习，CV, NLP的同学特有帮助 			#副标题
date:       2019-06-12
author:     Valuebai
header-img: img/bg_common.jpg 	#这篇文章标题背景图片
catalog: true
tags:
    - 实用工具
---

Jupyter Notebook（此前被称为 IPython notebook）是一个交互式笔记本，支持运行 40 多种编程语言。
Jupyter Notebook 的本质是一个 Web 应用程序，便于创建和共享文学化程序文档，支持实时代码，数学方程，可视化和 markdown。 用途包括：数据清理和转换，数值模拟，统计建模，机器学习等等

- 数据挖掘领域中最热门的比赛 Kaggle 里的资料都是Jupyter 格式

## 本地安装使用(Windows/Mac)

### 安装notebook
Anaconda是安装Jupyter最简便的方式，自带Jupyter.

在Conda中安装，可以用 conda install jupyter notebook.

Jupyter也可以用pip安装 pip install jupyter notebook.

### 启动Jupyter服务器
在控制台或者teminal里面启动Notebook jupyter notebook. Jupyter需要命令行来启动。 你在哪个路径下启动jupyter，文本就保存在哪个路径下。

当你启动jupyter，它的主页会在浏览器中自动打开。 默认地址为http://localhost:8888. localhost 指你的本机，而不是网络中其他电脑。8888是你连接的端口. 只要server是在运行的, 你都可以在浏览器中访问 http://localhost:8888 。

如果你另外开了一个server，它会默认想去启动 8888端口,但因为已经占用了，它会去默认开启端口8889. 你可以访问http://localhost:8889.

例如这样:
![enter description here](https://www.github.com/Valuebai/Valuebai.github.io/raw/master/img/201912121576122347063.png)

【参考】Jupyter介绍和使用 中文版：https://segmentfault.com/a/1190000013014274


## 远程安装使用(Linux)

安装启动同上，只不过直接用IP访问远程的linux服务器运行代码，减少本地电脑的压力（特别是电脑配置没那么好的同学）



## Kaggle-Notebook
- 强烈推荐使用，大佬都在这，里面的经验很值得学习，能顺便学英语
- 上面的语料能直接复制到你自己的notebook下运行
- 地址：https://www.kaggle.com/notebooks


## Googlel-Colaboratory

- 国内需要翻墙
- 地址：https://colab.research.google.com/


## 腾讯Ti-One

- 薅羊毛用
- 地址：https://cloud.tencent.com/product/tione


## 阿里天池

- 地址：https://tianchi.aliyun.com/competition/


## 百度飞桨

- 地址：https://www.paddlepaddle.org.cn/



