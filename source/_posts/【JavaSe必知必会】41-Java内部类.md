---
title: 【JavaSe必知必会】41-Java内部类
date: 2018-11-15 18:35:28
tags: javase
categories: javase
---
# 内部类概述
把类定义在其他类的内部，这个类就被称为内部类。
### 举例
在类A中定义了一个类B，类B就是内部类。
## 内部类的访问特点
- 内部类可以直接访问外部类的成员，包括私有。
- 外部类要访问内部类的成员，必须创建对象

```
/*
	内部类：
		把类定义在其他类的内部，这个类就被称为内部类。
		举例：在类A中定义一个类B，类B就是内部类
		
	内部类的访问特点：
		A：内部类可以直接访问外部类的成员，包括私有的
		B：外部类要访问内部类的成员，必须创建对象
*/
class Outer{
	private int num = 10;
	
	class Inner{
		public void show(){
			System.out.println(num);
		}
	}
	
	public void method(){
		//找不到符号
		//show();
		
		Inner i = new Inner();
		i.show();
	}
}

public class InnerDemo{
	public static void main(String[] args){
		Outer o = new Outer();
	}
}
```

# 内部类位置
按照内部类在类中定义的位置不同，可以分为如下两种格式：
- 成员位置（成员内部类）
- 局部位置（局部内部类）

```
/*
	内部类位置
		成员位置：在成员位置定义的类，被称为成员内部类
		局部位置：在局部位置定义的类，被称为局部内部类
*/
class Outer{
	private int num = 10;
	
	//成员位置
	/*class Inner{
		
	}*/
	
	public void method(){
		class Inner{
		
		}
	}
}

public class InnerClassDemo{
	public static void main(String[] args){
		
	}
}
```

## 成员内部类
### 外界如何创建对象
外部类名.内部类名 对象名 = 外部类对象.内部类对象;
### 成员内部类的常见修饰符
- private 为了保证数据的安全性
- static 为了让数据访问更方便
  - 被静态修饰的成员内部类只能访问外部类的静态成员
  - 内部类方法被静态修饰后的方法
    - 静态方法
    - 非静态方法

```
/*
	成员内部类的修饰符：
		private:为了保证数据的安全性
		static:为了方便访问数据
			注意：静态内部类访问的外部类数据必须用静态修饰。
	
	案例：我是一个人（人有身体，身体内有心脏）
	
		class Body{
			
			private class Heart{
				public void operator(){
					System.out.println("心脏支架手术");
				}
			}
			
			public void method(){
				if(如果你是外科医生){
					Heart h = new Heart();
					h.operator();
				}
			}
		}
		
		按照我们刚才的讲解，来使用一下。
		Body.Heart bh = new Body().new Heart();
		bh.operator();
		//加了private之后，就不能被访问了，那么，怎么玩呢？
		Body b = new Body();
		b.method();
*/
class Outer{
	private int num = 10;
	private static int num2 = 100;
	
	public static class Inner{
		public void show(){
			//System.out.println(num);
			System.out.println(num2);
		}
		
		public static void show2(){
			//System.out.println(num);
			System.out.println(num2);
		}
	}
}

public class InnerClassDemo3{
	public static void main(String[] args){
		//Outer.Inner oi = new Outer().new Inner();
		//oi.show();
		//oi.show2();
		//成员内部类被静态修饰后的访问方式：
		//格式：外部类名.内部类名 对象名 = new 外部类名.内部类名
		Outer.Inner oi = new Outer.Inner();
		oi.show();
		oi.show2();
		
		Outer.Inner.show2();
	}
}
```

### 局部内部类
- 可以直接访问外部类的成员
- 可以创建内部类对象，通过对象调用内部类方法，来使用局部内部类功能
- 局部内部类访问局部变量的注意事项：
  - 必须被final修饰
  - 为什么呢？
    - 因为局部变量会随着方法的调用完毕而消失，这个时候，局部对象并没有立马从对内存中消失，还要使用那个变量。为了让数据还能继续被使用，就用final修饰，这样，在堆内存里面存储的其实是一个常量值。通过反编译工具可以看一下。

```
/*
	局部内部类：
		A:可以直接访问外部类的成员
		B:在局部位置，可以创建内部类对象，通过对象调用内部类方法，来使用局部内部类功能
		
	局部内部类访问局部变量的注意事项？
		A：局部内部类访问局部变量必须用final修饰
		B：为什么呢？
			局部变量是随着方法的调用而调用，随着调用完毕而消失。
			而对内存的内容并不会立即消失。所以，我们加final修饰。
			加如final修饰后，这个变量就成了常量，既然是常量，你消失了，
			我在内存中存储的是数据20，所以，我还是有数据在使用的。
*/
class Outer{
	private int num = 10;
	
	public void method(){
		int num2 = 20;
		class Inner{
			public void show(){
				System.out.println(num);
				System.out.println(num2);
			}
		}
		
		Inner i = new Inner();
		i.show();
	}
}

public class InnerClassDemo4{
	public static void main(String[] args){
		Outer o = new Outer();
		o.method();
	}
}
```

## 匿名内部类
- 就是内部类的简化写法
- 前提：存在一个类或者接口
  - 这里的类可以是具体类也可以是抽象类
- 格式：
  - new 类名或者接口名(){重写方法}
- 本质：
  - 是一个继承了类或者实现了接口的子类匿名对象

```
/*
	匿名内部类：
		就是内部类的简化写法。
		
	前提：存在一个类或者接口
		这里的类可以是具体的类也可以是抽象类。
		
	格式：
		new 类名或者接口名(){
			重写方法;
		}
		
	本质是什么呢？
		是一个继承了该类或者实现了该接口的子类匿名对象
*/
interface Inter{
	public abstract void show();
	public abstract void show2();
}

class Outer{
	public void method(){
		//一个方法的时候
		/*new Inter(){
			public void show(){
				System.out.println("show");
			}
			public void show()2{
				System.out.println("show");
			}
		}.show();
		*/
		//两个方法的时候
		/*new Inter(){
			public void show(){
				System.out.println("show");
			}
			public void show2(){
				System.out.println("show");
			}
		}.show();
		new Inter(){
			public void show(){
				System.out.println("show");
			}
			public void show2(){
				System.out.println("show");
			}
		}.show2();
		*/
		//如果接口或类有很多个方法，就很麻烦
		//那么，如何改进呢？
		Inter i = new Inter(){//多态
			public void show(){
				System.out.println("show");
			}
			public void show2(){
				System.out.println("show");
			}
		};
		i.show();
		i.show2();
	}
}

public class InnerClassDemo5{
	public static void main(String[] args){
		Outer o = new Outer();
		o.method();
	}
}
```
