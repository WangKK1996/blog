---
title: java10的环境配置
date: 2018-09-10 20:24:17
tags: JAVA
categories: CS之路
---
好久没碰JAVA，今天重新下了个JDK10，发现配置较之前学习的有所变化。主要是PATH和JRE的环境配置：

<!--more-->

## CLASSPATH配置
* 首先在环境变量中添加JAVA_HOME为jdk的安装路径；
* 新建一个CLASSPATH的系统变量，并添加`.;%JAVA_HOME%\lib;%JAVA_HOME%\lib\tools.jar`
  
  注意前面不要忘记加点和分号。


## PATH配置
直接用绝对路径，添加`<PATH_TO_JDK\bin>`

（并不需要把jre也加进去）

## 验证安装是否成功
老三样，打开cmd，依次输入：
```
java -version
javac
java
```
都成功就说明装完啦~
