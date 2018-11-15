---
title: 【JavaSe必知必会】21-类与对象的定义与使用
date: 2018-11-15 17:11:50
tags: javase
categories: javase
---
# 类与对象关系

- 我们学习编程语言，就是为了模拟现实世界的事物，实现信息化。
  - 比如：去超市买东西的计费系统，去银行办业务的系统。
- 我们如何表示一个现实世界事物呢：
  - 属性	就是该事物的描述信息
  - 行为	就是该事物能够做什么
  - 举例：学生事物
- 我们学习的Java语言最基本单位是类，所以，我们就应该把事物用一个类来体现。

```
 类：是一组相关的属性和行为的集合

 对象：是该类事物的具体体现
 举例：

 类	学生
 对象	班长就是一个对象
```
类：可以理解为构造对象的一个蓝图或者模版，是抽象的概念
对象：是以类为模型创建的具体实例，是对类的一种具体化。


```
/*
	案例：定义一个学生类
	
	学生事物：
		属性：姓名，年龄，性别
		行为：学习，吃饭，睡觉
	
	把事物要转化为对应的类：
	
	学生类：
		成员变量：姓名，年龄，性别
		成员方法：学习，吃饭，睡觉
		
	成员变量：和以前变量的定义是一样的格式，但是位置不同，在类中方法外。
	成员方法：和以前的方法定义是一样的格式，但是我们今天先去掉static。
	
	首先我们应该定义一个类，然后完成类的成员。

*/
//这就是学生类
class Student{
	//定义成员变量
	//姓名
	String name;
	//年龄
	int age;
	//性别
	String sex;
	
	//定义成员方法
	//学习的方法
	public void study(){
		System.out.println("我在看呆萌钟的Java视频学习中ing...");
	}
	
	//吃饭的方法
	public void eat(){
		System.out.println("大口吃饭中ing...");
	}
	
	//睡觉的方法
	public void sleep(){
		System.out.println("天色好晚，我要睡觉啦~");
	}
}

```

```
/**
	手机事物：
		属性：品牌，价格，颜色
		行为：打电话，发短信，玩游戏
	
	手机类：
		成员变量：品牌，价格，颜色
		成员方法：打电话，发短信，玩游戏
*/
class Phone{
	//品牌
	String brand;
	//价格
	int price;
	//颜色
	String color;
	
	//打电话
	public void call(String name){
		System.out.println("给"+name+"打电话");
	}
	
	//发短信
	public void sendMessage(){
		System.out.println("发短信。。。);
	}
	
	//玩游戏
	public void playGame(){
		System.out.println("王者荣耀carry中。。。");
	}
}
```
# 对象的使用
- 创建对象：
  - 类名 对象名 = new 类名();
- 对象名.成员变量
- 对象名.成员方法

```
/*
	在一个java文件中写两个类：一个基本的类，一个测试类。
	注意：文件名称和测试类名称一致。
	
	如何使用呢?
		创建对象使用。
		
	如何创建对象呢?
		格式：类名 对象名 = new 类名();
		
	如何使用成员变量呢?
		对象名.变量名
	如何使用成员方法呢?
		对象名.方法名(...)
*/
//这是学生类
class Student {
	//姓名
	String name; //null
	//年龄
	int age; //0
	//地址
	String address; //null
	
	//学习
	public void study() {
		System.out.println("学生爱学习");
	}
	
	//吃饭
	public void eat() {
		System.out.println("学习饿了，要吃饭");
	}
	
	//睡觉
	public void sleep() {
		System.out.println("学习累了，要睡觉");
	}
}

//这是学生测试类
class StudentDemo {
	public static void main(String[] args) {
		//类名 对象名 = new 类名();
		Student s = new Student();
		
		//输出成员变量值
		//System.out.println(s.name);
		//System.out.println(s.age);
		//System.out.println(s.address);
		//改进写法
		System.out.println(s.name+"---"+s.age+"---"+s.address);
		
		
		//给成员变量赋值
		s.name = "林青霞";
		s.age = 27;
		s.address = "北京";
		//赋值后的输出
		System.out.println(s.name+"---"+s.age+"---"+s.address);
		
		//调用方法
		s.study();
		s.eat();
		s.sleep();
	}
}
```

```
/*
	手机类的测试
*/
class Phone {
	//品牌
	String brand;
	//价格
	int price;
	//颜色
	String color;
	
	//打电话的方法
	public void call(String name) {
		System.out.println("给"+name+"打电话");
	}
	
	//发短信的方法
	public void sendMessage() {
		System.out.println("群发短信");
	}
	
	//玩游戏的方法
	public void playGame() {
		System.out.println("玩游戏");
	}
}

class PhoneDemo {
	public static void main(String[] args) {
		//创建手机对象
		//类名 对象名 = new 类名();
		Phone p = new Phone();
		
		//直接输出成员变量值
		System.out.println(p.brand+"---"+p.price+"---"+p.color);
		
		//给成员变量赋值
		p.brand = "诺基亚";
		p.price = 100;
		p.color = "灰色";
		//再次输出
		System.out.println(p.brand+"---"+p.price+"---"+p.color);
		
		//调用方法
		p.call("林青霞");
		p.sendMessage();
		p.playGame();
	}
}
```
