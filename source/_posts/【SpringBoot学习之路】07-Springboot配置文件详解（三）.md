---
title: 【SpringBoot学习之路】07.Springboot配置文件详解（三）
date: 2018-11-20 23:05:55
tags: 
	- springboot
categories: 常用框架
---
# Profile多环境支持
Profile是Spring对不同环境提供不同配置功能的支持，可以通过激活、指定参数等方式快速切换环境
## 多Profile文件
- 我们在主配置文件编写的时候，文件名可以是 application-{profile}.properties/yml
- 默认使用application.properties的配置；
## yml支持多文档块方式
```
server:
  port: 8081
spring:
  profiles:
    active: dev #激活指定配置
--- #三个短横线分隔多个profiles区
server:
  port: 8091
spring:
  profiles: dev
---
server:
  port: 8092
spring:
  profiles: prod #指定属于哪个环境
---
server:
  port: 8080
spring:
  profiles: default #表示未指定默认配置
```
## 激活指定profile
- 在配置文件中指定 spring.profiles.active=dev
- 命令行：
  - java -jar spring-boot-02-config-0.0.1-SNAPSHOT.jar --spring.profiles.active=dev
  - 可以直接在测试的时候，配置传入命令行参数
- 虚拟机参数；
  - -Dspring.profiles.active=dev
# 配置文件加载位置
springboot 启动会扫描以下位置的application.properties或者application.yml文件作为Spring boot的默认配置文件
- –file:./config/
- –file:./
- –classpath:/config/
- –classpath:/
> 以上是按照优先级从高到低的顺序，所有位置的文件都会被加载，高优先级配置内容会覆盖低优先级配置内容。

SpringBoot会从这四个位置全部加载主配置文件；互补配置；

我们还可以通过spring.config.location来改变默认的配置文件位置。

**项目打包好以后，我们可以使用命令行参数的形式，启动项目的时候来指定配置文件的新位置；指定配置文件和默
认加载的这些配置文件共同起作用形成互补配置；**

java -jar spring-boot-02-config-02-0.0.1-SNAPSHOT.jar --spring.config.location=配置文件路径
# 外部配置加载顺序
==**Spring Boot 支持多种外部配置方式
SpringBoot也可以从以下位置加载配置； 优先级从高到低；高优先级的配置覆盖低优先级的配置，所有的配置会
形成互补配置**==
#### 1.命令行参数
- 所有的配置都可以在命令行上进行指定
- java -jar spring-boot-02-config-02-0.0.1-SNAPSHOT.jar --server.port=8087 --server.context-path=/abc
- 多个配置用空格分开； --配置项=值
#### 2.来自java:comp/env的JNDI属性
#### 3.Java系统属性（System.getProperties()）
#### 4.操作系统环境变量
#### 5.RandomValuePropertySource配置的random.*属性值
### 由jar包外向jar包内进行寻找；
### 优先加载带profile
#### 6.jar包外部的application-{profile}.properties或application.yml(带spring.profile)配置文件
#### 7.jar包内部的application-{profile}.properties或application.yml(带spring.profile)配置文件
### 再来加载不带profile
#### 8.jar包外部的application.properties或application.yml(不带spring.profile)配置文件
#### 9.jar包内部的application.properties或application.yml(不带spring.profile)配置文件
#### 10.@Configuration注解类上的@PropertySource
#### 11.通过SpringApplication.setDefaultProperties指定的默认属性