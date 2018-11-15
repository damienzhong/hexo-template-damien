---
title: 【JavaSe必知必会】37-抽象类
date: 2018-11-15 18:32:00
tags: javase
categories: javase
---
# 抽象类特点
- 抽象类和抽象方法必须用abstract关键字修饰
  - abstract class 类名{}
  - public abstract void eat();
- 抽象类不一定有抽象方法，有抽象方法的类一定是抽象类
- 抽象类不能实例化
  - 那么，抽象类如何实例化呢？
  - 按照多态的方式，由具体的子类实例化。其实这也是多态的一种，抽象类多态
- 抽象类的子类
  - 要么是抽象类
  - 要么重写抽象类中的所有抽象方法

```
/*
	抽象类的概述：
		动物不应该定义为具体的东西，而且动物中的吃、睡等也不应该是具体。
		我们把一个不是具体的功能称为抽象的功能，而一个类中如果由抽象的功能，该类必须是抽象类。
		
	抽象类的特点：
		A：抽象类和抽象方法必须用abstract关键字修饰
		B：抽象类中不一定有抽象方法，但是有抽象方法的类必须定义为抽象类
		C：抽象类不能实例化
			因为它不是具体的。
			抽象类有构造方法，但是不能实例化。构造方法有什么用？
			用于子类访问父类数据的初始化。
		D：抽象的子类
			a：如果不想重写抽象方法，该子类是一个抽象类
			b：重写所有的抽象方法，这个时候子类是一个具体的类
			
		抽象类的实例化其实是靠具体的子类实现的，是多态的方式。
*/
abstract class Animal{//抽象类的声明格式
	//抽象方法
	//public abstract void eat(){}//空方法体，这个会报错，抽象方法不能有主体
	public abstract void eat();
	
	public Animal(){}
}
//子类是抽象类
abstract class Dog extends Animal{
	
}
//子类是具体类，重写抽象方法
class Cat extends Animal{
	public void eat(){
		System.out.println("猫吃鱼");
	}
}

public class AbstractDemo{
	public static void main(String[] args){
		//创建对象
		//Animal是抽象的; 无法实例化
		//Animal a = new Animal();
		//通过多态的方式
		Animal a = new Cat();
		a.eat();
	}
}
```
# 抽象类的成员特点
- 成员变量
  - 可以是变量
  - 也可以是常量
- 构造方法
  - 有构造方法，但是不能实例化
  - 那么，构造方法的作用是什么呢？
    - 用于子类访问父类数据的初始化
- 成员方法
  - 可以有抽象方法，限定子类必须完成某些动作
  - 也可以有非抽象方法，提供代码复用性
 
```
/*
	抽象类的成员特点：
		成员变量：既可以是变量，也可以是常量
		构造方法：有。
					用于子类访问父类数据的初始化
		成员方法：既可以是抽象的，也可以是非抽象的
		
	抽象类的成员方法特性：
		A：抽象方法	强制要求子类做的事情。
		B：非抽象方法	子类继承的事情，提高代码复用性
*/
abstract class Animal{
	public int num = 100;
	public final int num2 = 20;
	
	public Animal(){}
	
	public Animal(String name){}
	
	public abstract void show();
	
	public void method(){
		System.out.println("show Animal method");
	}
}

class Dog extends Animal{
	public void show(){
		System.out.println("show Dog");
	}
}

public class AbstractDemo2{
	public static void main(String[] args){
		//创建对象
		Animal a = new Dog();
		a.num = 200;
		System.out.println(a.num);
		//a.num2 = 30;
		System.out.println(a.num2);
		System.out.println("------------------------");
		a.show();
		a.method();
	}
}
```
# 抽象类注意事项

```
/*
	一个类如果没有抽象方法，可不可以定义为抽象类？如果可以，有什么意义？
		A:可以
		B:不让创建对象
	
	
	抽象类不能和哪些关键字共存
		private 冲突
		final 冲突
		static 无意义
*/
abstract class Fu{
	//非法的修饰符组合: abstract和private
	//private abstract void show();
	// 非法的修饰符组合: abstract和final
	//final abstract void show();
	//非法的修饰符组合: abstract和static/
	//static abstract void show();
	
	public static void method(){
		System.out.println("method");
	}
}
class Zi extends Fu{
	public void show(){}
}
public class AbstractDemo3{
	public static void main(String[] args){
		Fu.method();
	}
}
```
