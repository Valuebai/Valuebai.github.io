---
layout:     post					# 使用的布局（不需要改）
title:      安利神器-小书匠-写markdown文章+图床+github博客		# 标题
subtitle:   一款专注写作+高颜值+功能强大+cool+个性自由开放灵活的写作软件    			#副标题
date:       2019-06-01
author:     Valuebai
header-img: img/back-gunicorn.jpg 	#这篇文章标题背景图片
catalog: true
tags:
    - 机器学习
    - 深度学习
    - 自然语言处理
---

# 我的推荐

今年6月份遇到了小书匠，被颜值吸引，功能也超级强大，被深深吸粉，已成为小书匠的重度用户。使用github创建自己的博客，用小书匠写markdown格式的文章以及作为图床保存图片，真是太方便了，必须安利！

![enter description here](https://www.github.com/Valuebai/Valuebai.github.io/raw/master/img/201911231574516301551.png)

## 小书匠官网

- 【官网】http://soft.xiaoshujiang.com/
- 【小书匠 常用快捷键及设置】https://www.cnblogs.com/wushuaishuai/p/9308094.html

我使用小书匠做这些

### 小书匠写markdown格式文章

### 小书匠保存markdown格式文章到github
- 注意需要在github生成token

### 使用小书匠做图片（就是保存图片）
- 注意需要在github生成token
- 注意保存图片的格式：/img/{{year}}{{month}}{{date}}{{filename}}


## 用github创建个人博客

- 详情见：https://github.com/Valuebai/Valuebai.github.io



## 注意点：
1、复制图片过来，要先等一会！要先等一会！！要先等一会！！！让小书匠保存成github的图床图片，先不要保存到github上的文章，不然图片获取用的是：(./images/1561707358500.png)，会导致复制到CSDN上无法使用
2、复制图片过来先保存一遍，不然容易出现(./images/1561707358500.png)


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



## Hello Mr.Lucky


注意点：
1、复制图片过来，要先等一会！要先等一会！！要先等一会！！！让小书匠保存成github的图床图片，先不要保存到github上的文章，不然图片获取用的是：(./images/1561707358500.png)，会导致复制到CSDN上无法使用
2、复制图片过来先保存一遍，不然容易出现(./images/1561707358500.png)



【小书匠 常用快捷键及设置】https://www.cnblogs.com/wushuaishuai/p/9308094.html



【环境】win10_x64 + python3.6.5


【Me】https://github.com/Valuebai/


【参考】
1、出处：地址
```



