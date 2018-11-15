---
title: 【JavaSe必知必会】25-数组定义与初始化
date: 2018-11-15 17:17:43
tags: javase
categories: javase
---
# 数组概述
- 需求：现在需要统计某公司员工的工资情况，例如计算平均工资、找到最高工资等。假设该公司有80名员工，用前面所学的知识，程序首先需要声明80个变量来分别记住每位员工的工资，然后在进行操作，这样做会显得很麻烦。为了解决这种问题，Java就提供了数组供我们使用。
- 那么数组到底是什么呢?有什么特点呢?通过上面的分析：我们可以得到如下两句话：
  - 数组是存储多个变量(元素)的东西(容器)
  - 这多个变量的数据类型要一致
# 数组概念
- 数组概念
  - 数组是存储同一种数据类型多个元素的集合。也可以看成是一个容器。
  - 数组既可以存储基本数据类型，也可以存储引用数据类型。
- 数组的定义格式
  - 格式1：数据类型[] 数组名;
  - 格式2：数据类型 数组名[];
> **注意：这两种定义做完了，数组中是没有元素值的。**
> - 针对数组定义两种格式，推荐使用第一种格式。因为第一种的可读性更强。
> -   第二种可以早期的时候确实有很多人这样用。不过，现在这样用的人越来越少了。
> - 作为Java的粉丝C#(Java的模仿者)就不再支持第二种语法格式了。越来越多的语言可能会抛弃第二种格式。
> 
# 数组的初始化
## 数组初始化概述
- Java中的数组必须先初始化,然后才能使用。
- 所谓初始化：就是为数组中的数组元素分配内存空间，并为每个数组元素赋值。
## 数组的初始化方式
- 动态初始化：初始化时只指定数组长度，由系统为数组分配初始值。
- 静态初始化：初始化时指定每个数组元素的初始值，由系统决定数组长度。
## 动态初始化代码演示
```
/*
	数组:存储同一种数据类型的多个元素的容器。
	
	定义格式：
		A:数据类型[] 数组名;
		B:数据类型 数组名[];
		
	举例：
		A:int[] a; 定义一个int类型的数组a变量
		B:int a[]; 定义一个int类型的a数组变量
		
	注意：效果可以认为是一样的，都是定义一个int数组，但是念法上有些小区别。推荐使用第一种。
	
	如何对数组进行初始化呢?
		A:何谓初始化呢? 就是为数组开辟内存空间，并为每个数组元素赋予值
		B:有几种方式呢?
			a:动态初始化 只指定长度，由系统给出初始化值
			b:静态初始化 给出初始化值，由系统决定长度
			
	动态初始化的格式：
		数据类型[] 数组名 = new 数据类型[数组长度];
		
		举例：
		int[] arr = new int[3];	
		
	如何获取数组中的元素呢?
		通过:
			数组名[索引]
			索引其实就是每个元素的编号，从0开始，最大索引是数组的长度-1。
*/
class ArrayDemo {
	public static void main(String[] args) {
		//定义一个数组
		//int[] a;
		//可能尚未初始化变量a
		//System.out.println(a);
		
		int[] arr = new int[3];
		/*
			左边：
				int:说明数组中的元素的数据类型是int类型
				[]:说明这是一个数组
				arr:是数组的名称
				
			右边：
				new:为数组分配内存空间。
				int:说明数组中的元素的数据类型是int类型
				[]:说明这是一个数组
				3:数组长度，其实也就是数组中元素的个数
		*/
		
		System.out.println(arr); //[I@175078b 地址值。
		//我要地址值没有意义啊，我就要数据值，怎么办呢?
		//不用担心，java为你考虑到了。
		//其实数组中的每个元素都是有编号的，并且是从0开始。最大编号是数组的长度-1。
		//用数组名和编号的配合就可以获取数组中的指定编号的元素。这个编号的专业叫法：索引
		//通过数组名访问数据的格式是：数组名[索引];
		System.out.println(arr[0]);
		System.out.println(arr[1]);
		System.out.println(arr[2]);
	}
}
```
### 一个数组的内存图演示
```
/*
	定义一个数组，输出该数组的名称和数组元素值。
	给数组元素赋值，再次输出该数组的名称和数组元素值。
*/
class ArrayDemo2 {
	public static void main(String[] args) {
		//定义一个数组
		int[] arr = new int[3];
		
		//输出数组名称
		System.out.println(arr);
		//输出数组元素值
		System.out.println(arr[0]);
		System.out.println(arr[1]);
		System.out.println(arr[2]);
		System.out.println("----");
		
		//给数组元素赋值
		arr[0] = 100;
		arr[2] = 200;
		
		//输出数组名称
		System.out.println(arr);
		//输出数组元素值
		System.out.println(arr[0]);
		System.out.println(arr[1]);
		System.out.println(arr[2]);
	}
}
```
![image](http://image.damienzhong.com/%E4%B8%80%E4%B8%AA%E6%95%B0%E7%BB%84%E5%86%85%E5%AD%98%E5%9B%BE.JPG)
### 两个数组的内存图演示
```
/*
	定义两个数组，分别输出两个数组各自的数组名及元素值。
	然后给每个数组的元素重新赋值，再次分别输出两个数组各自的数组名及元素值。
*/
class ArrayDemo3 {
	public static void main(String[] args) {
		//定义第一个数组
		int[] arr = new int[2];
		//定义第二个数组
		int[] arr2 = new int[3];
		
		//输出数组名和元素值
		System.out.println(arr);
		System.out.println(arr[0]);
		System.out.println(arr[1]);
		System.out.println("----");
		
		System.out.println(arr2);
		System.out.println(arr2[0]);
		System.out.println(arr2[1]);
		System.out.println(arr2[2]);
		System.out.println("----");
		
		//给元素重新赋值
		arr[1] = 20;
		
		arr2[1] = 30;
		arr2[0] = 40;
		
		//输出数组名和元素值
		System.out.println(arr);
		System.out.println(arr[0]);
		System.out.println(arr[1]);
		System.out.println("----");
		
		System.out.println(arr2);
		System.out.println(arr2[0]);
		System.out.println(arr2[1]);
		System.out.println(arr2[2]);
	}
}
```
![image](http://image.damienzhong.com/%E4%B8%A4%E4%B8%AA%E6%95%B0%E7%BB%84%E5%86%85%E5%AD%98%E5%9B%BE.JPG)
### 三个数组的内存图演示
```
/*
	定义第一个数组,定义完毕后，给数组元素赋值。赋值完毕后，在输出数组名称和元素。
	定义第二个数组,定义完毕后，给数组元素赋值。赋值完毕后，在输出数组名称和元素。
	定义第三个数组,把第一个数组的地址值赋值给它。(注意类型一致)，通过第三个数组的名称去把元素重复赋值。
	最后，再次输出第一个数组数组名称和元素。
*/
class ArrayDemo4 {
	public static void main(String[] args) {
		//定义第一个数组
		int[] arr = new int[3];
		arr[0] = 88;
		arr[1] = 33;
		arr[2] = 66;
		System.out.println(arr);
		System.out.println(arr[0]);
		System.out.println(arr[1]);
		System.out.println(arr[2]);
		System.out.println("----");
		
		//定义第二个数组
		int[] arr2 = new int[3];
		arr2[0] = 22;
		arr2[1] = 44;
		arr2[2] = 55;
		System.out.println(arr2);
		System.out.println(arr2[0]);
		System.out.println(arr2[1]);
		System.out.println(arr2[2]);
		System.out.println("----");
		
		//定义第三个数组
		int[] arr3 =  arr;
		arr3[0] = 100;
		arr3[1] = 200;
		System.out.println(arr);
		System.out.println(arr[0]);
		System.out.println(arr[1]);
		System.out.println(arr[2]);
	}
}
```
![image](http://image.damienzhong.com/%E4%B8%89%E4%B8%AA%E6%95%B0%E7%BB%84%E7%9A%84%E5%86%85%E5%AD%98%E5%9B%BE.png)
## 数组静态初始化

```
/*
	数组的静态初始化：
		格式：数据类型[] 数组名 = new 数据类型[]{元素1,元素2,…};
		简化格式：
			数据类型[] 数组名 = {元素1,元素2,…};
		
		举例：
			int[] arr = new int[]{1,2,3};
			
			简化后：
			
			int[] arr = {1,2,3};
			
	注意事项：
		不要同时动态和静态进行。
		如下格式：
			int[] arr = new int[3]{1,2,3}; //错误
*/
class ArrayDemo5 {
	public static void main(String[] args) {
		//定义数组
		int[] arr = {1,2,3};
		
		System.out.println(arr);
		System.out.println(arr[0]);
		System.out.println(arr[1]);
		System.out.println(arr[2]);
	}
}
```
### 内存图演示
![image](http://image.damienzhong.com/%E6%95%B0%E7%BB%84%E9%9D%99%E6%80%81%E5%88%9D%E5%A7%8B%E5%8C%96%E5%86%85%E5%AD%98%E5%9B%BE.JPG)