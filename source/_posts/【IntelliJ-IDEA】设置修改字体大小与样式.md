---
title: 【IntelliJ IDEA】设置修改字体大小与样式
date: 2018-11-20 18:14:48
tags: 
	- idea
	- IntelliJ IDEA
categories: 工具教程
---
# 字体修改
## 界面主题字体修改
![image](http://image.damienzhong.com/idea%E4%B8%BB%E9%A2%98%E5%AD%97%E4%BD%93%E4%BF%AE%E6%94%B901.png)
- 标注1：点击工具栏最上方的File选项
- 标注2：选择Setting选项
![image](http://image.damienzhong.com/idea%E4%B8%BB%E9%A2%98%E5%AD%97%E4%BD%93%E4%BF%AE%E6%94%B902.png)
- 标注1：重写默认主题字体（必选）
- 标注2：具体可以修改字体大小的数值

如上图所示，我们定位到==Appearance & Behavior > Appearance==界面，如果确定要修改主题字体大小的话，**标注1** 所示的==Override default fonts by XXX==为必选项，否则的话，不能修改字体，因为 IntelliJ IDEA 默认是不推荐修改的；**标注2** 所示的为我们具体可以修改字体大小的数值。在这里，选择Size为 20，演示一下修改后的效果：
![image](http://image.damienzhong.com/idea%E4%B8%BB%E9%A2%98%E5%AD%97%E4%BD%93%E4%BF%AE%E6%94%B9%E6%95%88%E6%9E%9C.png)
如上图所示，这是在选择==Size==为 14、点击==Apply==之后的效果，显然界面主题的字体明显都变大了很多。

在这里，有一点需要注意，那就是：有的字体是包含中文的，有的字体则是不包含中文的。一般情况下，使用英文的国家是不需要额外担心乱码问题的，但是我们需要啊！如果我们选择的字体不包含中文的话，很多位置上可能会出现类似于 口口口口口 这样的乱码问题。例如，==Courier New==和==Monaco==就是纯英文字体，而==Microsoft YaHei==就是包含中文的字体。
## 代码编辑区字体修改
与第一张图一样，先进入setting设置弹框==File > Settings==,然后定位到==Editor > Font==
![image](http://image.damienzhong.com/idea%E7%BC%96%E8%BE%91%E5%99%A8%E5%AD%97%E4%BD%93%E5%A4%A7%E5%B0%8F%E4%BF%AE%E6%94%B9.png)
- 标注1：字体具体大小的数值
- 标注2：行宽（行与行之间的距离）

如上图所示，我们定位到==Editor > Font==界面，在这里，我们选择Size为 16，演示一下修改后的效果：
![image](http://image.damienzhong.com/idea%E7%BC%96%E8%BE%91%E5%99%A8%E5%AD%97%E4%BD%93%E5%A4%A7%E5%B0%8F%E4%BF%AE%E6%94%B9%E6%95%88%E6%9E%9C.png)
如上图所示，这是在选择==Size==为 16、点击==Apply==之后的效果，显然编辑区主题的字体明显都变大了很多。
## 控制台输出字体修改
![image](http://image.damienzhong.com/idea%E6%8E%A7%E5%88%B6%E5%8F%B0%E5%AD%97%E4%BD%93%E5%A4%A7%E5%B0%8F%E4%BF%AE%E6%94%B9.png)
如上图所示，我们定位到==Editor > Color Scheme > Console Font== 
- 标注1：是否替换默认字体大小（需要修改的话就勾选）
- 标注2：字体具体大小的数值
- 标注3：行宽（行与行之间的距离）

在这里，我们选择Size为 16，演示一下修改后的效果：
![image](http://image.damienzhong.com/idea%E6%8E%A7%E5%88%B6%E5%8F%B0%E5%AD%97%E4%BD%93%E5%A4%A7%E5%B0%8F%E4%BF%AE%E6%94%B9%E6%95%88%E6%9E%9C.png)
如上图所示，这是在选择==Size==为 16、点击==Apply==之后的效果，运行程序后，控制台的输出字体显示大了，也清晰了很多。

