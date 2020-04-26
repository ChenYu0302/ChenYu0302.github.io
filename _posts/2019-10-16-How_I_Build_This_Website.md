---
layout: blog
title:  这个网站是如何搭建的？
permalink: /blog/HowDoIBuildThisWebsite.html
author: 陈宇
lang: zh-cn
date: 2019-10-16 00:00:00 +0800
categories: 开发
tags: 计算机网络
---

此个人网站基于 [Jekyll](https://jekyllrb.com) 框架搭建。

------

参见 [官方文档逐步教程](https://jekyllrb.com/docs/step-by-step/01-setup/) 、[Mike Dane](https://www.youtube.com/channel/UCvmINlrza7JHB1zkIOuXEbw) - [Jekyll - Static Site Generator Tutorial](https://www.youtube.com/playlist?list=PLLAZ4kZ9dFpOPV5C5Ay0pHaa0RJFhcmcB)，逐步搭建：

1. 搭建开发环境，参见 [官网 macOS 环境搭建](https://jekyllrb.com/docs/installation/macos/) ：
   1. 安装 `Ruby >= 2.4.0` 。[Ruby](https://www.ruby-lang.org/zh_cn/) 是用于开发 Jeykll 框架的编程语言。macOS 自带 Ruby ，可以在终端输入 `ruby -v` 查看可执行的 Ruby 版本，输入 `which ruby` 查看可执行的 Ruby 路径。
      - 对于 Catalina ，系统自带 `Ruby 2.6.3` 。
      - 对于 Mojave 及其更早的操作系统，系统自带位于 [/usr/bin/ruby](/usr/bin/ruby) 的 `Ruby 2.3.7`，不满足版本要求。在安装了 [homebrew](https://brew.sh) 的前提下， `brew install ruby` 命令更新 Ruby。最新的 Ruby 安装到 [/usr/local/lib/ruby/gems](/usr/local/lib/ruby/gems) 路径。这并不会覆盖系统自带的 `Ruby` 版本，避免了覆盖带来的兼容性问题。每次使用命令行前， `export PATH=/usr/local/opt/ruby/bin:$PATH` 命令添加新 Ruby 的环境变量，再输入 `ruby -v` 就可查看到可执行的 Ruby 是最新版本。
   3. 安装 Jeykll。`gem install jekyll bundler` 命令安装 Jekyll gem。[gem](https://jekyllrb.com/docs/ruby-101/#gems) 是 ruby 项目封装包，Jekyll 框架、Jekyll 的各种主题和插件都是 gem。在 Ruby 安装路径下可查看本地安装了哪些 gem。
   
2. 新建项目。参见 [官网命令行使用](https://jekyllrb.com/docs/usage/)。`jekyll new myblog` 命令用于在当前路径创建一个名为 myblog 的 Jekyll 项目。对于操作命令加上 `bundle exec` 前缀会通过 bundler 使用项目里 [Gemfile](https://jekyllrb.com/docs/ruby-101/#gemfile) 内记录所需的 gems ，避免了使用错误版本的 gems，这需 `bundle install` 命令从网络安装 Gemfile 内的 gem。`bundle exec jekyll build`  命令单次生成一个 site 文件夹下的静态网站，可直接放到服务器上部署。 `bundle exec jekyll serve`  命令生成一个会实时更新的本地服务器接口（_site 文件夹也会随着更新）。

4. 编写博客。_post 文件夹存放发布的 Markdown，会随着生成网站命令被转成 _site 文件夹下的 .html 网页。 _draft 文件夹存放草稿 Markdown ，输入 `bundle exec jekyll serve --draft` 可生成草稿网页。位于 Markdown 文档开头的 [前言 front matter](https://jekyllrb.com/docs/front-matter/) 包含了页面的各种键值对，我的设置如下

   > layout: 在 _layout 选定的布局
> title:  页面的标题
   > englishtitle: 我自定义的页面的英文标题
   > permalink: 页面的 url 连接
   > author: 作者名字
   > lang: 页面语言
   > date: 日期
   > categories: 分类
   > tags: 标签

6. 配置 Markdown 选项。参见 [官网 Markdown 选项](https://jekyllrb.com/docs/configuration/markdown/) 。Jeykll 使用 [kramdown](https://kramdown.gettalong.org/index.html)  作为 Markdown 渲染引擎。由于我使用 [Typora](https://typora.io/) 作为 markdown 编辑器，故要求把 Karmdown 配置成生成的网页与 [Typora](https://typora.io/) 的查看有相同效果。
  
   1. 实现 [GitHub Favored Markdown, GFM](https://github.github.com/gfm/) 主题外观。
   2. 实现 [MathJax](https://www.mathjax.org/) 作为数学公式渲染引擎。 
   
5. 重写/设计主题。新建项目默认使用名为 minima 的[主题 gem](https://jekyllrb.com/docs/themes/#understanding-gem-based-themes) ，`open $(bundle info --path minima)` 命令访问项目所用主题的 gem 文件夹。默认主题是 `m` ，输入 `c` 命令。使用 [Liquid](https://jekyllrb.com/docs/liquid/) 语言，在 `.html` 中嵌入分支/循环。

   1. 设计页面布局。`_layout` 文件夹。默认的 主题 `default.html` 和 `` 两种布局，在此文件夹
   2. 设计页面成员。`_include` 文件夹。

6. 。

7. 部署网站。

   1. 部署到 GitHub Page 。
   2. 将 _site 文件夹作为根目录拷贝到服务器即可。

------

通用 Markdown 效果：

------

# 一级标题

## 二级标题

### 三级标题

#### 四级标题

##### 五级标题

###### 六级标题

------

**加粗**

*斜体*

***加粗斜体***

<u>下划线</u>

~~删除线~~

[苹果](https://www.apple.com/)

[谷歌][]

[谷歌]: https://www.google.com

苹果[^1] 在 2019 年发布了 iPhone 11 。

[^1]: 计算机公司

------

表格

| 第一列靠右表头 | 第一列居中表头 | 第三列靠左表头 |
| -------------: | :------------: | :------------- |
|       靠右内容 |    居中内容    | 靠左内容       |

------

代码块

```c
#include "stdio.h"

int main()
{
  printf("Hello World!");
  return 0;
}
```

------

引用

> 第一层引用
>
> > 第二层引用
> >
> > > 第三层引用
> > >
> > > > 第四层引用
> > > >
> > > > > 第五层引用
> > > > >
> > > > > > 第六层引用

------

无序列表

*   Red
*   Green
*   Blue

* 一级缩进
  * 二级缩进
    * 三级缩进
      * 四级缩进
        * 五级缩进
          * 六级缩进

------

有序列表

1.  Red
2. 	Green
3.	Blue

1.  一级缩进
    1.  二级缩进
        1.  三级缩进
            1.  四级缩进
                1.  五级缩进
                    1.  六级缩进

------

任务列表

- [ ] incomplete
- [x] completed

------

MathJax 公式块
$$
\mathbf{V}_1 \times \mathbf{V}_2 =  \begin{vmatrix}\mathbf{i} & \mathbf{j} & \mathbf{k} \\\frac{\partial X}{\partial u} &  \frac{\partial Y}{\partial u} & 0 \\\frac{\partial X}{\partial v} &  \frac{\partial Y}{\partial v} & 0 \\\end{vmatrix}
$$

------

