---
title: 【JavaSe必知必会】27-二维数组定义详解
date: 2018-11-15 17:20:08
tags: javase
categories: javase
---
# 二维数组概述
二维数组其实就是一个元素为一维数组的数组。
## 二维数组定义格式
### 格式1
- 数据类型[][] 变量名 = new 数据类型[m][n];
- m表示这个二维数组有多少个一维数组
- n表示每一个一维数组的元素个数
- 举例：
  - int[][] arr = new int[3][2];
  - 定义了一个二维数组arr
  - 这个二维数组有3个一维数组，名称是arr[0],arr[1],arr[2]
  - 每个一维数组有2个元素，可以通过arr[m][n]来获取
  - 表示获取第m+1个一维数组的第n+1个元素
#### 代码演示

```
/*
	二维数组：就是元素为一维数组的一个数组。
	
	格式1：
		数据类型[][] 数组名 = new 数据类型[m][n];
		
		m:表示这个二维数组有多少个一维数组。
		n:表示每一个一维数组的元素有多少个。
		
	注意：
		A:以下格式也可以表示二维数组
			a:数据类型 数组名[][] = new 数据类型[m][n];
			b:数据类型[] 数组名[] = new 数据类型[m][n];
		B:注意下面定义的区别
			int x;
			int y;
			int x,y;
			
			int[] x;
			int[] y[];
			
			int[] x,y[];
*/
class Array2Demo {
	public static void main(String[] args) {
		 //定义一个二维数组
		 int[][] arr = new int[3][2];
		 //定义了一个二维数组arr
		 //这个二维数组有3个一维数组的元素
		 //每一个一维数组有2个元素
		 //输出二维数组名称
		 System.out.println(arr); //地址值	[[I@175078b
		 //输出二维数组的第一个元素一维数组的名称
		 System.out.println(arr[0]); //地址值	[I@42552c
		 System.out.println(arr[1]); //地址值	[I@e5bbd6
		 System.out.println(arr[2]); //地址值	[I@8ee016
		 //输出二维数组的元素
		 System.out.println(arr[0][0]); //0
		 System.out.println(arr[0][1]); //0
	}
}
```
#### 内存图展示
![image](http://image.damienzhong.com/%E4%BA%8C%E7%BB%B4%E6%95%B0%E7%BB%84%E6%A0%BC%E5%BC%8F1%E5%86%85%E5%AD%98%E5%9B%BE.JPG)
### 格式2
数据类型[][] 变量名 = new 数据类型[m][];
- m表示这个二维数组有多少个一维数组
- 这一次没有直接给出一维数组的元素个数，可以动态的给出。
- 举例：
  - int[][] arr = new int[3][];
  - arr[0] = new int[2];
  - arr[1] = new int[3]
  - arr[2] = new int[1];
#### 代码演示

```
/*
	格式2：
		数据类型[][] 数组名 = new 数据类型[m][];
		
		m:表示这个二维数组有多少个一维数组。
		列数没有给出，可以动态的给。这一次是一个变化的列数。
*/
class Array2Demo2 {
	public static void main(String[] args) {
		//定义数组
		int[][] arr = new int[3][];
		
		System.out.println(arr);	//[[I@175078b
		System.out.println(arr[0]); //null
		System.out.println(arr[1]); //null
		System.out.println(arr[2]); //null
		
		//动态的为每一个一维数组分配空间
		arr[0] = new int[2];
		arr[1] = new int[3];
		arr[2] = new int[1];
		
		System.out.println(arr[0]); //[I@42552c
		System.out.println(arr[1]); //[I@e5bbd6
		System.out.println(arr[2]); //[I@8ee016
		
		System.out.println(arr[0][0]); //0
		System.out.println(arr[0][1]); //0
		//ArrayIndexOutOfBoundsException
		//System.out.println(arr[0][2]); //错误
		
		arr[1][0] = 100;
		arr[1][2] = 200;
	}
}
```
#### 内存图展示
![image](http://image.damienzhong.com/%E4%BA%8C%E7%BB%B4%E6%95%B0%E7%BB%84%E6%A0%BC%E5%BC%8F2%E5%86%85%E5%AD%98%E5%9B%BE.JPG)
### 格式3
```
 数据类型[][] 变量名 = new 数据类型[][]{{元素…},{元素…},{元素…}};
 简化版格式：
 数据类型[][] 变量名 = {{元素…},{元素…},{元素…}};
 举例：
   int[][] arr =  {{1,2,3},{4,6},{6}};
```
  
#### 代码演示

```
/*
	格式3：
		基本格式：
			数据类型[][] 数组名 = new 数据类型[][]{{元素1,元素2...},{元素1,元素2...},{元素1,元素2...}};
		简化版格式：
			数据类型[][] 数组名 = {{元素1,元素2...},{元素1,元素2...},{元素1,元素2...}};
			
		举例：
			int[][] arr = {{1,2,3},{4,5,6},{7,8,9}};
			int[][] arr = {{1,2,3},{4,5},{6}};
*/
class Array2Demo3 {
	public static void main(String[] args) {
		//定义数组
		int[][] arr = {{1,2,3},{4,5},{6}};
		
		System.out.println(arr);
		System.out.println(arr[0]);
		System.out.println(arr[1]);
		System.out.println(arr[2]);
		
		System.out.println(arr[0][0]); //1
		System.out.println(arr[1][0]); //4
		System.out.println(arr[2][0]); //6
		
		System.out.println(arr[0][1]); //2
		System.out.println(arr[1][1]); //5
		//越界
		System.out.println(arr[2][1]); //错误
	}
}
```
#### 内存图展示
![image](http://image.damienzhong.com/%E4%BA%8C%E7%BB%B4%E6%95%B0%E7%BB%84%E6%A0%BC%E5%BC%8F3%E5%86%85%E5%AD%98%E5%9B%BE.JPG)
