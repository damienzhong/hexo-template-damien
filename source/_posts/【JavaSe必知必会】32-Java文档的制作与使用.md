---
title: 【JavaSe必知必会】32-Java文档的制作与使用
date: 2018-11-15 18:26:58
tags: javase
categories: javase
---
# 工具类制作
## 工具类中使用静态

```
/**
	我要堆数组进行操作
	
	在同一个文件夹下，类定义在两个文件中和定义在一个文件中其实一样的。
*/
public class ArrayDemo{
	public static void main(String[] args){
		//定义一个数组
		int[] arr = {18,23,6,55,21};
		
		//遍历数组
		/*for(int x=0;x<arr.length;x++){
			if(x==arr.length){
				System.out.println(arr[x]);
			}else{
				System.out.print(arr[x]+",");
			}
		}*/
		//如果我有多个数组都要进行遍历，那么，代码的重复都就很高
		//如何改进？用方法改进
		//printArray(arr);
		
		//测试类的作用：创建其他类的对象，调用其他类的功能
		//而我们现在的操作是跟数组相关的，所有，应该把这些操作定义到数组操作类中。
		//定义一个数组的操作类
		//ArrayTool t = new ArrayTool();
		//t.printArray(arr);
		
		//方法改进为静态后，就可以直接通过类名调用
		ArrayTool.printArray(arr);
	}
	
	/*public static void printArray(int[] arr){
		for(int x=0;x<arr.length;x++){
			if(x==arr.length){
				System.out.println(arr[x]);
			}else{
				System.out.print(arr[x]+",");
			}
		}
	}*/
}
```

```
public class ArrayTool{
	//把构造方法私有，外界就不能再创建对象了
	private ArrayTool(){}
	
	public static void printArray(int[] arr){
		for(int x=0;x<arr.length;x++){
			if(x==arr.length){
				System.out.println(arr[x]);
			}else{
				System.out.print(arr[x]+",");
			}
		}
	}
}
```



# 制作帮助文档
## 制作工具类

```
/**
*	数组常用操作工具类
*	@author 呆萌在
*	@version v1.0
*/
public class ArrayTool{
	//把构造方法私有，外界就不能再创建对象了
	private ArrayTool(){}
	
	/**
	*	遍历数组
	*	@param arr
	*/
	public static void printArray(int[] arr){
		for(int x=0;x<arr.length;x++){
			if(x==arr.length){
				System.out.println(arr[x]);
			}else{
				System.out.print(arr[x]+",");
			}
		}
	}
	
	/**
	*	获取指定数值的索引
	*	@param arr,value
	*	@return int
	*/
	public static int getIndex(int[] arr,int value){
		int index = -1;
		
		for(int x=0;x<arr.length;x++){
			if(arr[x]==value){
				index = x;
				break;
			}
		}
		return index;
	}
	
	/**
	*	获取数组中的最大值
	*	@param arr
	*	@return int
	*/
	public static int getMax(int[] arr){
		int max = arr[0];
		for(int x=1;x<arr.length;x++){
			if(arr[x]>max){
				max = arr[x];
			}
		}
		return max;
	}
}
```

## 制作帮助文档（API）
javadoc -d 目录 -author -version ArrayTool.java
# 通过API学习Math类
## Math类概述
Math包含用于执行基本数学运算的方法
## Math类特点
没有构造方法，因为成员都是静态的

```
/*
	Math：用于执行基本的数字运算
	
	由于Math类在java.lang包下，所以不需要导包
	
	特点：
		没有构造方法，因为它的成员全部是静态的
		
	掌握一个方法：
		获取随机数
		public static double random();返回带正号的double值，该值大于等于0.0且小于1.0
*/
public class MathDemo{
	public static void main(String[] args){
		//获取一个随机数
		//double d = Math.random();
		//System.out.println(d);
		
		//我要获取一个1-100之间的随机数
		for(int i=0;i<100;i++){
			int num = (int)(Math.random()*100)+1;
			System.out.println(num);
		}	
	}
}
```
## 猜数字小游戏

```
/*
	猜数字小游戏（数据在1-100之间）
	
	分析：
		A：程序产生一个随机数。（被猜的）
		B：键盘录入数据。（你猜的）
		C：把你猜的和被猜的进行比较
			a：大了
			b：小了
			c：猜中了
		D：给出多次猜的机会，猜中就结束
			
*/
import java.util.Scanner;
public class GuessNumber{
	public static void main(String[] args){
		//程序产生一个随机数。（被猜的）
		int number = (int)(Math.random()*100)+1;
		
		//给出多次猜的机会，猜中就结束
		while(true){
			//键盘录入数据。（你猜的）
			Scanner sc = new Scanner(System.in);
			System.out.println("请输入您要猜的数据（1-100）：");
			int guessNumber = sc.nextInt();
			
			//把你猜的和被猜的进行比较
			if(guessNumber > number){
				System.out.println("你猜的数据"+guessNumber+"大了");
			}else if(guessNumber < number){
				System.out.println("你猜的数据"+guessNumber+"小了");
			}else{
				System.out.println("恭喜你，猜中了，五百万带回家！！！");
				break;
			}
		}
	}
}

```
