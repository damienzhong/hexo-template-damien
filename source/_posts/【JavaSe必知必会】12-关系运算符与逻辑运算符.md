---
title: 【JavaSe必知必会】12-关系运算符与逻辑运算符
date: 2018-11-15 15:32:16
tags: javase
categories: javase
---
# 关系运算符
## 概述
![image](http://image.damienzhong.com/%E5%85%B3%E7%B3%BB%E8%BF%90%E7%AE%97%E7%AC%A6.jpg)
- 注1：比较运算符的结果都是boolean型，也就是要么是true，要么是false。
- 注2：比较运算符“==”不能误写成“=” 。
## 代码演示

```
/*
	比较运算符：
		==,!=,>,>=,<,<=
		
	特点：
		无论你的操作是简单还是复杂，结果是boolean类型。
		
	注意事项：
		"=="不能写成"="。
*/
class OperatorDemo {
	public static void main(String[] args) {
		int x = 3;
		int y = 4;
		int z = 3;
	
		System.out.println(x == y);
		System.out.println(x == z);
		System.out.println((x+y) == (x+z));
		System.out.println("------------");
		
		System.out.println(x != y);
		System.out.println(x > y);
		System.out.println(x >= y);
		System.out.println(x < y);
		System.out.println(x <= y);
		System.out.println("------------");
		
		int a = 10;
		int b = 20;
		
		//boolean flag = (a == b);
		//boolean flag = (a = b); //这个是有问题的，不兼容的类型
		//System.out.println(flag);
		
		int c = (a = b); //把b赋值给a，然后把a留下来
		System.out.println(c);
	}
}
```
# 逻辑运算符
## 概述
![image](http://image.damienzhong.com/%E9%80%BB%E8%BE%91%E8%BF%90%E7%AE%97%E7%AC%A6.png)
- 逻辑运算符用于连接布尔型表达式，在Java中不可以写成3<x<6，应该写成x>3 & x<6 。
- “&”和“&&”的区别：
  - 单&时，左边无论真假，右边都进行运算；
  - 双&时，如果左边为真，右边参与运算，如果左边为假，那么右边不参与运算。
  - “|”和“||”的区别同理，双或时，左边为真，右边不参与运算。
- 异或( ^ )与或( | )的不同之处是：当左右都为true时，结果为false。

```
/*
	逻辑运算符：
		&,|,^,!
		&&,||
		
	特点：
		逻辑运算符一般用于连接boolean类型的表达式或者值。
			
		表达式：就是用运算符把常量或者变量连接起来的符合java语法的式子。
			算术表达式：a + b
			比较表达式：a == b
			
	结论：
		&逻辑与:有false则false。
		|逻辑或:有true则true。
		^逻辑异或:相同为false，不同为true。
			举例：情侣关系。男男,男女,女男,女女
		!逻辑非:非false则true，非true则false。
			特点：偶数个不改变本身。
*/
class OperatorDemo {
	public static void main(String[] args) {
		int a = 3;
		int b = 4;
		int c = 5;
		
		//&逻辑与
		System.out.println((a > b) & (a > c)); //false & false = false
		System.out.println((a > b) & (a < c)); //false & true = false
		System.out.println((a < b) & (a > c)); //true & false = false
		System.out.println((a < b) & (a < c)); //true & true = true
		System.out.println("---------------");
		
		//|逻辑或
		System.out.println((a > b) | (a > c)); //false | false = false
		System.out.println((a > b) | (a < c)); //false | true = true
		System.out.println((a < b) | (a > c)); //true | false = true
		System.out.println((a < b) | (a < c)); //true | true = true
		System.out.println("---------------");
		
		//^逻辑异或
		System.out.println((a > b) ^ (a > c)); //false ^ false = false
		System.out.println((a > b) ^ (a < c)); //false ^ true = true
		System.out.println((a < b) ^ (a > c)); //true ^ false = true
		System.out.println((a < b) ^ (a < c)); //true ^ true = false
		System.out.println("---------------");
		
		//!逻辑非
		System.out.println(!(a > b)); //!false = true
		System.out.println(!(a < b)); //!true = false
		System.out.println(!!(a > b)); //!!false = false
		System.out.println(!!!(a > b)); //!!false = true
	}
}
```

```
/*
	&&和&的区别? 同理||和|的区别?
		A:最终结果一样。
		B:&&具有短路效果。左边是false，右边不执行。
		
	开发中常用的逻辑运算符：
		&&,||,!
*/
class OperatorDemo2 {
	public static void main(String[] args) {
		int a = 3;
		int b = 4;
		int c = 5;
		
		//&&双与
		System.out.println((a > b) && (a > c)); //false && false = false
		System.out.println((a > b) && (a < c)); //false && true = false
		System.out.println((a < b) && (a > c)); //true && false = false
		System.out.println((a < b) && (a < c)); //true && true = true
		System.out.println("----------------");
		
		int x = 3;
		int y = 4;
		
		//boolean b1 = ((x++ == 3) & (y++ == 4));
		//boolean b1 = ((x++ == 3) && (y++ == 4));
		//boolean b1 = ((++x == 3) & (y++ == 4));
		boolean b1 = ((++x == 3) && (y++ == 4));
		System.out.println("x:"+x);
		System.out.println("y:"+y);
		System.out.println(b1);
	}
}
```
