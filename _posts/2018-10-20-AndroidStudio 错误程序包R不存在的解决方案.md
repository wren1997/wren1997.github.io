---
layout:     post
title:      AS错误：程序包R不存在的解决方案
subtitle:   走的坑
date:       2018-10-20
author:     王政乔
header-img: img/post-bg-android.png
catalog: true
tags:
    - Android Studio
    - Android
    - 解决方案
    - 程序包R
---
## Android Studio 错误：程序包R不存在的解决方案

### 问题描述

​	使用Android Studio打开自己github上的项目时，在R处红色，提示错误是程序包R不存在的解决方案，并且重置项目设置并不能解决问题。

### 问题原因

​	由于包的名称出现了问题，因此在调用时出现了文件无法找到的问题。

### 解决方案

​	在出错的文件上输入R，按Alt+Enter，选择提示中的任意一个并回车，系统会自动加载选择。再编译后问题解决。