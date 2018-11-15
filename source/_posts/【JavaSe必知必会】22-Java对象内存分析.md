---
title: 【JavaSe必知必会】22-Java对象内存分析
date: 2018-11-15 17:13:22
tags: javase
categories: javase
---
# Java中的内存分配
Java 程序在运行时，需要在内存中的分配空间。为了提高运算效率，就对空间进行了不同区域的划分，因为每一片区域都有特定的处理数据方式和内存管理方式。
- 栈 存储局部变量
  - 局部变量    在方法定义中或者方法声明上的变量都称为局部变量，使用完毕，立即消失
- 堆 存储new出来的东西
  - 每一个实体都有首地址值
  -	每一个实体内的数据都有默认值
  
		byte,short,int,long 0

		float,double 0.0
		
		char ‘\u0000’
		
		boolean false
		
		引用类型：null
  - 使用完毕后，会被垃圾回收器空闲的时候回收。
- 方法区 被虚拟机加载的类信息、常量、静态常量等。
- 本地方法区 (和系统相关)
- 寄存器 (给CPU使用)


```
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
		System.out.println("发短信。。。");
	}
	
	//玩游戏
	public void playGame(){
		System.out.println("王者荣耀carry中。。。");
	}
}

class PhoneDemo{
	public static void main(String[] args){
		//使用前需要创建对象
		//类名 对象名 = new 类名();
		Phone p = new Phone();
		
		System.out.println(p.brand+"==="+p.price+"==="+p.color);
		
		//给成员赋值
		p.brand = "iPhone X";
		p.price = 6888;
		p.color = "黑色";
		System.out.println(p.brand+"==="+p.price+"==="+p.color);
		
		//调用方法
		p.call("呆萌钟");
		p.sendMessage();
		p.playGame();
		
		System.out.println("------------------------");
		
		Phone p2 = new Phone();
		
		System.out.println(p2.brand+"==="+p2.price+"==="+p2.color);
		
		//给成员赋值
		p2.brand = "锤子";
		p2.price = 2299;
		p2.color = "红色";
		System.out.println(p2.brand+"==="+p2.price+"==="+p2.color);
		
		//调用方法
		p2.call("迪丽热巴");
		p2.sendMessage();
		p2.playGame();
		System.out.println("------------------------");
		Phone p3 = p;
		System.out.println(p3.brand+"==="+p3.price+"==="+p3.color);
		
		//给成员赋值
		p3.brand = "华为";
		p3.price = 1999;
		p3.color = "蓝色";
		System.out.println(p3.brand+"==="+p3.price+"==="+p3.color);
		System.out.println(p.brand+"==="+p.price+"==="+p.color);
		
	}
}
```
# 一个对象的内存图
![image](http://image.damienzhong.com/%E4%B8%80%E4%B8%AA%E5%AF%B9%E8%B1%A1%E7%9A%84%E5%86%85%E5%AD%98%E5%9B%BE.JPG)
# 两个对象的内存图
![image](http://image.damienzhong.com/%E4%B8%A4%E4%B8%AA%E5%AF%B9%E8%B1%A1%E7%9A%84%E5%86%85%E5%AD%98%E5%9B%BE.JPG)
# 三个对象的内存图
![image](http://image.damienzhong.com/%E4%B8%89%E4%B8%AA%E5%AF%B9%E8%B1%A1%E7%9A%84%E5%86%85%E5%AD%98%E5%9B%BE.png)