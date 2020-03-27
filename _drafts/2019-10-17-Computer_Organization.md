---
layout: post
title:  "计算机系统"
date:   2019-10-17 02:03:56 +0800
categories: Computer System
---

> 参考
>
> * [Crash Course](https://www.youtube.com/channel/UCX6b17PVsYBQ0ip5gyeme-Q) - [计算机科学速成课](https://www.bilibili.com/video/av21376839)  [Computer Science](https://www.youtube.com/playlist?list=PL8dPuuaLjXtNlUrzyH5r6jN9ulIgZBpdo)
>* 卡内基-梅隆大学
>   * *[Computer Systems: A Programmer's Perspective](http://www.csapp.cs.cmu.edu/)* ，[深入理解计算机系统](https://item.jd.com/12006637.html)
> * 麻省理工学院
>   * [计算机导论系列课程](https://ocw.mit.edu/courses/intro-programming/)
>   * [Structure and Interpretation of Computer Programs](https://mitpress.mit.edu/sites/default/files/sicp/index.html)
>   * 计算机科学及编程导论 - 2008 

计算机系统内的所有信息，如硬盘中的文件，内存中的程序与数据，网络上的数据，都是由 0 或 1 组成的 bit （比特位）序列。每 8 个 bit 组成一个 byte （字节）。序列是有序的，有开始（低位）和结束（高位），高的是 MSB，低的是 LSB。

字节的取值有 $2^8=256$ 种，范围是 $0$ ~ $255$ ，是计算机最广泛使用的最小单位。可以用两个十六[进制](#进制)数表示（$16*16=256$），如8个位全是1的字节就是 0xFF ，如8个位里0和1间隔分布的字节就是 0xAA 。

文件的定义就是字节序列，分为文本文件和二进制文件：

1. 文本文件里的一或多个字节对应了一个字符，可以根据[字符编码](#字符编码)的规则解读为文本。
2. 二进制文件里字节与字符没有对应关系。



# C 程序的生命周期



# 字符编码

一个字节对应了一个字符是窄字符编码；多个字节对应了一个字符是宽字符编码。

# 进制

# 并行运算

并行，parallelism，指两个或更多独立的活动同时发生。。

计算机中的并发：。

多进程并发与多线程并发：

* 多进程，
* 多线程，multi-thread，。。

并发带来的优势：

* 分离关注点。最常见的例子就是并发运行用户界面和后端任务。

* 提高性能。有两种方法：任务并行，task parallelism，将大任务分成小任务，同时执行并协调好各小任务；数据并行，data parallelism，不同的数据部分上执行相同的操作。

如果出现收益比不上付出的情况，就不适用并发：

* 太简单



# 编程概念

* 变量
* 函数
* 语法糖，
* 上下文，context 
* λ表达式，
* 