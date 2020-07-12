---
title: guava
date: 2018-02-04 17:48:14
excerpt: true
categories: "java"
tags: [java]
---
## 基本介绍
Guava,中文是石榴的意思 ，一个基于JDK1.6类库集合的扩展项目
<!--more-->
com.google.common.annotations：普通注解类型。 
　com.google.common.base：基本工具类库和接口。 
　com.google.common.cache：缓存工具包，非常简单易用且功能强大的JVM内缓存。 
　com.google.common.collect：带泛型的集合接口扩展和实现，以及工具类，这里你会发现很多好玩的集合。
  com.google.common.eventbus：发布订阅风格的事件总线。 
　com.google.common.hash： 哈希工具包。 
  com.google.common.io：I/O工具包。 
　com.google.common.math：原始算术类型和超大数的运算工具包。 
　com.google.common.net：网络工具包。 
　com.google.common.primitives：八种原始类型和无符号类型的静态工具包。 
　com.google.common.reflect：反射工具包。 
　com.google.common.util.concurrent：多线程工具包。
  com.google.common.xml xml操作包
  18.0 was released on August 25, 2014
maven引入
```XML
<dependency>
    <groupId>com.google.guava</groupId>
    <artifactId>guava</artifactId>
    <version>18.0</version>
</dependency>
```
## Strings和StringUtils
org.apache.commons.lang.StringUtils中方法的操作对象是java.lang.String类型的对象，是JDK提供的String类型操作方法的补充，并且是null安全的(即如果输入参数String为null则不会抛出NullPointerException，而是做了相应处理，例如，如果输入为null则返回也是null等，具体可以查看源代码)。
除了构造器，StringUtils中一共有130多个方法，并且都是static的。
[详细参考](http://blog.csdn.net/chenleixing/article/details/43068331)
```java
public static void main( String[] args )
    {
        System.out.println(Strings.isNullOrEmpty(""));//true
        System.out.println(Strings.nullToEmpty(null));//""
        System.out.println(Strings.nullToEmpty("ay"));//"ay"
        System.out.println(Strings.emptyToNull(""));//null
        System.out.println(Strings.emptyToNull("ay"));//"ay"
        System.out.println(Strings.commonPrefix("aaay", "aal"));//返回"aa"，若无返回""
        System.out.println(Strings.commonSuffix("aaay", "aal"));//返回"aac"，若无返回""
    }
```
## Basic Utilities
### Optional
1.常用静态方法：
　　Optional.of(T)：获得一个Optional对象，其内部包含了一个非null的T数据类型实例，若T=null，则立刻报错。
　　Optional.absent()：获得一个Optional对象，其内部包含了空值
　　Optional.fromNullable(T)：将一个T的实例转换为Optional对象，T的实例可以不为空，也可以为空[Optional.fromNullable(null)，和Optional.absent()等价。
2.实例方法：
　　1>. boolean isPresent()：如果Optional包含的T实例不为null，则返回true；若T实例为null，返回false
　　2>. T get()：返回Optional包含的T实例，该T实例必须不为空；否则，对包含null的Optional实例调用get()会抛出一个IllegalStateException异常
　　3>. T or(T)：若Optional实例中包含了传入的T的相同实例，返回Optional包含的该T实例，否则返回输入的T实例作为默认值
　　4>. T orNull()：返回Optional实例中包含的非空T实例，如果Optional中包含的是空值，返回null，逆操作是fromNullable()
　　5>. Set<T> asSet()：返回一个不可修改的Set，该Set中包含Optional实例中包含的所有非空存在的T实例，且在该Set中，每个T实例都是单态，如果Optional中没有非空存在的T实例，返回的将是一个空的不可修改的Set。
### Preconditions
Guava 提供两个基本 "functional" 接口:
Function<A, B>, 声明了单个方法 B apply(A input). Function 通常被期待是引用透明的-- 无副作用 -- 且 ”equals ”语义 和 equals 一致。 a.equals(b) 等同function.apply(a).equals(function.apply(b)).
Predicate<T>, 声明了单个方法 boolean apply(T input).  Predicate 通常也被期待为无副作用函数，并且”equals ”语义与equals一致。
``` java
Function<String, Integer> lengthFunction = new Function<String, Integer>() {
  public Integer apply(String string) {
    return string.length();
  }
};
Predicate<String> allCaps = new Predicate<String>() {
  public boolean apply(String string) {
    return CharMatcher.JAVA_UPPER_CASE.matchesAllOf(string);
  }
};
Multiset<Integer> lengths = HashMultiset.create(
  Iterables.transform(Iterables.filter(strings, allCaps), lengthFunction));
  ```
[引用地址](http://blog.csdn.net/east196/article/details/31371523)
### Ordering
```java
Ordering<String> byLengthOrdering = new Ordering<String>() {
  public int compare(String left, String right) {
    return Ints.compare(left.length(), right.length());
  }
};
For example, let's say you want a comparator for the class...

class Foo {
  @Nullable String sortedBy;
  int notSortedBy;
}
...that can deal with null values of sortedBy. Here is a solution built atop the chaining methods:

Ordering<Foo> ordering = Ordering.natural().nullsFirst().onResultOf(new Function<Foo, String>() {
  public String apply(Foo foo) {
    return foo.sortedBy;
  }
});
```
### Object methods
Object common methods
1.equals
Objects.equal("a", "a"); // returns true
Objects.equal(null, "a"); // returns false
Objects.equal("a", null); // returns false
Objects.equal(null, null); // returns true
2.hashCode
Objects.hashCode(Object...)&Objects.hash(Object...)
3.toString
```java
   // Returns "ClassName{x=1}"
   MoreObjects.toStringHelper(this)
       .add("x", 1)
       .toString();

   // Returns "MyObject{x=1}"
   MoreObjects.toStringHelper("MyObject")
       .add("x", 1)
       .toString();
```
4.compare/compareTo
```java
class Person implements Comparable<Person> {
  private String lastName;
  private String firstName;
  private int zipCode;

  public int compareTo(Person other) {
    int cmp = lastName.compareTo(other.lastName);
    if (cmp != 0) {
      return cmp;
    }
    cmp = firstName.compareTo(other.firstName);
    if (cmp != 0) {
      return cmp;
    }
    return Integer.compare(zipCode, other.zipCode);
  }
}
//use guava lazy
  public int compareTo(Foo that) {
     return ComparisonChain.start()
         .compare(this.aString, that.aString)
         .compare(this.anInt, that.anInt)
         .compare(this.anEnum, that.anEnum, Ordering.natural().nullsLast())
         .result();
   }
```
### Throwables
## Collections
### Immutable Collections
```
public static final ImmutableSet<String> COLOR_NAMES = ImmutableSet.of(
  "red",
  "orange",
  "yellow",
  "green",
  "blue",
  "purple");

class Foo {
  final ImmutableSet<Bar> bars;
  Foo(Set<Bar> bars) {
    this.bars = ImmutableSet.copyOf(bars); // defensive copy!
  }
}
```
Interface|	JDK or Guava?|	Immutable Version
----|------|----
Collection|	JDK	|ImmutableCollection
List|	JDK|	ImmutableList
Set	|JDK	|ImmutableSet
SortedSet/NavigableSet|	JDK	|ImmutableSortedSet
Map|	JDK|	ImmutableMap
SortedMap|	JDK	|ImmutableSortedMap
Multiset|	Guava	|ImmutableMultiset
SortedMultiset|	Guava	|ImmutableSortedMultiset
Multimap|	Guava	|ImmutableMultimap
ListMultimap|	Guava|	ImmutableListMultimap
SetMultimap|	Guava	|ImmutableSetMultimap
BiMap	|Guava|	ImmutableBiMap
ClassToInstanceMap	|Guava|	ImmutableClassToInstanceMap
Table|	Guava	|ImmutableTable
### New collection types
**Multiset**
**Multimap**
**BiMap**
**Table**
**ClassToInstanceMap**
**RangeSet**
**RangeMap**
###Utility Class
Interface	|JDK or Guava?	|Corresponding Guava utility class
----|------|----
Collection|	JDK|	Collections2
List|	JDK|	Lists
Set|	JDK	|Sets
SortedSet|	JDK|	Sets
Map|	JDK|	Maps
SortedMap|	JDK|	Maps
Queue|	JDK	|Queues
Multiset|	Guava	|Multisets
Multimap|	Guava|	Multimaps
BiMap	|Guava|	Maps
Table|	Guava|	Tables
#### Iterables
#### Lists
#### Sets
#### Maps
#### Multisets
#### Multimaps
#### Tables
### Extension Utilities
## Graphs
## Caches
## Functional Idioms
## Concurrency
## Strings
1.Joiner
```java
Joiner joiner = Joiner.on("; ").skipNulls();
return joiner.join("Harry", null, "Ron", "Hermione");
```
2.Splitter
```java
Splitter.on(',')
    .trimResults()
    .omitEmptyStrings()
    .split("foo,bar,,   qux");
 ```
 3.CharMatcher
## Networking
## Primitives
## Ranges
## I/O
## Hashing
## EventBus
## Math
## Reflection
TypeToken
```java
TypeToken<String> stringTok = TypeToken.of(String.class);
TypeToken<Integer> intTok = TypeToken.of(Integer.class);
TypeToken<List<String>> stringListTok = new TypeToken<List<String>>() {};
```

[code](https://github.com/eugenp/tutorials/tree/master/guava)
[github](https://github.com/google/guava/wiki/Release19)