---
title: 【JavaSe必知必会】11-Java运算符之算术运算符
date: 2018-11-15 15:29:21
tags: javase
categories: javase
---
# 运算符
- 运算
  - 对常量和变量进行操作的过程称为运算。
- 运算符
  -	对常量和变量进行操作的符号称为运算符
- 操作数
  -	参与运算的数据称为操作数
- 用运算符把常量或者变量连接起来符号java语法的式子就可以称为表达式。
- 不同运算符连接的式子体现的是不同类型的表达式。


```
举例：
	int a = 3 + 4;
	
	这是做了一个加法运算
	+就是运算符，是算术运算符，我们还有其他很多的运算符
	3，4就是参与运算的操作数据
	3 + 4整体其实就是一个算数表达式
```

## 运算符类别
- 算术运算符
- 赋值运算符
- 比较运算符
- 逻辑运算符
- 位运算符
- 三目运算符
# 算术运算符
![image](http://image.damienzhong.com/%E7%AE%97%E6%9C%AF%E8%BF%90%E7%AE%97%E7%AC%A6.png)
## 基本用法

```
/*
	运算符：
		就是对常量和变量进行操作的符号。
		
	分类：算术运算符，赋值运算符，比较运算符，逻辑运算符，位运算符，三目运算符

	算术运算符：
		+,-,*,/,%,++,--
		
	注意事项：
		A:整数相除只能得到整数。如果想得到小数，必须把数据变化为浮点数类型
		B:/获取的是除法操作的商，%获取的是除法操作的余数
*/

class OperatorDemo {
	public static void main(String[] args) {
		//定义变量
		int x = 3;  //把3赋值给int类型的变量x
		int y = 4;
		
		System.out.println(x+y);
		System.out.println(x-y);
		System.out.println(x*y);
		System.out.println(x/y); //整数相除只能得到整数
		
		//我就想得到小数，该肿么办呢?
		//只需要把操作的数据中任意的一个数据变为浮点数
		System.out.println(x*1.0/y);
		
		//%的应用
		System.out.println(x%y); //得到的是余数
	}
}
```
### ++和--的应用
- 单独使用效果相同
- 参与运算使用,在操作数的前后效果不同
- 
```
/*
	++,--运算符的使用：
		单独使用：
			放在操作数的前面和后面效果一样。(这种用法是我们比较常见的)
		参与运算使用：
			放在操作数的前面，先自增或者自减，然后再参与运算。
			放在操作数的后面，先参与运算，再自增或者自减。
			
	作用：就是对变量进行自增1或者自减1。
*/
public class OperatorDemo2 {
		public static void main(String[] args) {
			//定义两个变量
			int x = 3;
			int y = 4;
			
			//字符串的拼接
			//System.out.println("x:"+x);
			//System.out.println("y:"+y);
			
			System.out.println("x:"+x+",y:"+y);
			
			//单独使用
			//x++;
			//y--;
			++x;
			--y;
			//System.out.println(x);
			System.out.println("x:"+x+",y:"+y);
			
			//意外的类型,常量是不可以这样做的
			//System.out.println(10++);
			
			System.out.println("-------------------");
			//参与运算使用
			int a = 3;
			int b = 4;
			
			//int c = a++;
			//int d = b--;
			
			int c = ++a;
			int d = --b;
			
			System.out.println("a:"+a); //4, 4
			System.out.println("b:"+b); //3, 3
			System.out.println("c:"+c); //3, 4
			System.out.println("d:"+d); //4, 3
		}
}
```

```
/*
	++,--的练习题
	
	第一题：
	int a = 10;
	int b = 10;
	int c = 10;

	a = b++;
	c = --a;
	b = ++a;
	a = c--;
	请分别计算出a,b,c的值
	
	第二题：
	int x = 4;
	int y = (x++)+(++x)+(x*10);
	请分别计算出x,y的值
*/
public class OperatorTest {
	public static void main(String[] args) {
		int a = 10;
		int b = 10;
		int c = 10;

		a = b++; //a=10,b=11,c=10
		c = --a; //a=9,b=11,c=9
		b = ++a; //a=10,b=10,c=9
		a = c--; //a=9,b=10,c=8
		
		System.out.println("a:"+a);
		System.out.println("b:"+b);
		System.out.println("c:"+c);
		System.out.println("--------------");
		
		int x = 4;
		int y = (x++)+(++x)+(x*10);
		//4+6+60
		//x=5,6
		
		System.out.println("x:"+x);
		System.out.println("y:"+y);
	}
}
```
### 运算符的优先级
![image](http://image.damienzhong.com/%E8%BF%90%E7%AE%97%E7%AC%A6%E7%9A%84%E4%BC%98%E5%85%88%E7%BA%A7.png)

==**如果在程序中，要改变运算顺序，可以使用()**。==
### +运算符的用法

```
/*
	+的用法：
		A:加法
		B:正号
		C:字符串连接符
*/
class OperatorDemo3 {
	public static void main(String[] args) {
		//加法
		System.out.println(3+4);
		
		//正号
		System.out.println(+4);
		
		System.out.println('a');
		System.out.println('a'+1); //这里是加法
		
		//字符串连接符
		System.out.println("hello"+'a'+1);
		System.out.println('a'+1+"hello");
	}
}
```
## 赋值运算符
> 符号：
> = , +=, -=, *=, /=, %=
>
> =为基本的赋值运算符，其他的为扩展的赋值运算符

- = 赋值号
 
- +=加赋值
  - 把左边和右边的结果赋值给左边。
  - 注意：====左边不能是常量====

```
/*
	赋值运算符：
		基本赋值运算符：=
			把=右边的数据赋值给左边。
		扩展的赋值运算符：+=，-=，/=，%=
*/
public class OperatorDemo4{
	public static void main(String[] args){
		//定义一个变量
		int x = 10;
		
		//其他用法
		int a,b;
		a = b = 10;
		System.out.println(a);
		System.out.println(b);
		System.out.println("-------------------------------");
		
		//定义一个变量
		int y = 10;
		
		y += 10;//等价于y = y + 10;
		
		System.out.println(y);
	}
}
```
### 面试题解析

```
/*
	面试题：
		short s=1;s = s+1; 
		
		short s=1;s+=1;
		上面两个代码有没有问题，如果有，那里有问题。
		
		为什么第二个木有问题呢?
			扩展的赋值运算符其实隐含了一个强制类型转换。
			
			s += 1;
			不是等价于 s = s + 1;
			而是等价于 s = (s的数据类型)(s + 1);
*/
class OperatorTest {
	public static void main(String[] args) {
		//short s = 1;
		//s = s + 1;
		//System.out.println(s);
		
		short s = 1;
		s += 1; //好像是 s = s + 1;
		System.out.println(s);
	}
}
```


