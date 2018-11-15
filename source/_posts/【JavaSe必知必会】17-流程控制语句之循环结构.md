---
title: 【JavaSe必知必会】17-流程控制语句之循环结构
date: 2018-11-15 15:47:42
tags: javase
categories: javase
---
# 概述
> 循环语句可以在满足循环条件的情况下，反复执行某一段代码，这段被重复执行的代码被称为循环体语句，当反复执行这个循环体时，需要在合适的时候把循环判断条件修改为false，从而结束循环，否则循环将一直执行下去，形成死循环。
> 
# 循环语句的组成
- 初始化语句：
  - 一条或者多条语句，这些语句完成一些初始化操作。
- 判断条件语句：
  - 这是一个boolean 表达式，这个表达式能决定是否执行循环体。
- 循环体语句：
  - 这个部分是循环体语句，也就是我们要多次做的事情。
- 控制条件语句：
  - 这个部分在一次循环体结束后，下一次循环判断条件执行前执行。通过用于控制循环条件中的变量，使得循环在合适的时候结束。
# for循环语句
## for循环语句格式

```
for(初始化语句;判断条件语句;控制条件语句) {
         循环体语句;
    }
```

## 执行流程
- A:执行初始化语句
- B:执行判断条件语句，看其结果是true还是false
  - 如果是false，循环结束。
  - 如果是true，继续执行。
- C:执行循环体语句
- D:执行控制条件语句
- E:回到B继续


![image](http://image.damienzhong.com/for%E5%BE%AA%E7%8E%AF%E6%B5%81%E7%A8%8B%E5%9B%BE.png)
## 代码演示

```
/*
	循环语句：for循环,while循环,do...while循环。
	
	for循环格式：
		for(初始化语句;判断条件语句;控制条件语句) {
			循环体语句;
		}
		
		执行流程：
			A:执行初始化语句
			B:执行判断条件语句,看其返回值是true还是false
				如果是true，就继续执行
				如果是false，就结束循环
			C:执行循环体语句;
			D:执行控制条件语句
			E:回到B继续。
			
	注意事项：
		A:判断条件语句无论简单还是复杂结果是boolean类型。
		B:循环体语句如果是一条语句，大括号可以省略；如果是多条语句，大括号不能省略。建议永远不要省略。
		C:一般来说：有左大括号就没有分号，有分号就没有左大括号
			
	需求：请在控制台输出10次"HelloWorld"
*/
class ForDemo {
	public static void main(String[] args) {
		//最原始的做法
		System.out.println("HelloWorld");
		System.out.println("HelloWorld");
		System.out.println("HelloWorld");
		System.out.println("HelloWorld");
		System.out.println("HelloWorld");
		System.out.println("HelloWorld");
		System.out.println("HelloWorld");
		System.out.println("HelloWorld");
		System.out.println("HelloWorld");
		System.out.println("HelloWorld");
		System.out.println("----------");
		
		//这种做法不好,代码的重复度太高。
		//所以呢，我们用循环改进
		for(int x=1;x<=10;x++) {
			System.out.println("HelloWorld");
		}
	}
}
```

## 注意事项
- 判断条件语句的结果是一个boolean类型
- 循环体语句如果是一条语句，大括号可以省略；如果是多条语句，大括号不能省略。建议永远不要省略。
- 一般来说：有左大括号就没有分号，有分号就没有左大括号
## 练习
### 第一题
#### 请在控制台输出数据1-10

```
/*
	需求：请在控制台输出数据1-10
*/
class ForDemo2 {
	public static void main(String[] args) {
		//原始做法
		System.out.println(1);
		System.out.println(2);
		System.out.println(3);
		System.out.println(4);
		System.out.println(5);
		System.out.println(6);
		System.out.println(7);
		System.out.println(8);
		System.out.println(9);
		System.out.println(10);
		
		System.out.println("-------------");
		
		//如何改进呢?用循环改进
		for(int x=1; x<=10; x++) {
			System.out.println(x);
		}
		
		System.out.println("-------------");
		
		//从0开始
		for(int x=0; x<10; x++) {
			System.out.println(x+1);
		}
	}
}	
```
### 第二题
#### 求出1-10之间数据之和

```
/*
	需求：求出1-10之间数据之和
	
	分析：
		0+1=1
			1+2=3
				3+3=6
					6+4=10
						10+5=15
							 ...
							 
		由此可见我们要定义两个变量：
			一个变量用于存储第一个加数，第一个加数其实保存的是以前的所有数据和。默认初始化值应该是0。
			一个变量用于存储第二个加数，第二个加数其实就是每次的数据变化的值。
			
	求和思想。		
*/
class ForDemo3 {
	public static void main(String[] args) {
		//原始做法
		System.out.println(1+2+3+4+5+6+7+8+9+10);
		
		//定义第一个加数
		int sum = 0;
		
		for(int x=1; x<=10; x++) {
			//这里的x其实是第二个加数
			sum = sum + x;
			/*
				0 + 1 = 1
						1 + 2 = 3
								3 + 3 = 6
								...
			*/
			
			//sum += x;
		}
		
		System.out.println("sum:"+sum);
	}
}
```

### 第三题
#### A:求1-100之和。
#### B:求出1-100之间偶数和
#### C:求出1-100之间奇数和(自己做)
```
/*
	需求：
		A:求1-100之和。
		B:求出1-100之间偶数和
		C:求出1-100之间奇数和(自己做)
*/
class ForDemo4 {
	public static void main(String[] args) {
		//求1-100之和。
		int sum1 = 0;
		
		for(int x=1; x<=100; x++) {
			sum1 +=x;
		}
		
		System.out.println("1-100之和是："+sum1);
		System.out.println("------------------");
		
		//求出1-100之间偶数和
		//方式1
		int sum2 = 0;
		
		for(int x=1; x<=100; x++) {
			if(x%2 == 0) {
				sum2 += x;
			}
		}
		
		System.out.println("1-100偶数之和是："+sum2);
		System.out.println("------------------");
		
		//方式2
		int sum3 = 0;
		
		for(int x=0; x<=100; x+=2) {
				sum3 += x;
		}
		
		System.out.println("1-100偶数之和是："+sum3);
		System.out.println("------------------");
	}
}
```
### 第四题
#### 在控制台输出所有的”水仙花数”

```
/*
	需求：在控制台输出所有的”水仙花数”
	
	分析：
		我们都不知道什么叫"水仙花数"，你让我怎么做呢?
		
		所谓的水仙花数是指一个三位数，其各位数字的立方和等于该数本身。
		举例：153就是一个水仙花数。
		153 = 1*1*1 + 5*5*5 + 3*3*3 = 1 + 125 + 27 = 153

		A:三位数其实是告诉了我们范围。
		B:通过for循环我们就可以实现获取每一个三位数
		  但是麻烦是如何获取这个三位数的个,十,百位上的数据
		  
		  我们如何获取一个数据的个,十,百呢?
			假设有个一个数据:153
			ge:	153%10 = 3
			shi: 153/10%10 = 5
			bai：153/10/10%10 = 1
			qian：x/10/10/10%10
			wan:  x/10/10/10/10%10
			...

		C:让ge*ge*ge+shi*shi*shi+bai*bai*bai和该数据比较
		  如果相同，就把该数据在控制台输出。
*/
class ForDemo6 {
	public static void main(String[] args) {
		//三位数其实是告诉了我们范围。
		for(int x=100; x<1000; x++) {
			int ge = x%10;
			int shi = x/10%10;
			int bai = x/10/10%10;
			
			//让ge*ge*ge+shi*shi*shi+bai*bai*bai和该数据比较
			if(x == (ge*ge*ge+shi*shi*shi+bai*bai*bai)) {
				//如果相同，就把该数据在控制台输出。
				System.out.println(x);
			}
		}
	}
}
```
# while循环语句
## while循环语句格式

```
基本格式
   while(判断条件语句) {
         循环体语句;
   }
扩展格式
   初始化语句;
   while(判断条件语句) {
         循环体语句;
         控制条件语句;
    }
```
## 流程图
![image](http://image.damienzhong.com/while%E5%BE%AA%E7%8E%AF%E6%B5%81%E7%A8%8B%E5%9B%BE.png)
## 代码演示
```
/*
	while循环语句格式:
		基本格式
		   while(判断条件语句) {
				 循环体语句;
		   }
		扩展格式
		   初始化语句;
		   while(判断条件语句) {
				 循环体语句;
				 控制条件语句;
			}
		通过这个格式，我们就可以看到其实和for循环是差不多的
		for(初始化语句;判断条件语句;控制条件语句){
			循环体语句;
		}
*/
public class WhileDemo{
	public static void main(String[] args){
		//输出10次我的淘宝店铺名：DM潮人社区
		for(int x=0;x<10;x++){
			System.out.println("我的淘宝店铺名：DM潮人社区");
		}
		System.out.println("===========================");
		int x=0;
		while(x<10){
			System.out.println("我的淘宝店铺名：DM潮人社区");
			x++;
		}
	}
}
```

## for循环和while循环的区别
**for循环语句和while循环语句可以等价转换，但还是有些小区别的**
- 使用区别：
控制条件语句所控制的那个变量，在for循环结束后，就不能再被访问到了，而while循环结束还可以继续使用，如果你想继续使用，就用while，否则推荐使用for。原因是for循环结束，该变量就从内存中消失，能够提高内存的使用效率。
- 场景区别：
for循环适合针对一个范围判断进行操作
while循环适合判断次数不明确操作

```
/*
	while循环和for循环的区别?
		使用区别：如果你想在循环结束后，继续使用控制条件的那个变量，用while循环，否则用for循环。不知道用for循环。
		          因为变量及早的从内存中消失，可以提高内存的使用效率。
				  
		其实还有一种场景的理解:
			如果是一个范围的，用for循环非常明确。
			如果是不明确要做多少次，用while循环较为合适。
				举例：吃葡萄。
*/
class WhileDemo4 {
	public static void main(String[] args) {
	    for(int i=0;i<10;i++){
			System.out.println("祝大家端午节快乐，代码越敲越溜！");
		}
		//这里不能再继续访问了
		//System.out.println(i);
		System.out.println("=============================");
		Scanner sc = new Scanner(System.in);
		int j = sc.nextInt();
		while(j<10){
			System.out.println("祝大家端午节快乐，代码越敲越溜！");
			j++;
		}
		System.out.println(j);
	}
} 
```
### 练习

```
/*
	我国最高山峰是珠穆朗玛峰：8848m，我现在有一张足够大的纸张，厚度为：0.01m。
	请问，我折叠多少次，就可以保证厚度不低于珠穆朗玛峰的高度?

	分析：
		A:定义一个统计变量，默认值是0
		B:最高山峰是珠穆朗玛峰：8848m这是最终的厚度
		  我现在有一张足够大的纸张，厚度为：0.01m这是初始厚度
		C:我折叠多少次，就可以保证厚度不低于珠穆朗玛峰的高度?
		  折叠一次有什么变化呢?就是厚度是以前的2倍。
		D:只要每次变化的厚度没有超过珠穆朗玛峰的高度，就折叠，统计变量++
		E:输出统计变量。
*/

class WhileDemo5 {
	public static void main(String[] args) {
		//定义一个统计变量，默认值是0
		int count = 0;
		
		//最高山峰是珠穆朗玛峰：8848m这是最终的厚度
		//我现在有一张足够大的纸张，厚度为：0.01m这是初始厚度
		//为了简单，我把0.01变成1，同理8848就变成了884800
		int end = 884800;
		int start = 1;
		
		while(start<end) {
			//只要每次变化的厚度没有超过珠穆朗玛峰的高度，就折叠，统计变量++
			count++;
			
			//折叠一次有什么变化呢?就是厚度是以前的2倍。
			start *= 2;
			
			System.out.println("第"+count+"次厚度是"+start);
		}
		
		//输出统计变量。
		System.out.println("要叠"+count+"次");
	}
}
```
## do…while循环语句
#### do…while循环语句格式

```
基本格式
   do {
         循环体语句;
   }while((判断条件语句);
扩展格式
   初始化语句;
   do {
         循环体语句;
         控制条件语句;
    } while((判断条件语句);

```
### 流程图
![image](http://image.damienzhong.com/dowhile.jpg)

```
/*
	do...while循环的基本格式：
		do {
			循环体语句;
		}while(判断条件语句);
		
		扩展格式；
		初始化语句;
		do {
			循环体语句;
			控制条件语句;
		}while(判断条件语句);
*/
class DoWhileDemo {
	public static void main(String[] args) {
		//输出10次HelloWorld。
		int x = 0;
		do {
			System.out.println("HelloWorld");
			x++;
		}while(x<10);
		
		System.out.println("--------------");
		
		//求和1-100
		int sum = 0;
		int a = 1;
		do {
			sum += a;
			a++;
		}while(a<=100);
		
		System.out.println(sum);
	}
}
```
# 区别及注意事项
**三种循环语句其实都可以完成一样的功能，也就是说可以等价转换，但还是有小区别的:**

- do…while循环至少会执行一次循环体。
- for循环和while循环只有在条件成立的时候才会去执行循环体
### 代码演示

```
/*
	循环语句的区别:
		do...while循环至少执行一次循环体。
		而for,while循环必须先判断条件是否成立，然后决定是否执行循环体语句。
		
	那么，我们一般使用哪种循环呢?
		优先考虑for，其次考虑while，最后考虑do...while
*/
class DoWhileDemo2 {
	public static void main(String[] args) {
		int x = 3;
		while(x < 3) {
			System.out.println("DM潮人社区的衣服超酷的哟~");
			x++;
		}
		
		System.out.println("--------------");
		
		int y = 3;
		do {
			System.out.println("DM潮人社区的衣服超酷的哟~");
			y++;
		}while(y < 3);
	}
}
```

**注意事项：**
- 写程序优先考虑for循环，再考虑while循环，最后考虑do…while循环。
- 如下代码是死循环

```
while(true){}
 for(;;){}
```
### 代码演示

```
/*
	注意死循环：
		A:一定要注意控制条件语句控制的那个变量的问题，不要弄丢了，否则就容易死循环。
		B:两种最简单的死循环格式
			while(true){...}
			for(;;){...}
			
*/
class DoWhileDemo3 {
	public static void main(String[] args) {
		int x = 0;
		while(x < 10) {
			System.out.println(x);
			x++;
		}
		System.out.println("--------------");
		
		/*
		while(true) {
			System.out.println("今天我很高兴，学会了把循环弄死");
		}
		*/
		
		for(;;){
			System.out.println("今天我很高兴，学会了把循环弄死");
		}
		
		//System.out.println("--------------");
	}
}
```
# 经典练习
### 第一题
```
/*
	在控制台输出一个四行五列的*图案
		*****
		*****
		*****
		*****
	总结：内层循环控制列数，外层循环控制行数
*/
import java.util.Scanner;
public class ForForTest{
	public static void main(String[] args){
		//最傻最傻的办法，不合适
		System.out.println("*****");
		System.out.println("*****");
		System.out.println("*****");
		System.out.println("*****");
		System.out.println("------------------------");
		//单for循环，不合适
		for(int i = 0;i<4;i++){
			System.out.println("*****");
		}
		System.out.println("------------------------");
		Scanner sc = new Scanner(System.in);
		System.out.println("请输入要输出的列数：");
		int n = sc.nextInt();
		System.out.println("请输入要输出的行数：");
		int m = sc.nextInt();
		//控制行数
		for(int j = 0;j<m;j++){
			//控制每行的列数
			for(int i=0;i<n;i++){
				System.out.print("*");
			}
			System.out.println();
		}
	}
}
```
### 第二题

```
/*
	用*符号输出一个正三角形
		*
		**
		***
		****
		*****
*/
public class ForForTest2{
	public static void main(String[] args){
		//5行5列
		for(int i = 0;i<5;i++){
			for(int j = 0;j<5;j++){
				System.out.print("*");
			}
			System.out.println();
		}
		/*
			第1行1个
			第2行2个
			第3行3个
			第4行4个
			第5行5个
			*/
		for(int i = 0;i<5;i++){
			for(int j=0;j<=i;j++){
				System.out.print("*");
			}
			System.out.println();
		}
		
	}
}
```
### 第三题

```
/*
	需求：在控制台输出九九乘法表。
	
	首先我们写出九九乘法表：
		1*1=1
		1*2=2	2*2=4
		1*3=3	2*3=6	3*3=9
		1*4=4	2*4=8	3*4=12	4*4=16
		...
		1*9=9	2*9=18	3*9=27	...
		
	我们先把这个九九乘法表看出是这样的一个形状：
		*
		**
		***
		****
		*****
		******
		*******
		********
		*********
		
	注意：
		'\x' x表示任意，这种做法叫转移字符。
		
		'\t'	tab键的位置
		'\r'	回车
		'\n'	换行
*/
class ForForDemo3 {
	public static void main(String[] args) {
		for(int x=0; x<9; x++) {
			for(int y=0; y<=x; y++) {
				System.out.print("*");
			}
			System.out.println();
		}
		System.out.println("--------------");
		//为了使用数据，我们从1开始
		for(int x=1; x<=9; x++) {
			for(int y=1; y<=x; y++) {
				System.out.print(y+"*"+x+"="+y*x+"\t");
			}
			System.out.println();
		}
	}
}
```

