---
title: 【JavaSe必知必会】36-面向对象三大特性之多态
date: 2018-11-15 18:31:11
tags: javase
categories: javase
---
# 多态概述  
## 概述
- 某一个事物，在不同时刻表现出来的不同状态
- 举例：
  - 猫可以是猫的类型。猫 m = new 猫();
  - 同时猫也是动物的一种，也可以把猫称为动物。
    - 动物 d = new 猫(); 
    
## 多态前提和体现
- 有继承关系
- 有方法重写
- 有父类引用指向子类对象
# 多态案例及成员访问特地
## 多态案例
## 成员访问特点
- 成员变量
  - 编译看左边，运行看左边
- 成员方法
  - 编译看左边，运行看右边
- 静态方法
  - 编译看左边，运行看左边
  - 所以前面我们说静态方法不能算方法重写

```
/*
	多态：同一个对象（事物），在不同时刻体现出来的不同状态。
	举例：
		猫是猫，猫是动物。
		水（液体、固体、气体）。
		猫 m = new 猫();
		动物 d = new 猫();
	多态的前提：
		A：要有继承关系
		B：要有方法重写
			其实没有也是可以的，但是如果没用这个就没有意义。
		C：要有父类引用指向子类对象。
			父 f = new Zi();
			
	多态中的成员访问特点：
		A：成员变量
			编译看左边，运行看左边
		B：构造方法
			创建子类对象的时候，访问父类的构造方法，对父类的数据进行初始化。
		C：成员方法
			编译看左边，运行看右边
		D：静态方法
			编译看左边，运行看左边
			(静态和类相关，算不上重写，所以访问还是左边的)
			
		由于成员方法存在方法重写，所以它运行看右边。
*/
class Fu{
	public int num = 100;
	public void show(){
		System.out.println("show Fu");
	}
	
	public static void function(){
		System.out.println("function Fu");
	}
}

class Zi extends Fu{
	public int num = 1000;
	public int num2 = 200;
	public void show(){
		System.out.println("show Zi");
	}
	
	public void method(){
		System.out.println("method Zi");
	}
	
	public static void function(){
		System.out.println("function Zi");
	}
}

public class DuoTaiDemo{
	public static void main(String[] args){
		//要有父类引用指向子类对象。
		//父 f = new Zi();
		Fu f = new Zi();
		System.out.println(f.num);
		//找不到符号
		//System.out.println(f.num2);
		f.show();
		//找不到符号
		//f.method();
		f.function();
	}
}
```

# 多态的好处和弊端
## 多态的好处
- 提供了程序的维护性（由继承保证）
- 提供了程序的扩展性（由多态保证）

```
/*
	多态的好处：
		A：提高了代码的维护性（继承保证）
		B：提高了代码的扩展性(由多态保证)
		
	猫狗案例
*/
class Animal{
	public void eat(){
		System.out.println("eat");
	}
	
	public void sleep(){
		System.out.println("sleep");
	}
}

class Dog extends Animal{
	public void eat(){
		System.out.println("狗吃肉");
	}
	
	public void sleep(){
		System.out.println("狗站着睡觉");
	}
}

class Cat extends Animal{
	public void eat(){
		System.out.println("猫吃鱼");
	}
	
	public void sleep(){
		System.out.println("猫趴着睡觉");
	}
}

class Pig extends Animal{
	public void eat(){
		System.out.println("猪吃饭");
	}
	
	public void sleep(){
		System.out.println("猪侧着睡觉");
	}
}

//针对动物操作的工具类
class AnimalTool{
	private AnimalTool(){}
	/*8public static void useCat(Cat c){
		c.eat();
		c.sleep();
	}
	
	public static void useDog(Dog d){
		d.eat();
		d.sleep();
	}
	
	public static void usePig(Pig p){
		p.eat();
		p.sleep();
	}*/
	public static void useAnimal(Animal a){
		a.eat();
		a.sleep();
	}
}

public class DuoTaiDemo2{
	public static void main(String[] args){
		//养一只猫
		Cat c = new Cat();
		c.eat();
		c.sleep();
		//我特别喜欢猫，又养了一只
		Cat c2 = new Cat();
		c2.eat();
		c2.sleep();
		//再一只猫
		Cat c3 = new Cat();
		c3.eat();
		c3.sleep();
		System.out.println("-------------------");
		//问题来了，我养了很多只猫，每次创建对象是可以接受的，
		//但是呢？调用方法，除了对象名不同外，其他代码冗余了。
		//AnimalTool.useCat(c);
		//AnimalTool.useCat(c2);
		//AnimalTool.useCat(c3);
		//System.out.println("-------------------");
		//我还喜欢狗，养了只狗
		Dog d = new Dog();
		//再养一只狗
		Dog d2 = new Dog();
		/*AnimalTool.useDog(d);
		AnimalTool.useDog(d2);
		*/
		System.out.println("-------------------");
		//我喜欢宠物猪
		//定义一个猪类，它要继承自动物，提供两个方法，并且还得再工具类中添加该类方法调用
		Pig p = new Pig();
		Pig p2 = new Pig();
		Pig p3 = new Pig();
		/*AnimalTool.usePig(p);
		AnimalTool.usePig(p2);
		AnimalTool.usePig(p3);*/
		AnimalTool.useAnimal(c);
		AnimalTool.useAnimal(c2);
		AnimalTool.useAnimal(c3);
		AnimalTool.useAnimal(d);
		AnimalTool.useAnimal(d2);
		AnimalTool.useAnimal(p);
		AnimalTool.useAnimal(p2);
		AnimalTool.useAnimal(p3);
	}
	
}
```

## 多态的弊端
- 不能访问子类特有功能
- 那么我们如何才能访问子类特有功能呢？
  - 多态中的转型

```
/*
	多态的弊端：
		不能使用子类特有功能。
		
	我就想使用子类的特有功能？行不行？
		行
	怎么用呢？
		A：创建子类对象调用方法。（可以，但是很多时候不合理，而且，太占用内存）
		B：把父类的引用强制转化为子类的引用。（向下转型）
		
	对象间的转型问题：
		向上转型：
			Fu f = new Zi();
		向下转型：
			Zi z = (Zi)f;//要求该f必须是能够转换为Zi
*/
class Fu{
	public void show(){
		System.out.println("show Fu");
	}
}

class Zi extends Fu{
	public void show(){
		System.out.println("show Zi");
	}
	
	public void method(){
		System.out.println("method Zi");
	}
}

public class DuoTaiDemo3{
	public static void main(String[] args){
		Fu f = new Zi();
		//f.show();
		//f.method();
		//创建子类对象
		//Zi zi = new Zi();
		//zi.show();
		//zi.method();
		//把子的对象赋值给父亲，但是因为父的引用类型与子的不一致，所以我们需要做个强制类型转化
		Zi z = (Zi)f;
		z.show();
		z.method();
	}
}
```
# 多态中的转型问题
- 向上转型
  - 从子到父
  - 父类引用指向子类对象
- 向下转型
  - 从父到子
  - 父类引用转为子类对象


