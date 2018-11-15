---
title: 【JavaSe必知必会】26-数组常见问题与操作
date: 2018-11-15 17:18:47
tags: javase
categories: javase
---
# 数组操作常见的两个小问题
- 数组索引越界
  - ArrayIndexOutOfBoundsException
  - 访问到了数组中的不存在的索引时发生。
- 空指针异常
  - NullPointerException
  - 数组引用没有指向实体，却在操作实体中的元素时。

```
/*
	数组操作的两个常见小问题：
		ArrayIndexOutOfBoundsException:数组索引越界异常
			原因：你访问了不存在的索引。
		
		NullPointerException:空指针异常
			原因：数组已经不在指向堆内存了。而你还用数组名去访问元素。
			
		作用：请自己把所有的场景Exception结尾的问题总结一下。以后遇到就记录下来。
			  现象，原因，解决方案。
*/
class ArrayDemo6 {
	public static void main(String[] args) {
		//定义数组
		int[] arr = {1,2,3};
		
		//System.out.println(arr[3]);
	
		//引用类型的常量：空常量 null
		arr = null;
		System.out.println(arr[0]);
	}
}
```
# 数组练习(常见操作)
## 数组遍历(依次输出数组中的每一个元素)

```
/*
	数组遍历：就是依次输出数组中的每一个元素。
	
	注意：数组提供了一个属性length，用于获取数组的长度。
		  格式：数组名.length
*/
class ArrayTest {
	public static void main(String[] args) {
		//定义数组
		int[] arr = {11,22,33,44,55};
		
		//获取每一个元素
		//如何获取呢?我们知道数组名结合编号(索引)就可以找到数据
		System.out.println(arr[0]);
		System.out.println(arr[1]);
		System.out.println(arr[2]);
		System.out.println(arr[3]);
		System.out.println(arr[4]);
		System.out.println("--------------------");
		
		//虽然这种做法可以，但是不是我想要的
		//我们发现，代码的重复度很高
		//输出语句，数组名都是相同的，仅仅是索引是变化的
		//我们就可以使用循环搞定索引值
		for(int x=0; x<5; x++) {
			//x=0,1,2,3,4
			System.out.println(arr[x]);
		}
		System.out.println("--------------------");
		
		//从0开始我们是明确的，但是为什么到5呢，我们是数了一下数组的个数
		//继续看下个数组如何遍历
		int[] arr2 = {1,2,3,4,5,6,7,8,9,10,11,2,2,3,4,5,7,8,5,3,5,6,8,7,8,5,3,5,6,8,7,8,5,3,5,6,8,7,8,5,3,5,6,8,7,8,5,3,5,6,8};
		//而我们在很多时候，数组的元素不能靠数
		//这个时候，数组就给我们提供了一个属性：length专门用于获取数组的长度
		//格式：数组名.length 返回数组的长度
		System.out.println(arr.length);
		System.out.println(arr2.length);
		System.out.println("--------------------");
		
		//改进第一个程序
		for(int x=0; x<arr.length; x++) {
			System.out.println(arr[x]);
		}
		System.out.println("--------------------");
		
		//我们如果想要对多个数组进行遍历，每个数组的遍历我们都把代码写一遍，麻烦不
		//麻烦，所以，我们准备用方法改进。
		//用方法改进后，请调用
		printArray(arr);
		System.out.println("--------------------");
		printArray(arr2);
		System.out.println("--------------------");
		printArray2(arr);
	}
	
	/*
		遍历数组的方法
		
		两个明确：
			返回值类型：void
			参数列表：int[] arr
	*/
	public static void printArray(int[] arr) {
		for(int x=0; x<arr.length; x++) {
			System.out.println(arr[x]);
		}
	}
	
	//请看改进版本
	public static void printArray2(int[] arr) {
		System.out.print("[");
		for(int x=0; x<arr.length; x++) {
			if(x == arr.length-1) { //这是最后一个元素
				System.out.println(arr[x]+"]");
			}else {
				System.out.print(arr[x]+", ");
			}
		}
	}
}
```

## 数组获取最值(获取数组中的最大值最小值)

```
/*
	数组获取最值(获取数组中的最大值最小值)
	
	分析：
		A:定义一个数组，并对数组的元素进行静态初始化。
		B:从数组中任意的找一个元素作为参照物(一般取第一个),默认它就是最大值。
		C:然后遍历其他的元素，依次获取和参照物进行比较，如果大就留下来，如果小，就离开。
		D:最后参照物里面保存的就是最大值。
*/
class ArrayTest2 {
	public static void main(String[] args) {
		//定义一个数组
		int[] arr = {34,98,10,25,67};
		
		//请获取数组中的最大值
		/*
		//从数组中任意的找一个元素作为参照物
		int max = arr[0];
		//然后遍历其他的元素
		for(int x=1; x<arr.length; x++) {
			//依次获取和参照物进行比较，如果大就留下来，如果小，就离开。
			if(arr[x] > max) {
				max = arr[x];
			}
		}
		//最后参照物里面保存的就是最大值。
		System.out.println("max:"+max);
		*/
	
		//把这个代码用方法改进
		//调用方法
		int max = getMax(arr);
		System.out.println("max:"+max);
			
		//请获取数组中的最小值
		int min = getMin(arr);
		System.out.println("min:"+min);
	}
	
	/*
		需求：获取数组中的最大值
		两个明确：
			返回值类型：int
			参数列表：int[] arr
	*/
	public static int getMax(int[] arr) {
		//从数组中任意的找一个元素作为参照物
		int max = arr[0];
		//然后遍历其他的元素
		for(int x=1; x<arr.length; x++) {
			//依次获取和参照物进行比较，如果大就留下来，如果小，就离开。
			if(arr[x] > max) {
				max = arr[x];
			}
		}
		//最后参照物里面保存的就是最大值。
		return max;
	}
	
	public static int getMin(int[] arr) {
		//从数组中任意的找一个元素作为参照物
		int min = arr[0];
		//然后遍历其他的元素
		for(int x=1; x<arr.length; x++) {
			//依次获取和参照物进行比较，如果小就留下来，如果大，就离开。
			if(arr[x] < min) {
				min = arr[x];
			}
		}
		//最后参照物里面保存的就是最小值。
		return min;
	}
}
```

## 数组元素逆序 (就是把元素对调)

```
/*
	数组元素逆序 (就是把元素对调)
	
	分析：
		A:定义一个数组，并进行静态初始化。
		B:思路
			把0索引和arr.length-1的数据交换
			把1索引和arr.length-2的数据交换
			...
			只要做到arr.length/2的时候即可。
*/
class ArrayTest3 {
	public static void main(String[] args) {
		//定义一个数组，并进行静态初始化。
		int[] arr = {12,98,50,34,76};
		
		//逆序前
		System.out.println("逆序前：");
		printArray(arr);
		
		//逆序后
		System.out.println("逆序后：");
		//reverse(arr);
		reverse2(arr);
		printArray(arr);
	}
	
	/*
		需求：数组逆序
		两个明确：
			返回值类型：void (有人会想到应该返回的是逆序后的数组，但是没必要，因为这两个数组其实是同一个数组)
			参数列表：int[] arr
	*/
	public static void reverse(int[] arr) {
		/*
		//第一次交换
		int temp = arr[0];
		arr[0] = arr[arr.length-1-0];
		arr[arr.length-1-0] = temp;
		
		//第二次交换
		int temp = arr[1];
		arr[1] = arr[arr.length-1-1];
		arr[arr.length-1-1] = temp;
		
		//第三次交换
		int temp = arr[2];
		arr[2] = arr[arr.length-1-2];
		arr[arr.length-1-2] = temp;
		*/
		//用循环改进
		for(int x=0; x<arr.length/2; x++) {
			int temp = arr[x];
			arr[x] = arr[arr.length-1-x];
			arr[arr.length-1-x] = temp;
		}
	}
	
	public static void reverse2(int[] arr) {
		for(int start=0,end=arr.length-1; start<=end; start++,end--) {
			int temp = arr[start];
			arr[start] = arr[end];
			arr[end] = temp;
		}
	}
	
	//遍历数组
	public static void printArray(int[] arr) {
		System.out.print("[");
		for(int x=0; x<arr.length; x++) {
			if(x == arr.length-1) { //这是最后一个元素
				System.out.println(arr[x]+"]");
			}else {
				System.out.print(arr[x]+", ");
			}
		}
	}
}
```

## 数组元素查找(查找指定元素第一次在数组中出现的索引)


```
/*
	需求：数组元素查找(查找指定元素第一次在数组中出现的索引)
	
	分析：
		A:定义一个数组，并静态初始化。
		B:写一个功能实现
			遍历数组，依次获取数组中的每一个元素，和已知的数据进行比较
			如果相等，就返回当前的索引值。
*/
class ArrayTest5 {
	public static void main(String[] args) {
		//定义一个数组，并静态初始化
		int[] arr = {200,250,38,888,444};
		
		//需求：我要查找250在这个数组中第一次出现的索引
		int index = getIndex(arr,250);
		System.out.println("250在数组中第一次出现的索引是："+index);
		
		int index2 = getIndex2(arr,250);
		System.out.println("250在数组中第一次出现的索引是："+index2);
		
		int index3 = getIndex2(arr,2500);
		System.out.println("2500在数组中第一次出现的索引是："+index3);
	}
	
	/*
		需求：查找指定数据在数组中第一次出现的索引
		两个明确：
			返回值类型：int
			参数列表：int[] arr,int value
	*/
	public static int getIndex(int[] arr,int value) {
		//遍历数组，依次获取数组中的每一个元素，和已知的数据进行比较
		for(int x=0; x<arr.length; x++) {
			if(arr[x] == value) {
				//如果相等，就返回当前的索引值。
				return x;
			}
		}
		
		//目前的代码有一个小问题
		//就是假如我要查找的数据在数组中不存在，那就找不到，找不到，你就对应的返回吗?
		//所以报错。
		
		//只要是判断，就可能是false，所以大家要细心。
		
		
		//如果找不到数据，我们一般返回一个负数即可，而且是返回-1
		return -1;
	}
	
	public static int getIndex2(int[] arr,int value) {
		//定义一个索引
		int index = -1;
		
		//有就修改索引值
		for(int x=0; x<arr.length; x++) {
			if(arr[x] == value) {
				index = x;
				break;
			}
		}
		
		//返回index
		return index;
	}
}
```
