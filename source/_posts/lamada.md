---
title: Java8 Stream API
date: 2019-03-04 18:18:31
categories: "java"
tags: ["java"]
---

## Java8 Stream API
## 委托函数

## Stram生命周期
![streams](java-streams.png)
java.util.stream API
* 构建Stream的4种方式
* 流的操作类型
**Intermediate**： 一个流可以后面跟随零个或多个 intermediate 操作。如：map (mapToInt, flatMap 等)、 filter、 distinct、 sorted、 peek、 limit、 skip、 parallel、 sequential、 unordered。
**Terminal**：一个流只能有一个 terminal 操作，当这个操作执行后，流就被使用“光”了，无法再被操作。所以这必定是流的最后一个操作。如：forEach、 forEachOrdered、 toArray、 reduce、 collect、 min、 max、 count、 anyMatch、 allMatch、 noneMatch、 findFirst、 findAny、 iterator。
**Short-circuiting**：当操作一个无限大的 Stream，而又希望在有限时间内完成操作，则在管道内拥有一个 short-circuiting 操作是必要非充分条件。如：anyMatch、 allMatch、 noneMatch、 findFirst、 findAny、 limit
1. 函数式编程
2. 链式编程

More info: 
[stream-api](https://www.logicbig.com/tutorials/core-java-tutorial/java-util-stream/stream-api-intro.html)
[java8streamapi](https://developer.ibm.com/zh/articles/j-lo-java8streamapi/)
