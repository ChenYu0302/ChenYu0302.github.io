---
layout: post
title:  "版本控制系统"
date:   2019-12-18 02:03:56 +0800
categories: Programing
---

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

2. 从别处克隆：

2. 设置路径内文件过滤规则：在 `MyGitProject` 路径内建立 `.gitignore` ，打开编辑：

   1. 若过滤某个文件、某个文件类型、某个文件夹：

      ```
      *.rar
      ```

   2. 若过滤所有文件，只追踪某个文件、某个文件类型、某个文件夹

      ```
      *.*
      
      ```

