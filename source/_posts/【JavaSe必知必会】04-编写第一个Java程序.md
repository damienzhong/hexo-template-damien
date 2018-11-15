---
title: 【JavaSe必知必会】04-编写第一个Java程序
date: 2018-11-15 11:14:18
tags: javase
categories: javase
---
# 前言
现在，大家应该都已经安装好jdk环境和环境变量配置好了吧！是不是已经跃跃欲试，按耐不住心中的小激动了？那我们现在就来写我们java学习生涯中的第一个java程序。
# 文件相关设置
为了方便后面大家的学习呢？有一点大家还是需要提前设置一下的，就是文件的相关设置（如果已经做过相关设置，跳过这一段）
首先随便进入一个文件夹，我们会发现文件夹下的文件都只有文件名，却没有文件是属于那种类型的后缀名，设置成功之后应该是长这样的，先给大家看设置成功的样子

![image](http://image.damienzhong.com/%E6%96%87%E4%BB%B6%E8%AE%BE%E7%BD%AE01.png)

如果你的已经是长这样了，那就不用设置啦，说明已经设置过了，如果不是长上面那样的同学，那你们就需要再往下看咯！

首先我们看一下文件夹上方的工具栏，是不是有一个工具选项，点击它，然后选择文件夹选项

![image](http://image.damienzhong.com/%E6%96%87%E4%BB%B6%E8%AE%BE%E7%BD%AE02.png)

选择查看，然后把显示隐藏的文件选择上，把隐藏已知文件的扩展名这个√去掉，搞定之后点击确定就大功告成了！

![image](http://image.damienzhong.com/%E6%96%87%E4%BB%B6%E8%AE%BE%E7%BD%AE03.png)

# 文本编辑器编写代码

可能很多朋友在看别的程序员敲代码的时候都是用各种炫酷的集成IDE开发工具，好黑科技的感觉对不对？不用羡慕他们，后面我们也会变得炫酷。那如何才能以后变得炫酷呢？骚年，莫急，现在我们就要介绍炫酷coding的开山鼻祖——文本编辑器直接直接写代码。

啥是文本编辑器？(⊙o⊙)…额，应该都知道吧。那我们就直接说咯！

首先自己选择一个文件夹，最好新建一个专门用于存储我们自己写的代码的文件夹，进入文件夹之后点击鼠标右键，选择新建，然后选择文本文档

![image](http://image.damienzhong.com/%E6%96%87%E4%BB%B6%E8%AE%BE%E7%BD%AE04.png)

把文件名重命名为HelloJava，把txt后缀名改为java，命名完成出现下图提示点击是

![image](http://image.damienzhong.com/%E6%96%87%E4%BB%B6%E8%AE%BE%E7%BD%AE05.png)

创建完成之后，我们会发现文件的类型变为Java类型，我们选中该文件，点击鼠标右键，选择编辑，打开文本编辑框后输入如下内容

![image](http://image.damienzhong.com/%E6%96%87%E4%BB%B6%E8%AE%BE%E7%BD%AE06.png)

编辑完成后关闭文件回到该文件所在目录（即文件夹），然后在当前目录打开命令行DOS窗口，输入命令javac HelloJava.java,然后回车，发现命令行DOS窗口没啥反应，但是如果你仔细一点，你会发现，当前目录下多了一个叫做HelloJava.class的文件，如下图

![image](http://image.damienzhong.com/%E6%96%87%E4%BB%B6%E8%AE%BE%E7%BD%AE07.png)

好，我先不解释它是啥，因为后续会说到，如果出现这一步，我们继续在DOS窗口输入下一条命令：java HelloJava，回车，是不是发现此时窗口里有反应了，多出了两行文字

![image](http://image.damienzhong.com/%E6%96%87%E4%BB%B6%E8%AE%BE%E7%BD%AE09.png)

这两行内容其实就是我们刚才在文本编辑器中的代码让其打出的，这就是用文本编辑器的方式编写运行代码的方式！

# Java9的JShell方式编写代码

什么是jshell呢？那我就简单的先给大家介绍一下。

> jshell是Java 9 新增的一个脚本工具，意思是可以在命令行里直接运行java的代码，而无需创建Java文件，然后再编译，最后运行。我觉得jshell的好处就是即写即得，平常只想看看几行代码运行的结果是怎么样的，有了jshell就方便多了，直接在命令行上敲。

那如何使用它呢？

打开DOS命令窗口，输入命令：jshell，回车，稍等几秒钟就会看到JShell启动成功的欢迎提示语，出现下图说明启动成功！

![image](http://image.damienzhong.com/jshell01.png)

然后，怎么用呢？比如，输入 1+1:

![image](http://image.damienzhong.com/jshell02.png)

结果输出$1 ==> 2，其中$1表示第一个临时变量。

如果输出我们刚才用文本编辑器输出的内容呢？

![image](http://image.damienzhong.com/jshell03.png)

我们再用它创建一个方法，方法具体是什么我们后面再详细说，现在先简单的看效果

![image](http://image.damienzhong.com/jshell04.png)

如果想修改方法，怎么办？重写吗？不用这样的亲，可以输入“/edit sum”，会弹出编辑界面：

![image](http://image.damienzhong.com/jshell05.png)
![image](http://image.damienzhong.com/jshell06.png)


调用修改过的方法，这里的j是我们定义的变量，所以它没有”$”符号。

![image](http://image.damienzhong.com/jshell07.png)

如果我们想看看之前自己所运行的所有脚本，我们可以用“/list”来查看

![image](http://image.damienzhong.com/jshell08.png)

然后，我们可以通过“/import”来查看脚本的默认导入的包，至于什么是包，就是当前程序运行需要引用的一些东西

![image](http://image.damienzhong.com/jshell09.png)

最后，我们输入“/exit”来退出jshell环境：

![image](http://image.damienzhong.com/jshell10.png)

# 结语
好啦，两种方式都介绍完了，赶紧去尝试一下吧！