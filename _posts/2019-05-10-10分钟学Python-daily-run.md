---
layout:     post					# 使用的布局（不需要改）
title:      10分钟学Python-daily-run		# 标题
subtitle:   记录学习python的小例子    			#副标题
date:       2019-05-10
author:     Valuebai
header-img: img/bg_common.jpg 	#这篇文章标题背景图片
catalog: true
tags:
    - Python
---

## 提取Dataframes除指定列以外所有列

【学习地址】https://mp.weixin.qq.com/s/6Wjfyu5OA3kCYOmf-6MbnA

![enter description here](https://www.github.com/Valuebai/Valuebai.github.io/raw/master/img/20191221575267154081.png)

![enter description here](https://www.github.com/Valuebai/Valuebai.github.io/raw/master/img/20191221575267142439.png)



## Python自动群发邮件

```python
import smtplib
from email import (header)
from email.mime import (text, application, multipart)
import time

def sender_mail():
    smt_p = smtplib.SMTP()
    smt_p.connect(host='smtp.qq.com', port=25)
    sender, password = '113097485@qq.com', "**************"
    smt_p.login(sender, password)
    receiver_addresses, count_num = [
        'guozhennianhua@163.com', 'xiaoxiazi99@163.com'], 1
    for email_address in receiver_addresses:
        try:
            msg = multipart.MIMEMultipart()
            msg['From'] = "zhenguo"
            msg['To'] = email_address
            msg['subject'] = header.Header('这是邮件主题通知', 'utf-8')
            msg.attach(text.MIMEText(
                '这是一封测试邮件，请勿回复本邮件~', 'plain', 'utf-8'))
            smt_p.sendmail(sender, email_address, msg.as_string())
            time.sleep(10)
            print('第%d次发送给%s' % (count_num, email_address))
            count_num = count_num + 1
        except Exception as e:
            print('第%d次给%s发送邮件异常' % (count_num, email_address))
            continue
    smt_p.quit()

sender_mail()

```

注意：
发送邮箱是qq邮箱，所以要在qq邮箱中设置开启SMTP服务，设置完成时会生成一个授权码，将这个授权码赋值给文中的password变量。

如果要群发的邮件带有附件怎么办？star gitHub库，里面有相关例子：Python群发带附件的邮件

https://github.com/jackzhenguo/python-small-examples


## AAA


## AAA

## AAA

## AAA

## AAA


【Me】https://github.com/Valuebai/


【参考】
1、出处：地址