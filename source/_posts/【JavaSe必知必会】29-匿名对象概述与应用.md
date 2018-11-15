---
title: 【JavaSe必知必会】29-匿名对象概述与应用
date: 2018-11-15 17:22:10
tags: javase
categories: javase
---
# 匿名对象
- 匿名对象：就是没有名字的对象
  - 是对象的一种简化表示形式
- 匿名对象的两种使用情况
  - 对象调用方法仅仅一次的时候
  - 作为实际参数传递
## 代码演示

```
/**
	注意：一个类文件中可以写多个类，但是只有一个类能带public，而且该类名必须与文件名相同
	
	匿名对象：就是没有名字的对象
	
	匿名对象的应用场景：
		A：调用方法，仅仅只调用一次的时候
			注意：调用多次的时候，不适合
				那么，这种匿名对象有什么好处呢？
				有，匿名对象调用完毕就是垃圾。可以被垃圾回收器回收
		B：匿名对象可以作为实际参数进行传递
*/
class Student{
	public void study(){
		System.out.println("我最爱看呆萌钟的视频学习编程了~");
	}
}

class StudentDemo{
	public void method(Student s){
		s.study();
	}
}

public class AnonymousDemo{
	public static void main(String[] args){
		//带名字的调用
		Student s = new Student();
		System.out.println(s);
		System.out.println(s);
		s.study();
		s.study();
		System.out.println("----------------------------");
		
		//匿名对象
		//new Student();
		System.out.println(new Student());
		System.out.println(new Student());//这里其实是重新创建了一个对象
		//匿名对象调用方法
		new Student().study();
		new Student().study();
		System.out.println("----------------------------");
		
		//匿名对象作为实际参数传递
		StudentDemo sd = new StudentDemo();
		//Student ss = new Student();
		//sd.method(ss);
		//匿名对象
		sd.method(new Student());
		
		//全用匿名对象
		new StudentDemo().method(new Student());
	}
}	
```
