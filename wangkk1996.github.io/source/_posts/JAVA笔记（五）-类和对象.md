---
title: JAVA笔记（五）-类和对象
date: 2018-09-12 10:32:37
tags: JAVA
categories: CS之路
---
《JAVA程序设计教程》笔记（五）——CHAP6 类和对象

**重点**：
* 类的构造方法
*  
<!--more-->

# 类
## 类的声明

## 类体
类体中包含变量的声明以及类方法的定义。
### 类的构造方法
* 构造方法的名称和类名相同
* 没有返回类型，返回值，也不需要修饰符
* 虽然看起来和一般的成员方法没有区别，但不能被直接调用，只能被new运算符调用
* 构造方法不能被继承（因为它不是类的成员）
* 子类可以调用父类的构造方法

**【举个栗子】** 创建一个car类并调用。
```java
class Car{
    private String Brand;
    int gas;
    Car (String vBrand, int vgas ){ //构造方法
        Brand = vBrand;
        gas = vgas;
    }
    void run(){
        if (gas > 0)
        gas -=10;
        else
        System.out.println("没油了，不能跑啦~");
    }
    void Disp(){
        System.out.println("品牌："+Brand+"油量"+gas);
    }
}
class Example6_1{
    public static void main(String args[]){
        Car MyCar = new Car("Audi", 10); //创建对象mycar
        MyCar.Disp(); //调用disp方法
        MyCar.run(); //调用run方法
        System.out.println("car is running……");
        MyCar.run();
    }
}
```
## 成员变量