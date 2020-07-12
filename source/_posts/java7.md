---
title: java7
date: 2018-03-04 16:28:31
categories: "java"
tags: ["java"]
---

## java7 Coin

1.swicth支持String类型,原来只支持byte,char,short,int,char enum
2.更强的数值文本表示法
    int x=Integer.pareeInt("1100110",2)//二进制转十进制 java 6
    int x=0b1100110//java 7
3.数字中的下划线
例如：long along=2_147_483_648L;
4.catch多个异常进行处理
5.try-with-resources(TWR)
    try(OutputStream out=new FileOutputStream(file);
        Input Stream is=url.openStream()){
            byte[] buf=new byte[4096];
            int len;
            while((len=is.read(buf))>0){
                out.write(buf,0,len);
            }
        }
6钻石语法
    Map<Integer,Map<String,String>> item6=new HashMap<Integer,Map<String,String>>();//java 6
    Map<Integer,Map<String,String>> item7=new HashMap<>();
## java7新I/O即NIO.2
1.Path对象
2.WatchService对象
3.异步I/O
## java7 DI
1.@Inject注解可出现在3种类成员之前
构造器，方法，属性
    @Inject public MurmurMessage(Header header,Content content){
        this.header=header;
        this.content=content;
    }
2.Qualifier
3.Guice DI 框架和Spring
## java 并发
1.synchronized
2.volatile
在java1.0就已经把valatile作为关键字了，它是一种简单的对象域同步处理方法，包括原始类型。一个volatile遵循如下规则：
*线程所见的值在使用之前总会从主内存中再读出来
*线程所写的值总会在指令完成前被刷回到主内存中
3.ConcurrentHashMap和Atomic
## 类文件和字节码
![类加载过程示意图](http://img.blog.csdn.net/20160308184325593)
1.类加载器
 *根类加载器
 *扩展类加载器
 *应用类加载器
 *自定义加载器
## 性能调优

## 函数式编程 备选JVM语言
1.Groovy
2.Scala
3.Clojure











