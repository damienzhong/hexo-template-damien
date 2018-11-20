---
title: 【Linux教程学习笔记】14.Linux压缩与解压指令
date: 2018-11-20 17:28:49
tags: 
	- linux
categories: 操作系统
---
# gzip/gunzip 指令
gzip 用于压缩文件，gunzip 用于解压的
## 基本语法
- gzip 文件（功能描述：压缩文件，只能将文件压缩为*.gz文件）
- gunzip 文件.gz（功能描述：解压缩文件命令）
### 细节说明
当我们使用gzip对文件进行压缩后，不会保留原来的文件。
# zip/unzip 指令
zip 用于压缩文件，unzip 用于解压的，这个在项目打包发布中很有用的
## 基本语法
- zip [选项] XXX.zip 将要压缩的内容（功能描述：压缩文件和目录的命令）
- unzip [选项] XXX.zip（功能描述：解压缩文件）
### zip常用选项
-r：递归压缩，即压缩目录
### unzip的常用选项
-d<目录> ：指定解压后文件的存放目录
# tar 指令
tar 指令是打包指令，最后打包后的文件是.tar.gz 的文件。
## 基本语法
tar [选项] XXX.tar.gz 打包的内容(功能描述：打包目录，压缩后的文件格式.tar.gz)
### 选项说明
![image](http://image.damienzhong.com/tar%E9%80%89%E9%A1%B9%E8%AF%B4%E6%98%8E.png)
