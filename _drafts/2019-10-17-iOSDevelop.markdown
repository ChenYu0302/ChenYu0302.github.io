---
layout: post
title:  "iOS Develop"
date:   2019-10-17 02:03:56 +0800
categories: Apple
---
# 开发 iOS 应用程序

参考链接

* https://swift.org
* [Apple Developer](https://developer.apple.com)
* [Apple Developer - Documentation](https://developer.apple.com/documentation)
* [Apple Books  - The Swift Programming Language.ePub](https://books.apple.com/us/book-series/swift-programming-series/id888896989)
* [Apple Books  - Everyone can Code Series](https://books.apple.com/us/book-series/everyone-can-code/id1118575554)

* [podcasts - Stanford - Developing iOS11 Apps with Swift](https://podcasts.apple.com/cn/podcast/developing-ios-11-apps-with-swift/id1315130780)

## iOS 概述

[iOS](https://www.apple.com/ios) 是苹果公司为其移动设备所开发的操作系统，运行于 iPhone、 iPad、iPod touch 电子产品上。iOS 最初随第一代 iPhone 亮相于 2007 年，旨在设计一款移动版的 [macOS](https://www.apple.com/macos) 。所以与 macOS 一样，iOS 的操作系统核心基于 Darwin 的类 Unix 系统，属于 BSD 操作系统家族，与 macOS 的主要区别包括：

1. 平台不同，MacOS 运行于 x86-64 指令集的 intel 处理器上，iOS 运行于 ARM 指令集的苹果 A 系列处理器上；
2. iOS 应用程序经过沙盒处理，意味着它们只能修改其各个主目录中的数据，想要获取其他的各种权限，如摄像头、蜂窝数据、设备地理位置信息等，都将受到严格的控制，这一定上保护了用户的隐私以及避免了应用程序的文件碎片化。
3. 交互方式不同，macOS 上位于的架构最顶层的用户交互层称为“Cocoa”层，可以追溯到史蒂夫·乔布斯于 1985 年创办的 NeXT 电脑公司所开发的编程环境 NeXTSTEP 和 OPENSTEP，苹果计算机公司于 1996 年 12 月收购了 NeXT，将这些工作转化到了 macOS 下的 Cocoa 中，Cocoa 通过用户使用鼠标键盘与电脑进行交互操作。在 iOS 上该交互层被替换为“Cocoa Touch”层，从字面上即可知这是旨在为触摸交互而设计的。Cocoa Touch 通过识别用户在触摸屏上的各种手势作出反应，实现用户与移动设备的交互操作。

iOS 的层次结构下表所示，越往上越接近用户交互操作，越往下越接近设备底层。

| 层级                        | 功能                                          | 框架                                                         |
| --------------------------- | --------------------------------------------- | ------------------------------------------------------------ |
| Cocoa Touch<br>可可触摸层   | 主要运行 UIKit 框架，实现用户与应用程序的交互 | Multi-Touch<br>Alerts<br>Core Motion<br>Web View<br>View Hierarchy<br>Map Kit<br>Localization<br>Image Picker<br>Controls<br>Camera<br> |
| Media<br>媒体层             | 管理设备的文本、动画渲染，音视频处理等        | Core Audio<br>OpenAL<br>Audio Mixing<br>Audio Recording<br>Video Playback<br>JPEG/PNG/TIFF<br>PDF<br>Quartz (2D)<br>Core Animation<br>OpenGL ES |
| Core Services<br>核心服务层 | 提供了包括网络、位置、多线程、数据库等服务    |                                                              |
| Core OS<br>核心操作系统层   | 基本都是基于 C 语言的 Unix 接口               | OSX Kernel<br>Mach 3.0<br>BSD<br>Sockets<br>Security<br>Power Management<br>Keychain Access<br>Certificates<br>File System<br>Bonjour |

在开发 iOS 应用程序时，应该尽量使用上层的框架来代替下面的框架。因为更高层
次的框架是对底层框架基于对象的抽象。

## 开发工具

### [Swift](https://swift.org)

Swift 随苹果公司在 2014 年苹果开发者年会（WWDC）首次亮相，像 C、C++、Objective – C 编程语言一样，可以通过 LLVM 编译器，将代码编译为二进制文件，直接输给处理器高效执行；Swift语言的语法经过精心的优化，遵循规则而设计的程序阅读起来非常接近人类的自然语言。

Swift是一门面向对象编程语言，所有的类都继承于NSObject类，在类与结构体的属性与方法前加入关键字实现访问控制，包括了私有```private```、公开```public```、只读```private (set)```等，同时使用as关键字可以将实例的类型转换为其父类或子类。

Swift中的协议（protocol）为方法、属性、以及其他特定的任务需求或功能定义蓝图，类似于C++中的虚基类。协议可被类、结构体、或枚举类型采纳以提供所需功能的具体实现，称为遵循了该协议。遵循了该协议的类、结构体、或枚举类型必须编写协议的具体实现方法、属性的代码。

Swift 使用自动引用计数（ARC, Automatic Reference Counting）机制来追踪和管理应用程序的内存，这是一种自动添加内存管理功能的编译器特性。其原理为：当一个实例被创建并储存在堆内存中时，ARC会记录代码中别处对该实例的引用次数，即当前有多少指针指向该对象。当引用次数为零时，ACR认为已经没有对该实例感兴趣的代码，会自动释放类实例所占用的内存。在大多数情况下，ACR会让开发人员不需要自己考虑内存管理。然而在少数情况下，当两个对象相互引用，而外界没有对他们引用时，会造成二者的内存得不到释放，出现内存泄漏进而使应用程序奔溃。解决方法使用```weak```或```unowned```关键字为声明二者之间的引用为弱引用或无主引用。

### Xcode

集成开发环境Xcode由苹果公司推出，可用于开发苹果系统下的应用程序。iOS应用程序项目可运行于macOS下的iPhone虚拟机中，但无法测试各种硬件功能；也可以将手机用USB连接mac电脑，通过真机调试，测试蓝牙、Wi-Fi、陀螺仪、GPS等硬件功能。Xcode提供了游乐场（playground），该功能提供所编即所见的强大互动效果，可以像脚本语言一样逐条运行。Xcode还内置了Git用于代码版本控制、instrument用于测试代码性能、分析CPU、内存占用等，这些功能都提高了应用程序开发效率。

# Apple SDK

通常属于某个框架的某各类的类名都以该框架的缩写作为前缀，如：<br>
NS - NeXTSTEP 框架的缩写，Cocoa类对象大部分类型的前缀，源自于乔布斯的另一家公司NEXT。<br>
UI - UIKit 框架的简写，编写 iOS 应用程序用户交互界面。<br>
CG - Core Graphic 框架的简写，常用于绘制自定义视图，纯C的API，使用Quartz2D做引擎。<br>