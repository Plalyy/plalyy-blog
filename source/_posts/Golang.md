---
title: Golang
date: 2023-06-07 00:10
category: 技术
---

Go 学习

<!--more-->

# GMP 模型

推荐文章：[GMP模型](http://go.cyub.vip/gmp/gmp-model.html)

这个文章看一遍就对 GMP 模型了解差不多了，本质是一种混合线程模型(N:M)，很好处理了协程(用户级线程)和系统级线程的关系，既减少上下文切换，又充分利用线程的CPU调度。模型的两个极端分别是用户级线程模型(N:1)和内核级线程模型(1:1)。

值得看的地方：
(1). M(内核级线程)在LRQ和GRQ(RQ: run queue)找不到G时，如何从其他MP偷取G(work stealing)
(2). G因系统调用阻塞时，M和P解除关系，P寻找空闲M或新建；G因I/O等原因时，不阻塞M而是挂起？这块可以看下源码实现 
(3). 全局有M0，每个M都G0，分别做了什么事情
(4). 数据结构了解

# Golang 中的设计模式

整体结构 interface struct method

链式调用

# Channel 和 Map 等

# 锁