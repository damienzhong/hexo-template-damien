---
title: 【SpringBoot学习之路】04.Springboot项目快速搭建
date: 2018-11-20 23:02:56
tags: 
	- springboot
categories: 常用框架
---
# 方式一
### IDEA：使用 Spring Initializer快速创建项目
- 选择Spring Initializer选项，然后Next

![image](http://image.damienzhong.com/springboot%E5%BF%AB%E9%80%9F%E5%88%9B%E5%BB%BA.png)
- 编辑Group与Artifact，然后直接下一步

![image](http://image.damienzhong.com/springbootquick.png)
- 选择所需的依赖，然后下一步

![image](http://image.damienzhong.com/springbootquick2.png)
- 直接点击Finish

![image](http://image.damienzhong.com/springbootquick3.png)
# 方式二
- 用浏览器打开地址：https://start.spring.io/

![image](http://image.damienzhong.com/springbootquick4.png)
- 把下载下来的项目解压，用IDEA打开即可
# 总结
默认生成的Spring Boot项目
  - 主程序已经生成好了，我们只需要我们自己的逻辑
  - resources文件夹中目录结构
    - static：保存所有的静态资源； js css images；
    - templates：保存所有的模板页面；（Spring Boot默认jar包使用嵌入式的Tomcat，默认不支持JSP页面）；可以使用模板引擎（freemarker、thymeleaf）；
    - application.properties：Spring Boot应用的配置文件；可以修改一些默认设置；