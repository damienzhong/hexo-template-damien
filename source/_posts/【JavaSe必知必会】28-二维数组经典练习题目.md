---
title: 【JavaSe必知必会】28-二维数组经典练习题目
date: 2018-11-15 17:21:09
tags: javase
categories: javase
---
# 二维数组遍历

```
/*
	需求：二维数组遍历
	
	外循环控制的是二维数组的长度，其实就是一维数组的个数。
	内循环控制的是一维数组的长度。
*/
class Array2Test {
	public static void main(String[] args) {
		//定义一个二维数组
		int[][] arr = {{1,2,3},{4,5,6},{7,8,9}};
		
		//请问谁代表{1,2,3}
		//arr[0]就是第一个数组
		//arr[0] = {1,2,3};
		for(int x=0; x<arr[0].length; x++) {
			System.out.println(arr[0][x]);
		}
		System.out.println("--------------");
		
		for(int x=0; x<arr[1].length; x++) {
			System.out.println(arr[1][x]);
		}
		System.out.println("--------------");
		
		for(int x=0; x<arr[2].length; x++) {
			System.out.println(arr[2][x]);
		}
		System.out.println("--------------");
		
		//用循环改进
		for(int x=0; x<3; x++) {
			for(int y=0; y<arr[x].length; y++) {
				System.out.print(arr[x][y]+" ");
			}
			System.out.println();
		}
		System.out.println("--------------");
		
		//这个时候，注意了，3是我们根据上面的代码得出来的
		//但是，它不能针对任何的数组都可以这样
		//所以，我们应该想办法改进
		//其实，外面的这个循环的长度就是二维数组的长度
		
		for(int x=0; x<arr.length; x++) {
			for(int y=0; y<arr[x].length; y++) {
				System.out.print(arr[x][y]+" ");
			}
			System.out.println();
		}
		System.out.println("--------------");
		
		//用方法改进
		//调用方法
		printArray2(arr);
		System.out.println("--------------");
		
		//我们再来一个列数是变化的
		int[][] arr2 = {{1,2,3},{4,5},{6}};
		printArray2(arr2);
	}
	
	/*
		需求：遍历二维数组
		两个明确：
			返回值类型：void
			参数列表：int[][] arr
	*/
	public static void printArray2(int[][] arr) {
		for(int x=0; x<arr.length; x++) {
			for(int y=0; y<arr[x].length; y++) {
				System.out.print(arr[x][y]+" ");
			}
			System.out.println();
		}
	}
}
```
# 二维数组求和
## 公司年销售额求和
- 某公司按照季度和月份统计的数据如下：单位(万元)
- 第一季度：22,66,44
- 第二季度：77,33,88
- 第三季度：25,45,65
- 第四季度：11,66,99

```
/*
	公司年销售额求和
	某公司按照季度和月份统计的数据如下：单位(万元)
	第一季度：22,66,44
	第二季度：77,33,88
	第三季度：25,45,65
	第四季度：11,66,99
	
	分析：
		A:把题目的数据用二维数组来表示
			int[][] arr = {{22,66,44},{77,33,88},{25,45,65},{11,66,99}};
		B:如何求和呢?
			求和其实就是获取到每一个元素，然后累加即可。
		C:定义一个求和变量sum，初始化值是0。
		D:通过遍历就可以得到每一个二维数组的元素。
		E:把元素累加即可。
		F:最后输出sum，就是结果。
*/
class Array2Test2 {
	public static void main(String[] args) {
		//把题目的数据用二维数组来表示
		int[][] arr = {{22,66,44},{77,33,88},{25,45,65},{11,66,99}};
		
		//定义一个求和变量sum，初始化值是0。
		int sum = 0;
		
		//通过遍历就可以得到每一个二维数组的元素。
		for(int x=0; x<arr.length; x++) {
			for(int y=0; y<arr[x].length; y++) {
				//把元素累加即可。
				sum += arr[x][y];
			}
		}
		
		//最后输出sum，就是结果。
		System.out.println("一年的销售额为："+sum+"万元");
	}
}
```
# 打印杨辉三角形(行数可以键盘录入)

```
/*

	需求：打印杨辉三角形(行数可以键盘录入)
	
	1
	1 1	
	1 2 1
	1 3 3 1
	1 4 6 4 1 
	1 5 10 10 5 1

	分析：看这种图像的规律
		A:任何一行的第一列和最后一列都是1
		B:从第三行开始，每一个数据是它上一行的前一列和它上一行的本列之和。
	
	步骤：
		A:首先定义一个二维数组。行数如果是n，我们把列数也先定义为n。
		  这个n的数据来自于键盘录入。
		B:给这个二维数组任何一行的第一列和最后一列赋值为1
		C:按照规律给其他元素赋值
			从第三行开始，每一个数据是它上一行的前一列和它上一行的本列之和。
		D:遍历这个二维数组。
*/
import java.util.Scanner;

class Array2Test3 {
	public static void main(String[] args) {
		//创建键盘录入对象
		Scanner sc = new Scanner(System.in);
		
		//这个n的数据来自于键盘录入。
		System.out.println("请输入一个数据：");
		int n = sc.nextInt();
		
		//定义二维数组
		int[][] arr = new int[n][n];
		
		//给这个二维数组任何一行的第一列和最后一列赋值为1
		for(int x=0; x<arr.length; x++) {
			arr[x][0] = 1; //任何一行第1列
			arr[x][x] = 1; //任何一行的最后1列
		}
		
		//按照规律给其他元素赋值
		//从第三行开始，每一个数据是它上一行的前一列和它上一行的本列之和。
		for(int x=2; x<arr.length; x++) {
			//这里如果y<=x是有个小问题的，就是最后一列的问题
			//所以这里要减去1
			//并且y也应该从1开始，因为第一列也是有值了
			for(int y=1; y<=x-1; y++) {
				//每一个数据是它上一行的前一列和它上一行的本列之和。
				arr[x][y] = arr[x-1][y-1] + arr[x-1][y];
			}
		}
		
		//遍历这个二维数组。
		/*
		for(int x=0; x<arr.length; x++) {
			for(int y=0; y<arr[x].length; y++) {
				System.out.print(arr[x][y]+"\t");
			}
			System.out.println();
		}
		*/
		//这个时候，要注意了，内循环的变化必须和曾经讲过的九九乘法表类似
		for(int x=0; x<arr.length; x++) {
			for(int y=0; y<=x; y++) {
				System.out.print(arr[x][y]+"\t");
			}
			System.out.println();
		}
	}
}
```
# 思考题1

```
/*
	思考题1：看程序写结果，然后分析为什么是这个样子的。并画图讲解。最后总结Java中参数传递规律。
	
	Java中的参数传递问题：
		基本类型：形式参数的改变对实际参数没有影响。
		引用类型：形式参数的改变直接影响实际参数。
*/
class ArgsDemo {
	public static void main(String[] args) {
		int a = 10;
		int b = 20;
		System.out.println("a:"+a+",b:"+b); //a:10,b:20
		change(a,b);
		System.out.println("a:"+a+",b:"+b); //???	a:10,b:20

		int[] arr = {1,2,3,4,5}; 
		change(arr);
		System.out.println(arr[1]); //???	4
	}

	public static void change(int a,int b) { //a=10,b=20
		System.out.println("a:"+a+",b:"+b); //a:10,b:20
		a = b;	//a=20
		b = a + b; //b=40
		System.out.println("a:"+a+",b:"+b); //a:20,b:40
	}

	public static void change(int[] arr) { //arr={1,2,3,4,5};
		for(int x=0; x<arr.length; x++) {
			if(arr[x]%2==0) {
				arr[x]*=2;
			}
		}
		//arr={1,4,3,8,5};
	}
}
```
### 内存图演示
![image](http://image.damienzhong.com/%E5%80%BC%E4%BC%A0%E9%80%92%E5%86%85%E5%AD%98%E5%9B%BE.JPG)
# 思考题2

```
/*
	某个公司采用公用电话传递数据信息，数据是小于8位的整数，为了确保安全，
	在传递过程中需要加密，加密规则如下：
		首先将数据倒序，然后将每位数字都加上5，再用和除以10的余数代替该数字，
		最后将第一位和最后一位数字交换。 请任意给定一个小于8位的整数，
		然后，把加密后的结果在控制台打印出来。 
		
	题目要求：
		A:数据是小于8位的整数
			定义一个int类型的数据
			int number = 123456;
		B:加密规则
			a:首先将数据倒序
				结果 654321
			b:然后将每位数字都加上5，再用和除以10的余数代替该数字
				结果 109876
			c:最后将第一位和最后一位数字交换
				结果 609871
		C:把加密后的结果输出在控制台
		
		通过简单的分析，我们知道如果我们有办法把这个数据变成数组就好了。
		不是直接写成这个样子的：
			int[] arr = {1,2,3,4,5,6};
			
		如何把数据转成数组呢?
			A:定义一个数据
				int number = 123456;
			B:定义一个数组,这个时候问题就来了，数组的长度是多少呢?
				int[] arr = new int[8]; //不可能超过8
				在赋值的时候，我用一个变量记录索引的变化。
				定义一个索引值是0
				int index = 0;
			C:获取每一个数据
				int ge = number%10
				int shi = number/10%10
				int bai = number/10/10%10
				
				arr[index] = ge;
				index++;
				arr[index] = shi;
				index++;
				arr[index] = bai;
				...
*/
class JiaMiDemo {
	public static void main(String[] args) {
		//定义一个数据
		int number = 123456;
		
		//定义一个数组
		int[] arr = new int[8];
		
		//把数据中每一位上的数据获取到后存储到数组中
		/*
		int index = 0;
		arr[index] = number%10; //arr[0]=6;
		index++;
		arr[index] = number/10%10; //arr[1]=5;
		index++;
		arr[index] = mumber/10/10%10; //arr[2]=4;
		*/
		
		//通过观察这个代码，我们发现应该是可以通过循环改进的
		int index = 0;
		
		while(number > 0) { //number=123456,number=12345,number=1234,number=123,number=12,number=1,number=0
			arr[index] = number%10; //arr[0]=6,arr[1]=5,arr[2]=4,arr[3]=3,arr[4]=2,arr[5]=1
			index++;//index=1,index=2,index=3,index=4,index=5,index=6
			number/=10;//number=12345,number=1234,number=123,number=12,number=1,number=0
		}
		
		//然后将每位数字都加上5，再用和除以10的余数代替该数字
		for(int x=0; x<index; x++) {
			arr[x] += 5;
			arr[x] %= 10;
		}
		
		//最后将第一位和最后一位数字交换
		int temp = arr[0];
		arr[0] = arr[index-1];
		arr[index-1] = temp;
		
		//输出数据
		for(int x=0; x<index; x++) {
			System.out.print(arr[x]);
		}
		System.out.println();
	}
}
```
## 改进版

```
/*
	把刚才的代码改进一下：
		A:把数据改进为键盘录入
		B:把代码改进为方法实现
		
		
		另一个数据的测试：
		number:1234567
		第一步：7654321
		第二步：2109876
		第三步：6109872
		
	知识点：
		变量
		数据类型
		运算符
		键盘录入
		语句
		方法
		数组
*/
import java.util.Scanner;

class JiaMiDemo2 {
	public static void main(String[] args) {
		//创建键盘录入对象
		Scanner sc = new Scanner(System.in);
		
		//请输入一个数据
		System.out.println("请输入一个数据(小于8位)：");
		int number = sc.nextInt();
		
		//写功能实现把number进行加密
		//调用
		String result = jiaMi(number);
		System.out.println("加密后的结果是："+result);
	}
	
	/*
		需求：写一个功能，把数据number实现加密。
		两个明确：
			返回值类型：String 做一个字符串的拼接。
			参数列表：int number
	*/
	public static String jiaMi(int number) {
		//定义数组
		int[] arr = new int[8];
		
		//定义索引
		int index = 0;
		
		//把number中的数据想办法放到数组中
		while(number > 0) {
			arr[index] = number%10;
			index++;
			number /= 10;
		}
		
		//把每个数据加5，然后对10取得余数
		for(int x=0; x<index; x++) {
			arr[x] += 5;
			arr[x] %= 10;
		}
		
		//把第一位和最后一位交换
		int temp = arr[0];
		arr[0] = arr[index-1];
		arr[index-1] = temp;
		
		//把数组的元素拼接成一个字符串返回
		//定义一个空内容字符串
		String s = "";
		
		for(int x=0; x<index; x++) {
			s += arr[x];
		}
		
		return s;
	}
}
```
