---
title: 命令模式
date: 2017-06-14 
tags: 设计模式
categories: Design Pattern
---

#### 定义 ####

命令模式(Command Pattern):将一个请求封装为一个对象，从而使我们可用不同的请求对客户进行参数化；对请求排队或者记录请求日志，以及支持可撤销的操作。命令模式是一种对象行为型模式，又叫做动作(Action)模式或事务(Transaction)模式。
 
#### 模式结构 ####

- client：创建具体的命令和接收者
- command：命令的抽象类
- ConcreteCommand：具体的命令，定义接收者和行为之间的弱耦合
- Invoker：负责调用命令对象，执行请求
- receiver：处理请求，任何一个类都可以成为接收者
 
![类图](/images/command_pattern_class_diagram.png)

#### 时序图 ####

![时序图](/images/command_pattern_sequence_diagram.png)

#### 代码 ####

[GitHub](https://github.com/xusx1024/DesignPatternDemoCode/tree/master/CommandPattern)

#### 分析 ####

使用频率非常高的设计模式，它可以将请求发送者与接收者解耦，请求发送者通过命令对象来间接引用请求接收者，使得系统具有更换的灵活性和可扩展性。

##### 优点 #####
- 新的命令可以很容易地添加
- 比较容易地设计一个命令队列或宏命令
- 为请求的撤销和恢复操作提供了一种设计和实现方案

##### 缺点 #####
- 可能会导致某些系统有过多的具体命令类。

#### 适用场景 ####

- 系统需要在不同的时间指定请求、将请求排队和执行请求。一个命令对象和请求的初始调用者可以有不同的生命期，换言之，最初的请求发出者可能已经不在了，而命令对象本身仍然是活动的，可以通过该命令对象去调用请求接收者，无须关心请求调用者的存在性，可以通过请求日志文件等机制来具体实现。
- 系统需要支持命令的撤销和恢复操作
- 系统需要将一组操作组合在一起形成宏命令

##### 实例 #####

- 电视遥控器
- 宏命令
- 收音机

#### 扩展 ####
- 基于敏捷开发的原则，我们在设计程序的时候，如果按照目前的需求，不使用某种模式也能很好地解决，那么我们就不要引入它，因为要引入一种设计模式并不困难，我们大可以在真正需要用到的时候再对系统进行一下，引入这个设计模式。
- 在实际操作中，可省略接收者角色，让命令对象直接实现请求而不是将工作委托给接收者。
