---
title: 【Hexo搭建GitPage博客系列】04.主题更换
date: 2018-11-20 14:43:33
tags: 
	- Hexo
	- 博客搭建
categories: blog
---
# 前言
前面我们介绍了如何从零开始搭建Hexo博客，并且已经部署到Github上去了。每个人的审美观不一样，所以肯定会有人不喜欢当前的博客主题。接下来，我就为大家介绍如何更换博客主题，让博客变得更加炫酷。
# 主题切换
Hexo的默认主题是landscape，就是刚刚搭建好以后大家看到的样子。

估计很多小伙伴都不太喜欢这样的风格，其实我们可以很容易做一些主题的切换和配置。在[Hexo官网](https://hexo.io/themes/)提供了很多主题（theme）风格，大家可以挑选自己喜欢的主题进行配置和调整。
![image](http://image.damienzhong.com/hexo%E5%AE%98%E7%BD%91.png)

在Hexo选择一款你喜欢的主题，点击图片预览demo，点击下面的名字进入该主题的github项目或者官方网站。

这里我们以[Next主题](http://theme-next.iissnan.com/getting-started.html)为例子，因为这个主题比较成熟，而且有详细的官方文档可以帮助你快速地安装和配置。关于主题的安装和配置很简单，在这里就不演示了，大家可以根据官方文档的指示完成。
## 安装主题
在博客themes目录下右键点击Git Bash，输入以下命令。其他的主题也类似操作。
```
git clone https://github.com/主题git路径
```
## 启用主题
修改博客根目录下的_config.yml中的theme属性，将其设置为你下载下来的主题名。
```
theme: zhutiming
```
## 配置主题
如果你需要定制主题相关配置显得更加个性化，修改主题目录下的_config.yml配置文件
## 主题发布
分别在Git Bash中执行如下指令发布博客到Github

```
hexo clean
```

```
hexo g
```

```
hexo d
```
部署成功后访问你的地址：http://用户名.github.io，查看效果，有时候有缓存，需要多刷新几次。