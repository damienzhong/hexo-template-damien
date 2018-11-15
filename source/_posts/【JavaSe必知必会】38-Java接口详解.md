---
title: 【JavaSe必知必会】38-Java接口详解
date: 2018-11-15 18:32:45
tags: javase
categories: javase
---
# 接口特点
- 接口用关键字interface表示
  - 格式：interface 接口名{}
- 类实现接口用implements表示
  - 格式：class 类名 implements 接口名{}
- 接口不能实例化
  - 那么，接口如何实例化呢？
  - 按照多态的方式，由具体的子类实例化。其实这也是多态的一种，接口多态
- 接口的子类
  - 要么是抽象类
  - 要么重写接口中的所有抽象方法
# 接口成员特点
- 成员变量
  - 只能是常量
  - 默认修饰符public static final
- 构造方法
  - 没有，因为接口主要是扩展功能的，而没有具体存在
- 成员方法
  - 只能是抽象方法
  - 默认修饰符public abstract

```
/*
	接口成员特点：
		成员变量：只能是常量,并且是静态的
				默认修饰符：public static final
				建议：自己手动给出。
		构造方法：接口没有构造方法
		成员方法：只能是抽象方法
				默认修饰符：public abstract
				建议：自己手动给出。
		
	所有的类都默认继承自一个类：Object
	类Object是类层次结构的根类。每个类都使用Object作为超类。
*/
interface Inter{
	public int num = 10;
	public final int num2 = 20;
	public static final int num3 = 30;
	// 需要<标识符>
	//public Inter(){}
	//接口抽象方法不能带有主体
	//public void show(){}
	void show();
}
//接口名+Impl这种格式是接口的实现类格式
/*class InterImpl implements Inter{
	public InterImpl(){
		super();
	}
}*/
class InterImpl extends Object implements Inter{
	public InterImpl(){
		super();
	}
	
	void show(){}
}

public class InterfaceDemo2{
	public static void main(String[] args){
		//创建对象
		Inter i = new InterImpl();
		System.out.println(i.num);
		System.out.println(i.num2);
		System.out.println("---------------------");
		//i.num = 100;//无法为最终变量num分配值
		//i.num2 = 200;//无法为最终变量num2分配值
		//System.out.println(i.num);
		//System.out.println(i.num2);
		System.out.println(Inter.num);
		System.out.println(Inter.num2);
		System.out.println(Inter.num3);
	}
}
```
# 抽象类和接口的区别
- 成员区别
  - 抽象类  变量，常量；又抽象方法；抽象方法；非抽象方法
  - 接口    常量；抽象方法
- 关系区别
  - 类与类  继承，单继承
  - 类与接口    实现，单实现，多实现
  - 接口与接口  继承，单继承，多继承
- 设计理念
  - 抽象类  呗继承体现的是：“is a”的关系。共性功能
  - 接口    被实现体现的是：“like a”的关系，扩展功能

```
/*
	类与类：
		继承关系，只能单继承，可以多层继承
	类与接口：
		实现关系,可以单实现，也可以多实现
	接口与接口：
		继承关系，可以单继承，也可以实现多继承,可以多层继承
*/
interface Father{
	public abstract void show();
}

interface Mother extends NaiNai{
	public abstract void show2();
}

interface NaiNai{
	public abstract void show3();
}

interface Sister extends Father,Mother{
	
}

class Son implements Father,Mother{
	public void show(){
		System.out.println("show Son");
	}
	public void show2(){
		System.out.println("show2 Son");
	}
	public void show3(){
		System.out.println("show3 Son");
	}
}

public class InterfaceDemo3{
	public static void main(String[] args){
		Son s = new Son();
		s.show();
		s.show2();
		s.show3();
	}
}
```
