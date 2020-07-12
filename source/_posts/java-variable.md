---
title: java 基础系列之基本类型
date: 2017-11-12 21:34:42
excerpt: true
categories: "java"
---
java有8个基础数据类型 4个整型，2个浮点型，1个布尔型和1个字符型

## 基本类型取值范围

类型 | 字节长度 | 范围
----|------|----
byte | 1个字节  | -128~127
short | 2个字节  | -32768~32767
int | 4个字节  | -2147 483 648~2147483647
long | 8个字节  | -9223372036854775808~9223372036854775807
float | 4个字节  | 大约土3.40282347E+38F(6~7位有效小数位)
double | 8个字节  |大约土1.79769313486231570E+308(15位有效小数位)

### char类型
char类型使用UTF-16字符编码
### bool类型
bool类型有两种true和false，在java中布尔类型不是数字类型，和整数0和1没有关系

### 算术操作符
![Alt text](../../../../css/images/javaoperator.jpg)

## 整型
1.Integer和int区别
int初始值为0，Integer初始值为null
*int和Integer相比都为true，因为Integer自动拆箱为int再比较。
*java在编译Integer i2 = 128的时候,被翻译成-> Integer i2 = Integer.valueOf(128);而valueOf()函数会对-128到127之间的数进行缓存
所以i4和i5指向同一对象。两个都是非new出来的Integer，如果数在-128到127之间，则是true,否则为false。
``` java
public class TestInteger {
    public static void main(String[] args) {
        int i = 128;
        Integer i2 = 128;
        Integer i3 = new Integer(128);
        //Integer会自动拆箱为int，所以为true
        System.out.println(i == i2);//true
        System.out.println(i == i3);//true
        System.out.println("**************");
        //java在编译的时候,被翻译成-> Integer i4 = Integer.valueOf(127);
        Integer i4 = 127;
        Integer i5 = 127;
        Integer i6 = 128;
        Integer i7 = 128;
        System.out.println(i4 == i5);//true
        System.out.println(i6 == i7);//false
        
        Integer ii5 = new Integer(127);
        System.out.println(i5 == ii5); //false
        
        Integer i8 = new Integer(128);
        Integer i9 = new Integer(123);
        System.out.println(i8== i9);  //false
    }
}
```
