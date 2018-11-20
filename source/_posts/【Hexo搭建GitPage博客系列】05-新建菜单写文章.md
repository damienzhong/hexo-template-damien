---
title: 【Hexo搭建GitPage博客系列】05.新建菜单写文章
date: 2018-11-20 15:00:05
tags: 
	- Hexo
	- 博客搭建
categories: blog
---
在Hexo博客系统中, 可以创建菜单、文章、分类、标签。在我们的主题中,菜单和文章需要手动创建,而分类和标签不用手动创建,
# 创建菜单
在博客根目录下打开Git Bash执行如下命令创建一个新的菜单：hexo new page "菜单名"
```
$ hexo new page "虚拟化"
INFO  =========================================
INFO    Welcome to use Snippet theme for hexo
INFO  =========================================
INFO  Created: D:\DamienGit\hexo-blog-template\source\虚拟化\index.md
```
这个指令会在source目录创建一个名为“虚拟化”的文件夹,并在文件夹中创建一个index.md的文件 

修改index.md文件，指定type
```
---
title: 虚拟化
date: 2018-11-20 14:18:39
type: 虚拟化
---

```
然后在进入theme文件夹下的主题文件夹里面的_config.yml配置文件，在里面的menu配置选项中新增一个虚拟化菜单选项
```
## menu
menu:
- page: home
  url: /
  icon: fa-home
- page: Java基础
  url: /categories/javase/
  icon: 
- page: 博客教程
  url: /categories/blog/
  icon: 
- page: 虚拟化
  url: /categories/虚拟化/
  icon:
```
本地部署查看效果执行如下命令
```
$ hexo clean && hexo g && hexo s
```
![image](http://image.damienzhong.com/%E6%96%B0%E5%A2%9E%E8%8F%9C%E5%8D%95%E6%95%88%E6%9E%9C.png)

当你点击新增的菜单的时候可能会报404找不到页面的提示，是因为该目录下没有文章，后续我们指定文章到该菜单下就可以了，往下看即可解决
# 写文章
在博客根目录下打开Git Bash执行如下命令创建文章：hexo new "文章名"
```
$ hexo new "【Hexo搭建GitPage博客系列】04.主题更换"
INFO  =========================================
INFO    Welcome to use Snippet theme for hexo
INFO  =========================================
INFO  Created: D:\DamienGit\hexo-blog-template\source\_posts\【Hexo搭建GitPage博客系列】04-主题更换.md
```
命令执行完毕后可以看到source/_posts/目录下生产了一个刚才我们创建的同名md文件。

打开该文件进行编辑博文
```
---
title: 【Hexo搭建GitPage博客系列】04.主题更换
date: 2018-11-20 14:43:33
tags:
---
博文内容写这里
```
本地部署查看效果执行如下命令
```
$ hexo clean && hexo g && hexo s
```
## 文章指定分类与标签

```
title: 【Hexo搭建GitPage博客系列】04.主题更换
date: 2018-11-20 14:43:33
tags:           //标签名
	- Hexo 
	- 博客搭建
categories: 虚拟化  //分类名
```
![image](http://image.damienzhong.com/%E8%8F%9C%E5%8D%95%E6%95%88%E6%9E%9C2.png)