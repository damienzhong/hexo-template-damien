---
title: 【Hexo搭建GitPage博客系列】03.Hexo博客搭建
date: 2018-11-19 21:43:36
tags: 
	- Hexo
	- 博客搭建
categories: blog
---
# 前言
前面我们已经把环境准备好了，接下来我们就可以正式开始我们的博客搭建之路了！
# 搭建步骤
## 创建Github仓库
- 点击创建仓库
![image](http://image.damienzhong.com/github%E5%88%9B%E5%BB%BA%E4%BB%93%E5%BA%93.png)
- 项目必须要遵守格式：账户名.github.io，不然接下来会有很多麻烦。并且需要勾选Initialize this repository with a README
![image](http://image.damienzhong.com/%E5%88%9B%E5%BB%BAgithub%E4%BB%93%E5%BA%932.png)
- 在建好的项目右侧有个settings按钮，点击它，向下拉到GitHub Pages，你会看到那边有个网址，访问它，你将会惊奇的发现该项目已经被部署到网络上，能够通过外网来访问它。如果没有，你可以直接在浏览器输入自己仓库名，在浏览器进行访问，能访问成功说明也OK。
![image](http://image.damienzhong.com/gitpage.png)
## 初始化博客
- 安装Hexo，在自己认为合适的地方创个文件夹，然后通过命令行进入到该文件夹里面
- 输入npm install hexo -g，开始安装Hexo
  ![image](http://image.damienzhong.com/%E5%AE%89%E8%A3%85hexo.png)
- 输入hexo -v，检查hexo是否安装成功

  ![image](http://image.damienzhong.com/hexo-v.png)
- 输入hexo init，初始化该文件夹（有点漫长的等待。。。）
  ![image](http://image.damienzhong.com/hexoinit.png)
- 输入npm install，安装所需要的组件
  ![image](http://image.damienzhong.com/npminstall.png)
- 输入hexo g，生成博客所需文件

  ![image](http://image.damienzhong.com/hexog.png)
- 输入hexo s，本地开启服务器，访问该网址，正式体验Hexo
  ![image](http://image.damienzhong.com/hexos.png)
- 出现如下图就成功了
  ![image](http://image.damienzhong.com/hexo%E9%A2%84%E8%A7%88.png)
## 发布博客到Github
- 配置Deployment，在其文件夹中，找到_config.yml文件，修改repo值（在末尾）
  ![image](http://image.damienzhong.com/%E9%85%8D%E7%BD%AE%E6%96%87%E4%BB%B6%E4%BD%8D%E7%BD%AE.png)

![image](http://image.damienzhong.com/deploy_config.png)
- repo值的获取位置，需要把Clone方式切换成SSH形式，然后复制地址就可以了
  ![image](http://image.damienzhong.com/repo%E5%80%BC%E8%8E%B7%E5%8F%96.png)
- 在生成以及部署文章之前，需要安装一个扩展：npm install hexo-deployer-git --save
![image](http://image.damienzhong.com/hexo-deployer.png)
- 使用命令：hexo d -g就可以进行生成部署到Github上了

  ![image](http://image.damienzhong.com/hexo%E9%83%A8%E7%BD%B2%E5%8D%9A%E5%AE%A2.png)
- 部署成功后访问你的地址：http://用户名.github.io。那么将看到我们之前在本地部署一样的页面，说明我们就部署成功啦！