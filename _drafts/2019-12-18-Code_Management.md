---
layout: post
title:  "代码管理"
permalink: /blog/CodeManagement.html
author: 陈宇
date:   2019-10-17 02:03:56 +0800
categories: 开发
tags: 音乐 创作
---

# 版本控制系统 

## Git 分布式

# Git

> 参考
>
> * [git - 简明指南](https://www.runoob.com/manual/git-guide/)
>
> * [Pro Git Book](https://git-scm.com/book/zh/v2) 

[Git](https://git-scm.com/) 是一种分布式版本控制技术，基于哈希值校验的原理，类似于“快照”，记录文件发生的修改，可在不同的版本之间实现查看修改、撤销、分支、合并等操作，参考。

## 命令行工作流程

1. 安装与配置
   [下载](https://git-scm.com/downloads)安装 Git，支持 Windows/macOS/Linux 操作系统。

2. 获取一个 git  repository 管理的路径：

   1. 在本地建立：`mkdir MyGitProject` ， `cd .\MyGitProject\` ， `git init` 。

3. 从别处克隆：

4. 设置路径内文件过滤规则：在 `MyGitProject` 路径内建立 `.gitignore` ，打开编辑：

   1. 若过滤某个文件、某个文件类型、某个文件夹：

      ```
      *.rar
      ```

   2. 若过滤所有文件，只追踪某个文件、某个文件类型、某个文件夹

      ```
      *.*
      
      ```



# doxygen 代码文档生成工具

> 参考
>
> [Arpan Sen - 学习用 doxygen 生成源码文档](https://www.ibm.com/developerworks/cn/aix/library/au-learningdoxygen/index.html)
>
> [许振坪 - 绘制函数调用图（call graoh）（4）：doxygen + graphviz](https://blog.csdn.net/benkaoya/article/details/79763668)
>
> [Mirosoft - Code maps and dependency diagrams](https://docs.microsoft.com/en-us/visualstudio/modeling/visualize-code?view=vs-2019)

[doxygen](http://www.doxygen.nl/index.html) ，支持多种编程语言，支持 Windows/macOS/Linux 。

# graphviz 导图绘制

[graphviz](http://www.graphviz.org/) 用于绘制导图，

## doxygen + graphviz 绘制程序关系导图



开发者经常需要分析较为复杂的程序项目，理解其中的代码继承、调用等关系。对于 IDE ，Microsoft Visual Studio 和 Apple Xcode 都提供了可视化分析代码依赖的功能。