---
layout: blog
title: 网站开发
permalink: /blog/WebsiteDevelopement.html
author: 陈宇
date: 2020-02-05 00:00:00 +0800
categories: 开发
tags: 开发 计算机网络
---

此博客用于记录学习网页开发。

> 参见
>
> * [Mike Dane](https://www.youtube.com/channel/UCvmINlrza7JHB1zkIOuXEbw) - [Web Development](https://www.youtube.com/channel/UCvmINlrza7JHB1zkIOuXEbw/playlists?view=50&sort=dd&shelf_id=3)，快速入门 HTML & CSS & JavaScript。
> * [mmtuts](https://www.youtube.com/channel/UCzyuZJ8zZ-Lhfnz41DG5qLw) -[HTML and CSS Tutorials](https://www.youtube.com/watch?v=TKYsuU86-DQ&list=PL0eyrZgxdwhwNC5ppZo_dYGVjerQY3xYU) / [JavaScript Tutorials](https://www.youtube.com/watch?v=ItYye9h_RXg&list=PL0eyrZgxdwhxNGMWROnaY35NLyEjTqcgB) ，HTML & CSS & JavaScript 视频教程。
> * [Learn X in Y minutes](https://learnxinyminutes.com) : [html](https://learnxinyminutes.com/docs/html/) / [css](https://learnxinyminutes.com/docs/css/) / [javascript](https://learnxinyminutes.com/docs/javascript/) ，编程语言语法速成。
> * *[Learning Web Design, 5th Edition, ISBN: 978-1-491-96020-2](https://www.oreilly.com/library/view/learning-web-design/9781491960196/)* ，Web 开发完整教程。
> * [W3School](https://www.w3schools.com)，全世界最大的 Web 开发网站。
> * [W3School.cn](https://www.w3school.com.cn/) ，中文版。
> * [MDN Web 文档](https://developer.mozilla.org/zh-CN/docs/Learn) ，Web 开发社区，每个人都可学习与贡献。

前端，frontend，面向浏览器开发，负责网页多媒体；后端，backend，面向服务器开发，负责应用程序和数据库。 

Internet，英特网；web，。

# HTML - 内容与结构

HTML，Hyper Text Markup Language，超文本标记语言，后缀名 `.html` 的文本文件，浏览器打开后生成网页。

标记语言不是编程语言，只有结构描述，没有逻辑。

由 `<TagName>TagValue<\TagName>` 的标签结构，多级嵌套而构成，描述了网页的内容。

标签名不区分大小写。

`index.html` 会被认为是网站的主页。参见 [理解网站的 Index.html 页面](https://www.lifewire.com/index-html-page-3466505) 。

使用 `<head>` 、 `<main>` 、 `<article>` 等标签去组织网页内容是一个很好的习惯，这有助于搜索引擎分析网页的内容。

标签可以添加属性（attribute）键值对，赋予某些特性，如 `` 。

Block 类型的元素各自占据一整行，典型如 `<div>`；inline 类型的元素排布在一行内，典型如 `<span>`。

# CSS - 外观

Sass & Scss

Less

## Web 字体

> 参见
>
> 

# JavaScript - 交互

起初，在网站开发领域，轻量化的 JavaScript 被设计成：重量化的 Java 的补充，顾名。

在 HTLM 文件中 `<script>` 标签调用 JavaScript 脚本，用两种方式

1. 直接在
2. ，调用外部文件 `.js` 文件。

## 语法

> 特点：
>
> * 动态语言——不编译，从头到尾一步一步逐行执行脚本。
>
> * 弱类型——无需定义变量和函数返回值的类型。
> * 

```javascript
// C风格单行注释
/*
 C风格多行注释
*/

doSometing(); // 语句(statement)以分号结尾
doSometing() // 默认也会在换行处插入隐式分号，但不建议

/* --- 内置类型 --- */
3; 1.5;// 所有的数值类型都是浮点数（64位 IEEE 754 双精度浮点）
5/0 // = Nan。
true; false;// 布尔型
"Mike"; // 字符串类型

/* --- 定义 --- */
var myAge = 23; // 变量
myAge = 23 + 1; // 变量可变
let myBirthday = 3.2; // 常量，不可变
[]// 方括号-数组(array)。作为各种对象的顺序集合。
// 通过索引访问元素

/* --- 对象 ---*/

{}// 花括号-对象(object)。


/* --- 分支 ---*/
/* --- 循环 ---*/
/* --- 函数 ---*/
```

> 扩展
>
> 1. Anime.js
> 2. Howler.js
> 3. Chart.js
> 4. Reveal.js
> 5. Three.js
> 6. Pixi.js
> 7. Video.js

## Node.js

此项目提供了面向 Google Chrome V8 引擎的独立运行时环境。

## jQuery

jQuery 官方网站 [jQuery.com](https://jquery.com) ，是框架（库）。

## React

# SVG - 可缩放矢量图形

SVG ，与 HTML 对应。