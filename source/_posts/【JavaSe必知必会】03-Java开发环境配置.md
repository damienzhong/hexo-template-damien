---
title: 【JavaSe必知必会】03-Java开发环境配置
date: 2018-11-15 10:00:34
tags: javase
categories: javase
---
# 前言
在上一篇文章对Java做了一个简单介绍之后，我想大家都已经对她有一个初步的认识了吧！那踏入正式学习使用Java之前，我们有一步是不得不做的，它是什么呢？没有错，就是我们本篇文章的标题所说，搭建Java的开发环境配置。那我们就正式进入主题吧！
# JDK的下载与安装
## JDK下载
- 通过官方网站获取JDK
http://www.oracle.com
- 针对不同操作系统，下载不同的JDK版本
识别计算机的操作系统
### 下载图解
1. 浏览器访问==Oracle==官网：http://www.oracle.com
![image](http://image.damienzhong.com/jdk%E4%B8%8B%E8%BD%BD01.png)
- 标注1：浏览器输入==Oracle==官网地址（回车）
- 标注2：点击==Java==选项
- 标注3：选择==Java SE==选项（等待跳转新页面）
2. 找到Java开发平台，访问链接
![image](http://image.damienzhong.com/jdk%E4%B8%8B%E8%BD%BD02.png)
- 标注1：选择==Technologies==（技术）选项
- 标注2：选择==Java SE==选项
- 标注3：点击==Java Platform, Standard Edition==链接
3. 选择自己想要的JDK版本，进入下载页面
![image](http://image.damienzhong.com/jdk%E4%B8%8B%E8%BD%BD03.png)
- 标注1：选择==Download==选项
- 标注2：点击==JDK==下的==DOWNLOAD==按钮（选择自己想要下载的JDK版本）
4. 选择想要下载的版本号进行下载（这里选择==Jdk8==的==8u162==）
![image](http://image.damienzhong.com/jdk%E4%B8%8B%E8%BD%BD04.png)
- 标注1：选择接受版本协议（必选）
- 标注2：根据自己的==操作系统位数==选择对应版本进行下载
### Windows操作系统位数查看
- 回到桌面，找到==我的电脑==-->==鼠标右键==-->==属性==
![image](http://image.damienzhong.com/jdk%E4%B8%8B%E8%BD%BD05.png)
- 标注1：操作系统位数（图片显示的是64位操作系统）

## JDK安装
1. 找到之前下载的JDK安装文件

![image](http://image.damienzhong.com/jdk%E5%AE%89%E8%A3%8501.png)

- 标注1：该文件即为java安装可执行文件

2. 双击该文件执行安装，弹出如下图：

![image](http://image.damienzhong.com/jdk%E5%AE%89%E8%A3%8502.png)

- 标注1：点击下一步
3. 定制安装弹窗：

![image](http://image.damienzhong.com/jdk%E5%AE%89%E8%A3%8503.png)

- 标注1：选择==开发工具==
- 标注2：更改到自己想要存放的文件目录
- 标注3：点击下一步
4. 等待进度条加载完成（此过程中不要进行任何操作）

![image](http://image.damienzhong.com/jdk%E5%AE%89%E8%A3%8504.png) 

5. 安装==Jre==

![image](http://image.damienzhong.com/jdk%E5%AE%89%E8%A3%8505.png)
- 标注1：把Jre的安装目录更改成和之前Jdk的同级目录
- 标注2：点击下一步
6. 等待安装进度条执行完

![image](http://image.damienzhong.com/jdk%E5%AE%89%E8%A3%8506.png)

7. 弹出安装成功窗口

![image](http://image.damienzhong.com/jdk%E5%AE%89%E8%A3%8507.png)
- 标注1：直接点击关闭即可
### 验证安装结果
![image](http://image.damienzhong.com/jdk%E5%AE%89%E8%A3%8508.png)
- 标注1：DOS窗口命令行输入：==java==，回车，展示如上图片内容则安装成功
# JDK目录介绍
![image](http://image.damienzhong.com/jdk%E7%9B%AE%E5%BD%95%E4%BB%8B%E7%BB%8D01.png)
- bin：JDK的各种工具命令即JDK开发工具的可执行文件其中这些可执行文件都是二进制的
- db：jdk自带数据库
- include：一些供C语言使用的标题文件
- jre：运行Java程序所必须的JRE环境
- lib：支持Java运行的核心类库
- src：Java所有核心类库的源代码
# 环境变量配置
> 环境变量（environment variables）一般是指在操作系统中用来指定操作系统运行环境的一些参数，如：临时文件夹位置和系统文件夹位置等。
> 
> 环境变量是在操作系统中一个具有特定名字的对象，它包含了一个或者多个应用程序所将使用到的信息。例如Windows和DOS操作系统中的path环境变量，当要求系统运行一个程序而没有告诉它程序所在的完整路径时，系统除了在当前目录下面寻找此程序外，还应到path中指定的路径去找。用户通过设置环境变量，来更好的运行进程。
1. 找到我的电脑，点击鼠标右键，选择属性，弹出如下窗口
![image](http://image.damienzhong.com/%E7%8E%AF%E5%A2%83%E5%8F%98%E9%87%8F%E9%85%8D%E7%BD%AE01.png)
- 标注1：点击==高级系统设置==
2. 点击环境变量按钮
![image](http://image.damienzhong.com/%E7%8E%AF%E5%A2%83%E5%8F%98%E9%87%8F%E9%85%8D%E7%BD%AE02.png)
- 标注1：环境变量按钮
3. 点击==环境变量==下的==新建按钮==
![image](http://image.damienzhong.com/%E7%8E%AF%E5%A2%83%E5%8F%98%E9%87%8F%E9%85%8D%E7%BD%AE03.png)
4. 新建==JAVA_HOME==变量
![image](http://image.damienzhong.com/%E7%8E%AF%E5%A2%83%E5%8F%98%E9%87%8F%E9%85%8D%E7%BD%AE04.png)
- 标注1：变量名为“JAVA_HOME”(复制我引号内的内容就可以了，不含引号）
- 标注2：变量值，必须是自己装jdk时的路径
- 标注3：设置完成点击确定按钮
5. 找到“CLASSPATH”,没有的话就“新建”
![image](http://image.damienzhong.com/%E7%8E%AF%E5%A2%83%E5%8F%98%E9%87%8F%E9%85%8D%E7%BD%AE05.png)
- 标注1：变量名为“==CLASSPATH==”(复制我引号内的内容就可以了，不含引号）
- 标注2：变量值“==.;%JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar;==”(不含引号）
- 标注3：设置完成点击确定按钮
6. 找到Path，对其进行编辑
![image](http://image.damienzhong.com/%E7%8E%AF%E5%A2%83%E5%8F%98%E9%87%8F%E9%85%8D%E7%BD%AE06.png)
- 标注1：==%JAVA_HOME%\bin==
- 标注2：==%JAVA_HOME%\jre\bin==
- 标注3：设置完成点击确定按钮，把之前窗口的所有确定按钮都点击
## 验证方式
- 任意窗口下打开Dos窗口，输入命令==javac==，看是否输出如下图所示内容，有则配置成功
![image](http://image.damienzhong.com/%E7%8E%AF%E5%A2%83%E5%8F%98%E9%87%8F%E9%85%8D%E7%BD%AE07.png)