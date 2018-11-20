---
title: 【Linux教程学习笔记】17.Linux定时任务调度
date: 2018-11-20 17:32:42
tags: 
	- linux
categories: 操作系统
---
# crond 任务调度
crontab 进行定时任务的设置。
## 概述
### 任务调度
是指系统在某个时间执行的特定的命令或程序。
### 任务调度分类
- 系统工作：有些重要的工作必须周而复始地执行。如病毒扫描等
- 个别用户工作：个别用户可能希望执行某些程序，比如对mysql数据库的备份。
### 基本语法
crontab [选项]
#### 常用选项
![image](http://image.damienzhong.com/crontab%E5%B8%B8%E7%94%A8%E9%80%89%E9%A1%B9.png)
## 快速入门
- 设置任务调度文件：/etc/crontab
- 设置个人任务调度。执行crontab –e命令。
- 接着输入任务到调度文件如：*/1 * * * * ls –l /etc/ > /tmp/to.txt
- 意思说每小时的每分钟执行ls –l /etc/ > /tmp/to.txt命令
### 参数细节说明
#### 5个占位符的说明
![image](http://image.damienzhong.com/crond%E5%8D%A0%E4%BD%8D%E7%AC%A6%E8%AF%B4%E6%98%8E.png)
#### 特殊符号的说明
![image](http://image.damienzhong.com/crond%E7%89%B9%E6%AE%8A%E7%AC%A6%E5%8F%B7%E8%AF%B4%E6%98%8E.png)
#### 特定时间执行任务案例
![image](http://image.damienzhong.com/crond%E7%89%B9%E5%AE%9A%E6%97%B6%E9%97%B4%E6%89%A7%E8%A1%8C%E6%A1%88%E4%BE%8B.png)
### crond 相关指令
- crontab –r：终止任务调度。
- crontab –l：列出当前有那些任务调度
- service crond restart [重启任务调度]