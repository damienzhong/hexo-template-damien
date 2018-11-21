---
title: 【Hexo搭建GitPage博客系列】06.绑定独立域名
date: 2018-11-21 18:25:44
tags: 
	- Hexo
	- 博客搭建
categories: blog
---
# 前言
因为Hexo个人博客是托管在github之上，每次访问都要使用githubname.github.io这么一个长串的域名来访问，会显得非常繁琐。这个时候我们可以购买一个域名，设置DNS跳转，以达到通过域名即可访问我们的个人博客。通过查阅文档发现，github pages是支持域名绑定的。
# 购买域名
国内的域名服务商有新网，腾讯云，还有阿里云的万网等。下面以阿里云的万网为例：

在万网购买了自己心仪的域名后，进入阿里云的管理控制台-域名与网站-域名就可以看到购买的域名此时的域名状态是未实名认证的，然后就是实名认证（一般需要2小时左右）。
# 域名解析
先获取自己 github 的二级域名的 IP地址，windows 下直接在 cmd 里 ping 一下自己的博客就会得到 IP 地址
![image](http://image.damienzhong.com/ping%E5%9F%9F%E5%90%8D.png)

下面通过 DNS域名解析将购买的域名指向 github 的二级域名：username.github.io，进入阿里云的管理控制台-域名与网站-云解析 DNS，进入域名的解析设置，点击新手指导，将得到的 IP 地址填到记录值一栏，点击确定就 OK 了。填完以后的解析列表会出现：
![image](http://image.damienzhong.com/DNS%E8%AE%BE%E7%BD%AE.png)
记录值就是自己 github 的二级域名的 IP地址。
# 设置CNAME
在 hexo 项目下，source 文件夹下面创建 CNAME 文件（没有后缀名的），在里面写上购买的域名。比如：

![image](http://image.damienzhong.com/%E8%AE%BE%E7%BD%AECNAME.png)
在 github 上面，打开 username.github.io 项目的（Settings）设置，然后在 GitHub Pages的 Custom domain设置里填上购买的域名。比如：
![image](http://image.damienzhong.com/gitpage%E5%9F%9F%E5%90%8D%E8%AE%BE%E7%BD%AE.png)

好了，新域名配置完成，可以访问了。