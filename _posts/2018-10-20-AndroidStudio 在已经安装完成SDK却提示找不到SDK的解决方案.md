---
layout:     post
title:      AS在已经安装完成SDK，却提示找不到SDK的解决方案
subtitle:   走过的坑
date:       2018-10-20
author:     王政乔
header-img: img/post-bg-android.png
catalog: true
tags:
    - Android Studio
    - SDK
    - 解决方案
---
## Android Studio 在已经安装完成SDK，却提示找不到SDK的解决方案

### 问题描述

​	在从gitee克隆下的一个项目，在打开的时候，明明已经完成了Android SDK的安装，但是提示没有找到SDK，哪怕重新安装新的SDK，或者在系统变量添加ANDROID_HOME也无济于事。

### 解决方案

​	在InteliJ或者Android Studio界面中，File-Settings，Appearance & Behavior，System Settings， Android SDK，在Android SDK Location后点击edit，无需改变SDK目录，直接下一步，直到Finish，它会自动重新配置好地址。