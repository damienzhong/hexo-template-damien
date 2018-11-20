---
title: 【Linux教程学习笔记】19.Linux网络配置
date: 2018-11-20 17:35:27
tags: 
	- linux
categories: 操作系统
---
## 查看网络IP和网关
### 查看虚拟网络编辑器
![image](http://image.damienzhong.com/%E6%9F%A5%E7%9C%8B%E8%99%9A%E6%8B%9F%E7%BD%91%E7%BB%9C%E7%BC%96%E8%BE%91%E5%99%A8.png)
### 修改ip地址
![image](http://image.damienzhong.com/%E4%BF%AE%E6%94%B9ip%E5%9C%B0%E5%9D%80.png)
### 查看网关
![image](http://image.damienzhong.com/%E6%9F%A5%E7%9C%8B%E7%BD%91%E5%85%B3.png)
### 查看windows环境的中VMnet8网络配置(ipconfig指令)
![image](http://image.damienzhong.com/ipconfig.png)
## ping 测试主机之间网络连通性
### 基本语法
ping 目的主机（功能描述：测试当前服务器是否可以连接目的主机）
### 应用实例
- 测试当前服务器是否可以连接百度
- ping www.baidu.com
## linux网络环境配置
### 第一种方法(自动获取)
说明：登陆后，通过界面的来设置自动获取ip

![image](http://image.damienzhong.com/%E7%AC%AC%E4%B8%80%E7%A7%8D%E6%96%B9%E6%B3%95%28%E8%87%AA%E5%8A%A8%E8%8E%B7%E5%8F%96%29.png)
特点：linux启动后会自动获取IP,缺点是每次自动获取的ip地址可能不一样。
### 第二种方法(指定固定的ip)
- 说明
  - 直接修改配置文件来指定IP,并可以连接到外网(程序员推荐)，编辑vi /etc/sysconfig/network-scripts/ifcfg-eth0
  - 要求：将ip地址配置的静态的，ip地址为192.168.184.130
- ifcfg-eth0文件说明
  - DEVICE=eth0 #接口名（设备,网卡）
  - HWADDR=00:0C:2x:6x:0x:xx #MAC地址
  - TYPE=Ethernet #网络类型（通常是Ethemet）
  - UUID=926a57ba-92c6-4231-bacb-f27e5e6a9f44 #随机id
  - #系统启动的时候网络接口是否有效（yes/no）
  - ONBOOT=yes
  - # IP的配置方法[none|static|bootp|dhcp]（引导时不使用协议|静态分配IP|BOOTP协议|DHCP协议）
  - BOOTPROTO=static
  - #IP地址
  - IPADDR=192.168.184.130
  - #网关
  - GATEWAY=192.168.184.2
  - #域名解析器
  - DNS1=192.168.184.2
- 重启网络服务或者重启系统生效
- service network restart 、reboot