---
layout:     post					# 使用的布局（不需要改）
title:      crontab的语法规则格式		# 标题
subtitle:   方便查询使用    			#副标题
date:       2020-2-2
author:     Valuebai
header-img: img/bg_common.jpg 	#这篇文章标题背景图片
catalog: true
tags:
    - 好用工具
---

## crontab的语法规则格式

crontab的语法规则格式（每分钟、每小时、每天、每周、每月、每年定时执行 规则） 


## 在线查询工具

在线查询工具： https://tool.lu/crontab

![enter description here](https://www.github.com/Valuebai/Valuebai.github.io/raw/master/img/2020251580899934955.png)

crontab的语法规则格式（每分钟、每小时、每天、每周、每月、每年定时执行 规则） https://blog.csdn.net/xinyflove/article/details/83178876

 
![enter description here](https://www.github.com/Valuebai/Valuebai.github.io/raw/master/img/2020251580899893919.png)


## 举个栗子

jenkins里面的轮询 SCM就是用的crontab的

1.每分钟定时执行一次规则：
每1分钟执行： */1 * * * *或者* * * * *
每5分钟执行： */5 * * * *

2.每小时定时执行一次规则：
每小时执行： 0 * * * *或者0 */1 * * *
每天上午7点执行：0 7 * * *
每天上午7点10分执行：10 7 * * *

3.每天定时执行一次规则：
每天执行 0 0 * * *

4.每周定时执行一次规则：
每周执行 0 0 * * 0

5.每月定时执行一次规则：
每月执行 0 0 1 * *

6.每年定时执行一次规则：
每年执行 0 0 1 1 *

7.其他例子
5 * * * * 指定每小时的第5分钟执行一次ls命令
30 5 * * * ls 指定每天的 5:30 执行ls命令
30 7 8 * * ls 指定每月8号的7：30分执行ls命令
30 5 8 6 * ls 指定每年的6月8日5：30执行ls命令
30 6 * * 0 ls 指定每星期日的6:30执行ls命令[注：0表示星期天，1表示星期1，以此类推，也可以用英文来表示，sun表示星期天，mon表示星期一等。]
30 3 10,20 * * ls 每月10号及20号的3：30执行ls命令[注：“，”用来连接多个不连续的时段]
25 8-11 * * * ls 每天8-11点的第25分钟执行ls命令[注：“-”用来连接连续的时段]
*/15 * * * * ls 每15分钟执行一次ls命令 [即每个小时的第0 15 30 45 60分钟执行ls命令 ]
30 6 */10 * * ls 每个月中，每隔10天6:30执行一次ls命令[即每月的1、11、21、31日是的6：30执行一次ls命令。 ]



【参考】
1、出处：https://www.cnblogs.com/shamo89/p/10160946.html