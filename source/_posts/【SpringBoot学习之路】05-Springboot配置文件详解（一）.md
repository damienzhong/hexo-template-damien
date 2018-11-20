---
title: 【SpringBoot学习之路】05.Springboot配置文件详解（一）
date: 2018-11-20 23:03:59
tags: 
	- springboot
categories: 常用框架
---
# 配置文件
- Spring Boot使用一个全局的配置文件
  - application.properties
  - application.yml
- 配置文件放在src/main/resources目录或者类路径/config下
- 全局配置文件的可以对一些默认配置值进行修改
## YAML配置文件
- 以前的配置文件；大多都使用的是 xxxx.xml文件
- yml是YAML（YAML Ain't Markup Language）语言的文件，以数据为中心，比json、xml等更适合做配置文件
### 配置例子
#### YAML

```
server:
  port: 8081
```
#### XML

```
<server>
    <port>8081</port>
</server>
```
### YAML基本语法
- 使用缩进表示层级关系
- 缩进时不允许使用Tab键，只允许使用空格。
- 缩进的空格数目不重要，只要相同层级的元素左侧对齐即可
- 大小写敏感
### YAML支持的三种数据结构
- 对象：键值对的集合
- 数组：一组按次序排列的值
- 字面量：单个的、不可再分的值
#### 对象（Map）
- 对象的一组键值对，使用冒号分隔。如：username: admin
- 冒号后面跟空格来分开键值；
- {k: v}是行内写法
##### k: v的方式
```
person:
  name: damienzhong
  age: 18
```
##### 行内写法

```
perosn: {name: damienzhong,age: 18}
```
#### 数组
- 一组连词线（-）开头的行，构成一个数组，[]为行内写法
- 数组，对象可以组合使用

```
animals:
  - cat
  - dog
  - pig
```
##### 行内写法

```
animals: [cat,dog,pig]
```
#### 字面量
- 数字、字符串、布尔、日期
- 字符串
  - 默认不使用引号
  - 可以使用单引号或者双引号，单引号会转义特殊字符
  - 字符串可以写成多行，从第二行开始，必须有一个单空格缩进。换行符会被转为空格。
### 配置文件值注入
#### 配置文件

```
person:
  lastName: 呆萌钟
  age: 20
  boss: true
  birth: 2018/10/30
  maps: {k1: v1,k2: v2}
  lists:
    - zhangsan
    - lisi
  dog:
    name: 哈士奇
    age: 6
```
#### javaBean

```
/**
 * 将配置文件中配置的每一个属性的值，映射到这个组件中
 * @ConfigurationProperties：告诉SpringBoot将本类中的所有属性和配置文件中相关的配置进行绑定；
 *      prefix = "person"：配置文件中哪个下面的所有属性进行一一映射
 *
 * 只有这个组件是容器中的组件，才能容器提供的@ConfigurationProperties功能；
 *  @ConfigurationProperties(prefix = "person")默认从全局配置文件中获取值；
 *
 */
@Component
@ConfigurationProperties(prefix = "person")
public class Person {
    private String lastName;
    private Integer age;
    private Boolean boss;
    private Date birth;
    private Map<String,Object> maps;
    private List<Object> lists;
    private Dog dog;
}

```
我们可以导入配置文件处理器，以后编写配置就有提示了

```
 <!--导入配置文件处理器，配置文件进行绑定就会有提示-->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-configuration-processor</artifactId>
            <optional>true</optional>
        </dependency>
```
## peroperties配置文件

```
person.last-name=呆萌钟
person.age=20
person.boss=true
person.birth=2018/10/30
person.maps.k1=v1
person.maps.k2=v2
person.lists=zhangsan,lisi
person.dog.name=哈士奇
person.dog.age=2
```
### properties配置文件在idea中默认utf-8可能会乱码
#### 解决方案
![image](http://image.damienzhong.com/peroperties%E4%B9%B1%E7%A0%81%E8%A7%A3%E5%86%B3%E8%AE%BE%E7%BD%AE.png)