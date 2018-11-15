---
title: 【JavaSe必知必会】18-流程控制语句之跳转控制语句
date: 2018-11-15 15:48:44
tags: javase
categories: javase
---
# 跳转控制语句
前面我们已经说过了，Java中的goto是保留字，目前不能使用。虽然没有goto语句可以增强程序的安全性，但是也带来很多不便，比如说，我想在某个循环知道到某一步的时候就结束，现在就做不了这件事情。为了弥补这个缺陷，Java就提供了break，continue和return来实现控制语句的跳转和中断。
## break 中断
### break的使用场景
- 在选择结构switch语句中
- 在循环语句中
- 离开使用场景的存在是没有意义的
### break的作用
- 跳出单层循环
- 跳出多层循环
  - 带标签的跳出
  - 格式：标签名: 循环语句
  - 标签名要符合Java的命名规则
###  案例演示

```
/*
	跳转控制语句：
		1、break 中断
		2、continue  继续
		3、return	返回
		
	break：中断
	使用场景：
		A：switch语句中
		B：循环语句中
			（循环语句中加入if判断的情况）
		注意：离开上面两种场景，无意义
	
	如何使用？
		A：跳出单层循环
		B：跳出多层循环
			要想实现多层循环，就必须知道一个东西。
			带标签的语句：
				格式：
					标签名:语句
*/
public class BreakDemo{
	public static void main(String[] args){
		//在 switch 或 loop 外部中断
		//break;
		
		//跳出单层循
		for(int i = 0;i<10;i++){
			if(i==2){
				break;
			}
			System.out.println("我的淘宝男装店铺名叫DM潮人社区");
		}
		System.out.println("广告时间结束");
		System.out.println("============================");
		
		wc:for(int i = 0;i<5;i++){
			nc:for(int j=0;j<4;j++){
				if(j==2){
					break nc;
				}
				System.out.print("*");
			}
			System.out.println();
		}
	}
}
```
## continue 继续
### continue的使用场景
- 在循环语句中
- 离开使用场景的存在是没有意义的
### continue的作用
- break  退出当前循环
- continue  退出本次循环
- 也可以带标签的使用
### 案例演示

```

/*
	continue:继续
	continue的使用场景：
		循环中，离开此场景没用意义。
	测试，对比break与continue的区别：
	break:跳出单层循环
	continue：跳出单层循环，进入下一次的执行
*/
public class ContinueDemo{
	public static void main(String[] args){
		for(int x=0;x<10;x++){
			if(x==3){
				//break;
				continue;
			}
			System.out.println(x);
		}
		System.out.println("-------------------------");
		
		for(int i =1;i<=10;i++){
			if(i%3==0){
				//在此处填写代码
				//在控制台输出2次
				//break;
				//在控制台输出7次
				//continue;
				//在控制台输出13次
				System.out.println("DM潮人社区是呆萌钟的淘宝男装店，希望大家多多支持");
			}
			System.out.println("DM潮人社区是呆萌钟的淘宝男装店，希望大家多多支持");
		}
		
	}
}
```

## return 返回
return关键字不是为了跳转出循环体，更常用的功能是结束一个方法，也就是退出一个方法。跳转到上层调用的方法。这个在方法的使用那里会在详细的讲解。

### 案例演示

```
/*
	return:返回
	
	其实它的作用不是结束循环的，而是结束方法的。
*/
class ReturnDemo {
	public static void main(String[] args) {
		for(int x=0; x<10; x++) {
			if(x == 2) {
				System.out.println("退出");
				//break;
				//continue;
				return;
			}
			
			System.out.println(x);
		}
		
		System.out.println("over");
	}
}
```
