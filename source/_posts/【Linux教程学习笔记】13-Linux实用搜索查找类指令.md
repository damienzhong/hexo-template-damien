---
title: 【Linux教程学习笔记】13.Linux实用搜索查找类指令
date: 2018-11-20 17:26:58
tags: 
	- linux
categories: 操作系统
---
# find指令
find指令将从指定目录向下递归地遍历其各个子目录，将满足条件的文件或者目录显示在终端。
## 基本语法
find [搜索范围] [选项]
### 选项说明
![image](http://image.damienzhong.com/find%E9%80%89%E9%A1%B9%E8%AF%B4%E6%98%8E.png)
# locate指令
locaate指令可以快速定位文件路径。locate指令利用事先建立的系统中所有文件名称及路径的locate数据库实现快速定位给定的文件。Locate指令无需遍历整个文件系统，查询速度较快。为了保证查询结果的准确度，管理员必须定期更新locate时刻。
## 基本语法
locate 搜索文件
### 特别说明
由于locate指令基于数据库进行查询，所以第一次运行前，必须使用updatedb指令创建locate数据库。
# grep指令和管道符号|
grep 过滤查找，管道符，“|”，表示将前一个命令的处理结果输出传递给后面的命令处理。
## 基本语法
grep [选项]查找内容源文件
### 常用选项
![image](http://image.damienzhong.com/grep%E5%B8%B8%E7%94%A8%E9%80%89%E9%A1%B9.png)
