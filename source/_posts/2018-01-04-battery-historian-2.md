---
layout: post
title:  Android电量优化(使用Battery Historian)
date:   2018-01-04
categories: android
tag: Android
---

#### 目录 ####

- 如何收集数据
- 数据图表的含义
- 如何分析并优化

#### 收集数据 ####

- 手机连接USB,执行`adb shell dumpsys batterystats --reset`命令,清空电池的历史状态
- 断开USB,打开目标应用,正常使用5分钟左右
- 连接USB,执行`adb bugreport bugreport.zip`,可以到处zip文件到当前目录下
- 浏览器进入`Battery Historian`,上传已生成的zip,然后会自动生成分析图表文件

#### 

 