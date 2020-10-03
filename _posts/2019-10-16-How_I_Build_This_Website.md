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

此个人网站基于[Jekyll](https://jekyllrb.com)框架搭建。教程资源参见[官方文档逐步教程](https://jekyllrb.com/docs/step-by-step/01-setup/)、[Mike Dane](https://www.youtube.com/channel/UCvmINlrza7JHB1zkIOuXEbw) - [Jekyll - Static Site Generator Tutorial](https://www.youtube.com/playlist?list=PLLAZ4kZ9dFpOPV5C5Ay0pHaa0RJFhcmcB)。

搭建开发环境，参见[官网安装](https://jekyllrb.com/docs/installation)，需要Ruby、Jekyll。

安装 `Ruby >= 2.4.0`，[Ruby](https://www.ruby-lang.org/zh_cn/)是用于开发Jekyll的编程语言。macOS自带Ruby，可以在终端输入`ruby -v` 查看可执行的Ruby版本，输入`which ruby`查看当前可执行的Ruby路径。对于macOS Catalina，系统自带有位于[`/usr/bin/ruby`](/usr/bin/ruby)的`Ruby 2.6.3`。[gem](https://jekyllrb.com/docs/ruby-101/#gems)是Ruby项目封装包，Jekyll框架、Jekyll的各种主题和插件都是gem。。在[`/Library/Ruby/Gems`](/Library/Ruby/Gems)可查看全局系统安装了哪些gem。

`gem install jekyll bundler`命令安装Jekyll gem和Bundler gem。[Bundler](https://jekyllrb.com/docs/ruby-101/#bundler)作用是提供一个恒定的环境，但不是必须的，[Bnndler与Jekyll一起使用](https://jekyllrb.com/tutorials/using-jekyll-with-bundler/)可以保证环境依赖无误。Jekyll项目下的[`./Gemfile`](https://jekyllrb.com/docs/ruby-101/#gemfile)文档记录了所依赖的gem，`bundle install`命令从网络安装`./Gemfile`内要求的gem到全局系统，也可以进阶地[自定义Bundler安装路径](https://jekyllrb.com/tutorials/using-jekyll-with-bundler/#configure-bundler-install-path)；随后对于Jekyll命令（如`jekyll build`）加上 `bundle exec` 前缀（如`bundle exec jekyll build`），会在Bundler的gem环境下运行此Jekyll命令。

Jeykll通过**命令行**实现各种操作，参见[官网命令行使用](https://jekyllrb.com/docs/usage/)。

**新建项目。**`jekyll new myblog`命令用于在当前路径创建一个名为“myblog”的 Jekyll 项目，会自带`./Gemfile`。

**生成网站。**`jekyll build`命令单次生成一个`./_site/`内的静态网站，可直接放到服务器上部署。`jekyll serve`命令生成一个会根据`./_post/`内文档更新而实时同步`/_site/`文件夹的本地服务器接口，`jekyll serve --`命令则项目内任何文件被修改都会实时同步。

编写博客。`_post`文件夹存放发布的Markdown文档，会随着生成网站命令被转成`_site`文件夹下的 .html 网页。 _draft 文件夹存放草稿 Markdown ， `jekyll serve --draft`命令可生成草稿网页。位于 Markdown 文档开头的[前言 front matter](https://jekyllrb.com/docs/front-matter/)包含了页面的各种键值对。

通过`./_config.yml`文档或命令的参数，控制生成网站的各设置。参见[Configuration](https://jekyllrb.com/docs/configuration/)。

配置Markdown选项，参见[官网 Markdown 选项](https://jekyllrb.com/docs/configuration/markdown/)。Jekyll 使用 [kramdown](https://kramdown.gettalong.org/index.html)  作为 Markdown 渲染引擎。由于我使用 [Typora](https://typora.io/) 作为 markdown 编辑器，故要求把 Karmdown 配置成生成的网页与 [Typora](https://typora.io/) 的查看有相同效果。

1. 实现 [GitHub Favored Markdown, GFM](https://github.github.com/gfm/) 主题外观。
2. 实现 [MathJax](https://www.mathjax.org/) 作为数学公式渲染引擎。 

新建的Jekyll项目使用[minima](https://github.com/jekyll/minima)作为默认的主题，会安装`./Gemfile`里默认的Jekyll主题 gem[主题 gem](https://jekyllrb.com/docs/themes/#understanding-gem-based-themes) ，`open $(bundle info --path minima)` 命令访问项目所用主题的 gem 文件夹。默认主题是 `m` ，输入 `c` 命令。使用 [Liquid](https://jekyllrb.com/docs/liquid/) 语言，在 `.html` 中嵌入分支/循环。

1. 设计页面布局。`_layout` 文件夹。默认的 主题 `default.html` 和``两种布局，在此文件夹。

2. 设计页面成员。`_include` 文件夹。

   部署网站。部署到 GitHub Page 或 Gitee Page。将 _site 文件夹作为根目录拷贝到服务器即可。

`jekyll new-theme`创建一个主题基本框架，在此基础上设计个性化主题，最后打包成gem发行出去。

------

测试Markdown 效果：

# 一级标题

## 二级标题

### 三级标题

#### 四级标题

##### 五级标题

###### 六级标题

**加粗**

*斜体*

***加粗斜体***

<u>下划线</u>

~~删除线~~

[苹果官网](https://www.apple.com/)

[谷歌官网][]

[谷歌官网]: https://www.google.com	"谷歌"

苹果[^1] 在 2019 年发布了 iPhone 11 。

[^1]: 总部位于美国加州库比蒂诺的跨国科技公司

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

