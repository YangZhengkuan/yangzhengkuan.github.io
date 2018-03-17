---
layout: post
title: 并发与性能调优
tags: Interview
---

1. [高并发情况下 如何支撑大量的请求](http://blog.csdn.net/qianqian901108_/article/details/76112304)
2. [集群中几种session同步（回话同步）解决方案的比较](http://blog.csdn.net/Rongbo_J/article/details/49913365)
3. [负载均衡原理](http://blog.csdn.net/cdnight/article/details/52190316)
4. [正向代理与反向代理【总结】](http://www.cnblogs.com/Anker/p/6056540.html)
5. [如果有一个特别大的访问量，到数据库上，怎么做优化（DB设计，DBIO，SQL优化，Java优化）](https://zhidao.baidu.com/question/1672959048760987707.html)
6. [性能瓶颈调优](http://www.cnblogs.com/Lam7/p/5567359.html)
7. [如何查找 造成 性能瓶颈出现的位置，是哪个位置照成性能瓶颈](https://zhidao.baidu.com/question/1962744715444582100.html)
8. [五步定位性能瓶颈](http://blog.csdn.net/sd4015700/article/details/50358267)


### 有个每秒钟5k个请求，查询手机号所属地的笔试题(记得不完整，没列出)，如何设计算法?请求再多，比如5w，如何设计整个系统?

暂定：对移动、联通、电信数据分表（或按前n位分表），提高查询速度
高并发，参考（1. 高并发情况下 如何支撑大量的请求）

### 你的项目中使用过缓存机制吗？有没用用户非本地缓存

sql查询缓存

用户非本地缓存？

