---
title: JSP、Cookie、Session学习
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
	- <%-- ... ---%> jsp注释

##### jsp原理 #####

- jsp其实是一个特殊的servlet。
- 当jsp第一次被访问，服务器会把jsp编译成Java文件，这个Java文件其实实现了servlet接口
- 把该Java编译成.class文件
- 然后创建该类对象
- 最好调用其service方法
- 第二次请求时，直接调用其service方法

#### 会话跟踪技术 ####

- Cookie

#### Cookie ####

- 由服务器创建保存到客户端的浏览器的一个键值对，服务器保存Cookie的响应头：Set-Cookie:aaa=AAA
- Cookie由HTTP协议制定的
- 当浏览器请求服务器时，会把该服务器保存的Cookie随请求发送给服务器。浏览器归还Cookie的请求头
- 1个Cookie最大4kb
- 1个服务器最多向一个浏览器保存20个Cookie
- 1个浏览器最多保存300个Cookie，由于浏览器竞争，肯定都超4kb,20,300了。

##### 作用 #####

- 服务端使用Cookie来跟踪客户端状态
- 保存商品浏览记录
- 显示上次登录名

##### 使用 #####

- response.addCookie()
- request.getCookies()

##### 详解 #####

- maxAge:最大生命时长以秒为单位
- path：并非Cookie在客户端的路径，而是浏览器访问服务器的路径，如果包含某个Cookie的路径，那么就会归还这个Cookie
- domain：指定Cookie的域名，当多个二级域中共享Cookie时才有用
	- 例如：www.baidu.com,zhidao.baidu.com,news.baidu.com,tieba.baidu.com共用Cookie时使用domain,设置domain为:cookie.setDomain(".baidu.com");
	- 必须设置path为：cookie.setPath("/");

#### HttpSession ####

- JavaWeb提供的类，用来会话跟踪的类。session是服务端对象，保存在服务器
- HttpSession是Servlet三大域对象之一
- HttpSession底层依赖Cookie，或是URL重写
- 会话范围
- session是JSP内置对象

##### session原理 #####

- UUID生成session，32位长，不重复的
- getSession
- getMaxInactiveInterval(),获取最大不活动时间，秒单位
- invalidate() 让session立刻失效，用于用户登出
- isNew() session是否为最新
- web.xml中可以配置session的最大不活动时间
	- <session-config><session-timeout>4</session-timeout></session-config>


##### URL重写 #####

- 浏览器禁用cookie时，URL重写添加JSession字段
- response.encodeURL("/xxxxservlet");会查看cookie是否存在，如果存在就只encode这个url，否则在url添加JSessionId。这就是智能URL重写

#### JSP三大指令 ####

##### page #####

- <%@page language="java" info="xxx" ...%>一个jsp页面中可以0-N个指令定义
- 习惯性放在jsp文件的首行
- pageEncoding：指定当前jsp页面的编码
- contentType
##### include #####
##### taglib #####

#### JSP九大内置对象 ####

#### JSP动作标签 ####

#### JavaBean概念 ####

#### EL表达式 ####

 