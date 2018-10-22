---
layout:     post
title:      Tomcat Linux配置方法
subtitle:   教程-日记
date:       2018-10-22
author:     王政乔
header-img: img/post-bg-android.png
catalog: true
tags:
    - Java
    - Tomcat
    - Linux
    - 教程
---
# Tomcat Linux配制方法
	学习使用Java Web时，需要搭建apache tomcat环境以运行java web application，在windows上安装使用tomcat相对容易，但在Linux上最初使用时不知为何总是出错。后来我按照自己的理解重新部署，最终成功。我将它写下来以记录。

## 0.环境

- Deepin 15
- JDK1.8
- JRE

## 1.下载Tomcat Binary包
	http://tomcat.apache.org/download-70.cgi
​	从上方网站下载需要的tomcat，并解压到一个合适的目录（有介绍说需要放到/opt/目录下，事实上个人认为没有这个必要，我通常会放到Home目录下，于是tomcat就存在于/home/joger/tomcat文件夹中）。

## 2.添加Tomcat到环境变量

```bash
sudo nano /etc/profile
```

​	使用nano 打开/etc/profile，注意管理员权限，也可以使用vim或者gedit等文本编辑器进行。
在最下方添加
```bash
TOMCAT_HOME=/home/joger/tomcat
```
​	前提是你已经完成了JAVA_HOME的定义。
## 3.应用环境变量更改
```bash
source /etc/profile
```
应用环境变量的更改。
## 4. 启动Tomcat
​	在tomcat目录，运行
```bash
sudo ./bin/startup.sh
```
​	此时会提示Tomcat Started，这时候说明已经成功启动。我们接下来可以验证
 ## 5.验证Tomcat是否成功安装
 	在浏览器浏览http://localhost:8080，出现Tomcat界面说明成功