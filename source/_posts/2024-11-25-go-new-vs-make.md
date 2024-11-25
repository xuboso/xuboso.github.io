---
title: go new vs make
date: 2024-11-25 22:00:52
tags:
  - go
---

new一般只用来分配内存空间，并且设置类型的默认值，比如int设置为0，bool设置为false
比如 `ptr := new(int)`为int类型分配内存空间，并且初始化为0，返回指向变量的指针。

make可用来数据的初始化，
比如初始化一个长度为3，capacity为6的slice，那么就应该用make

`s: = make([]int, 3, 6)`




### 参考

[https://www.codingexplorations.com/blog/understanding-the-difference-make-vs-new-in-go](https://www.codingexplorations.com/blog/understanding-the-difference-make-vs-new-in-go)




