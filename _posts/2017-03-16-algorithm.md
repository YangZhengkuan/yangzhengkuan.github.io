---
layout: post
title: 算法
tags: Interview
---

### 使用随机算法产生一个数，要求把1-1000W之间这些数全部生成。（考察高效率，解决产生冲突的问题）

1. HashSet
2. Shuffle

### 计算一个正整数的正平方根

1. 直接调用Math.sqrt()
2. 递归
```java
/**
 * Created by yzk on 2018/3/16.
 */
public class Sqrt {

    public static double sqrt(double c) {
        if (c < 0) return Double.NaN;
        if (c == 0) return 0;
        double t = c;
        double e = 1e-15;
        while (Math.abs(t - c / t) > e * t) {
            t = (t + c / t) / 2;
        }

        return t;
    }

    public static void main(String[] args) {
        System.out.println(sqrt(13));
    }
}
```

3. 对于正平方根整数部分，可以采用二分法

### [逆波兰计算器）](http://blog.csdn.net/lpveneno/article/details/54287858)

后缀表达式
```
(a+b)*(c+d)转换为ab+cd+*
```

### [Hoffman 编码](http://blog.csdn.net/sddxqlrjxr/article/details/51114809)

### [查找树与红黑树](https://www.cnblogs.com/edwinchen/p/4797055.html)

