---
layout:     post
title:      IntelliJ IDEA 配置Tomcat的方法
subtitle:   教程-日记
date:       2018-10-22
author:     王政乔
header-img: img/post-bg-android.png
catalog: true
tags:
    - Java
    - Tomcat
    - Linux
    - IDEA
    - 教程
---

## IntelliJ IDEA 配置Tomcat的方法
​	使用idea编辑java web时，需要对idea进行一定的配置，即便是配置了TOMCAT_HOME，也不一定能够一次成功。所以最好的方式是再配置一次。

### 0.前提条件

- JDK
- JRE
- TOMCAT
- IDEA

### 1.创建新项目
​	[Create New Project]-[Java]-[Java EE Web Application]-[勾选Create web.xml]-[Next]

### 2.配置project structure
1. 完成项目的创建后，需要配置project structure。

2. 界面右上角运行右侧，有Project Structure，打开
3. 在[Modules]-[%Project Name%]-[Sources]的WEB-INF文件夹下新建两个文件夹'lib''classes'
4. 在Paths中选择[Use modules compile output path]，并将下方两个path填上上述classes文件夹所在的地址。
5. 在Dependencies中添加[Jars or directory]，并选择上述lib文件夹所在地址，在提示框中选择[Jar Directory]。

### 3.配置Configurations
1. [run]-[Edit Configurations]打开

2. 新建Tomcat Service，在http proxy填写8080。
3. 在Deployment上添加Artifact
4. OK

### 4.设置TOMCAT可执行
1. 打开TOMCAT所在目录/bin，在此打开终端，输入

```bash
sudo chmod +x *.sh
```
2. 并且确保Tomcat处于关闭状态，若不确定，可以执行

```
sudo ./shutdown.sh
```
一试。


### 5.运行WEBAPP
这时候就可以正常运行WEB了。