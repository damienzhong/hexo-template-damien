---
title: 【Hexo搭建GitPage博客系列】02.环境搭建
date: 2018-11-19 21:38:40
tags: 博客搭建
categories: blog
---
# 前言
Hexo搭建博客需要基于Node.js环境，而且依赖于Git，本篇文章就给大家详细介绍如何搭建环境。
# Node环境搭建
Node.js 是一个基于 Chrome V8 引擎的 JavaScript 运行环境。Node.js 使用了一个事件驱动、非阻塞式 I/O 的模型，使其轻量又高效。 Node.js 的使用包管理器 npm来管理所有模块的安装、配置、删除等操作，使用起来非常方便，但是想要配置好npm的使用环境还是稍微有点复杂，下面跟着我一起来学习在windows系统上配置NodeJS和NPM吧。
## 安装NodeJS
打开NodeJS的官网，默认的情况主页就提供了Windows版本的下载链接，我们下载LTS版，LTS代表长期支持版本，一般新手建议使用这个版本，因为这个版本使用的人最多，出问题能找到解决方案的概率较大。如下图所示：
![image](http://image.damienzhong.com/nodejs%E7%89%88%E6%9C%AC%E9%80%89%E6%8B%A9.png)
- 下载之后直接打开执行安装操作，直接NEXT
- 这一步是选择安装哪些模块，默认是全部安装，对于新手来说建议全部安装。点开那个add path选项前面的+号，我们看到，会主动把NodeJS和NPM这两个模块的命令路径添加到系统路径里，对于我们来说就非常方便了。点击next继续下一步，然后确认信息，点击Install开始安装，然后程序就开始复制文件等一系列步骤。一直到安装完毕。
![image](http://image.damienzhong.com/nodejs%E5%AE%89%E8%A3%85%E6%A8%A1%E5%9D%97%E9%80%89%E6%8B%A9.png)
- 安装完毕后点击finish结束安装进程，然后在桌面图标上点右键，点运行。输入cmd后敲回车，在打开的命令行界面，依次输入命令：
  - node -v
  - npm -v
![image](http://image.damienzhong.com/nodejs%E9%AA%8C%E8%AF%81.png)
# 安装Git
- 访问Git官网下载地址：https://git-scm.com/downloads
- 选择对应自己操作系统的Git客户端进行下载。
- 打开下载好的文件，执行安装步骤，一路NEXT
- 安装Git和配置好Git环境，安装成功的象征就是在电脑上任何位置鼠标右键能够出现如下两个选择

![image](http://image.damienzhong.com/git%E5%AE%89%E8%A3%85%E9%AA%8C%E8%AF%81.png)
## 设置本地Git与Github远程SSH
后面的操作需要你已经注册了Github账号，如果没有，请先去注册。
- 输入cd ~/.ssh，检查是否有.ssh的文件夹
  - 如果没有，提示如下图，如果有，删除该文件
  ![image](http://image.damienzhong.com/%E6%B2%A1%E6%9C%89ssh%E6%96%87%E4%BB%B6.png)
  - 然后切换到主用户目录下cd ~，并生成.ssh文件ssh-keygen -t rsa -C "xxxx@xxx.xxx"，执行命令之后连续回车三次
  ![image](http://image.damienzhong.com/%E7%94%9F%E6%88%90ssh%E6%96%87%E4%BB%B6.png)
  - 打开.ssh文件中的id_rsa.pub，复制其中的信息 
  - 之后进入GitHub，右上角头像下拉选择Settings，弹出界面中左侧栏选择SSH and GPG keys，然后选择New SSH key，将之前复制的id_rsa.pub粘贴到key栏中，title随便取，之后点击Add SSH key就完事儿啦
  ![image](http://image.damienzhong.com/addsshkey.png)
  - 之后在本地配置好config信息
  
  ![image](http://image.damienzhong.com/git%E8%AE%BE%E7%BD%AEssh01.png)
  - 输入ssh -T git@github.com，测试添加ssh是否成功。如果看到Hi后面是你的用户名，就说明成功了
  ![image](http://image.damienzhong.com/%E6%B5%8B%E8%AF%95ssh.png)

