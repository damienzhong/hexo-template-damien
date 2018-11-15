---
title: 【JavaSe必知必会】40-Java权限修饰符
date: 2018-11-15 18:34:38
tags: javase
categories: javase
---
![image](http://image.damienzhong.com/%E6%9D%83%E9%99%90%E4%BF%AE%E9%A5%B0%E7%AC%A6.png)
```
/*
	权限修饰符：
					本类	同一个包下（子类和无关系）	不同包下（子类）	不同包下（无关系）
		private	     Y															
		默认         Y			Y							
		protected    Y			Y							Y
		public       Y  		Y							Y						Y
*/
package com.damien;

public class Father{
	private void show(){
		System.out.println("show");
	}
	
	void show2(){
		System.out.println("show2");
	}
	
	protected void show3(){
		System.out.println("show3");
	}
	
	public void show4(){
		System.out.println("show4");
	}
	
	public static void main(String[] args){
		Father f = new Father();
		f.show();
		f.show2();
		f.show3();
		f.show4();
	}
}
```
# 类及其组成可以用的修饰符
## 类
- 默认、public、final、abstract
- 我们自己定义：public居多
## 成员变量
- 四种权限修饰符均可，final,static
- 我们自己定义：private居多
## 构造方法
- 四种权限修饰符均可，其他不可
- 我们自己定义：public居多
## 成员方法
- 四种权限修饰符均可，final,static,abstract
- 我们自己定义：public居多

```
/*
	修饰符：
		权限修饰符：private,默认的,protected,public
		状态修饰符：static,final
		抽象修饰符：abstract
		
	类：
		权限修饰符：默认的,public
		状态修饰符：final
		抽象修饰符：abstract
		
		用的做多的就是：public 
	成员变量：
		权限修饰符：private,默认的,protected,public
		状态修饰符：static,final
		
		用的做多的就是：private
	构造方法：
		权限修饰符：private,默认的,protected,public
		
		用的做多的就是：public 
	成员方法：
		权限修饰符：private,默认的,protected,public
		状态修饰符：static,final
		抽象修饰符：abstract
		
		用的做多的就是：public 
		
	除此以外的组合规则：
			成员变量：public static final
			成员方法：public static 
					  public abstract
					  public final
*/
public class Demo{
	//成员变量
	private int x = 10;
	int y = 20;
	protected int z = 30;
	public int a = 40;
	public final int b = 50;
	public static int c = 60;
	public static final int d = 70;
	//此处不允许使用修饰符abstract
	//abstract int e = 80;
	
	//构造方法
	private Demo(){}
	Demo(String name){}
	protected Demo(String name,int age){}
	public Demo(String name,int age,String sex){}
	
	//public static Demo(){}
	//public final Demo(){}
	//public abstract Demo(){}
	
	//成员方法
	//static void show(){}
	//abstract void show();
	final void show(){}
}
```
