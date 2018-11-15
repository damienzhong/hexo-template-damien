---
title: 【JavaSe必知必会】15-Java键盘录入
date: 2018-11-15 15:42:41
tags: javase
categories: javase
---
# 键盘录入数据
## 概述
我们目前在写程序的时候，数据值都是固定的，但是实际开发中，数据值肯定是变化的，所以，我准备把数据改进为键盘录入，提高程序的灵活性。
## 如何实现键盘录入数据呢?(目前先记住使用)
- 导包(位置放到class定义的上面)
  - import java.util.Scanner;
- 创建对象
  - Scanner sc = new Scanner(System.in);
- 接收数据
  - int x = sc.nextInt();
## 代码演示

```
/*
	为了让程序的数据更符合开发的数据，我们就加入了键盘录入。
	让程序更灵活一下。
	
	那么，我们如何实现键盘数据的录入呢?
		A:导包
			格式：
				import java.util.Scanner; 
			位置：
				在class上面。
		B:创建键盘录入对象
			格式：
				Scanner sc = new Scanner(System.in);
		C:通过对象获取数据	
			格式：
				int x = sc.nextInt();
*/
import java.util.Scanner;

class ScannerDemo {
	public static void main(String[] args) {
		//创建键盘录入数据对象
		Scanner sc = new Scanner(System.in);
		
		System.out.println("请你输入一个数据：");
		int x = sc.nextInt();
		
		System.out.println("你输入的数据是："+x);
	}
}
```


# 键盘录入数据练习
- 键盘录入两个数据，并对这两个数据求和，输出其结果

```
/*
	键盘录入练习：
		键盘录入两个数据，并对这两个数据求和，输出其结果
*/
import java.util.Scanner;

class ScannerTest {
	public static void main(String[] args) {
		//键盘录入两个数据，并对这两个数据求和，输出其结果
		//创建键盘录入对象
		Scanner sc = new Scanner(System.in);
		
		System.out.println("请输入第一个数据：");
		int x = sc.nextInt();
		
		System.out.println("请输入第二个数据：");
		int y = sc.nextInt();
		
		//把键盘录入的数据进行相加即可
		int sum = (x + y);
		System.out.println("sum:"+sum);
	}
}
```

- 键盘录入两个数据，获取这两个数据中的最大值

```
/*
	键盘录入练习：键盘录入两个数据，获取这两个数据中的最大值
*/

import java.util.Scanner;

class ScannerTest2 {
	public static void main(String[] args) {
		//创建键盘录入对象
		Scanner sc = new Scanner(System.in);
		
		System.out.println("请输入第一个数据：");
		int a = sc.nextInt();
		
		System.out.println("请输入第二个数据：");
		int b = sc.nextInt();
		
		//获取这两个数据中的最大值
		int max = (a > b? a: b);
		System.out.println("max:"+max);
	}
}
```

- 键盘录入三个数据，获取这三个数据中的最大值
- 键盘录入两个数据，比较这两个数据是否相等

```
/*
	练习：
		键盘录入三个数据，获取这三个数据中的最大值
		键盘录入两个数据，比较这两个数据是否相等
*/
import java.util.Scanner;

class ScannerTest3 {
	public static void main(String[] args) {
		//键盘录入三个数据，获取这三个数据中的最大值
	
		//创建键盘录入对象
		Scanner sc = new Scanner(System.in);
		
		System.out.println("请输入第一个数据：");
		int a = sc.nextInt();
		
		System.out.println("请输入第二个数据：");
		int b = sc.nextInt();
		
		System.out.println("请输入第三个数据：");
		int c = sc.nextInt();
		
		//获取这三个数据中的最大值
		int temp = ((a > b)? a: b);
		int max = (temp > c? temp : c);
		System.out.println("max:"+max);
		System.out.println("------------------");
		
		//键盘录入两个数据
		System.out.println("请输入第一个数据：");
		int x = sc.nextInt();
		
		System.out.println("请输入第二个数据：");
		int y = sc.nextInt();
		
		//比较这两个数据是否相等
		boolean flag = (x == y);
		System.out.println("flag:"+flag);
	}
}
```

