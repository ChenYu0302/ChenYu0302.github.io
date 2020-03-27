---
layout: blog
title:  iOS macOS 程序开发
englishtitle:  iOS macOS App Development Summary
date:   2019-10-17 02:03:56 +0800
categories: Apple
---
> 参见
>
> [Apple Developer](https://developer.apple.com) ，苹果开发者官网。
>
> [Apple Developer - Documentation](https://developer.apple.com/documentation) ，苹果开发手册文档。
>
> [Apple Books  - Everyone can Code Series](https://books.apple.com/us/book-series/everyone-can-code/id1118575554) ，苹果发起的人人可编程项目。

# 斯坦福大学 iOS 开发学习笔记

此学习笔记用于记录坦福大学工程学院 2017 年秋季 CS193P 公开课 —— [Swift 开发 iOS 11  应用程序](https://podcasts.apple.com/cn/podcast/developing-ios-11-apps-with-swift/id1315130780) 。此课程共计 17 节长课， 3 节知识扩展短课。

L1：介绍 iOS 、Xcode、Siwft 。

​	iOS 系统从上至下的四个层级 Cocoa Touch - Media - Core Services - Core OS 。

L2：MVC 设计模式

L3：Swift 编程语言

L4：Siwft 编程语言补充

L5：

L6：

L7：



L8：



L9：



L10：多线程与自动布局



L11：拖放、列表、集合。



L12：



L5：



L5：



# iOS / macOS 开发概念

[iOS](https://www.apple.com/ios) 是苹果公司为其移动设备所开发的操作系统，运行于 iPhone、iPad、iPod touch 电子产品上。iOS 最初随第一代 iPhone 亮相于 2007 年，旨在设计一款移动版的 [macOS](https://www.apple.com/macos) 。与 macOS 一样，iOS 的操作系统核心基于 Darwin 的类 Unix 系统，属于 BSD 操作系统家族，与 macOS 的主要区别包括：

1. **平台不同**。MacOS 运行于 x86-64 指令集的 intel 处理器上，iOS 运行于 ARM 指令集的苹果 A 系列处理器上；
2. **更为严格**。iOS 应用程序经过沙盒处理，意味着它们只能修改其各个主目录中的数据，想要获取其他的各种权限，如摄像头、蜂窝数据、设备地理位置信息等，都将受到严格的控制，这一定上保护了用户的隐私以及避免了应用程序的文件碎片化。
3. **交互不同**。macOS 上位于的架构最顶层的用户交互层称为“Cocoa”层，可以追溯到乔布斯于 1985 年创办的 NeXT 电脑公司所开发的编程环境 NeXTSTEP 和 OPENSTEP，苹果计算机公司于 1996 年 12 月收购了 NeXT，将这些工作转化到了 macOS 下的 Cocoa 中，Cocoa 通过用户使用鼠标键盘与电脑进行交互操作。在 iOS 上该交互层被替换为“Cocoa Touch”层，从字面上即可知这是旨在为触摸交互而设计的。Cocoa Touch 通过识别用户在触摸屏上的各种手势作出反应，实现用户与移动设备的交互操作。

iOS 的层次结构下表所示，越往上越接近用户交互操作，越往下越接近设备底层。

| 层级                              | 功能                                          | 框架                                                         |
| --------------------------------- | --------------------------------------------- | ------------------------------------------------------------ |
| **Cocoa Touch**<br />可可触摸层   | 主要运行 UIKit 框架，实现用户与应用程序的交互 | Multi-Touch<br>Alerts<br>Core Motion<br>Web View<br>View Hierarchy<br>Map Kit<br>Localization<br>Image Picker<br>Controls<br>Camera<br> |
| **Media**<br />媒体层             | 管理设备的文本、动画渲染，音视频处理等        | Core Audio<br>OpenAL<br>Audio Mixing<br>Audio Recording<br>Video Playback<br>JPEG/PNG/TIFF<br>PDF<br>Quartz (2D)<br>Core Animation<br>OpenGL ES |
| **Core Services**<br />核心服务层 | 提供了包括网络、位置、多线程、数据库等服务    |                                                              |
| **Core OS**<br>核心操作系统层     | Unix 内核，为上层提供 C 语言的接口。          | OSX Kernel<br>Mach 3.0<br>BSD<br>Sockets<br>Security<br>Power Management<br>Keychain Access<br>Certificates<br>File System<br>Bonjour |

在开发 iOS 应用程序时，应该尽量使用上层的框架来代替下面的框架。因为更高层次的框架是对底层框架基于对象的抽象封装。

命名规范。



# Swift 编程语言

> 参见
>
> [Swift.org](https://swift.org) ，Swift 编程语言社区网站。
>
> [Swift 编程语言](https://www.cnswift.org) ，Swift.org 的同步中文翻译。

Swift 随苹果公司在 2014 年苹果开发者年会（WWDC）首次亮相。

与 C、C++、Objective – C ，共属于 C 语言家族。通过 LLVM 编译器，将代码文本编译为二进制文件，直接输给处理器高效执行；Swift语言的语法经过精心的优化，遵循规则而设计的程序阅读起来非常接近人类的自然语言。

Swift是一门面向对象编程语言，所有的类都继承于 NSObject 类，

[The Basics](https://docs.swift.org/swift-book/LanguageGuide/TheBasics.html#) [基础内容](https://www.cnswift.org/the-basics)

> 变量与常量
>
> ```swift
> let maximumNumberOfLoginAttempts = 10	// 声明一个常量，不可重新赋值。
> var currentLoginAttempt = 0				// 声明一个变量，可重新赋值。
> var x = 0.0, y = 0.0, z = 0.0			// 在同一行内声明多个变量
> 
> var welcomeMessage: String		// 声明变量时指明此变量的类型，并不赋值。
> welcomeMessage = "Hello"		// 后期可以用字符串值赋值。
> var red, green, blue: Double	// 在同一行内声明同类型的多个变量
> 
> let π = 3.14159			// Unicode 字符可以作为变量名与常量名
> let 你好 = "你好世界"		// 不可有空格、数学、
> let 🐶🐮 = "dogcow"		// 用(`)包围的 Swift 关键字也可以，但不建议。
> 
> print(你好)	// print 函数用于打印常量与变量
> ```
>
> 注释
>
> ```swift
> // 与C家族语言一样，这是行注释。
> 
> /*
> 与C家族语言一样，
> 这是块注释。
> */
> ```
>
> 分号
>
> 整数
>
> 浮点数
>
> 类型安全与类型推断
>
> 数值型字面值
>
> 类型别名
>
> ```Swift
> typealias AudioSample = UInt16
> ```
>
> bool value 布尔值
>
> tumple 元组
>
> error handling 错误处理
>
> 断言和先决条件

[Basic Operators](https://docs.swift.org/swift-book/LanguageGuide/BasicOperators.html) [基本运算符](https://www.cnswift.org/basic-operators)

[Strings and Characters](https://docs.swift.org/swift-book/LanguageGuide/StringsAndCharacters.html) [字符串和字符](https://www.cnswift.org/strings-and-characters)

[Collection Types](https://docs.swift.org/swift-book/LanguageGuide/CollectionTypes.html) [集合类型](https://www.cnswift.org/collection-types)

[Control Flow](https://docs.swift.org/swift-book/LanguageGuide/ControlFlow.html) [控制流](https://www.cnswift.org/control-flow)

[Functions](https://docs.swift.org/swift-book/LanguageGuide/Functions.html) [函数](https://www.cnswift.org/functions)

[Closures](https://docs.swift.org/swift-book/LanguageGuide/Closures.html) [闭包](https://www.cnswift.org/closures)

[Enumerations](https://docs.swift.org/swift-book/LanguageGuide/Enumerations.html) [枚举](https://www.cnswift.org/enumerations)

[Structures and Classes](https://docs.swift.org/swift-book/LanguageGuide/ClassesAndStructures.html) [类和结构体](https://www.cnswift.org/classes-and-structures)

[Properties](https://docs.swift.org/swift-book/LanguageGuide/Properties.html) [属性](https://www.cnswift.org/properties)

[Methods](https://docs.swift.org/swift-book/LanguageGuide/Methods.html) [方法](https://www.cnswift.org/methods)

[Subscripts](https://docs.swift.org/swift-book/LanguageGuide/Subscripts.html) [下标](https://www.cnswift.org/subscripts)

> 
>
> ```swift
> // 内置集合类型的下标运算符用来访问成员元素
> someArray[index]		// 依据索引访问数组的成员元素
> someDictionary[key]		// 依据键访问字典的成员元素
> ```
>
> 





[Inheritance](https://docs.swift.org/swift-book/LanguageGuide/Inheritance.html) [继承](https://www.cnswift.org/inheritance)

[Initialization](https://docs.swift.org/swift-book/LanguageGuide/Initialization.html) [初始化](https://www.cnswift.org/initialization)

[Deinitialization](https://docs.swift.org/swift-book/LanguageGuide/Deinitialization.html) [反初始化](https://www.cnswift.org/deinitialization)

[Optional Chaining](https://docs.swift.org/swift-book/LanguageGuide/OptionalChaining.html) [可选链](https://www.cnswift.org/optional-chaining)

[Error Handling](https://docs.swift.org/swift-book/LanguageGuide/ErrorHandling.html) [错误处理](https://www.cnswift.org/error-handling)

[Type Casting](https://docs.swift.org/swift-book/LanguageGuide/TypeCasting.html) [类型转换](https://www.cnswift.org/type-casting)

同时使用 as 关键字可以将实例的类型转换为其父类或子类。

[Nested Types](https://docs.swift.org/swift-book/LanguageGuide/NestedTypes.html) [内嵌类型](https://www.cnswift.org/nested-types)

[Extensions](https://docs.swift.org/swift-book/LanguageGuide/Extensions.html) [扩展](https://www.cnswift.org/extensions)

[Protocols](https://docs.swift.org/swift-book/LanguageGuide/Protocols.html) [协议](https://www.cnswift.org/protocols)

协议（protocol）为方法、属性、以及其他特定的任务需求或功能定义蓝图，类似于C++中的虚基类。协议可被类、结构体、或枚举类型采纳以提供所需功能的具体实现，称为遵循了该协议。遵循了该协议的类、结构体、或枚举类型必须编写协议的具体实现方法、属性的代码。

[Generics](https://docs.swift.org/swift-book/LanguageGuide/Generics.html) [泛型](https://www.cnswift.org/generics)

[Opaque Types](https://docs.swift.org/swift-book/LanguageGuide/OpaqueTypes.html) [不透明类型](https://www.cnswift.org/opaquetypes)

[Automatic Reference Counting](https://docs.swift.org/swift-book/LanguageGuide/AutomaticReferenceCounting.html) [自动引用计数](https://www.cnswift.org/automatic-reference-counting)

Swift 使用自动引用计数（ARC, Automatic Reference Counting）机制来追踪和管理应用程序的内存，这是一种自动添加内存管理功能的编译器特性。其原理为：当一个实例被创建并储存在堆内存中时，ARC会记录代码中别处对该实例的引用次数，即当前有多少指针指向该对象。当引用次数为零时，ACR认为已经没有对该实例感兴趣的代码，会自动释放类实例所占用的内存。在大多数情况下，ACR会让开发人员不需要自己考虑内存管理。然而在少数情况下，当两个对象相互引用，而外界没有对他们引用时，会造成二者的内存得不到释放，出现内存泄漏进而使应用程序奔溃。解决方法使用```weak```或```unowned```关键字为声明二者之间的引用为弱引用或无主引用。

[Memory Safety](https://docs.swift.org/swift-book/LanguageGuide/MemorySafety.html) [内存安全性](https://www.cnswift.org/memory-safety)

[Access Control](https://docs.swift.org/swift-book/LanguageGuide/AccessControl.html) [访问控制](https://www.cnswift.org/access-control)

在类与结构体的属性与方法前加入关键字实现访问控制，包括了私有```private```、公开```public```、只读```private (set)```等，

[Advanced Operators](https://docs.swift.org/swift-book/LanguageGuide/AdvancedOperators.html) [高级运算符](https://www.cnswift.org/advanced-operators)

# Apple SDK

通常属于某个框架的某各类的类名都以该框架的缩写作为前缀，如：

* NS - NeXTSTEP 框架的缩写，Cocoa类对象大部分类型的前缀，源自于乔布斯的另一家公司NEXT。
* UI - UIKit 框架的简写，编写 iOS 应用程序用户交互界面。
* CG - Core Graphic 框架的简写，常用于绘制自定义视图，纯C的API，使用 Quartz2D 做引擎。

## UIKit - iOS 应用程序框架

## AppKit - macOS 应用程序框架

# Xcode - 苹果生态集成开发工具

Xcode 是苹果公司推出的 IDE ，用于开发苹果系统下的应用程序。

操作系统支持的最新 Xcode 可在 App Store 下载；前往 可下载各个历史版本的 Xcode。

[**Xcode Help**](https://help.apple.com/xcode/mac/) 是使用手册。

* 本地化
  * 本地化用于适应多语言。

iOS应用程序项目可运行于macOS下的iPhone虚拟机中，但无法测试各种硬件功能；也可以将手机用USB连接mac电脑，通过真机调试，测试蓝牙、Wi-Fi、陀螺仪、GPS等硬件功能。Xcode提供了游乐场（playground），该功能提供所编即所见的强大互动效果，可以像脚本语言一样逐条运行。Xcode还内置了Git用于代码版本控制、instrument用于测试代码性能、分析CPU、内存占用等，这些功能都提高了应用程序开发效率。

一个 Xcode 项目的 workspace, project, target, scheme 是什么？

project里面包含了所有的源文件，资源文件和构建一个或者多个product的信息。

project利用他们去编译我们所需的product，也帮我们组织它们之间的关系。一个project可以包含一个或者多个target。project定义了一些基本的编译设置，每个target都继承了project的默认设置，每个target可以通过重新设置target的编译选项来定义自己的特殊编译选项。

> [支持 Markdown 格式](https://developer.apple.com/library/archive/documentation/Xcode/Reference/xcode_markup_formatting_ref/index.html)
>
> * 先写函数、类的结构，再按 ⌘ + ⌥ + / 添加描述。

[Documentation Archive](https://developer.apple.com/library/archive/navigation/) 

# 拾遗

> ###### 如何在低版本 Xcode 实现在高版本的 iOS 设备上真机调试？
>
> 如果 iOS ，而 Xcode ，那么。

> 参见
>
> * iOS 开发者
>   * [Brian Advent](https://www.youtube.com/channel/UCysEngjfeIYapEER9K8aikw) 
>   * [Mark Moeykens](https://www.youtube.com/channel/UChH6WbyYeX0INJjrK2-6WSg)
>   * [Lets Build That App](https://www.youtube.com/channel/UCuP2vJ6kRutQBfRmdcI92mA) 
>   * [Sean Allen](https://www.youtube.com/channel/UCbTw29mcP12YlTt1EpUaVJw) 
>   * [raywenderlich.com](https://www.youtube.com/channel/UCz3cM4qLljXcQ8oWjMPgKZA)

