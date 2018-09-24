---
title: JAVA笔记（四）-数组
date: 2018-09-12 09:02:37
tags: JAVA
categories: CS之路
---
《JAVA程序设计教程》笔记（四）——CHAP5 数组

**重点**：
* java的高维数组每一个维数可以不一致
* 冒泡排序法    
<!--more-->
数组是用**相同类型的元素**组成的集合。这些元素可以是基本数据类型，也可以是构造出的数据类型。

包含以下几个部分：
* 数组名
* 数组类型
* 数组长度（有几个元素？）

数组中的元素是有顺序的。
## 一维数组
### 声明：
`int a[];`或者`int [] a;`均可。
### 初始化：
1. 直接在声明时初始化：`int a[] = {1,2,3};`，可用于**元素较少**的时候。
   但是不能先声明再使用静态的初始化:
```java
int a[];
a = {1,2,3}//会报错!
```
1. 为数组分配内存空间，后续再赋值
```java
类型 数组名[];
数组名 = new 类型[数组长度]；
```
    例如：
```java
int a = new int[4];
a[0] = 1;
a[1] = 2;
a[2] = 3;
a[3] = 4;
```
**【举个栗子】** 实现冒泡升序排列
```java
public class BubbleSort{
    public static void main(String args[])
    {
        int i,j;
        int intArray[] = {35,22,51,10,60};
        int len = intArray.length;
        for (i = 1; i < len; i++)
        for (j = 0; j < len - i - 1; j ++)        
            if (intArray[j] > intArray[j+1])
            {
                int t = intArray[j];
                intArray[j] = intArray[j + 1];
                intArray[j + 1] = t;
            }
        System.out.println("the result after bubblesort: ");
        for (i = 0; i < len - 1; i ++)
            System.out.println(intArray[i]);
    }   
}
```
### 把数组传递给方法


## 多维数组
### 二维数组的声明&创建
**声明：**
```java
int a[][];
double [][] b;
```
**分配内存空间**
1. 直接为每一维分配空间：
   `int a = new int[2][3];`创建一个2*3维的数组；
2. 从最高维开始分配：
   ```java
   int b = new int [2][];
   b[0] = new int[3];
   b[1] = new int[5];
   ```
得到的形式如下：

|  |  |  |  |  | 
| -- | -- | -- | -- | -- | -- |
|b[0][0] | b[0][1] | b[0][2] | | |
|b[1][0] | b[1][1] | b[1][2] | b[1][3] | b[1][4]| 

    
**注意** 
* java数组的每一维不需要等长。
* 使用new分配内存时，至少需要给出最高维的大小。







