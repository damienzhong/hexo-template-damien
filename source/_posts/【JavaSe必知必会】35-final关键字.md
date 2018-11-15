---
title: 【JavaSe必知必会】35-final关键字
date: 2018-11-15 18:29:48
tags: javase
categories: javase
---
# final关键字引入
final关键字是最终的意思。可以修饰类、成员方法、成员变量。
```
/*
	继承的代码体现：
		由于继承中方法有一个现象：方法重写。
		所以，父类的功能，就会被子类给覆盖。
		有些时候，我们不想让子类去覆盖掉父类的功能，只能让他使用。
		这个时候，Java就为我们提供了一个关键字：final
		
		final:最终的意思。常见的它可以修饰类、方法、变量。
*/
class Fu{
	public final void show(){
		System.out.println("绝密文件，任何人不能修改");
	}
}

class Zi extends Fu{
	public void show(){
		System.out.println("这是什么鬼，看不懂，撕掉！");
	}
}

public class ZiDemo{
	public static void main(String[] args){
		Zi z = new Zi();
		z.show();
	}
}
```
# final关键字修饰特点
- 修饰类，该类不能被继承。
- 修饰方法，该方法不能被重写（覆盖）。
- 修饰变量，变量就变成了常量，只能被赋值一次。
```
/*
	fianl可以修饰类、方法、变量
	
	特点：
		final可以修饰类，该类不能被继承。
		final可以修饰方法，该方法不能被重写（覆盖）
		final可以修饰变量，该变量不能被重新赋值，因为这个变量其实是常量。
		
	常量：
		A：字面值常量
			"hello",10,true
		B：自定义常量
			final int x = 10;
*/
//final class Fu	//无法从最终Fu进行继承
class Fu{
	public int num = 10;
	public final int num2 = 20;
	/*public final void show(){
		
	}*/
}

class Zi extends Fu{
	public void show(){
		num = 100;
		System.out.println(num);
		
		num2 = 200;//无法为最终变量num2分配值
		System.out.println(num2);
	}
}

public class FinalDemo{
	public static void main(String[] args){
		Zi z = new Zi();
		z.show();
	}
}
```
# final修饰局部变量的问题

```
/*
	面试题:final修饰局部变量的问题
	基本类型：基本类型的值不能发生改变。
	引用类型：引用类型的地址值不能发生改变，但是，该对象的堆内存的值是可以改变的。
*/
class Student{
	int age = 10;
}

public class FinalTest{
	public static void main(String[] args){
		//局部变量是基本数据类型
		int x = 10;
		x = 100;
		System.out.println(x);
		final int y = 10;
		//无法为最终变量y分配值
		//y = 100;
		System.out.println(y);
		System.out.println("-------------------");
		//局部变量是引用类型
		Student s = new Student();
		System.out.println(s.age);
		s.age = 100;
		System.out.println(s.age);
		System.out.println("-------------------");
		
		final Student ss = new Student();
		System.out.println(ss.age);
		ss.age = 100;
		System.out.println(ss.age);
		
		//重新分配内存空间
		//无法为最终变量ss分配值
		ss = new Student();
	}
}
```
# final修饰变量的初始化时机

```
/*
	final修饰变量的初始化时机
		A:被final修饰的变量只能赋值一次。
		B:在构造方法完毕前（非静态变量）
*/
class Demo{
	int num = 10;
	final int num2;
	//final int num2 = 20;
	
	{
		num2 = 10;
	}
	public Demo(){
		num = 100;
		num2 = 200;
	}
}

public class FinalTest2{
	public static void main(String[] args){
		Demo d = new Demo();
		System.out.println(d.num);
		System.out.println(d.num2);
	}
}

```
