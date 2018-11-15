---
title: 【JavaSe必知必会】10-数据类型转换与运算
date: 2018-11-15 11:24:00
tags: javase
categories: javase
---
## 数据类型转换默认转换
- +是一个运算符, 我们应该能够看懂，做数据的加法。
- boolean类型不能转换为其他的数据类型
- 默认转换
  - byte,short,char—int—long—float—double
  - byte,short,char相互之间补转换，他们参与运算首先转换为int类型

```
/*
	+是一个运算符(我们等会讲解)。做加法运算的。
	
	一般来说，我们在运算的时候，要求参与运算的数据类型必须一致。
	
	注意：
		boolean类型不能转换为其他的数据类型

	默认转换(从小到大的转换)
		A:byte,short,char—int—long—float—double
		B:byte,short,char相互之间不转换，他们参与运算首先转换为int类型
*/
class DataTypeDemo3 {
	public static void main(String[] args) {
		//直接输出的方式做加法
		//System.out.println(3 + 4);
	
		//两个int类型做加法
		int x = 3;
		int y = 4;
		int z = x + y;
		System.out.println(z);
		
		//定义一个byte类型，一个int类型，做加法
		byte a = 3;
		int b = 4;
		System.out.println(a + b);
		
		//可能损失精度
		//byte c =  a + b;
		int c = a + b;
		System.out.println(c);
	}
}
```
## 不同数据类型变量参与运算图解
![image](http://image.damienzhong.com/%E4%B8%8D%E5%90%8C%E6%95%B0%E6%8D%AE%E7%B1%BB%E5%9E%8B%E5%8F%98%E9%87%8F%E5%8F%82%E4%B8%8E%E8%BF%90%E7%AE%97%E5%9B%BE%E8%A7%A3.png)
## 强制转换
  - 目标类型 变量名=(目标类型)(被转换的数据);

```
/*
	强制转换：
		从大的数据类型到小的数据类型。
		
		格式：
			目标数据类型 变量 = (目标数据类型) (被转换的数据);
			
		注意：
			不要随意的去使用强制转换，因为它隐含了精度损失问题。
*/
class DataTypeDemo4 {
	public static void main(String[] args) {
		byte a = 3;
		int b = 4;
		
		//这个肯定没有问题
		//int c = a + b;
		
		//byte c = 7;
		//这个是有问题的
		//byte c = a + b; 
		//用强制类型转换改进
		byte c = (byte) (a + b);
		System.out.println(c);
	}
}
```
### 思考题

```
/*
	思考题1：请问下面这个有没有问题
		double d = 12.345;
		float f = d;
		
	思考题2：看看下面两个定义有没有区别呢?
		float f1 = (float)12.345;
		float f2 = 12.345f;
		
		f1其实是通过一个double类型转换过来的。
		而f2本身就是一个float类型。
*/
class DataTypeDemo5 {
	public static void main(String[] args) {
		//把double赋值给float，加了强制类型转换
		double d = 12.345;
		float f = (float)d;
		
		//看看下面两个定义有没有区别呢?
		float f1 = (float)12.345;
		float f2 = 12.345F;
	}
}
```
### 常量运算与变量运算的区别

```
/*
	面试题：
		byte b1=3,b2=4,b;
		b=b1+b2;
		b=3+4;
		哪句是编译失败的呢？为什么呢？
		b = b1 + b2;是有问题的。
		因为变量相加，会首先看类型问题，最终把结果赋值的也会考虑类型问题。
		常量相加，首先做加法，然后看结果是否在赋值的数据类型范围内，如果不是，才报错。
*/
class DataTypeDemo6 {
	public static void main(String[] args) {
		//定义了三个byte类型的变量，b1，b2，b3
		//b1的值是3，b2的值是4，b没有值
		byte b1 = 3,b2 = 4,b;
		
		//b = b1 + b2; //这个是类型提升，所有有问题
		
		b = 3 + 4; //常量，先把结果计算出来，然后看是否在byte的范围内，如果在就不报错。
	}
}
```
### 数据溢出原理解析


```
/*
	byte b = 130;有没有问题?如果我想让赋值正确，可以怎么做?结果是多少呢?
	
	练习：byte b = (byte)300;
*/
class DataTypeDemo7 {
	public static void main(String[] args) {
		//因为byte的范围是：-128到127。
		//而130不在此范围内，所以报错。
		//byte b = 130; 
		
		//我们可以使用强制类型转换
		byte b = (byte) 130;
		
		//结果是多少呢?
		System.out.println(b);
	}
}
/*
	分析过程：
		我们要想知道结果是什么，就应该知道是如何进行计算的。
		而我们又知道计算机中数据的运算都是补码进行的。
		而要得到补码，首先要计算出数据的二进制。
		
		A:获取130这个数据的二进制。
			00000000 00000000 00000000 10000010
			这是130的原码，也是反码，还是补码。
		B:做截取操作，截成byte类型的了。
			10000010 
			这个结果是补码。
		C:已知补码求原码。
					符号位		数值位
			补码：	1			0000010
			
			反码：	1			0000001
			
			原码：	1			1111110
*/

```
### 常用字符与ASCII代码对照表
![image](http://image.damienzhong.com/ASCII%E7%A0%81%E8%A1%A8.png)
### 字符参与运算

```
/*
	看程序写结果
	
	通过字符和一个整数相加，我们给出一张表：ASCII码表。
		通过看完这张表以后，我们要记住三个值：
			'a'		97
			'A'		65
			'0'		48
*/
class DataTypeDemo8 {
	public static void main(String[] args) {
		//直接输出一个字符
		System.out.println('a'); //a
		//输出一个字符和一个整数做加法
		System.out.println('a'+1); //98
	}
}
```
### 字符串参与运算
```
/*
	看程序写结果
		字符串数据和其他数据做+，结果是字符串类型。
		这里的+不是加法运算，而是字符串连接符。
*/
class DataTypeDemo9 {
	public static void main(String[] args) {
		System.out.println("hello"+'a'+1); //helloa1
		System.out.println('a'+1+"hello"); //98hello
		
		System.out.println("5+5="+5+5); //5+5=55
		System.out.println(5+5+"=5+5"); //10=5+5
	}
}
```
