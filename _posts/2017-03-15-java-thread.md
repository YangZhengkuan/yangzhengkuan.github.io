---
layout: post
title: Java Thread 知识总结
tags: Java Interview
---

1、Java创建线程之后，直接调用start()方法和run()的区别

[线程中start方法与run方法的区别-java教程](http://blog.csdn.net/u010953266/article/details/46546543)

2、常用的线程池模式以及不同线程池的使用场景

[Java线程池（ThreadPool）详解](http://www.cnblogs.com/kuoAT/p/6714762.html)

[java线程池与五种常用线程池策略使用与解析](http://blog.csdn.net/u011479540/article/details/51867886)

3、newFixedThreadPool此种线程池如果线程数达到最大值后会怎么办，底层原理。

newFixedThreadPool 创建一个定长线程池，可控制线程最大并发数，超出的线程会在队列中等待

4、多线程之间通信的同步问题，synchronized锁的是对象，衍伸出和synchronized相关很多的具体问题，
例如同一个类不同方法都有synchronized锁，一个对象是否可以同时访问。或者一个类的static构造方法加上synchronized之后的锁的影响。

[多线程通信](http://blog.csdn.net/zen99t/article/details/50837634)

5、了解可重入锁的含义，以及ReentrantLock 和synchronized的区别

6、同步的数据结构，例如concurrentHashMap的源码理解以及内部实现原理，为什么他是同步的且效率高

[JAVA HashMap(多线程)的死循环](https://coolshell.cn/articles/9606.html)

7、atomicinteger和volatile等线程安全操作的关键字的理解和使用

[AtomicInteger类的理解与使用](http://blog.csdn.net/u012734441/article/details/51619751)

8、线程间通信，wait和notify

9、定时线程的使用

10、场景：在一个主线程中，要求有大量(很多很多)子线程执行完之后，主线程才执行完成。多种方式，考虑效率。

11、进程和线程的区别

12、什么叫线程安全？举例说明

13、线程的几种状态

[Java线程的5种状态及切换(透彻讲解)](http://blog.csdn.net/pange1991/article/details/53860651)

14、并发、同步的接口或方法

[[沧海拾遗]java并发之CountDownLatch、Semaphore和CyclicBarrier](http://blog.csdn.net/yanhandle/article/details/9016329)  
[深入理解Semaphore](http://blog.csdn.net/qq_19431333/article/details/70212663)  
[Java并发编程之栅栏(CyclicBarrier)详解](http://blog.csdn.net/csujiangyu/article/details/44338307)  
[CountDownLatch的用法](https://www.jianshu.com/p/1ec1009ebab7)  
[Java线程(七)：Callable和Future](http://blog.csdn.net/ghsau/article/details/7451464)  
[Java线程之FutureTask与Future浅析](http://blog.csdn.net/zmx729618/article/details/51596414)

15、HashMap 是否线程安全，为何不安全。 ConcurrentHashMap，线程安全，为何安全。底层实现是怎么样的。

16、J.U.C下的常见类的使用。 ThreadPool的深入考察； BlockingQueue的使用。（take，poll的区别，put，offer的区别）；原子类的实现。

[【Java并发之】BlockingQueue](http://blog.csdn.net/suifeng3051/article/details/48807423)  
[LinkedBlockingQueue的put,add跟offer的区别](http://blog.csdn.net/z69183787/article/details/46986823)

17、简单介绍下多线程的情况，从建立一个线程开始。然后怎么控制同步过程，多线程常用的方法和结构

[多线程之线程同步的方法（7种）](http://www.cnblogs.com/upcwanghaibo/p/6535505.html)  
[ThreadLocal共享线程局部变量和线程同步机制的区别](http://blog.csdn.net/u012516914/article/details/39268681)

18、volatile的理解

[Java中violate关键字详解（2）？真正了解violate](http://blog.csdn.net/it_dx/article/details/70045286?locationNum=4&fps=1)

19、实现多线程有几种方式，多线程同步怎么做，说说几个线程里常用的方法
