---
title: 【JavaSe必知必会】16-流程控制语句之选择结构
date: 2018-11-15 15:45:53
tags: javase
categories: javase
---
# 概述
> 在一个程序执行的过程中，各条语句的执行顺序对程序的结果是有直接影响的。也就是说程序的流程对运行结果有直接的影响。所以，我们必须清楚每条语句的执行流程。而且，很多时候我们要通过控制语句的执行顺序来实现我们要完成的功能。
## 流程控制语句分类
- 顺序结构
- 选择结构
- 循环结构
# 顺序结构
## 顺序结构概述
- 是程序中最简单最基本的流程控制，没有特定的语法结构，按照代码的先后顺序，依次执行，程序中大多数的代码都是这样执行的。
-  总的来说：写在前面的先执行，写在后面的后执行
## 顺序结构图
![image](http://image.damienzhong.com/%E9%A1%BA%E5%BA%8F%E7%BB%93%E6%9E%84.png)

```
/*
	流程控制语句：可以控制程序的执行流程。
	
	分类：
		顺序结构
		选择结构
		循环结构
		
	顺序结构：
		从上往下，依次执行。
*/
class ShunXuJieGouDemo {
	public static void main(String[] args) {
		System.out.println("程序开始了");
		
		System.out.println("我爱Java");
		
		System.out.println("程序结束了");
	}
}
```
# 选择结构
- 也被称为分支结构。
- 选择结构有特定的语法规则，代码要执行具体的逻辑运算进行判断，逻辑运算的结果有两个，所以产生选择，按照不同的选择执行不同的代码。
- Java语言提供了两种选择结构语句
  - if语句
  - switch语句
## 选择结构(if语句)
### if语句有三种格式
#### if语句第一种格式：

```
if(关系表达式) {
		     语句体
	}
```
#### 执行流程
- 首先判断关系表达式看其结果是true还是false
- 如果是true就执行语句体
- 如果是false就不执行语句体

![image](http://image.damienzhong.com/if1.png)


```
/*
	选择结构：
		if语句
		switch语句
		
	if语句：
		格式1
		格式2
		格式3
		
	if语句的格式：
		if(比较表达式) {
			语句体;
		}
		
		执行流程：
			先计算比较表达式的值，看其返回值是true还是false。
			如果是true，就执行语句体；
			如果是false，就不执行语句体；
*/
class IfDemo {
	public static void main(String[] args) {
		int x = 10;
		
		if(x == 10) {
			System.out.println("x等于10");
		}
		
		if(x == 20) {
			System.out.println("x等于20");
		}
		
		System.out.println("over");
	}
}
```
#### 注意事项
- 关系表达式无论简单还是复杂，结果必须是boolean类型
- if语句控制的语句体如果是一条语句，大括号可以省略；如果是多条语句，就不能省略。建议永远不要省略。
- 一般来说：有左大括号就没有分号，有分号就没有左大括号

```
/*
	if语句的注意事项：
		A:比较表达式无论简单还是复杂，结果必须是boolean类型
		B:if语句控制的语句体如果是一条语句，大括号可以省略；
		  如果是多条语句，就不能省略。建议永远不要省略。
		C:一般来说：有左大括号就没有分号，有分号就没有左大括号
*/
class IfDemo2 {
	public static void main(String[] args) {
		int x = 10;
		
		if(x == 10) {
			System.out.println("x等于10");
		}
		
		if((x > 5) || (x == 10)) {
			System.out.println("x大于或者等于10");
		}
		System.out.println("-------------------");
		
		int a = 100;
		
		/*
		if(a == 100) {
			System.out.println("a的值是100");
		}
		*/
		
		if(a != 100) {
			System.out.println("a的值是100");
			System.out.println("over");
		}
		System.out.println("-------------------");
		
		int b = 100;
		if(b != 100);  //这里其实是有语句体的，只不过是空语句体。
		
		//代码块
		{
			System.out.println("b的值是100");
			System.out.println("over");
		}
	}
}
```
#### if语句第二种格式

```
if(关系表达式) {
		     语句体1;
	}else {
		     语句体2;
	}

```
#### 执行流程
- 首先判断关系表达式看其结果是true还是false
- 如果是true就执行语句体1
- 如果是false就执行语句体2

![image](http://image.damienzhong.com/if2.jpg)

```
/*
	if语句格式2：
		if(比较表达式) {
			语句体1;
		}else {
			语句体2;
		}
	执行流程：
		首先计算比较表达式的值，看其返回值是true还是false。
		如果是true，就执行语句体1；
		如果是false，就执行语句体2；
		
	注意：else后面是没有比较表达式的，只有if后面有。
*/
class IfDemo3 {
	public static void main(String[] args) {
		//判断两个数据是否相等
		
		int a = 10;
		int b = 20;
		
		if(a == b) {
			System.out.println("a等于b");
		}else {
			System.out.println("a不等于b");
		}
	}
}
 ```
#### 练习

```
/*
	if语句格式2的练习：
		A:获取两个数据中较大的值
		B:判断一个数据是奇数还是偶数,并输出是奇数还是偶数
*/
import java.util.Scanner;

class IfTest {
	public static void main(String[] args) {
		//创建键盘录入对象
		Scanner sc = new Scanner(System.in);
		
		//获取两个数据中较大的值
		System.out.println("请输入第一个数据：");
		int a = sc.nextInt();
		
		System.out.println("请输入第二个数据：");
		int b = sc.nextInt();
		
		//定义一个变量接收最大值
		int max;
		
		if(a > b) {
			max = a;
		}else {
			max = b;
		}
		
		System.out.println("max:"+max);
		System.out.println("----------------");
		
		//判断一个数据是奇数还是偶数
		System.out.println("请输入你要判断的数据：");
		int x = sc.nextInt();
		
		if(x%2 == 0) {
			System.out.println(x+"这个数据是偶数");
		}else {
			System.out.println(x+"这个数据是奇数");
		}
	}
}
```


- 我们前面讲解过三元运算符，它根据比较判断后，给出的也是两个结果，所以，这种情况和if语句的第二种格式很相似，他们在某些情况下应该是可以相互转换的。
- if语句第二种格式和三元运算符
  - 三元运算符的操作都可以使用if语句改进，反之不成立
  - 什么时候不成立呢?
    - 当if语句控制的语句体是一条输出语句的时候，就不成立。因为三元运算符是一个运算符，必须要求有一个结果返回
   而输出语句却不能作为一个返回结果。

```
/*
	由于if语句的第二种格式刚才也完成了三元运算符可以完成的效果。
	所以，我们就认为他们可以完成一样的操作。
	但是，他们就一点区别没有吗?肯定不是。
	
	区别：
		三元运算符实现的，都可以采用if语句实现。反之不成立。
		
		什么时候if语句实现不能用三元改进呢?
			当if语句控制的操作是一个输出语句的时候就不能。
			为什么呢?因为三元运算符是一个运算符，运算符操作完毕就应该有一个结果，而不是一个输出。
*/
class IfDemo4 {
	public static void main(String[] args) {
		//获取两个数据的最大值
		int a = 10;
		int b = 20;
		
		//用if语句实现
		int max1;
		if(a > b) {
			max1 = a;
		}else {
			max1 = b;
		}
		System.out.println("max1:"+max1);
		
		//用三元改进
		int max2 = (a > b)? a: b;
		System.out.println("max2:"+max2);
		System.out.println("----------");
		
		//判断一个数据是奇数还是偶数,并输出是奇数还是偶数
		int x = 100;
		
		if(x%2 == 0) {
			System.out.println("100是一个偶数");
		}else {
			System.out.println("100是一个奇数");
		} 
		
		//用三元改进
		//这种改进是错误的。
		//String s = (x%2 == 0)?System.out.println("100是一个偶数");:System.out.println("100是一个奇数");;
	}
}
```
#### if语句第三种格式

```
if(关系表达式1) {
		     语句体1;
	}else  if (关系表达式2) {
		     语句体2;
	}
    …
	else {
		     语句体n+1;
	}
```
#### 执行流程
- 首先判断关系表达式1看其结果是true还是false
- 如果是true就执行语句体1
- 如果是false就继续判断关系表达式2看其结果是true还是false
- 如果是true就执行语句体2
- 如果是false就继续判断关系表达式…看其结果是true还是false
- …
- 如果没有任何关系表达式为true，就执行语句体n+1。

![image](http://image.damienzhong.com/if3.jpg)


```
/*
	if语句的格式3：
		if(比较表达式1) {
			语句体1;
		}else if(比较表达式2) {
			语句体2;
		}else if(比较表达式3) {
			语句体3;
		}
		...
		else {
			语句体n+1;
		}
		
	执行流程：
		首先计算比较表达式1看其返回值是true还是false，
		如果是true，就执行语句体1，if语句结束。
		如果是false，接着计算比较表达式2看其返回值是true还是false，
		
		如果是true，就执行语句体2，if语句结束。
		如果是false，接着计算比较表达式3看其返回值是true还是false，
		...
		
		如果都是false，就执行语句体n+1。
*/
import java.util.Scanner;

class IfDemo5 {
	public static void main(String[] args) {
		//需求：键盘录入一个成绩，判断并输出成绩的等级。
		/*
			90-100 优秀
			80-90  好
			70-80  良
			60-70  及格
			0-60   不及格
		*/
		
		//创建键盘录入对象
		Scanner sc = new Scanner(System.in);
		
		//录入数据
		System.out.println("请输入你的考试成绩：");
		int score = sc.nextInt();
		
		/*
		if(score>=90 && score<=100) {
			System.out.println("优秀");
		}else if(score>=80 && score<90) {
			System.out.println("好");
		}else if(score>=70 && score<80) {
			System.out.println("良");
		}else if(score>=60 && score<70) {
			System.out.println("及格");
		}else {
			System.out.println("不及格");
		}
		*/
		//这样写已经满足我的基本要求，但是可能别人在使用的时候，不会按照你要求的数据给出了。
		//在做一个程序的基本测试的时候，一定要考虑这样的几个问题：
		//正确数据，错误数据，边界数据。
		//而我们刚才写的程序并没有处理错误数据，所以这个程序不是很好，要改进
		/*
		if(score>=90 && score<=100) {
			System.out.println("优秀");
		}else if(score>=80 && score<90) {
			System.out.println("好");
		}else if(score>=70 && score<80) {
			System.out.println("良");
		}else if(score>=60 && score<70) {
			System.out.println("及格");
		}else if(score>=0 && score<60){
			System.out.println("不及格");
		}else {
			System.out.println("你输入的成绩有误");
		}
		*/
		
		//另一种判断改进
		if(score<0 || score>100) {
			System.out.println("你输入的成绩有误");
		}else if(score>=90 && score<=100) {
			System.out.println("优秀");
		}else if(score>=80 && score<90) {
			System.out.println("好");
		}else if(score>=70 && score<80) {
			System.out.println("良");
		}else if(score>=60 && score<70) {
			System.out.println("及格");
		}else {
			System.out.println("不及格");
		}
	}
}
```
#### 练习题

```
/*
	键盘录入月份的值，输出对应的季节。
	
	春	3,4,5
	夏	6,7,8
	秋	9,10,11
	冬	12,1,2
	
	分析：
		A:键盘录入月份的值，所以我们要使用Scanner。
		B:我们应该判断这个月份在那个季节，而这个判断情况较多，所以，用if语句格式3。
		
	if语句的使用场景：
		A:针对表达式是一个boolean类型的判断
		B:针对一个范围的判断
*/
import java.util.Scanner;

class IfTest3 {
	public static void main(String[] args) {
		//创建键盘录入对象
		Scanner sc = new Scanner(System.in);
		
		//录入数据
		System.out.println("请你输入一个月份:");
		int month = sc.nextInt();
		
		//第三种格式实现即可
		if(month<1 || month>12) {
			System.out.println("你输入的月份有误");
		}else if(month == 1) {
			System.out.println("冬季");
		}else if(month == 2) {
			System.out.println("冬季");
		}else if(month == 3) {
			System.out.println("春季");
		}else if(month == 4) {
			System.out.println("春季");
		}else if(month == 5) {
			System.out.println("春季");
		}else if(month == 6) {
			System.out.println("夏季");
		}else if(month == 7) {
			System.out.println("夏季");
		}else if(month == 8) {
			System.out.println("夏季");
		}else if(month == 9) {
			System.out.println("秋季");
		}else if(month == 10) {
			System.out.println("秋季");
		}else if(month == 11) {
			System.out.println("秋季");
		}else {
			System.out.println("冬季");
		}
		System.out.println("--------------");
		
		//这个程序确实是符合了我们的需求，但是就是看起来比较麻烦
		//那么，我们能不能改进一下呢?
		//month == 3
		//month == 4
		//month == 5
		//我们发现，上面三个都是春季。
		//而他们本身每一个都是一个boolean表达式
		//所以，我们就可以考虑使用逻辑运算符给他们连接起来改进
		if(month<1 || month>12) {
			System.out.println("你输入的月份有误");
		}else if(month==3 || month==4 || month==5) {
			System.out.println("春季");
		}else if(month==6 || month==7 || month==8) {
			System.out.println("夏季");
		}else if(month==9 || month==10 || month==11) {
			System.out.println("秋季");
		}else {
			System.out.println("冬季");
		}
		System.out.println("--------------");
		
		//这个时候，程序代码以及可以了。
		//但是呢，假如我要求你输入一个月份，判断是上半年还是下半年。
		//这个时候，我们的判断条件连接就是6个boolean表达式
		//我们可能还有更多的连接
		//这个时候，其实我们还有另外的一种改进方案：
		//month == 3
		//month == 4
		//month == 5
		//month>=3 && month<=5
		//用范围也是可以改进的。
		if(month<1 || month>12) {
			System.out.println("你输入的月份有误");
		}else if(month>=3 && month<=5) {
			System.out.println("春季");
		}else if(month>=6 && month<=8) {
			System.out.println("夏季");
		}else if(month>=9 && month<=11) {
			System.out.println("秋季");
		}else {
			System.out.println("冬季");
		}
		System.out.println("--------------");
	}
}
```

```
/*
	获取三个数据中的最大值
	
	由此案例主要是为了讲解if语句是可以嵌套使用的。而且是可以任意的嵌套。
*/
class IfTest4 {
	public static void main(String[] args) {
		int a = 10;
		int b = 30;
		int c = 20;
		
		//三元实现
		//int temp = (a>b)? a: b;
		//int max = (temp>c)? temp: c;
		//System.out.println("max:"+max);
		//System.out.println("--------");
		
		//用if语句实现
		int max;
		if(a > b) {
			if(a > c) {
				max = a;
			}else {
				max = c;
			}
		}else {
			if(b > c) {
				max = b;
			}else {
				max = c;
			}
		}
		System.out.println("max:"+max);
	}
}
```
## 选择结构(switch语句)
**switch语句格式**：
    
```
switch(表达式) {
	      case 值1：
			语句体1;
			break;
		    case 值2：
			语句体2;
			break;
		    …
		    default：	
			语句体n+1;
			break;
    }
```

**执行流程**：

```
首先计算出表达式的值
其次，和case依次比较，一旦有对应的值，就会执行相应的语句，在执行的过程中，遇到break就会结束。
最后，如果所有的case都和表达式的值不匹配，就会执行default语句体部分，然后程序结束掉。
```
**Switch语句流程图**
![image](http://image.damienzhong.com//switch.png)
**代码演示**

```
/*
	switch语句格式：
		switch(表达式) {
			case 值1:
				语句体1;
				break;
			case 值2:
				语句体2;
				break;
			...
			default:
				语句体n+1;
				break;
		}
		
	格式的解释：
		switch:表示这是switch选择结构
		表达式:这个地方的取值是有限定的
			byte,short,int,char
			JDK5以后可以是枚举
			JDK7以后可以是字符串
		case:后面跟的是要和表达式进行比较的值
		语句体:要执行的代码
		break:表示中断，结束的意思，可以控制switch语句的结束。
		default:当所有的值都和表达式不匹配的时候，就执行default控制的语句。其实它就相当于if语句的else。
	
	面试题：
		byte可以作为switch的表达式吗?
		long可以作为switch的表达式吗?
		String可以作为switch的表达式吗?
		
	案例：
		键盘录入一个数据，根据这个数据，我们输出对应的星期?
			键盘录入1,对应输出星期一
			键盘录入2,对应输出星期二
			...
			键盘录入7,对应输出星期日
			
	分析：
		1:键盘录入，用Scanner实现
		2:判断我们既可以使用if语句，也可以使用我们要讲解的switch语句
		
	注意：
		A:遇到左大括号缩进一个tab的位置。
		B:关联不是很大的语句间空行
*/
import java.util.Scanner;

class SwitchDemo {
	public static void main(String[] args) {
		//创建键盘录入对象
		Scanner sc = new Scanner(System.in);
		
		//控制键盘录入数据
		System.out.println("请输入一个数据(1-7):");
		int week = sc.nextInt(); //3
		
		//switch判断语句
		switch(week) {
			case 1:
				System.out.println("星期一");
				break;
			case 2:
				System.out.println("星期二");
				break;
			case 3:
				System.out.println("星期三");
				break;
			case 4:
				System.out.println("星期四");
				break;
			case 5:
				System.out.println("星期五");
				break;
			case 6:
				System.out.println("星期六");
				break;
			case 7:
				System.out.println("星期日");
				break;
			default:
				System.out.println("你输入的数据有误");
				break;
		}
	}
}
```

**注意事项**
- case后面只能是常量，不能是变量，而且，多个case后面的值不能出现相同的
- default可以省略吗?
  - 可以省略。一般不建议。除非判断的值是固定的。(单选题)
- break可以省略吗?
  - 可以省略，一般不建议。否则结果可能不是你想要的
- default的位置一定要在最后吗?
  - 可以出现在switch语句任意位置。
- switch语句的结束条件
  - 遇到break
  - 执行到程序的末尾

```
/*
	switch语句的注意事项：
		A:case后面只能是常量，不能是变量，而且，多个case后面的值不能出现相同的
		B:default可以省略吗?
			可以省略，但是不建议，因为它的作用是对不正确的情况给出提示。
			特殊情况：
				case就可以把值固定。
				A,B,C,D
		C:break可以省略吗?
			可以省略，但是结果可能不是我们想要的。
			会出现一个现象：case穿透。
			最终我们建议不要省略
		D:default一定要在最后吗?
			不是，可以在任意位置。但是建议在最后。
		E:switch语句的结束条件
			a:遇到break就结束了
			b:执行到末尾就结束了
*/
import java.util.Scanner;

class SwitchDemo2 {
	public static void main(String[] args) {
		//创建键盘录入对象
		Scanner sc = new Scanner(System.in);
		
		//控制键盘录入数据
		System.out.println("请输入一个数据(1-7):");
		int week = sc.nextInt(); //3
		
		//定义常量
		//int number = 3;
		//然后把case后面的值改为number，就会报错
		
		//switch判断语句
		switch(week) {
			case 1:
				System.out.println("星期一");
				break;
			case 2:
				System.out.println("星期二");
				break;
			case 3:
				System.out.println("星期三");
				break;
			case 4:
				System.out.println("星期四");
				break;
			case 5:
				System.out.println("星期五");
				break;
			case 6:
				System.out.println("星期六");
				break;
			case 7:
				System.out.println("星期日");
				break;
			default:
				System.out.println("你输入的数据有误");
				//break;
		}
	}
}
```

    
# 选择结构(各自使用场景)
- 在做判断的时候，我们有两种选择，if语句和switch语句，那么，我们到底该如何选择使用那种语句呢?
- if语句使用场景：
  - 针对结果是boolean类型的判断
  - 针对一个范围的判断
  - 针对几个常量值的判断
- switch语句使用场景：
  - 针对几个常量值的判断

```
/*
	用switch语句实现键盘录入月份，输出对应的季节
	
	分析：
		A:键盘录入一个月份，用Scanner实现
		B:用switch语句实现即可
		
	if语句和switch语句的区别?
		if语句：
			A:针对结果是boolean类型的判断
			B:针对一个范围的判断
			C:针对几个常量值的判断
		
		switch语句：
			针对几个常量值的判断
*/
import java.util.Scanner;

class SwitchTest4 {
	public static void main(String[] args) {
		//创建键盘录入对象
		Scanner sc = new Scanner(System.in);
		
		//录入数据
		System.out.println("请输入月份(1-12)：");
		int month = sc.nextInt();
		
		/*
		switch(month) {
			case 1:
				System.out.println("冬季");
				break;
			case 2:
				System.out.println("冬季");
				break;
			case 3:
				System.out.println("春季");
				break;
			case 4:
				System.out.println("春季");
				break;
			case 5:
				System.out.println("春季");
				break;
			case 6:
				System.out.println("夏季");
				break;
			case 7:
				System.out.println("夏季");
				break;
			case 8:
				System.out.println("夏季");
				break;
			case 9:
				System.out.println("秋季");
				break;
			case 10:
				System.out.println("秋季");
				break;
			case 11:
				System.out.println("秋季");
				break;
			case 12:
				System.out.println("冬季");
				break;
			default:
				System.out.println("你输入的月份有误");
		}
		*/
		
		//这样写太麻烦了，我们使用一个我们不想使用的东西：case穿透
		switch(month) {
			case 1:
			case 2:
			case 12:
				System.out.println("冬季");
				break;
			case 3:
			case 4:
			case 5:
				System.out.println("春季");
				break;
			case 6:
			case 7:
			case 8:
				System.out.println("夏季");
				break;
			case 9:
			case 10:
			case 11:
				System.out.println("秋季");
				break;
			default:
				System.out.println("你输入的月份有误");
		}
	}
}
```
