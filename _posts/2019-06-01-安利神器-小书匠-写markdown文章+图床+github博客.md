---
layout:     post					# 使用的布局（不需要改）
title:      安利神器-小书匠-写markdown文章+图床+github博客		# 标题
subtitle:   一款专注写作+高颜值+功能强大+cool+个性自由开放灵活的写作软件    			#副标题
date:       2019-06-01
author:     Valuebai
header-img: img/bg_common.jpg 	#这篇文章标题背景图片
catalog: true
tags:
    - 好用工具
---

# 我的推荐

今年6月份遇到了小书匠，被颜值吸引，功能也超级强大，被深深吸粉，已成为小书匠的重度用户。使用github创建自己的博客，用小书匠写markdown格式的文章以及作为图床保存图片，真是太方便了，必须安利！

![enter description here](https://www.github.com/Valuebai/Valuebai.github.io/raw/master/img/201911231574516301551.png)

## 小书匠官网

- 【官网】[http://soft.xiaoshujiang.com/](http://soft.xiaoshujiang.com/)
- 【小书匠设置github数据&img图片】[https://github.com/wss434631143/xiaoshujiang](https://github.com/wss434631143/xiaoshujiang)
- 【小书匠 常用快捷键及设置】https://www.cnblogs.com/wushuaishuai/p/9308094.html

- 【修改编辑器颜色】为Tron Contrast
- 【预览主题颜色】为tomorrow night

我使用小书匠做这些

邮箱是745

### 小书匠写markdown格式文章

### 小书匠将markdown格式文章转为pdf（如简历）

### 小书匠生成思维导图

### 小书匠保存markdown格式文章到github
- 注意需要在github生成token

### 使用小书匠做图床（就是保存图片到github，有图片地址可访问）
- 注意需要在github生成token
- 注意保存图片的格式：/img/{{year}}{{month}}{{date}}{{filename}}


## 用github创建个人博客

- 详情见：https://github.com/Valuebai/Valuebai.github.io



## 注意点：
1、复制图片过来，要先等一会！要先等一会！！要先等一会！！！让小书匠保存成github的图床图片，先不要保存到github上的文章，不然图片获取用的是：(./images/1561707358500.png)，会导致复制到CSDN上无法使用
2、复制图片过来先保存一遍，不然容易出现(./images/1561707358500.png)


# 用小书匠写markdown格式简历并导出pdf文档

- 真是太cool，在小书匠里面可以选择不同的背景主题，导出来的格式的也很美观！！！
- 点击 小书匠主按钮>导出 按钮，进入导出操作界面，默认导出为pdf

![enter description here](./images/1575801619367.png)

## 我的小书匠文章模板
```md

---
layout:     post					# 使用的布局（不需要改）
title:      填写标题，这可不用时间，但保存在github的文件名需要2019-09-09		# 标题
subtitle:   填写副标题    			#副标题
date:       <% print((new Date()).getFullYear().toString()+ '-'+ ((new Date()).getMonth() + 1).toString() + '-'+ (new Date()).getDate().toString()); %>
author:     Valuebai
header-img: img/back-gunicorn.jpg 	#这篇文章标题背景图片
catalog: true
tags:
    - 机器学习
    - 深度学习
    - 自然语言处理
---


或者(标头二选一)


---
layout:     post                                        # 使用的布局（不需要改）
title:      填写标题，可不加时间，但保存在github的文件名需要手机加时间2019-09-09              # 标题
subtitle:   填写副标题                       #副标题
date:       <% print((new Date()).getFullYear().toString()+ '-'+ ((new Date()).getMonth() + 1).toString() + '-'+ (new Date()).getDate().toString()); %>
author:     Valuebai
header-img: https://images.gitee.com/uploads/images/2021/0609/111925_10d6266f_420440.jpeg       #这篇文章标题背景图片
catalog: true
tags:
    - python
    - 好用工具
    - 机器学习
    - 自然语言处理
---

## 0x01 第一

## 0x02 第二


## 0x08 部署环境（本段##内容为了提醒，可删除）
- 【环境】MacPro + python3.6.8

注意点：
1. 复制图片过来，要先等一会！要先等一会！！要先等一会！！！让小书匠保存成gitee的图床图片，先不要保存到为其他地方的文章，不然图片获取用的是：(./images/1561707358500.png)，会导致复制到CSDN上无法使用
2. 复制图片过来先让它自动保存为gitee一遍，不然容易出现(./images/1561707358500.png)

3. 【小书匠 常用快捷键及设置】https://www.cnblogs.com/wushuaishuai/p/9308094.html



**【参考】**
1. About me：[https://github.com/Valuebai/](https://github.com/Valuebai/)
2. 出处：地址[]()

```



