---
title: 【JavaSe必知必会】34-面向对象三大特性之继承
date: 2018-11-15 18:28:43
tags: javase
categories: javase
---
# 继承概述
- 多个类中存在相同属性和行为时，将这些内容抽取到单独一个类中，那么多个类无需再定义这些属性和行为，只要继承那个类即可。
- 通过extends关键字可以实现类与类的继承
  - class 子类名 extends 父类名{}
- 单独的这个类成为父类，基类或者超类；这多个类可以称为子类或者派生类。
- 有了继承以后，我们定义一个类的时候，可以在一个已经存在的类的基础上，还可以定义自己的新成员。
# 继承的好处
- 提高了代码的复用性
  - 多个类相同的成员可以放到同一个类中
- 提高了代码的维护性
  - 如果功能的代码需要修改，修改一处即可
- 让类与类之间产生了关系，是多态的前提
  - 其实这也是类的一个弊端：类的耦合性很强

```
/*
	继承概述：
		把多个类中相同的内容给提取出来定义到一个类中。
		
	如何实现继承？
		Java提供了关键字：extends
		
	格式：
		class 子类名 extends 父类名{}
		
	好处：
		A：提供了代码的复用性
		B：提供了代码的维护性
		C：让类与类之间产生关系，是多态的前提
		
*/
//继承前
/*class Student{
	public void eat(){
		System.out.println("吃饭");
	}
	
	public void sleep(){
		System.out.println("睡觉");
	}
}

class Teacher{
	public void eat(){
		System.out.println("吃饭");
	}
	
	public void sleep(){
		System.out.println("睡觉");
	}
}*/
//使用继承后
class Person{
	public void eat(){
		System.out.println("吃饭");
	}
	
	public void sleep(){
		System.out.println("睡觉");
	}
}

class Student extends Person{}

class Teacher extends Person{}

public class ExtendsDemo{
	public static void main(String[] args){
		Student s = new Student();
		s.eat();
		s.sleep();
		System.out.println("-------------");
		
		Teacher t = new Teacher();
		t.eat();
		t.sleep();
	}
}
```

#  继承的特点
- java中只支持单继承，不支持多继承
  - 一个类中只能有一个父类，不可以有多个父类
  - class SubDemo extends Demo{} //ok
  - class SubDemo extends Demo1,Demo2...//error
- java支持多层继承（继承体系）
  - class A{}
  - class B extends A{}
  - class C extends B{}
  
```
/*
	java中继承的特点：
		A：java中只支持单继承，不支持多继承
			有些语言是支持多继承的，格式：extends 类1,类2,...
		B：java支持多层继承（继承体系）
*/
/*
class Father{}
class Mother{}
class Son extends Father,Mother{}
*/
class GrandFather{
	public void show(){
		System.out.println("我是你爷爷");
	}
}
class Father extends GrandFather{
	public void method(){
		System.out.println("我是你爸爸");
	}
}

class Son extends Father{}

public class ExtendsDemo2{
	public static void main(String[] args){
		Son s = new Son();
		s.method();
		Father f = new Father();
		f.show();
		s.show();
	}
}
```

# 继承的注意事项
- 子类只能继承父类所有非私有的成员（成员方法和成员变量）
  - 其实这也体现了继承的另一个弊端：打破了封装性
- 子类不能继承父类的构造方法，但是可以通过super关键字去访问父类构造方法
- 不要为了部分功能而去继承
- 什么时候使用继承呢？
  - 继承中类之间体现的是：”is a“的关系
  
```
/*
	继承的注意事项：
		A：子类只能继承父类所有非私有的成员（成员方法和成员变量）
		B：子类不能继承父类的构造方法，但是可以通过super关键字去访问父类构造方法
		C：不要为了部分功能而去继承
			class A{
				public void show1(){}
				public void show2(){}
			}
			class B{
				public void show2(){}
				public void show3(){}
			}
			//我们发现B类中出现了和A类一样的show2()方法，所以，我们就用继承体现
			class B extends A{
				public void show3(){}
			}
			这样其实不好，因为这样你不但有了show2()方法，还多show1(),有可能这个show1()不是我们想要的。
			
		那么，我们什么适合考虑使用继承呢？
			继承中类之间体现的是：”is a“的关系
				Person
					Student
					Teacher
				水果
					苹果
					香蕉
					橘子
			采用假设法：
				如果有两个类A,B,只有她们符合A是B的一种，或者B是A的一种，就可以考虑继承
*/
class Father{
	private int num = 10;
	public int num2 = 20;
	
	private void method(){
		System.out.println(num);
		System.out.println(num2);
	}
	
	public void show(){
		System.out.println(num);
		System.out.println(num2);
	}
}

class Son extends Father{
	public void function(){
		//System.out.println(num);//num 在 Father 中是 private 访问控制
		System.out.println(num2);
	}
}

public class ExtendsDemo3{
	public static void main(String[] args){
		//创建对象
		Son s = new Son();
		//s.method();//子类不能继承父类的私有方法
		s.show();
		//System.out.println(s.num);//num 在 Father 中是 private 访问控制
		s.function();
	}
}
```

# 继承中成员变量的关系
在子类方法中访问一个变量
- 首先在子类局部范围找
- 然后在子类成员范围找
- 最后在父类成员范围找（肯定不能访问到父类局部范围）
- 如果还是没有就报错（不考虑父亲的父亲...）

```
/*
	类的组成：
		成员变量
		构造方法
		成员方法
	现在我们又讲了继承，所以，我们就应该考虑一下，类的组成部分的各自关系
	
	继承中的成员变量的关系：
		A:子类中的成员变量和父类中的成员变量名称不一样
		B:子类中的成员变量和父类中的成员变量名称一样
			在子类中访问一个变量的查找顺序：
				a：在子类方法的局部范围找，有就使用
				b：在子类的成员范围找，有就使用
				c：在父类的成员范围找，有就使用
				d：如果还找不到，会报错
				
*/
class Father{
	public int num = 10;
	
	public void method(){
		int num = 50;
	}
}

class Son extends Father{
	public int num2 = 20;
	public int num = 30;
	public void show(){
		int num = 40;
		System.out.println(num);
		System.out.println(num2);
		//System.out.println(num3);//找不到符号
	}
}

public class ExtendsDemo4{
	public static void main(String[] args){
		Son s = new Son();
		s.show();
	}
}
```

# super关键字
- super的用法和this很像
  - this代表本类对应的引用
  - super代表父类存储空间的标识（可以理解为父类引用）
## 用法
- 访问成员变量
  - this.成员变量
  - super.成员变量
- 访问构造方法
  - this(...)
  - super(...)
- 访问成员方法
  - this.成员方法()
  - super.成员方法()
# 继承中构造方法的关系
- 子类中所有的构造方法默认都会访问父类中空参的构造方法
  - 因为子类会继承父类中的数据，可能还会使用父类的数据。所以，子类初始化之前，一定要完成父类数据的初始化
  - 每一个构造方法的第一条语句默认都是：super()
- 如果父类中没有构造方法，该怎么办？
  - 子类通过super去显示调用父类其他的带参的构造方法
  - 子类通过this去调用本类的其他构造方法
    - 本类其他构造方法也必须首先访问了父类的构造方法
  - 一定要注意：
    - super(...)或者this(...)必须出现在第一条语句上
    - 否则，就会有父类数据的多次初始化
# 继承中成员方法的关系
- 通过子类对象去访问一个方法
  - 首先在子类中找
  - 然后在父类中找
  - 如果还是没有就报错
## 方法重写
### 概述
- 子类中出现了和父类中一模一样的方法声明，也被称为方法覆盖，方法复写。
- 使用特点：
  - 如果方法名不同，有就调用对应的方法。
  - 如果方法名相同，最终使用的就是子类自己的。
### 应用
当子类需要父类的功能，而功能主体子类有自己特有内容时，可以重写父类中的方法，这样，即沿袭了父类的功能，又定义了子类特有的内容。
### 注意事项
- 父类中私有方法不能被重写
- 子类重写父类方法时，访问权限不能更低
- 父类静态方法，子类也必须通过静态方法进行重写（其实算不上方法重写）