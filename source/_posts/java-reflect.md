---
title: java 基础系列之反射
date: 2017-11-12 21:34:42
categories: "java" 
tags: ["java","反射"]
---
在java.lang.reflect包中有3个类 Field类，Method类和Constructor类

## Class对象
每个类都有一个Class对象
``` bash
Object obj=new Person();
Class cl=obj.getClass();
or
Class cl2=Class.forName(className);
```
### 对象的构造
``` bash
无参构造
Class cl3=Class.forName("Person");
Object obj=cl3.newInstance();
/*已知构造函数参数情况下*/
Constructor constr=cl3.getConstructor(int.Class);
Object obj=constr.newInstance(33);
```
### 变量的获取和设置

``` bash
Object obj=new Person();
for(Field f:obj.getClass().getDeclaredFields()){
	f.setAccessible(true)//在使用私有的Field和Method对象之前，使用setAccessible方法解锁
	Object val=f.get(obj);
	System.out.println(f.getName()+":"+val);

	f.set(obj,val+"new");
}
```

### 方法调用

``` bash
Class cl4=Class.forName("Person");
Method m=cl4.getDeclareMethod("getName");
Object rel=m.invoke(obj,arg1,arg2,...)
```

### 获取JavaBean属性

``` bash
Class cl5=...;
BeanInfo info=Introspector.getBeanInfo(cl5);
PropertyDescriptor[] props=info.getPropertyDescriptors();
```
对给定的PropertyDescriptor，通过调用getName()和getPropertyType()方法可以获取属性的名称和类型。

More info: [Class](https://docs.oracle.com/javase/7/docs/api/java/lang/Class.html)