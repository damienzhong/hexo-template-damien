---
title: 【JavaSe必知必会】19-方法的定义与使用
date: 2018-11-15 15:49:43
tags: javase
categories: javase
---
# 方法的基本定义
## 方法定义及格式
- 简单的说：方法就是完成特定功能的代码块
在很多语言里面都有函数的定义
函数在Java中被称为方法
- 格式：

```
修饰符 返回值类型 方法名(参数类型 参数名1，参数类型 参数名2…) {
			函数体;
			return 返回值;
    }
```
## 方法格式的解释说明
### 方法格式解释
- **修饰符** 比较多，后面会详细介绍。目前public static
- **返回值类型** 用于限定返回值的数据类型
- **方法名** 一个名称，为了方便我们调用方法
- **参数类型** 限定调用方法时传入参数的数据类型
- **参数名** 是一个变量，接收调用方法时传入的参数
- **方法体** 完成功能的代码
- **return** 结束方法以及返回方法指定类型的值 
- **返回值** 程序被return带回的结果，返回给调用者
## 有返回值的方法调用
### 案例演示

```
/*
	方法：完成特定功能的代码块。
	
	注意：在很多语言里面有函数的定义，而在Java中函数被称为方法。

	方法格式：
		修饰符 返回值类型 方法名(参数类型 参数名1,参数类型 参数名2...) {
			方法体语句;
			return 返回值; 
		}
	详细解释：
		修饰符：目前就用 public static。后面我们再详细的讲解其他的修饰符。
		返回值类型：就是功能结果的数据类型。
		方法名：符合命名规则即可。方便我们的调用。
		参数：
			实际参数：就是实际参与运算的。
			形式参数；就是方法定义上的，用于接收实际参数的。
		参数类型：就是参数的数据类型
		参数名：就是变量名
		方法体语句：就是完成功能的代码。
		return：结束方法的。
		返回值：就是功能的结果，由return带给调用者。
		
	要想写好一个方法，就必须明确两个东西：
		A:返回值类型
			结果的数据类型
		B:参数列表
			你要传递几个参数，以及每个参数的数据类型
			
	需求：求两个数据之和的案例
	
	方法的执行特点：
		不调用，不执行。
		
	如何调用呢?(有明确返回值的调用)
		A:单独调用,一般来说没有意义，所以不推荐。
		B:输出调用,但是不够好。因为我们可能需要针对结果进行进一步的操作。
		C:赋值调用,推荐方案。
		
*/
class FunctionDemo {
	public static void main(String[] args) {
		int x = 10;
		int y = 20;
		
		//方式1：单独调用
		//sum(x,y);
	
		//方式2：输出调用
		//System.out.println(sum(x,y));
		//System.out.println(30);
	
		//方式3：赋值调用
		int result = sum(x,y);
		//result在这里可以进行操作
		System.out.println(result);
	}
	
	/*
		需求：求两个数据之和的案例
		
		两个明确：
			返回值类型：int
			参数列表：2个，都是int类型。
	*/
	public static int sum(int a,int b) {
			//如何实现呢?
			//int c = a + b;
			//return c;
			
			//c就是a+b,所以，我可以直接返回a+b
			return a + b;
	}
	
}
```
## 练习题
### 练习1

```
/*
	键盘录入两个数据，返回两个数中的较大值
*/
import java.util.Scanner;

class FunctionTest {
	public static void main(String[] args) {
		//创建键盘录入对象
		Scanner sc = new Scanner(System.in);
		
		System.out.println("请输入第一个数据:");
		int a = sc.nextInt();
		
		System.out.println("请输入第二个数据:");
		int b = sc.nextInt();
		
		int result = getMax(a,b);
		System.out.println("较大值是："+result);
	}
	
	/*
		需求：两个数中的较大值
		两个明确：
			返回值类型：int
			参数列表：int a,int b			
	*/
	public static int getMax(int a,int b) {
		//if语句
		/*
		if(a > b) {
			//System.out.println(a);
			return a;
		}else {
			//System.out.println(b);
			return b;
		}
		*/
		
		//用三元改进
		//int c = ((a > b)? a: b);
		//return c;
		
		//由于c就是后面的式子
		return ((a>b)? a : b);
	}
}
```
### 练习2

```
/*
	键盘录入两个数据，比较两个数是否相等
	
	分析：
		比较两个数是否相等结果是一个boolean类型。
*/
import java.util.Scanner;

class FunctionTest2 {
	public static void main(String[] args) {
		//创建键盘录入对象
		Scanner sc = new Scanner(System.in);
		
		System.out.println("请输入第一个数据:");
		int a = sc.nextInt();
		
		System.out.println("请输入第二个数据:");
		int b = sc.nextInt();
		
		boolean flag = compare(a,b);
		System.out.println(flag);
	}
	
	/*
		需求：比较两个数是否相等
		两个明确：
			返回值类型：boolean
			参数列表：int a,int b
	*/
	public static boolean compare(int a,int b) {
		//if语句的格式2实现
		/*
		if(a == b) {
			return true;
		}else {
			return false;
		}
		*/
		
		//三元改进
		//boolean flag = ((a==b)? true: false);
		//return flag;
		
		//继续改进
		//return ((a==b)? true: false);
		
		//最终版
		return a == b;
	}
}
```
### 练习3

```
/*
	键盘录入三个数据，返回三个数中的最大值
*/
import java.util.Scanner;

class FunctionTest3 {
	public static void main(String[] args) {
		//创建键盘录入对象
		Scanner sc = new Scanner(System.in);
		
		System.out.println("请输入第一个数据:");
		int a = sc.nextInt();
		
		System.out.println("请输入第二个数据:");
		int b = sc.nextInt();
		
		System.out.println("请输入第三个数据:");
		int c = sc.nextInt();
		
		int max = getMax(a,b,c);
		System.out.println("三个数据中的最大值是："+max);
	}
	
	/*
		需求；返回三个数中的最大值
		
		两个明确：
			返回值类型：int
			参数列表：int a,int b,int c
	*/
	public static int getMax(int a,int b,int c) {
		//if嵌套
		/*
		if(a > b) {
			if(a > c) {
				return a;
			}else {
				return c;
			}
		}else {
			if(b > c) {
				return b;
			}else {
				return c;
			}
		}
		*/
		
		//用三元改
		/*
		if(a > b) {
			return (a>c? a: c);
		}else {
			return (b>c? b: c);
		}
		*/
		
		//继续改进
		//return (a>b)? (a>c? a: c): (b>c? b: c);
		//不建议，写代码一定要注意阅读性强
		int temp = ((a>b)? a: b);
		int max = ((temp>c)? temp: c);
		return max;
	}
}
```
## 注意事项

```
/*
	方法的注意事项：
		A:方法不调用不执行
		B:方法与方法是平级关系，不能嵌套定义
		C:方法定义的时候参数之间用逗号隔开
		D:方法调用的时候不用在传递数据类型
		E:如果方法有明确的返回值，一定要有return带回一个值
*/
class FunctionDemo2 {
	public static void main(String[] args) {
		/*
		错误的
		public static int sum(int a,int b){
			return a + b;
		}
		*/
		
		//sum(10,20);
		
		//int x = 10;
		//int y = 20;
		//错误
		//sum(int x,int y);
	}
	
	public static int sum(int a,int b){
		return a + b;
	}
}
```
## void类型的方法调用

```
/*
	需求：在控制台输出如下的形状
		*****
		*****
		*****
		*****
		
	void类型返回值的方法调用：
		单独调用
		输出调用(错误)
		赋值调用(错误)
*/
class FunctionDemo3 {
	public static void main(String[] args) {
		//for循环嵌套输出图形
		for(int x=0; x<4; x++) {
			for(int y=0; y<5; y++) {
				System.out.print("*");
			}
			System.out.println();
		}
		System.out.println("--------------");
		
		//需求：我要在控制台输出一个6行7列的星形图形
		for(int x=0; x<6; x++) {
			for(int y=0; y<7; y++) {
				System.out.print("*");
			}
			System.out.println();
		}
		System.out.println("--------------");
		
		//如果需要继续改变，我们就应该考虑使用方法改进。
		//单独调用
		pringXing(3,4);
		System.out.println("--------------");
		pringXing(6,7);
		System.out.println("--------------");
		pringXing(8,9);
		
		//输出调用
		//此处不允许使用 '空' 类型
		//System.out.println(pringXing(3,4));
		
		//赋值调用
		//非法的表达式开始
		//void v = pringXing(3,4);
	}
	
	/*
		写一个什么样子的方法呢?写一个m行n列的代码
		
		两个明确：
			返回值类型：这个时候没有明确的返回值，不写东西还不行，所以，这里记住是void
			参数列表：int m,int n
	*/
	public static void pringXing(int m,int n) {
		for(int x=0; x<m; x++) {
			for(int y=0; y<n; y++) {
				System.out.print("*");
			}
			System.out.println();
		}
	}
}
```
### 练习

```
/*
	键盘录入一个数据n(1<=n<=9)，输出对应的nn乘法表
*/
import java.util.Scanner;
public class FunctionTest3{
	public static void main(String[] args){
		//创建对象
		Scanner sc = new Scanner(System.in);
		
		System.out.print("请输入n的值（1~9）:");
		int n = sc.nextInt();
		while(n<1||n>9){
			System.out.print("您输入的数据不再有效范围内，请重新输入：");
			n = sc.nextInt();
		}
		//调用
		printNN(n);
	}
	
	/*
		两个明确：
			返回值类型：void
			参数列表：int n
	*/
	public static void printNN(int n){
		for(int x=1;x<=n;x++){
			for(int y=1;y<=x;y++){
				System.out.print(y+"*"+x+"="+y*x+"\t");
			}
			System.out.println();
		}
	}

```


# 方法重载
### 方法重载概述
在同一个类中，允许存在一个以上的同名方法，只要它们的参数个数或者参数类型不同即可。
### 方法重载特点
与返回值类型无关，只看方法名和参数列表
在调用时，虚拟机通过参数列表的不同来区分同名方法



```
/*
	需求：我要求数的和
	
	我们的需求不断的发生改变，我们就对应的提供了多个求和的方法。
	但是呢，他们的名字是不一样的。
	而我们又要求方法命名做到：见名知意。
	但是，很明显，现在没有做到。
	那么，肿么办呢?
	针对这种情况：方法的功能相同，参数列表不同的情况，为了见名知意，Java允许它们起一样的名字。
	
	其实，这种情况有一个专业名词：方法重载。
	
	方法重载：
		在同一个类中，方法名相同，参数列表不同。与返回值类型无关。
		
		参数列表不同：
			A:参数个数不同
			B:参数类型不同
*/
class FunctionDemo4 {
	public static void main(String[] args) {
		//jvm会根据不同的参数去调用不同的功能
		System.out.println(sum(10,20));
		System.out.println(sum(10,20,30));
		System.out.println(sum(10,20,30,40));
		
		System.out.println(sum(10.5f,20f));
	}
	
	//需求1:求两个数的和
	public static int sum(int a,int b) {
		System.out.println("int");
		return a + b;
	}
	
	//需求2:求三数的和
	/*
	public static int sum1(int a,int b,int c) {
		return a + b + c;
	}
	*/
	
	public static int sum(int a,int b,int c) {
		return a + b + c;
	}
	
	//需求3:求四个数的和
	/*
	public static int sum2(int a,int b,int c,int d) {
		return a + b + c + d;
	}
	*/
	public static int sum(int a,int b,int c,int d) {
		return a + b + c + d;
	}
	
	public static float sum(float a,float b) {
		System.out.println("float");
		return a + b;
	}
}
```
