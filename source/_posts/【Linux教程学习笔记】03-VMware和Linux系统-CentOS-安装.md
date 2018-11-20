---
title: 【Linux教程学习笔记】03.VMware和Linux系统(CentOS)安装
date: 2018-11-20 15:39:08
tags: 
	- linux
categories: 操作系统
---
# 前言
学习Linux需要一个环境，我们需要创建一个虚拟机，然后在虚拟机上安装一个Centos系统来学习
1. 先安装virtual machine ,vm12
1. 再安装Linux (CentOS 6.8)
1. 原理示意图（VM和CentOS的关系）
![image](http://image.damienzhong.com/vm%E5%92%8Ccentos%E7%9A%84%E5%85%B3%E7%B3%BB.png)
# 安装VMware
1. 去BIOS里修改设置开启虚拟化设备支持（f2, f10）
![image](http://image.damienzhong.com/bios%E8%AE%BE%E7%BD%AE%E8%99%9A%E6%8B%9F%E5%8C%96.png)
1. 安装虚拟机软件（vm12）
 
参考文章：[VMware Workstation 12安装教程（附下载地址与激活码）](https://damienzhong.github.io/2018/11/20/VMware-Workstation-12%E5%AE%89%E8%A3%85%E6%95%99%E7%A8%8B%EF%BC%88%E9%99%84%E4%B8%8B%E8%BD%BD%E5%9C%B0%E5%9D%80%E4%B8%8E%E6%BF%80%E6%B4%BB%E7%A0%81%EF%BC%89/)
# CentOS安装
## 下载地址
- 网易镜像：http://mirrors.163.com/centos/6/isos/
- 搜狐镜像：http://mirrors.sohu.com/centos/6/isos
## 创建虚拟机
- 新建虚拟机

![image](http://image.damienzhong.com/%E6%96%B0%E5%BB%BA%E8%99%9A%E6%8B%9F%E6%9C%BA.png)
- 新建虚拟机向导

![image](http://image.damienzhong.com/%E6%96%B0%E5%BB%BA%E8%99%9A%E6%8B%9F%E6%9C%BA%E5%90%91%E5%AF%BC.png)
- 创建虚拟空白光盘

![image](http://image.damienzhong.com/%E5%88%9B%E5%BB%BA%E8%99%9A%E6%8B%9F%E7%A9%BA%E7%99%BD%E5%85%89%E7%9B%98.png)
- 安装Linux系统对应的CentOS版

![image](http://image.damienzhong.com/%E5%AE%89%E8%A3%85Linux%E7%B3%BB%E7%BB%9F%E5%AF%B9%E5%BA%94%E7%9A%84CentOS%E7%89%88.png)
- 虚拟机命名和定位磁盘位置

![image](http://image.damienzhong.com/%E8%99%9A%E6%8B%9F%E6%9C%BA%E5%91%BD%E5%90%8D%E5%92%8C%E5%AE%9A%E4%BD%8D%E7%A3%81%E7%9B%98%E4%BD%8D%E7%BD%AE.png)
- 处理器配置，看自己是否是双核、多核

![image](http://image.damienzhong.com/%E5%A4%84%E7%90%86%E5%99%A8%E9%85%8D%E7%BD%AE.png)
> 虚拟机处理器数量可以根据自己的机器配置来定，查看电脑的属性即可
- 设置内存为2GB

![image](http://image.damienzhong.com/%E8%AE%BE%E7%BD%AE%E5%86%85%E5%AD%98%E4%B8%BA2GB.png)
> 内存的大小要根据自己机器的内存来定，建议2G
- 网络设置NAT

![image](http://image.damienzhong.com/%E7%BD%91%E7%BB%9C%E8%AE%BE%E7%BD%AENAT.png)
> ==虚拟机的网络连接三种形式的说明==：
```
桥接网络：Linux可以和其它的系统通信。但是可能造成ip冲突
NAT(网络地址转换方式): linux可以访问外网，不会造成ip冲突。
主机模式：你的linux是一个独立的主机，不能访问外网
```
- 选择IO控制器类型

![image](http://image.damienzhong.com/%E9%80%89%E6%8B%A9IO%E6%8E%A7%E5%88%B6%E5%99%A8%E7%B1%BB%E5%9E%8B.png)
- 选择磁盘类型

![image](http://image.damienzhong.com/%E9%80%89%E6%8B%A9%E7%A3%81%E7%9B%98%E7%B1%BB%E5%9E%8B.png)

```
IDE: 老的磁盘类型
SCSI: 服务器上推荐使用的磁盘类型，串口。
SATA: 也是串口，也是新的磁盘类型。
```
- 新建虚拟磁盘

![image](http://image.damienzhong.com/%E6%96%B0%E5%BB%BA%E8%99%9A%E6%8B%9F%E7%A3%81%E7%9B%98.png)
- 设置磁盘容量

![image](http://image.damienzhong.com/%E8%AE%BE%E7%BD%AE%E7%A3%81%E7%9B%98%E5%AE%B9%E9%87%8F.png)
- 设置磁盘文件存储位置

![image](http://image.damienzhong.com/%E8%AE%BE%E7%BD%AE%E7%A3%81%E7%9B%98%E6%96%87%E4%BB%B6%E5%AD%98%E5%82%A8%E4%BD%8D%E7%BD%AE.png)
- 新建虚拟机向导配置完成

![image](http://image.damienzhong.com/%E6%96%B0%E5%BB%BA%E8%99%9A%E6%8B%9F%E6%9C%BA%E5%90%91%E5%AF%BC%E9%85%8D%E7%BD%AE%E5%AE%8C%E6%88%90.png)
- VM设置

![image](http://image.damienzhong.com/VM%E8%AE%BE%E7%BD%AE.png)
- 加载ISO

![image](http://image.damienzhong.com/%E5%8A%A0%E8%BD%BDISO.png)
## CentOS配置安装
- 启动虚拟机

![image](http://image.damienzhong.com/%E5%90%AF%E5%8A%A8%E8%99%9A%E6%8B%9F%E6%9C%BA.png)
- 初始化欢迎进入页面

![image](http://image.damienzhong.com/%E5%88%9D%E5%A7%8B%E5%8C%96%E6%AC%A2%E8%BF%8E%E8%BF%9B%E5%85%A5%E9%A1%B5%E9%9D%A2.png)
> 回车选择第一个开始安装配置，此外，在Ctrl+Alt可以实现Windows主机和VM之间窗口的切换
- 是否对CD媒体进行测试，直接跳过Skip

![image](http://image.damienzhong.com/%E5%AF%B9CD%E5%AA%92%E4%BD%93%E8%BF%9B%E8%A1%8C%E6%B5%8B%E8%AF%95.png)
- CentOS欢迎页面，直接点击Next

![image](http://image.damienzhong.com/CentOS%E6%AC%A2%E8%BF%8E%E9%A1%B5%E9%9D%A2.png)
- 选择简体中文进行安装
- ![image](http://image.damienzhong.com/%E9%80%89%E6%8B%A9%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87%E8%BF%9B%E8%A1%8C%E5%AE%89%E8%A3%85.png)
- 选择语言键盘

![image](http://image.damienzhong.com/%E9%80%89%E6%8B%A9%E8%AF%AD%E8%A8%80%E9%94%AE%E7%9B%98.png)
- 选择存储设备

![image](http://image.damienzhong.com/%E9%80%89%E6%8B%A9%E5%AD%98%E5%82%A8%E8%AE%BE%E5%A4%87.png)
![image](http://image.damienzhong.com/%E9%80%89%E6%8B%A9%E5%AD%98%E5%82%A8%E8%AE%BE%E5%A4%8702.png)
- 给计算机起名

![image](http://image.damienzhong.com/%E7%BB%99%E8%AE%A1%E7%AE%97%E6%9C%BA%E8%B5%B7%E5%90%8D.png)
- 选择时区

![image](http://image.damienzhong.com/%E9%80%89%E6%8B%A9%E6%97%B6%E5%8C%BA.png)
- 设置root密码 （一定记住）

![image](http://image.damienzhong.com/%E8%AE%BE%E7%BD%AEroot%E5%AF%86%E7%A0%81.png)
- 硬盘分区-1

![image](http://image.damienzhong.com/%E7%A1%AC%E7%9B%98%E5%88%86%E5%8C%BA-1.png)
- 根分区新建

![image](http://image.damienzhong.com/%E6%A0%B9%E5%88%86%E5%8C%BA%E6%96%B0%E5%BB%BA.png)
![image](http://image.damienzhong.com/%E6%A0%B9%E5%88%86%E5%8C%BA%E6%96%B0%E5%BB%BA02.png)
- Boot

![image](http://image.damienzhong.com/Boot.png)
![image](http://image.damienzhong.com/Boot02.png)
- swap分区设置

![image](http://image.damienzhong.com/swap%E5%88%86%E5%8C%BA%E8%AE%BE%E7%BD%AE.png)
![image](http://image.damienzhong.com/swap%E5%88%86%E5%8C%BA%E8%AE%BE%E7%BD%AE02.png)
- 分区完成

![image](http://image.damienzhong.com/%E5%88%86%E5%8C%BA%E5%AE%8C%E6%88%90.png)
![image](http://image.damienzhong.com/%E5%88%86%E5%8C%BA%E5%AE%8C%E6%88%9002.png)
![image](http://image.damienzhong.com/%E5%88%86%E5%8C%BA%E5%AE%8C%E6%88%9003.png)
- 程序引导，直接下一步

![image](http://image.damienzhong.com/%E7%A8%8B%E5%BA%8F%E5%BC%95%E5%AF%BC.png)
- 现在定制系统软件

![image](http://image.damienzhong.com/%E5%AE%9A%E5%88%B6%E7%B3%BB%E7%BB%9F%E8%BD%AF%E4%BB%B6.png)
- Web环境

![image](http://image.damienzhong.com/Web%E7%8E%AF%E5%A2%83.png)
- 可扩展文件系统支持

![image](http://image.damienzhong.com/%E5%8F%AF%E6%89%A9%E5%B1%95%E6%96%87%E4%BB%B6%E7%B3%BB%E7%BB%9F%E6%94%AF%E6%8C%81.png)
- 基本系统（不要去勾选java平台，因为后面我们自己需要安装）

![image](http://image.damienzhong.com/%E5%9F%BA%E6%9C%AC%E7%B3%BB%E7%BB%9F.png)
- 应用程序

![image](http://image.damienzhong.com/%E5%BA%94%E7%94%A8%E7%A8%8B%E5%BA%8F.png)
- 开发、弹性存储、数据库、服务器
可以都不勾，有需要，以后使用中有需要再手动安装
- 桌面,除了KDE，其他都选就可以了。

![image](http://image.damienzhong.com/%E6%A1%8C%E9%9D%A2.png)
- 语言支持

![image](http://image.damienzhong.com/%E8%AF%AD%E8%A8%80%E6%94%AF%E6%8C%81.png)
- 系统管理、虚拟化、负载平衡器、高可用性可以都不选
- 完成配置，开始安装CentOS

![image](http://image.damienzhong.com/%E5%AE%8C%E6%88%90%E9%85%8D%E7%BD%AE.png)
- 等待安装完成，等待等待等待等待……20分钟左右
- 安装完成，重新引导
![image](http://image.damienzhong.com/%E9%87%8D%E6%96%B0%E5%BC%95%E5%AF%BC.png)
- 欢迎引导页面

![image](http://image.damienzhong.com/%E6%AC%A2%E8%BF%8E%E5%BC%95%E5%AF%BC%E9%A1%B5%E9%9D%A2.png)
- 许可证

![image](http://image.damienzhong.com/%E8%AE%B8%E5%8F%AF%E8%AF%81.png)
- 创建用户，可以先不创建，用root账户登录就行

![image](http://image.damienzhong.com/%E5%88%9B%E5%BB%BA%E7%94%A8%E6%88%B7.png)
![image](http://image.damienzhong.com/%E8%B7%B3%E8%BF%87%E5%88%9B%E5%BB%BA%E7%94%A8%E6%88%B7.png)
- 时间和日期

![image](http://image.damienzhong.com/%E6%97%B6%E9%97%B4%E5%92%8C%E6%97%A5%E6%9C%9F.png)
- Kdump,去掉

![image](http://image.damienzhong.com/Kdump%E5%8E%BB%E6%8E%89.png)
- 重启后用root登录

![image](http://image.damienzhong.com/%E9%87%8D%E5%90%AF%E5%90%8E%E7%94%A8root%E7%99%BB%E5%BD%95.png)
- 配置可以上网

![image](http://image.damienzhong.com/%E9%85%8D%E7%BD%AE%E5%8F%AF%E4%BB%A5%E4%B8%8A%E7%BD%91.png)
- 使用火狐连接网络，看看是否可以连通

![image](http://image.damienzhong.com/%E7%81%AB%E7%8B%90%E8%BF%9E%E6%8E%A5%E7%BD%91%E7%BB%9C.png)