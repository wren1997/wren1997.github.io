---
layout:     post
title:      TF:No module named nets的解决方案
subtitle:   Tensorflow
date:       2018-11-18
author:     王政乔
catalog: true
tags:
    - Tensorflow
    - slim
    - 解决方案
---

## Tensorflow:No module named nets的解决方案

### 问题描述

​	在学习使用tensorflow的Tensorflow Object Detection API时，需要安装slim和proto，其中proto问题不大，需要安装3.3版本（3.5版本有一些bug），再一个就是如何添加slim到PYTHONPATH中了。

​	书上或者是官方文档描述的内容是，在research文件夹下，执行：

```bash
export PYTHONPATH=$PYTHONPATH:'pwd':'pwd'/slim
```

​	并且在执行完后，可以通过python的import slim来验证设置成功。这点没毛病。

​	紧接着，通过运行下面的程序来判断Tensorflow Object Detection API正确安装

```bash
python object_detection/builders/model_builder_test.py
```

​	但是并没有出现书上的结果，而是提示出了No module named nets的异常。

### 问题原因

​	其原因是在添加PYTHONPATH时，错误理解了那句export。

​	根据我从网络上其他用户的反馈，得到一个结论，pwd只是当前目录的代称，事实上完全可以使用完整绝对路径来实现这个。我的research文件夹所在的目录是/home/joger/Documents/Deep-Learning-21-Examples/chapter_5/research。

### 解决方案

​	于是我们可以根据我的目录得到结果：

```bash
export PYTHONPATH=$PYTHONPATH:/home/joger/Documents/Deep-Learning-21-Examples/chapter_5/research:/home/joger/Documents/Deep-Learning-21-Examples/chapter_5/research/slim
```

​	总的来说就是：

```bash
export PYTHONPATH=$PYTHONPATH:[research所在目录]:[slim所在目录]
```

​	之后就解决了这次问题。