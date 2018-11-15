---
title: 【JavaSe必知必会】30-面向对象三大特性之封装
date: 2018-11-15 17:23:30
tags: javase
categories: javase
---
# 封装概述
## 封装概述
- 是指隐藏对象的属性和实现细节，仅对外提供公共访问方式

```
/**
	定义一个女朋友：
		成员变量：name,cup,age
		成员方法：show()
		
	我们在使用这个案例的过程中，发现了一个问题
		通过对象去给成员变量赋值，可以赋值一些非法的数据。
		这是不合理的。
		我们应该在赋值之前，先对数据进行判断
		判断在哪里比较合适呢？
		GirlFriendDemo是一个测试类，测试类一般只创建对象，调用方法。
		所以，这个判断应该定义在GirlFriend类中
		我们在成员变量的位置不可以进行数据判断，因为数据校验，必须要依靠逻辑语句。
		有逻辑的这些语句我们应该定义在方法中。
		所以，我们应该在GirlFriend类中提供一个方法来进行数据校验
		
	按照我们前面的分析，我们给出了一个方法进行校验。
	但是呢，它偏偏不调用方法来赋值，还是直接赋值，这样我们的方法就没用起到作用。
	我们就应该要求调用者必须使用我的方法，而不能直接通过调用成员变量赋值。
	怎么去强制要求不能直接使用成员变量呢？
		针对这种情况，Java就提供了一个关键字private
		
	private:私有的。它可以直接修饰成员变量和成员方法
		注意：被private修饰的成员只能在本类中使用
		
	其实，我们描述的就是一个封装思想。
	封装：是指隐藏对象的属性和实现细节，仅对外提供公共访问方式。
*/
class GirlFriend{
	//姓名
	String name;
	//年龄
	private int age;
	//胸围
	String cup;
	
	//写一个方法对数据进行校验
	/*
		返回值类型：void
		参数列表：int a
	*/
	public void setAge(int a){
		if(a<25&&a>16){
			age = a;
		}else{
			System.out.println("该年龄不是我的菜！");
		}
	}
	
	//成员方法
	public void show(){
		System.out.println("姓名："+name);
		System.out.println("年龄："+age);
		System.out.println("胸围："+cup);
	}
}

public class GirlFriendDemo{
	public static void main(String[] args){
		//制作一个女朋友
		GirlFriend gf = new GirlFriend();
		gf.name = "迪丽热巴";
		//gf.age = 18;
		gf.cup = "C";
		gf.show();
		System.out.println("----------------------");
		gf.name = "罗玉凤";
		//gf.age = 38;
		gf.cup = "A";
		gf.show();
		System.out.println("----------------------");
		gf.setAge(18);
		gf.show();
		System.out.println("----------------------");
		//gf.age = 48;
		gf.show();
	}
}
```

## 好处
- 隐藏实现的细节，提供公共访问方式
- 提供了代码的复用性
- 提高安全性
## 封装原则
- 将不需要对外提供的内容都隐藏起来
- 把属性隐藏，提供公共方法对其访问

# private关键字
## private关键字
- 是一个权限修饰符
- 可以修饰成员（成员变量和成员方法）
- 被private修饰的成员只能在本类中才能访问

```
/**
	private:
		是一个权限修饰符
		可以修饰成员变量和成员方法
		其修饰的成员只能在本类中被访问
*/
class Demo{
	//int num = 10;
	//用private修饰
	private int num = 10;
	
	public void show(){
		System.out.println(num);
	}
	
	private void method(){
		System.out.println("method...");
	}
	
	public void function(){
		method();
	}
}

public class PrivateDemo{
	public static void main(String args){
		Demo d = new Demo();
		//不能访问方法私有的成员变量
		//System.out.println(d.num);
		d.show();
		//不能访问私有的成员方法
		//d.method();
		d.function();
	}
}
```

## private最常见的应用
- 把成员变量用private修饰
- 提供对应的getXxx()/setXxx()方法
- 一个标准的案例的使用

```
/**
	private最常见的应用:
		把成员变量用private修饰
		提供对应的getXxx()/setXxx()方法
*/
//定义学生类
class Student{
	//姓名
	private String name;
	//年龄
	private int age;
	
	//获取姓名值
	public String getName(){
		return name;
	}
	
	//设置姓名值
	public void setName(String n){
		name = n;
	}
	
	//获取年龄值
	public int getAge(){
		return age;
	}
	
	//设置年龄值
	public void setAge(int a){
		age = a;
	}
}

public class StudentTest{
	public static void main(String args){
		//创建学生对象
		Student s = new Student();
		
		//使用成员变量
		//错误：被私有修饰了，外界不能直接访问
		//System.out.println(s.name + "---" + s.age);
		System.out.println(s.getName() + "---" + s.getAge());
		
		//给成员变量赋值
		//s.name = "范冰冰";
		//s.age = 28;
		//通过方法赋值
		s.setName("范冰冰");
		s.setAge(28);
		System.out.println(s.getName() + "---" + s.getAge());
	}
}
```
# this关键字
- this：代表所在类的对象引用
- 记住：
  - 方法被哪个对象调用，this就代表那个对象
- 什么时候使用this呢？
  - 局部变量隐藏成员变量
  - 其他用法后面和super一起讲解

```
/**
	我们曾经约定：起名字要做到见名知意
	
	this:是当前类的对象引用。简单来说，它就代表当前类的一个对象。
		注意：谁调用这个方法，在该方法内部的this就代表谁
	
	this的场景：
		解决局部变量隐藏成员变量
*/
//定义学生类
class Student{
	//姓名
	private String name;
	//年龄
	private int age;
	
	//获取姓名值
	public String getName(){
		return name;
	}
	
	//设置姓名值
	public void setName(String name){//name = "范冰冰";
		//name = name;	//变量的使用规则：就近原则
		//这里是类名，目前还没有说过类似的用法，所以这个是有问题的
		//这里的调用只能通过对象名
		//这个对象如果存在，它应该代表的是Student的一个对象。
		//那么，谁能够代表当前类的对象呢？java就提供了一个关键字 this
		//Student.name = name;
		this.name = name;
	}
	
	//获取年龄值
	public int getAge(){
		return age;
	}
	
	//设置年龄值
	public void setAge(int a){
		age = a;
	}
}

public class StudentTest{
	public static void main(String args){
		//创建学生对象
		Student s = new Student();
		//给成员变量赋值
		s.setName("范冰冰");
		s.setAge(28);
		System.out.println(s.getName() + "---" + s.getAge());
	}
}
```
# 构造方法
## 构造方法作用概述
给对象的数据进行初始化
## 构造方法格式
- 方法名与类名相同
- 没用返回值类型，连void都没有
- 没有具体返回值

```
/**
	构造方法：
		给对象的数据进行初始化
	格式：
		A:方法名与类名相同
		B:没用返回值类型，连void都没有
		C:没有具体返回值
*/
class Student{
	
	private String name;//null
	private int age;//0
	
	public Student(){
		System.out.println("这是一个构造方法。。。");
	}
}

public class ConstructDemo{
	public static void main(String[] args){
		//创建对象
		Student s = new Student();
		System.out.println(s);
	}
}
```
## 构造方法注意事项
- 如果你不提供构造方法，系统会给出默认构造方法
- 如果你提供了构造方法，系统将不再提供
- 构造方法也是可以重载的
```
/**
	我们一直在使用构造方法，但是，我们却没有定义构造方法，用的是哪里来的呢？
	
	构造方法的注意事项：
		A：如果我们没有给出构造方法，系统将自动提供一个无参构造方法。
		B：如果我们给出了构造方法，系统将不再提供默认的无参构造方法。
			注意：如果我们还想使用无参构造方法，就必须自己给出，建议永远自己给出无参构造方法
		
	给成员变量赋值有两种方式：
		A：setXxx();
		B：构造方法
*/
class Student{
	
	private String name;
	private int age;
	
	public Studesnt(){
		System.out.println("这是无参构造方法");
	}
	
	//构造方法的重载
	public Student(String name){
		System.out.println("这是一个带String类型的构造方法");
		this.name = name;
	}
	
	public Student(int age){
		System.out.println("这是一个带int类型的构造方法");
		this.age = age;
	}
	
	public Student(String name,int age){
		System.out.println("这是一个带两个参数的构造方法");
		this.name = name;
		this.age = age;
	}
	
	public void show(){
		System.out.println(this.name + "----"+this.age);
	}
	
}

public class ConstructDemo2{
	public static void main(String[] args){
		//创建对象
		Student s = new Student();
		s.show();
		System.out.println("------------");
		//创建对象2
		Student s2 = new Student("呆萌钟");
		s2.show();
		System.out.println("------------");
		//创建对象3
		Student s3 = new Student(18);
		s3.show();
		System.out.println("------------");
		//创建对象4
		Student s4 = new Student("呆萌钟",18);
		s4.show();
		System.out.println("------------");
	}
}
```
**注意：可以通过反编译对比**
# 类的成员方法
成员方法其实就是我们前面讲过的方法
## 方法具体划分
- 根据返回值
  - 有明确返回值的方法
  - 返回void类型的方法
- 根据形式参数
  - 无参方法
  - 带参方法
# 一个基本类的标准代码写法
## 类
- 成员变量
- 构造方法
  - 无参构造方法
  - 带参构造方法
- 成员方法
  - getXxx()
  - setXxx
## 给成员变量赋值的方法
- 无参构造方法+setXxx()
- 带参构造方法
## 注意
- 目前的代码是为了练习的一种标准格式
- 给成员变量有两种方式，可以只写一种
- 如果不单独获取数据，可以不写getXxx()方法

```
/**
	一个标准类的最终版
	
	学生类：
		成员变量：
			name,age
		构造方法：
			无参，带两个参
		成员方法：
			getXxx()/setXxx()
			show();输出该类的所有成员变量值
	给成员变量赋值：
		A：setXxx();
		B：构造方法
	输出成员变量的方式“
		A：通过getXxx分别获取然后拼接
		B：通过调用show()方法
*/
class Student{
	//姓名
	private String name;
	//年龄
	private int age;
	
	public Student(){}
	
	public Student(String name,int age){
		this.name=name;
		this.age=age;
	}
	
	public String getName(){
		return name;
	}
	
	public void setName(String name){
		this.name=name;
	}
	
	public int getAge(){
		return age;
	}
	
	public void setAge(int age){
		this.age=age;
	}
	//输出所有的成员变量
	public void show(){
		System.out.println(name+"---"+age);
	}
}

//测试类
public class StudentTest3{
	public static void main(String[] args){
		//方式1给成员变量赋值
		Student s1 = new Student();
		s1.setName("呆萌钟");
		s1.setAge(24);
		//输出值
		System.out.println(s1.getName()+"---"+s1.getAge());
		s1.show();
		System.out.println();
		
		//方式2给成员变量赋值
		Student s2 = new Student("呆萌钟2",18);
		System.out.println(s2.getName()+"---"+s2.getAge());
		s2.show();
	}
}
```
# 类的初始化过程

Student s = new Student();在内存中做了哪些事情？

- 加载Student.class文件进内存
- 在栈内存中为s开辟空间
- 在堆内存中为学生对象开辟空间
- 对学生对象的成员变量进行默认初始化
- 对学生对象的成员变量进行显示初始化
- 通过构造方法对学生对象的成员变量赋值
- 学生对象初始化完毕，把对象地址赋值给s变量
![image](http://image.damienzhong.com/%E7%B1%BB%E7%9A%84%E5%88%9D%E5%A7%8B%E5%8C%96.JPG)