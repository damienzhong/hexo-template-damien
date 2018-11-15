---
title: 【JavaSe必知必会】13-Java运算符之三目运算符
date: 2018-11-15 15:33:40
tags: javase
categories: javase
---
# 三目运算符
## 概述
三目运算符也可称为三元运算符。

**格式**
==(关系表达式)?表达式1：表达式2；==
- 如果条件为true，运算后的结果是表达式1；
- 如果条件为false，运算后的结果是表达式2；

## 代码演示

```
/*
	单目运算符：~3
	双目运算符：3 + 4

	三目运算符：
		格式：比较表达式?表达式1:表达式2;
		
		比较表达式:结果是一个boolean类型。
		
		执行流程：
			根据比较表达式的计算返回一个true或者false。
			如果是true，就把表达式1作为结果。
			如果是false，就把表达式2作为结果。
*/
class OperatorDemo {
	public static void main(String[] args) {
		int x = 100;
		int y = 200;
		
		int z = ((x > y)? x: y);
		
		//int z = ((x < y)? x: y);
		
		//int z = ((x == y)? x: y);
		
		//报错
		//int z = ((x = y)? x : y);
		
		System.out.println("z:"+z);
	}
}
```

## 真题演练

```
/*
	练习：
		获取两个整数中的最大值
		获取三个整数中的最大值
		比较两个整数是否相同
*/
class OperatorTest {
	public static void main(String[] args) {
		//获取两个整数中的最大值
		int x = 100;
		int y = 200;
		
		int max = (x > y? x: y);
		System.out.println("max:"+max);
		System.out.println("--------");
		
		//获取三个整数中的最大值
		int a = 10;
		int b = 30;
		int c = 20;
		
		//分两步：
		//A:先比较a,b的最大值
		//B:拿a,b的最大值在和c进行比较
		int temp = ((a > b)? a: b);
		//System.out.println(temp);
		int max1 = (temp > c? temp: c);
		System.out.println("max1:"+max1);
		
		//一步搞定
		//int max2 = (a > b)?((a > c)? a: c):((b > c)? b: c);
		//这种做法不推荐。
		//int max2 = a > b?a > c? a: c:b > c? b: c;
		//System.out.println("max2:"+max2);
		System.out.println("--------");
		
		//比较两个整数是否相同
		int m = 100;
		int n = 200;
		
		//boolean flag = (m == n)? true: false;
		boolean flag = (m == n);
		System.out.println(flag);
	}
}
```
