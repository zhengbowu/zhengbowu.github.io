---
title: Spring 实战
date: 2018-03-04 16:34:14
excerpt: true
tags: ["java","spring"]
---

## Spring初步

1. Spring应用上下文
* ClasspathXmlApplicationContext --读取类路径下的XML配置文件
* FileSystemXmlApplicationContext
* XmlWEbApplicationContext --读取Web应用下的xml配置文件
2. Spring中Bean的生命周期
![bean生命周期](http://upload-images.jianshu.io/upload_images/44770-f312de031566217d.png)
3. Spring模块
![](/images/2223014C2-0.png)

4. Spring 2.5新特性
* 完全支持java6和java EE5
* 使用@AutoWired实现基于注解驱动的依赖注入和使用@Qualifier实现细粒度的自动装配控制
* 支持@Resource自动扫描使用@Component注解所标注的Spring组件
* 一个全新的基于注解驱动的Spring MVC编程模型，极大地简化了Spring Web开发
* 内嵌支持AspectJ的类加载织入

5. Spring 3.0新特性
* Spring MVC全面支持Rest
* 新的表达式语言吧Spring的依赖注入带到了一个新高度
* Spring MVC的新注解 包括@CookieValue和@RequestHeader
* 通过注解取得声明异步和调度方法
* 不再支持Java1.4

## 装配Bean
1. Spring的Bean作用域

作用域|定义
--|--
singletion | 每一个Spring容器中，一个Bean定义只有一个对象实例
prototype | 允许Bean的定义可以被实例化任意次（每次调用都创建一个实例）
request | 在一次Http请求中，每个Bean定义对应一个实例，该作用域仅限Web的Spring上下文中（Spring MVC）
session|在一次Http Session中，每个Bean定义对应一个实例，该作用域仅限Web的Spring上下文中（Spring MVC）
global-session|在一个全局Http Session中，每个Bean定义对应一个实例，该作用域仅限Portlet上下文中才有效

## Spring XML配置

## Spring AOP

## Spring 数据库

## Spring 事务

## Spring MVC

## Spring WebFlow






