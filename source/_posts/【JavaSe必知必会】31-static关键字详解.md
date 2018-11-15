---
title: 【JavaSe必知必会】31-static关键字详解
date: 2018-11-15 18:25:17
tags: javase
categories: javase
---
# static关键字的引入
```
/**
	定义一个人类
	
	姓名和年龄都是变化的，这个我能接受，因为每个人的性别和年龄都是不同的。
	但是，我们现在选取的几个人都是中国人，他们的国籍都是一样的。
	一样的国籍，我每次创建对象，在堆内存中都要开辟这样的空间，
	浪费了空间。
	怎么办？
	针对多个对象有共同的成员变量值的时候，java就提供了一个关键字来修饰：static
*/
class Person{
	//姓名
	String name;
	//年龄
	int age;
	//国籍
	//String country;
	static String country;
	
	public Person(){}
	
	public Person(String name,int age){
		this.name = name;
		this.age = age;
	}
	
	public Person(String name,int age,String country){
		this.name = name;
		this.age = age;
		this.country = country;
	}
	
	public void show(){
		System.out.println("姓名："+this.name+",年龄："+this.age+",国籍"+this.country);
	}
}

public class PersonDemo{
	public static void main(String[] args){
		//创建对象1
		Person p1 = new Person("呆萌钟",23,"中国");
		p1.show();
		//创建对象2
		//Person p2 = new Person("迪丽热巴",24,"中国");
		//p2.show();
		Person p2 = new Person("迪丽热巴",24);
		p2.show();
		//创建对象3
		//Person p3 = new Person("凤姐",31,"中国");
		//p3.show();
		Person p3 = new Person("凤姐",31);
		p3.show();
		
		p3.country = "美国";
		p3.show();
		
		p1.sho();
		p2.show();
	}
}	
```
## static内存分析
![image](http://image.damienzhong.com/static%E5%86%85%E5%AD%98%E5%9B%BE.JPG)
# static关键字
可以修饰成员变量和成员方法
## static关键字特点
- 随着类的加载而加载
- 优先于对象存在
- 被类的所有对象共享
  - 这也是我们判断是否使用静态关键字的条件
- 我们可以通过类名调用

```
/**
	static的特点：（它可以修饰成员变量，也可以修饰成员方法）
		A：随着类的加载而加载
			回想main方法
		B：优先于对象存在
		C：被类的所有对象共享
			举例：
				一个班的学生应该共用一个班级编号。
				什么时候该用静态？
				如果某个成员变量是被所有对象共享的，那么它就应该定义为静态的。
		D：可以通过类名调用
			其实它本身也可以通过对象调用
			推荐使用类名调用
			静态修饰的内容一般我们称其为：与类相关的，类成员。
*/
class Student{
	//非静态变量
	int num = 10;
	//静态变量
	static int num2 = 20;
}

public class StudentDemo{
	public static void main(String[] args){
		Student s = new Student();
		System.out.println(s.num);
		
		System.out.println(Student.num2);
		System.out.println(s.num);
	}
}
```
## static关键字注意事项
- 在静态方法中是没有this关键字的
- 静态方法只能访问静态的成员变量和静态的成员方法

```
/**
	static关键字注意事项:
		A：在静态方法中是没有this关键字的
			如何理解呢？
				静态是随着类的加载而加载，this是随着对象的创建而存在。
				静态比对象先存在。
		B：静态方法只能访问静态成员变量和静态成员方法
			静态方法：
				成员变量：只能访问静态变量
				成员方法：只能访问静态成员方法
			非静态方法：
				成员变量：可以是静态的，也可以是非静态的
				成员方法：可以是静态的成员方法，也可是非静态的成员方法
			简单记：
				静态只能访问静态
*/
class Teacher{
	public int num = 10;
	public static int num2 = 20;
	
	public void show(){
		System.out.println(num);//隐含的告诉你访问的是成员变量
		System.out.println(this.num);//明确的告诉你访问的是成员变量
		
		//function();
		//function2();
	}
	
	public static void method(){
		//无法从静态上下文中引用非静态变量num
		//System.out.println(num);
		System.out.println(num2);
		//无法从静态上下文中引用非静态方法function()
		//function();
		function2();
	}
	
	public void function(){
		
	}
	
	public static void function2(){
		
	}
}

public class TeacherDemo{
	public static void main(String[] args){
		//创建对象
		Teacher t = new Teacher();
		t.show();
		System.out.println("--------------------");
		t.method();
	}
}
```
# 静态变量和成员变量的区别
## 所属不同
- 静态变量属于类，所以也称为类变量
- 成员变量属于对象，所以也称为实例变量（对象变量）
## 内存中位置不同
- 静态变量存储于方法区的静态区
- 成员变量存储于堆内存
## 内存出现时间不同
- 静态变量随着类的加载而加载，随着类的消失而消失
- 成员变量随着对象的创建而存在，随着对象的消失而消失
## 调用不同
- 静态变量可以通过类名调用，也可以通过对象调用
- 成员变量只能通过对象名调用
# main方法是静态的
**public static void main(String[] args){}**
- public被jvm调用，访问权限足够大
- static被jvm调用，不用创建对象，直接类名访问
- void被jvm调用，不需要给jvm返回值
- main一个通用的名字，虽然不是关键字，但是被jvm识别
- String[] args以前用于接收键盘录入的

```
/**
	main方法的格式讲解：
		public static void main(String[] args){}
		
		public：公共的，访问权限是最大的。由于main方法是被jvm调用，所以权限要够大
		static：静态的，不需要创建对象，通过类名就可以。方便jvm调用。
		void：方法的返回值是返回给调用者的，而main方法是被jvm调用，返回内容给jvm没有意义。
		main：是一个常见的方法入口，很多语言都是用main作为方法入口的。
		String[] args：这是一个字符串数组。
					有什么用？怎么给值？
					这个东西早期是为了接收键盘录入的数据的。（因为jdk5之前没有Scanner）
					格式：
						java 类名 hello world java
*/
public class MainDemo{
	public static void main(String[] args){
		//System.out.println(args);//地址值
		//System.out.println(args.length);//0
		//System.out.println(args[0]);//ArrayIndexOutOfBoundsException
		
		//接收数据后
		System.out.println(args);
		System.out.println(args.length);
		//System.out.println(args[0]);
		for(int x=0;x<args.length;x++){
			System.out.println(args[x]);
		}
	}
}
```
