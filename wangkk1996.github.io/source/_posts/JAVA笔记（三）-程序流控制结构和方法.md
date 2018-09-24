---
title: JAVA笔记（三）-程序流控制结构和方法
date: 2018-09-11 12:19:18
tags: JAVA
categories: CS之路
---
《JAVA程序设计教程》笔记（三）——CHAP4 程序流控制结构和方法

**重点**：
* if elif条件嵌套
* 多选择结构switch+case
* 带标号的`continue`&`break`
* 递归算法
<!--more-->
## switch语句
**【举个栗子】switch + 三目条件运算**（见笔记（一））
本例可以把输入的字符串转换成数字：
**以及在Java中，用双引号""括起来的为String,用单引号''括起来的是Char**
```java
import java.io.*;
class SwitchTest2{
    public static void main(String args[]) throws IOException {
        char ch;
        System.out.print("enter a month: ");
        //这里是因为没有办法输入10,11,12这种两个字符的字节,故而用a,b,c代替
        ch = (char)System.in.read();
        {
            System.in.skip(2);
            switch(
                (ch == '1'||ch == '2'||ch == 'c')?1:
                    (ch == '3'||ch == '4'||ch == '5')?2:
                    (ch == '6'||ch == '7'||ch == '8')?3:
                    (ch == '9'||ch == 'a'||ch == 'b')?4:5)
                {
                    case 1: System.out.println("春季");
                            break;
                    case 2: System.out.println("夏季");
                            break;
                    case 3: System.out.println("秋季");
                            break;
                    case 4: System.out.println("冬季");
                            break; 
                    default:System.out.println(ch + "是无效月份！");                      
                }
                System.out.print("switch语句出口！");
                
        }
        
    }
}
```
## 结构化编程
### for 循环
`for(初值表达式1;循环条件表达式2;循环变量修改表达式3)`

注定一定要确定循环条件，以防陷入死循环。

**【举个栗子】计算1-100整数之和**
```java
class LoopTest3{
    public static void main(String args[]){
        System.out.println("0-100 个整数之和 ：\n");
        int i, sum = 0;
        for(i = 1; i <= 100; i++) sum += i;
        System.out.println("sum=" + sum +  ",i =" + i );

    }
}
```
另外，如果i是循环for里面定义的，则只在循环内有效。

**【补充】用for循环实现和while一样的结构**

```java
int x = 10;
for (;;;)
{
    if ( x > 0) break;
    x -- ;
}
```
这时则需要和break结合。

### 嵌套循环和continue和break
#### 带标识的continue
添加一个合法的JAVA标识符，并在其后面跟上冒号。
**【举个栗子】**
```java
import javax.swig.JOptionPane;
public class ContinueLabTest{
    public static void main(String args[])
    {
        String output = "";
        rownext：//添加标识符
        for (int row = 1; row <= 5; row ++)
        {
            output += "\n";
            for(int column = 1; column <= 10; column ++)
            {
                if (column > 2 * row - 1)
                    continue rownext; //这里就是带标识的地方，跳出第二层for循环，回到外层的循环并判断循环条件。
                    output += "*";
            }
        }
        JOptionPane.showMessageDialog(null, output, "testing continue with a label", JOptionPane.INFORMATION_MESSAGE);
        System.exit(0);
    }
}
```
#### break语句
* break语句除了放在循环里，还能放在switch里。
* break也可以带标号，常用在跳出多重循环里，只要在想跳出的循环前面加上break标号。

## 算法设计
这里先看一个基础的：递归
**【举个栗子】用递归方法求阶乘**LoopDGc
```java
class factor{
    public long factorial(long n){
        if (n == 1) return 1
        else return n * factor(n-1)
    }
} 
public class LoopDGc {
    public static void main (String args[])
    {
        long n = 20l;
        factor a = new factor();
        long result = a.factorial(n);
        System.out.println(" "+n+" 的阶乘为" + result);
    }
}
```
实际上这个地方还没怎么明白，尤其是主类和普通类。

首要还是要明白递归是什么东西……