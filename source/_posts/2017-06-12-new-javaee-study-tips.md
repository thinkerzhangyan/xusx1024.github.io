---
title: HttpRequest学习笔记
date: 2017-6-12 20:13:51
tags: javaEE
categories: work
---

#### cvc-complex-type.2.4.a: Invalid content was found starting with element 'display-name' ####

`web.xml`在自动生成servlet的时候出现的提示。

通常是由于标签位置，标签DTD的校验规则所影响的。

删除“http://xmlns.jcp.org/xml/ns/javaee/web-app_3_1.xsd”即不采用该校验规则 
 

#### request 重要方法 ####
- 获取IP
- 获取请求方法
- 获取请求参数
- 获取浏览器类型
- 获取协议
- 获取服务器名
- 获取服务器端口
- 获取项目名
- 获取servlet路径
- 获取GET参数
- 获取URI
- 获取URL
 
#### 使用referer完成防盗链 ####
- 在浏览器地址栏直接输入ip，referer为空
- 从百度输入ip，referer为百度

#### 获取request参数 ####
- 获取get参数
- 获取post参数
- 获取单值
- 获取多值
- 获取map