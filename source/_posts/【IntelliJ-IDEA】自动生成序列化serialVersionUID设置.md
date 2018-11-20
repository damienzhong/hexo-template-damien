---
title: 【IntelliJ IDEA】自动生成序列化serialVersionUID设置
date: 2018-11-20 18:18:31
tags: 
	- idea
	- IntelliJ IDEA
categories: 工具教程
---
# 自动生产序列ID
## 前言
实体类继承 java.io.Serializable后，需要设置序列化ID，java的序列化机制是通过在运行时判断类的serialVersionUID来验证版本一致性的。在进行反序列化时，JVM会把传来的字节流中的serialVersionUID与本地实体类中的serialVersionUID进行比较，如果相同则认为是一致的，便可以进行反序列化，否则就会报序列化版本不一致的异常。而IDEA，默认是不支持自动生成序列化ID的（我使用的是IDEA2017版本）。
## 具体设置
![image](http://image.damienzhong.com/idea%E8%87%AA%E5%8A%A8%E7%94%9F%E6%88%90%E5%BA%8F%E5%88%97%E5%8F%B7.png)
如上图所示，我们首先打开设置面板：==File > Settings==，然后定位到==Editor > Inspections==,找到==Java==选项，然后点开==Serialization issues==,然后找到==Serializable class without serialVersion==，勾选，然后点击==Apply==应用即可。
## 效果演示
我们新建一个==SerialIDTest==类进行测试，新建之后让该类实现==Serializable==接口，然后键盘按==Alt+Enter==键，弹出如下窗口：
![image](http://image.damienzhong.com/idea%E5%BA%8F%E5%88%97%E8%AF%9Did02.png)
鼠标点击==Add ‘SerialVersion’ field==或者直接回车即可自动生成序列化ID，如下效果图：
![image](http://image.damienzhong.com/idea%E5%BA%8F%E5%88%97%E5%8C%96ID03.png)