---
title: Android 内存泄露
date: 2017-11-09
tags: android
categories: Android
---

#### 什么是内存泄露

jvm会根据可达性算法,计算每个对象是否可被回收,如果有对象被持有引用,即可达,并且该对象已经无用.此时对象不可被回收但是占用内存的这种状态成为内存泄露.如果内存泄露情况比较多,很有可能引起OOM异常.

#### 原因

* 根源在android组件的生命周期和底层Java对象的生命周期不是直接匹配的
* 一个应用程序的启动分为三步:
	* 复刻受精卵进程
	* 系统为该进程添加运行时执行环境
	* 运行时执行环境加载可执行文件,即调用onCreate()方法启动应用程序
* 应用程序的生命周期理想状态下,是在运行时调用onTerminate()方法是结束,但一般情况下都不会如此.应用程序的生命周期是从第一个的组件被创建到最后一个组件被销毁,很有可能在onTerminate()方法还没有调用,当前进程已经被回收掉了.即应用程序的存活时间小于了Java对象的存活时间.
* 简单来说,就是长生命周期的对象引用了短生命周期的对象
* 应用程序生命周期内,考虑多线程情况下,线程的存活时间取决于当前任务的长度,任务就是应用程序代码定义的,CPU有序顺序执行的指令,所以线程如果比所在组件生命长,很有可能是这样,往往容易引起内存泄露

#### 常见情况及解决

| 情况 | 解决 |
|:---:|:---:|
| Thread + Handler | 优先考虑静态成员类 |
| 数据库连接,IO,Socket连接,Bitmap | 及时关闭,及时释放 |
| 静态容器,静态类,持有对短生命周期的对象 | 及时删除对象,使用弱引用,软引用 |