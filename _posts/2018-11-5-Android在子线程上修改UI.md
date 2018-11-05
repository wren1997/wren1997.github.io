---
layout:     post
title:      AS:Only the original thread that created a view hierarchy can touch its views的解决方案
subtitle:   Android
date:       2018-11-5
author:     王政乔
catalog: true
tags:
    - Android
    - Handle
    - 解决方案
---

## AS：Only the original thread that created a view hierarchy can touch its views的解决方案

### 问题描述

在开发Android UI时，尝试着修改已经显示的SweetAlertDialog的样式，运行时提示出了

> Only the original thread that created a view hierarchy can touch its views

这个错误，而且无论是多线程的调用还是重新在主线程定义都无法解决这个问题。

### 问题分析

经过查看资料，引起这个问题的原因是Android不允许跨view和控件的，说是不安全的（.net大法好），因此需要单独处理才可以进行。

根据网络上提供的方法，可以使用Handle解决此类问题（也是这种问题最佳解决方案）。

### 解决方案

通过Handle我们可以更新UI，依次下面的步骤，我们可以解决这个问题。

1. 创建Handle（必须在主线程中）
2. 构建Runnable对象，这个对象建立的目的是进行UI的更新修改
3. 在子线程的run方法向UI线程POST，这样会通过上方的Runnable对象来更新UI

在我的项目里，可以看到是这样的

```java
protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        requestWindowFeature(Window.FEATURE_NO_TITLE);
        setContentView(R.layout.checkio_activity);
        pDialog = new SweetAlertDialog(this, PROGRESS_TYPE);
        hander=new Handler();
        button_checkin.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                pDialog.getProgressHelper().setBarColor(Color.parseColor("#A5DC86"));
                pDialog.setTitleText("正在上传数据....");
                pDialog.setCancelable(false);
                pDialog.show();
                new Thread() {
                    public void run() {
                        try {
                            sleep(3000);
                        } catch (
                                InterruptedException e) {
                            e.printStackTrace();
                        } finally {
                            hander.post(ui_uploaddata_success);
                            try{
                                sleep(1000);
                            } catch (InterruptedException e) {
                                e.printStackTrace();
                            } finally {
                                pDialog.dismiss();
                            }
                        }
                    }
                }.start();

            }
        });
        init();

    }

    Runnable ui_uploaddata_success=new Runnable() {
        @Override
        public void run() {
            pDialog.changeAlertType(SUCCESS_TYPE);
        }
    };
```

其完成的效果就是在按钮上单击后，会调用SweetAlertDialog，然后等待3000ms，之后改变UI，从等待界面变为成功界面，再显示一秒，自动退出。

