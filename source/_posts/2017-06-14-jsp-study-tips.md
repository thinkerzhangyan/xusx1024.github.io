---
title: JSP学习笔记
date: 2017-06-14 
tags: javaEE
categories: work
---

#### JSP定义 ####
Java server page
##### jsp和servlet #####

- servlet不适合设置HTML响应体，需要大量的response.getWriter().pring("");
- servlet 动态资源，可以编程
- HTML是静态页面，不能包含动态信息
- HTML不用为输出HTML标签而发愁
- jsp在原有HTML的基础上添加Java脚本，构成jsp页面
- jsp作为请求发起/结束页面
- servlet作为请求中处理数据的环节

##### jsp组成 #####

- jsp = html + java脚本 + jsp标签
- jsp中无需创建即可使用的对象共9个，被称之为9大内置对象。例如：request对象、out对象
- 3中Java脚本
	- <%...%>放置Java代码
	- <%=...%>Java表达式，用于输出一条表达式或变量的结果
	- <%!...%>声明，用来创建类的成员变量和成员方法

##### jsp原理 #####

#### 会话跟踪技术 ####

#### Cookie ####

#### HttpSession ####

#### 一次性图片验证码

 