---
title: 【Linux教程学习笔记】05.远程登录到Linux服务器
date: 2018-11-20 17:00:51
tags: 
	- linux
categories: 操作系统
---
# 为什么需要远程登录Linux
> 说明: 公司开发时候，具体的情况是这样的
- linux服务器是开发小组共享的.
- 正式上线的项目是运行在公网的.
- 因此程序员需要远程登录到centos进行项目管理或者开发.
- 网络拓扑示意图

![image](https://note.youdao.com/yws/public/resource/f5c450ab492ccef08e40958c2a6586ae/7E86F9212B9447D4862A3610C1D17D4C?ynotemdtimestamp=1542704939956)
- 远程登录客户端有Xshell5，Xftp5 ,其它的远程工具大同小异.
# 远程登录Linux-Xshell5
- Xshell 是目前最好的远程登录到Linux操作的软件，流畅的速度并且完美解决了中文乱码的问题，是目前程序员首选的软件。
- Xshell[1]是一个强大的安全终端模拟软件，它支持SSH1, SSH2, 以及Microsoft Windows 平台的TELNET 协议。
- Xshell可以在Windows界面下用来访问远端不同系统下的服务器，从而比较好的达到远程控制终端的目的。

> 特别说明：如果希望安装好XShell5就可以远程访问Linux系统的话，需要有一个前提，就是Linux启用了SSHD服务，该服务会监听22号端口。
## 安装过程
基本上是下一步，不再讲述。
## XShell5的关键配置
![image](https://note.youdao.com/yws/public/resource/f5c450ab492ccef08e40958c2a6586ae/ED88A2A4AC8E4388B6BAEA15F62DE947?ynotemdtimestamp=1542704939956)
# 远程上传下载文件Xftp5
是一个基于windows平台的功能强大的SFTP、FTP文件传输软件。使用了Xftp 以后，windows 用户能安全地在UNIX/Linux和Windows PC 之间传输文件。
## Xftp5的配置和使用
![image](https://note.youdao.com/yws/public/resource/f5c450ab492ccef08e40958c2a6586ae/86B78DBFDEB54A8BA3B3B9E056EF3691?ynotemdtimestamp=1542704939956)
连接成功的界面如下：
![image](https://note.youdao.com/yws/public/resource/f5c450ab492ccef08e40958c2a6586ae/FAFEFC9FFCEE40A592C4ABD7F8421C23?ynotemdtimestamp=1542704939956)
## Xftp5中文乱码问题解决方案
![image](https://note.youdao.com/yws/public/resource/f5c450ab492ccef08e40958c2a6586ae/21F15468272F4B64895B6D7E967D41B7?ynotemdtimestamp=1542704939956)

按照上图配置之后，只要刷新一下即可解决
