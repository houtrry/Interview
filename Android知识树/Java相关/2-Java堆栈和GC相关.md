## 堆
1. 对内存的对象对所有的线程可见，对内存中的对象都可以被所有的线程访问。 
2. 堆 中对象由GC负责回收

## 栈
1. 每个线程都有一个单独的栈，为线程私有。
2. 栈中对象在方法结束后自动销毁

## 方法区
1. 被所有线程共享。 方法区中包含所有的class信息和static变量，方法信息


## GC
1. GC需要处理的区域有方法区、堆
2. 可达性分析算法（根搜索算法）： 通过一系列的名为“GC Root”的对象作为起点，从这些节点向下搜索，搜索所走过的路径称为引用链(Reference Chain)，当一个对象到GC Root没有任何引用链相连时，则该对象不可达，该对象是不可使用的，垃圾收集器将回收其所占的内存。 

## Java的四种引用
1. 强引用： 垃圾回收器绝对不会回收它。内存不足是，抛出OutOfMemoryError。
2. 软引用(Soft Reference)：如果对象由软引用，空间足够就不会回收它，空间不足才会回收。
3. 弱引用：在垃圾回收线程扫描它所管辖的内存区域的过程中，一旦发现了弱引用对象，不管当前内存是否足够，都会回收它的内存。
4. 虚引用(Phantom Reference)：在任何时候都可能被垃圾回收器回收。

## 参考
* [Java虚拟机的堆、栈、堆栈如何去理解？](https://www.zhihu.com/question/29833675)
* [Java中的堆和栈的区别](https://droidyue.com/blog/2014/12/07/differences-between-stack-and-heap-in-java/)
* [Java GC(绝对干货)](https://yq.aliyun.com/articles/91017?utm_campaign=wenzhang&utm_medium=article&utm_source=QQ-qun&2017531&utm_content=m_22117)