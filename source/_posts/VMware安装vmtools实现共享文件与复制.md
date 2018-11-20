---
title: VMware安装vmtools实现共享文件与复制
date: 2018-11-20 15:03:33
tags: 
	- VMware
	- 虚拟化
	- vmtools
categories: 虚拟化
---
# vmtools介绍
vmtools 安装后，可以让我们在windows下更好的管理vm虚拟机
- 可以直接粘贴命令在windows 和centos系统之间
- 可以设置windows和centos的共享文件夹
## 示意图
![image](http://image.damienzhong.com/vmtools%E5%8A%9F%E8%83%BD.png)
# 安装vmtools的步骤
1. 进入centos
1. 点击vm菜单的->install vmware tools
1. centos会出现一个vm的安装包
1. 点击右键解压, 得到一个安装文件
1. 进入该vm解压的目录，该文件在/root/桌面/vmware-tools-distrib/下
1. 安装./vmware-install.pl
1. 全部使用默认设置即可
1. 需要reboot重新启动即可生效
# 设置共享文件夹
- 为了方便，可以设置一个共享文件夹，比如d:/share
- windows 和contos 就可以共享文件了，但是在实际公司开发中，文件的上传下载是需要使用远程方式完成的，
- 远程方式登录，我们后面会具体讲解
## 具体步骤
- 菜单->vm->setting, 如图设置即可
- 注意:设置选项为always enable ,
- 这样可以读写了
- windows和centos可共享d:/share目录
- 可以读写文件了
- 在centos的/mnt/hgfs/ 下

![image](http://image.damienzhong.com/vmtools%E5%85%B1%E4%BA%AB%E6%96%87%E4%BB%B6%E5%A4%B9.png)