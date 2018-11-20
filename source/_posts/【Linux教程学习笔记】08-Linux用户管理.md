---
title: 【Linux教程学习笔记】08.Linux用户管理
date: 2018-11-20 17:19:53
tags: 
	- linux
categories: 操作系统
---
# 基本介绍
## 用户管理示意图
![image](http://image.damienzhong.com/Linux%E7%94%A8%E6%88%B7%E7%AE%A1%E7%90%86%E5%9B%BE.png)
## 说明
- Linux系统是一个多用户多任务的操作系统，任何一个要使用系统资源的用户，都必须首先向系统管理员申请一个账号，然后以这个账号的身份进入系统。
- Linux的用户需要至少要属于一个组
# 添加用户
## 基本语法
useradd [选项] 用户名
## 实际案例
添加一个用户xm。

![image](http://image.damienzhong.com/Linux%E6%B7%BB%E5%8A%A0%E7%94%A8%E6%88%B7xm.png)
### 特别说明
cd  表示change directory，切换目录
## 细节说明
- 当创建用户成功后，会自动的创建和用户同名的家目录
- 也可以通过useradd -d 指定目录新的用户名，给新创建的用户指定家目录

![image](http://image.damienzhong.com/Linux%E5%88%9B%E5%BB%BA%E6%96%B0%E7%94%A8%E6%88%B7.png)
# 给用户指定或修改密码
## 基本语法
passwd 用户名
## 应用案例
给xm指定密码
![image](http://image.damienzhong.com/Linux%E6%B7%BB%E5%8A%A0%E6%88%96%E4%BF%AE%E6%94%B9%E7%94%A8%E6%88%B7%E5%AF%86%E7%A0%81.png)
# 删除用户
## 基本语法
userdel 用户名
## 应用案例
- 删除用户xm，但是要保留家目录
  - userdel 用户名
- 删除用户以及用户主目录
  - userdel -r 用户名
## 注意事项
在删除用户时，我们一般不会将家目录删除
# 查询用户信息
## 基本语法
id 用户名
## 应用实例
请查询root 信息

![image](http://image.damienzhong.com/linux%E6%9F%A5%E8%AF%A2root%E7%94%A8%E6%88%B7.png)
## 细节说明
当用户不存在时，返回无此用户
# 切换用户
## 介绍
在操作Linux中，如果当前用户的权限不够，可以通过su -指令，切换到高权限用户，比如root
## 基本语法
su –切换用户名
## 应用实例
创建一个用户zf, ，指定密码，然后切换到zf.

![image](http://image.damienzhong.com/linux%E5%88%87%E6%8D%A2%E7%94%A8%E6%88%B7.png)
## 细节说明
- 从权限高的用户切换到权限低的用户，不需要输入密码，反之需要。
- 当需要返回到原来用户时，使用exit指令
# 查看当前用户/登录用户
## 基本语法
- whoami
- who am I
# 用户组
## 介绍
类似于角色，系统可以对有共性的多个用户进行统一的管理。
## 新增组
groupadd 组名
## 删除组
groupdel 组名
## 增加用户时直接加上组
useradd –g 用户组 用户名
### 操作演示
增加一个用户zwj, 直接将他指定到wudang

![image](http://image.damienzhong.com/%E7%BB%99%E6%8C%87%E5%AE%9A%E7%94%A8%E6%88%B7%E5%88%86%E9%85%8D%E5%88%B0%E7%94%A8%E6%88%B7%E7%BB%84.png)
## 修改用户的组
usermod –g 用户组 用户名
### 案例演示
![image](http://image.damienzhong.com/%E4%BF%AE%E6%94%B9%E7%94%A8%E6%88%B7%E7%9A%84%E7%94%A8%E6%88%B7%E7%BB%84.png)
# 用户和组的相关文件
## /etc/passwd 文件
- 用户（user）的配置文件，记录用户的各种信息
- 每行的含义：用户名:口令:用户标识号:组标识号:注释性描述:主目录:登录Shell

![image](http://image.damienzhong.com/etcpasswd.png)
## /etc/shadow 文件
- 口令的配置文件
- 每行的含义：登录名:加密口令:最后一次修改时间:最小时间间隔:最大时间间隔:警告时间:不活动时间:失效时间:标志
## /etc/group 文件
- 组(group)的配置文件，记录Linux包含的组的信息
- 每行含义：组名:口令:组标识号:组内用户列表

![image](http://image.damienzhong.com/etcgroup.png)