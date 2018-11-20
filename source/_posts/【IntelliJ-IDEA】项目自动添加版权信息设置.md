---
title: 【IntelliJ IDEA】项目自动添加版权信息设置
date: 2018-11-20 18:17:06
tags: 
	- idea
	- IntelliJ IDEA
categories: 工具教程
---
# 自动添加项目版权信息设置
![image](http://image.damienzhong.com/idea%E4%B8%BB%E9%A2%98%E5%AD%97%E4%BD%93%E4%BF%AE%E6%94%B901.png)
- 标注1：点击工具栏最上方==的File==选项
- 标注2：选择==Setting==选项 
## 方案一
![image](http://image.damienzhong.com/idea%E7%89%88%E6%9D%83%E8%AE%BE%E7%BD%AE01.png)
- 标注1：新增版权按钮

如上图所示，我们定位到==Editor > Copyright > Copyright Profiles==，如果确定要新增版权信息的话，点击**标注1** 所示的新型按钮，点击之后弹出版权名输入框，效果图如下：
![image](http://image.damienzhong.com/idea%E7%89%88%E6%9D%83%E8%AE%BE%E7%BD%AE02.png)
- 标注1：版权名输入框（输入自己的版权名）
- 标注2：确认按钮（确认新增则点击）

如上图所示，我们这里新增一个名为==damienzhong==的版权名，点击OK之后出现如下效果图：
![image](http://image.damienzhong.com/idea%E7%89%88%E6%9D%83%E8%AE%BE%E7%BD%AE03.png)
- 标注1：版权名输入框（在此可以更改版权名）
- 标注2：版权声明信息文本框（在此输入版权声明信息）
- 标注3：版权验证按钮
- 标注4：应用按钮（设置完必须点击，否则设置不生效）

如上图所示，我们按标注的顺序挨个进行操作，然后定位到上一级==Editor > Copyright==
![image](http://image.damienzhong.com/idea%E7%89%88%E6%9D%83%E8%AE%BE%E7%BD%AE04.png)
- 标注1：菜单选项（定位到此）
- 标注2：默认项目版权（点击下拉框选择你的的版权名）

如上图所示，我们直接点击默认版权的下拉框，在这里我们选择damienzhong这个版权名，选择完之后我们看下图：
![image](http://image.damienzhong.com/idea%E7%89%88%E6%9D%83%E8%AE%BE%E7%BD%AE05.png)
- 标注1：新增版权使用按钮（点击此按钮）
- 标注2：版权生效域（选择你需要添加版权的区域）
- 标注3：应用按钮

如上图所示，我们这边先点击+号按钮，然后选择==All==，代表所有区域，然后点击==Apply==按钮，即可生效。生效之后我们新建一个类文件，效果图如下：
![image](http://image.damienzhong.com/idea%E7%89%88%E6%9D%83%E8%AE%BE%E7%BD%AE06.png)
如上图所示，红框部分就是我们刚才所设置的版权信息。
## 方案二（方案一不生效用此方法）
打开==Setting==选项，定位到==Plugins==,如下图所示：
![image](http://image.damienzhong.com/idea%E7%89%88%E6%9D%83%E8%AE%BE%E7%BD%AE07.png)
- 标注1：选项路径
- 标注2：浏览器插件仓库查询按钮（点击此按钮）

我们点击**标注2**的按钮，出现弹框，如下图所示：
![image](http://image.damienzhong.com/idea%E7%89%88%E6%9D%83%E8%AE%BE%E7%BD%AE08.png)
- 标注1：搜索输入框（输入Copyright）
- 标注2：Copyright插件（选择此插件）
- 标注3：安装按钮（点击安装）

如上图所示，我们按标注的顺序进行操作，出现如下效果图：
![image](http://image.damienzhong.com/idea%E7%89%88%E6%9D%83%E8%AE%BE%E7%BD%AE09.png)

我们点击重启按钮，重启IDEA，重启之后按**方案一**的操作方式操作一遍即可生效，这边就不再重复演示了。
