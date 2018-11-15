---
title: 【JavaSe必知必会】24-形式参数是类名的方法的调用方式
date: 2018-11-15 17:15:30
tags: javase
categories: javase
---
# 形式参数是类名的方法的调用方式
## 形式参数的问题：
-  基本类型：形式参数的改变不影响实际参数
-  引用类型：形式参数的改变直接影响实际参数
```
/*
    形式参数的问题：
        基本类型：形式参数的改变不影响实际参数
        引用类型：形式参数的改变直接影响实际参数
*/
//形式参数是基本类型
class Demo{
    public int sum(int a,int b){
        return a + b;
    }
}

//形式参数是引用类型
class Student{
    public void study(){
        System.out.println("看呆萌钟的视频有助学习");
    }
}

class StudentDemo{
    public void method(Student s){
        s.study();
    }
}

class ArgsTest {
    public static void main(String[] args){
        //形式参数是基本类型的调用
        Demo d = new Demo();
        int result = d.sum(10,20);
        System.out.println("result:"+result);
        
        //形式参数是引用类型的调用
        //需求：我要调用StudentDemo类中的method()方法
        StudentDemo sd = new StudentDemo();
        //创建学生对象
        Student s = new Student();
        sd.method(s);//把s的地址给到了这里
    }
}
```
