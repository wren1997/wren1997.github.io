---
layout:     post
title:       No module named _tkinter, please install the python-tk package 解决方案
subtitle:   医学影像
date:       2018-10-24
author:     王政乔
catalog: true
tags:
    - python
    - 解决方案
    - 医学图像
---
## No module named _tkinter, please install the python-tk package 解决方案

### 问题描述

在使用pydicom打开医学图像时，常常需要安装pylab，pylab是matplotlib下的一个py库，因此使用时需要先安装pip

```bash
sudo apt-get install python-pip
```
然后再使用pip安装matplotlib
请注意，此时安装的matplotlib推荐2.0.2的，否则可能会出现其他的错误 No module named functools_lru_cache。也不知道为什么
所以
```bash
pip install matplotlib==2.0.2
```
之后使用python import pylab的时候会出现No module named _tkinter, please install the python-tk package

### 问题分析
这个是因为在安装的时候缺少依赖python-tk，我们只需要安装上去就行了

### 解决发难
使用包管理器apt安装依赖
```bash
sudo apt-get install python-tk
```
再次import pylab时就不会报错了。