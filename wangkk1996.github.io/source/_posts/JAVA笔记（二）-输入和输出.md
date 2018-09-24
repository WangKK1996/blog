---
title: JAVA笔记（二）-输入和输出
date: 2018-09-11 10:28:18
tags: JAVA
categories: CS之路
---
《JAVA程序设计教程》笔记（二）——CHAP3 Java的输入和输出

**重点**：
* System.out.write()
* 流式交互(InputStreamReader + BufferedReader)

<!--more-->
## 标准输入/输出方法
Java里System包提供输入/输出流。
### 输出方法
* `println()`输出后换行；
* `print()`输出后不换行；
* `write()`则被用来输出字节数组
  
以下举例：
* `void println(char[] X)`输出一个字符数组
* `void write(int b [])`输出字节数组中的某一个元素，其后不换行。
  ```java
  class PrintDemo{
    public static void main(Strng args[]){
        byte b[]  = {'f','g','h','i'};
        
        System.out.write(b,0,2);
        System.out.println(); //因为write后不换行，所以这里用println换行
        System.out.write(b[0]);
    }
  }
  ```
  输出结果是：`fg`和`f`

# 标准输入方法
用`System.in.read()`方法，有以下三种格式：
```
public abstract in read() //从键盘输入一个字符
public int read(byte[] b) //一次输入多个字节，并存在字节数组b中
public int read (byte[] b, int off, int len)//限定输入的字节
```
另外，因为键盘输入很容易出错，所以必须引入**异常处理**机制。引入格式有两种
1. 在main方法后直接用`throws java.io.IOException`子句抛出异常；
2. 先在程序开头`import java.io.*;`加载语句,接着在main方法后加上`throws IOExcrption`子句来跑出异常。

【举个栗子】在键盘上一次输入多个字符并显示：
```java
public class ReadCharDemo{
    public static void main(String args[]) throws java.io.IOException
    {
        byte b[] = new byte[16]; //定义长度为16的数组
        System.out.println("\n 从键盘输出不超过16个字符，按回车键结束")
        System.in.read(b);
        System.out.printlb("\n 从键盘输入的是：")
        System.out.write(b,0,16);//用write直接输出字节数组。
    }
}
```
**注意**
* 如果用的是print方法，则需要把每一个元素都转化成字符，比较麻烦。
* 使用read方法时，还可以用read(b, 0, 10)来限制读入长度。（见上面提到的方法3）

## 利用命令行传入参数
```java
public class HelloArgs{
    public static void main(String args[])
    {
        System.out.println(args[0] + args[1] + "Hello!");
    }
}
```
接着可以在命令行里直接传递参数：

```shell
E:\code\java-learning> java HelloArgs 王可 王小可
王可王小可Hello!
```

# 流式交互
```java
import java.io.*;
public class HelloA1
{
    public static void main(String [] args) throws IOException
    {
        InputStreamReader reader = new InputStreamReader(System.in);
        BufferedReader input = new BufferedReader(reader);
        System.out.print("Enter your name:");
        String name = input.readLine();
        System.out.println("Hello," + name + "!");
    }
```
这里reader作为InputStreamReader的一个实例存在，并且用作输入的System.in对象与之绑定；

接下在input作为BufferedReader的一个实例，与reader绑定；

用input的readLine方法来从键盘读取一整行的文字即可。

# 图形界面&自定义类
以后再填坑，目前用不上，跳过。 