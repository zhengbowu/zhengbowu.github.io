---
title: java 基础系列之常用集合
date: 2018-03-04 16:32:31
categories: "java"
tags: ["java"]
---

## Java中set map list区别
[引用资料](#参考资料)
[集合结构](http://images2015.cnblogs.com/blog/820406/201605/820406-20160529134155569-877986274.png)
![Java集合类的整体框架](http://img.blog.csdn.net/20140628144205625)
**list 元素允许重复，元素有顺序。查找效率高，增删效率低（增删会引起其他元素位置改变）**
1.ArrayList : 由数组实现的List。允许对元素进行快速随机访问，但是向List中间插入与移除元素的速度很慢。ListIterator只应该用来由后向前遍历ArrayList,而不是用来插入和移除元素。因为那比LinkedList开销要大很多。
2.LinkedList : 对顺序访问进行了优化，向List中间插入与删除的开销并不大。随机访问则相对较慢。（使用ArrayList代替。）还具有下列方法：addFirst(), addLast(), getFirst(), getLast(), removeFirst() 和removeLast(), 这些方法 （没有在任何接口或基类中定义过）使得LinkedList可以当作堆栈、队列和双向队列使用。
**set  元素不能重复，重复元素会被覆盖，元素无顺序。（set中元素位置由该元素的hashCode决定的，其位置是固定的）检索效率低，增删效率高**
1.HashSet : 为快速查找设计的Set。存入HashSet的对象必须定义hashCode()。
2.TreeSet : 保存次序的Set, 底层为树结构。使用它可以从Set中提取有序的序列。
3.LinkedHashSet : 具有HashSet的查询速度，且内部使用链表维护元素的顺序（插入的次序）。于是在使用迭代器遍历Set时，结果会按元素插入的次序显示。
**map  键值对数据结构，键值唯一**
1.HashMap : Map基于散列表的实现。插入和查询“键值对”的开销是固定的。可以通过构造器设置容量capacity和负载因子load factor，以调整容器的性能。
2.LinkedHashMap : 类似于HashMap，但是迭代遍历它时，取得“键值对”的顺序是其插入次序，或者是最近最少使用(LRU)的次序。只比HashMap慢一点。而在迭代访问时发而更快，因为它使用链表维护内部次序。
3.TreeMap : 基于红黑树数据结构的实现。查看“键”或“键值对”时，它们会被排序（次序由Comparabel或Comparator决定）。TreeMap的特点在于，你得到的结果是经过排序的。TreeMap是唯一的带有    subMap()方法的Map，它可以返回一个子树。
4.WeakHashMao : 弱键(weak key)Map，Map中使用的对象也被允许释放: 这是为解决特殊问题设计的。如果没有map之外的引用指向某个“键”，则此“键”可以被垃圾收集器回收。
5.IdentifyHashMap : 使用==代替equals()对“键”作比较的hash map。专为解决特殊问题而设计。
**线程安全的集合类型**
Vector,HashTable

### 参考资料
[https://www.cnblogs.com/paddix/p/5539326.html]
[http://blog.csdn.net/ns_code/article/details/35564663]