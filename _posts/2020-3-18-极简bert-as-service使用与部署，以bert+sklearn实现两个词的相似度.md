---
layout:     post					# 使用的布局（不需要改）
title:      极简bert-as-service使用与部署，以bert+sklearn实现两个词的相似度		# 标题
subtitle:   bert-as-service的安装&部署，使用记录    			#副标题
date:       2020-3-18
author:     Valuebai
header-img: img/bg_common.jpg 	#这篇文章标题背景图片
catalog: true
tags:
    - 自然语言处理
---



---
## # bert-as-service的安装&部署

bert-as-service github地址：[https://github.com/hanxiao/bert-as-service](https://github.com/hanxiao/bert-as-service)

### 1. 安装 python 3 环境
**我的python 版本为3.6.5**

[点击进入python教程](https://www.runoob.com/python3/python3-install.html)

[建议：Ptyhon项目单独创建虚拟环境](https://shimo.im/docs/yRjCrCkXq3xpydGg)



### 2. 部署自然语言模型

#### 2.1 下载模型压缩包
[点击下载中文版本的bert模型(由bert-as-service github官方提供)](https://storage.googleapis.com/bert_models/2018_11_03/chinese_L-12_H-768_A-12.zip)

P.S. linux可先下载到本地后，再用FileZilla上传上去

#### 2.2 解压压缩包

解压到本地

#### 2.3 安装 python 依赖包
```
    pip install tensorflow==1.14.0  -i https://pypi.tuna.tsinghua.edu.cn/simple
    pip install bert-serving-server==1.10.1 -i https://pypi.tuna.tsinghua.edu.cn/simple
    pip install bert-serving-client==1.10.1 -i https://pypi.tuna.tsinghua.edu.cn/simple
```
  P.S. 注意点，bert-serving-client使用python2和python3都可以，但是bert-serving-server必须python3才能部署，建议统一用python3
  
#### 2.4 启动模型
```
    # 进入chinese_L-12_H-768_A-12同级目录执行下面命令
    bert-serving-start -model_dir ./chinese_L-12_H-768_A-12/ -num_worker=1
   
```
上面部署运行后，看到all set, ready to serve request! 说明成功啦，接下来能用下面的代码进行测试了

#### 2.5 windows启动模型脚本
创建#start-bert服务启动脚本.bat，填入下面的内容
```
rem 这个脚本放到与模型文件夹同级目录执行
:: 需要安装 python 依赖包
:: pip install tensorflow==1.14.0  -i https://pypi.tuna.tsinghua.edu.cn/simple
:: pip install bert-serving-server==1.10.1 -i https://pypi.tuna.tsinghua.edu.cn/simple
:: pip install bert-serving-client==1.10.1 -i https://pypi.tuna.tsinghua.edu.cn/simple

bert-serving-start -model_dir ./chinese_L-12_H-768_A-12/ -num_worker=1

pause
```

### linux启动bert-as-serving
1. 安装包
```
    pip install tensorflow==1.14.0  -i https://pypi.tuna.tsinghua.edu.cn/simple
    pip install bert-serving-server==1.9.1 -i https://pypi.tuna.tsinghua.edu.cn/simple（centos7装了运行报错）
    pip install bert-serving-client==1.9.1 -i https://pypi.tuna.tsinghua.edu.cn/simple（centos7装了运行报错）    
    pip install bert-serving-server==1.10.1（centos7装这个）
    pip install bert-serving-client==1.10.1（centos7装这个）
    
```
2. 进入chinese_L-12_H-768_A-12同级目录执行下面命令
```
    bert-serving-start -model_dir ./chinese_L-12_H-768_A-12/ -num_worker=1
```

3. 给linux服务器增加虚拟内存
```
运行项目报错，提醒内存不足
Centos/linux 服务器的内存不够了怎么办？centos用虚拟内存扩展内存：

输入：free -m查看内存状态
dd if=/dev/zero of=/opt/swap bs=2048 count=2048000 //在opt分区建立名为swap，大小为1G的虚拟内存文件
chmod 600 /opt/swap //注意更改swap文件的权限
mkswap /opt/swap //将swap文件设置为swap分区文件
swapon /opt/swap //激活swap,启用分区交换文件
free -m //看下结果
参考：https://blog.csdn.net/herobacking/article/details/80371242

【注意】重启后这个就会没了，需要重新设置
```
  
4. 其他
```
    P.S.最后重启reboot，执行312步骤
    
    linux 部署时需要开启这2个默认端口，参考文章https://baijiahao.baidu.com/s?id=1646263423663635431&wfr=spider&for=pc
    指定客户端向服务端push数据的端口号，通过-port，默认5555
    指定服务端向客户端发布结果的的端口号，通过-port_out，默认5556
```



#### linux启动模型脚本
vim #start-bert-linux.sh，填入下面的内容
```
rem kill the existing process
ps -ef | grep 'bert-serving-start' | grep -v grep | awk '{print $2}' | xargs kill -s SIGINT

rem run bert, need to enter the same root
nohup bert-serving-start -model_dir ./chinese_L-12_H-768_A-12/ -num_worker=1 > bert.log 2>&1 &
```

## # bert+sklearn实现两个词的相似度
1. 下面代码默认我远程部署好的bert-as-serving服务的机器IP，自己部署的可改为localhost
2. 使用bert和sklearn的cosine_similarity计算两个词的相似度

```
#!/usr/bin/env python
# -*- coding: UTF-8 -*-
# @Time    : 2020/3/10 18:24
# @Software: PyCharm
# @Author  : https://github.com/Valuebai/
"""
    bert-as-serving的使用
    ~~~~~~~~~~~~~~~

    1. 调用远程Linux部署好的bert-as-serving服务
    2. 使用bert和sklearn的cosine_similarity计算两个词的相似度
"""

from bert_serving.client import BertClient
from sklearn.metrics.pairwise import cosine_similarity


class Encoding(object):
    def __init__(self):
        self.server_ip = "111.229.74.215"  # 调用远程部署好的bert-as-serving服务的机器IP
        # self.server_ip = "localhost"   # 调用本地远程部署好的bert-as-serving服务
        print('1. star BertClient')
        self.bert_client = BertClient(ip=self.server_ip, port=5555, port_out=5556, timeout=20000)
        print('2. end BertClient')

    def encode(self, query: str):
        """
        对输入的a list of strings to a list of vectors
        :param query: str,下面做了处理为a list of strings
        :return: 向量
        """
        tensor = self.bert_client.encode([query])
        return tensor

    def query_similarity(self, query_list):
        """
        查询输入列表的词的相似度
        :param query_list:如["孔子", "珠穆朗玛峰"]
        :return:返回概率大小0-100，概率越大，相似度越高
        """
        tensors = self.bert_client.encode(query_list)
        return cosine_similarity(tensors)[0][1]

    def cosine_two_words(self, base_text: str, compared_text: str):
        """
        用cosine计算2个词之间的相似度
        :param base_text: 想比较的词
        :param compared_text: 被比较的词
        :return: 返回概率大小0-100，概率越大，相似度越高
        """
        tensors = self.bert_client.encode([base_text, compared_text])
        return cosine_similarity(tensors)[0][1]


if __name__ == "__main__":
    ec = Encoding()
    print(ec.encode("孔子").shape)
    print(ec.encode("美国").shape)
    print("孔子和珠穆朗玛峰的向量相似度:", ec.query_similarity(["孔子", "珠穆朗玛峰"]))
    print("中国和孔子的向量相似度:", ec.query_similarity(["中国", "孔子"]))
    print("中国和香港的向量相似度:", ec.query_similarity(["中国", "香港"]))

    print(ec.cosine_two_words('中国', '美国'))

```



【环境】win10_x64 + python3.6.5


【Me】[https://github.com/Valuebai/](https://github.com/Valuebai/)

