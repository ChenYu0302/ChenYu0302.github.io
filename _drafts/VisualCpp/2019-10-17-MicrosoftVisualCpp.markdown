---
layout: post
title:  "Microsoft Visual C++"
date:   2019-10-22 02:03:56 +0800
categories: Development
---
# Microsoft Visual C++

Visual C++ 是微软的 C/C++ 开发环境，通过 Windows 操作系统 API（Win32 API）可以开发程序，开发 Windows 平台的桌面应用程序。

* [微软文档 - Windows 平台 C++ 语言开发应用程序](https://docs.microsoft.com/en-us/cpp/windows/overview-of-windows-programming-in-cpp)
* [Ivor Horton's Beginning Visual C++ 2013 by Ivor Horton](https://www.oreilly.com/library/view/ivor-hortons-beginning/9781118845776/)
* MFC_类库中文手册.chm

## 基础设施

*  win32 API 的主要设置用于开发32位或64位应用程序（虽然都叫 Win32 API）。
*  API 后缀 `W` / 后缀 `A` / 无后缀，表示 双字节字符/ 单字节字符 / 当前字符环境的字节字符。

常见类型

* `LPCSTR` ：
* ` LPCWSTR ` ： Unicode 编码字符串的32位指针。

## Visual Studio

Visual Studio 是微软的集成开发环境。[solution 与 project](https://docs.microsoft.com/en-us/visualstudio/ide/solutions-and-projects-in-visual-studio) 的区别为：一个 solution 可以包含一个或多个 project。

### Debug vs Release

参考：[How to: Debug a Release Build](https://docs.microsoft.com/en-us/cpp/build/how-to-debug-a-release-build) 。

**Debug**，调试版本，包含调试信息，并且不作任何编译优化，供程序员调试；**Release**，发布版本，进行了各种编译优化，使得程序在代码大小和运行速度上都是最优的，供用户使用。二者区别包括：

1. **ASSERT()**：从其宏定义可知：debug 版编译 Assert；release 版不编译 Assert。Assert 用于断言某些使程序能继续运行的条件，防止程序走向大崩溃。
2. **变量初始化**： debug 版初始化成 `0xcc` 是因为 `0xcc` 在 x86 平台是一条 `int 3` 单步中断指令，这样程序如果跑飞了遇到 `0xcc` 就会停下来，这和单片机编程时一般将没用的代码空间填入`jmp 0000`语句是一样 。编程时尤其是指针和数组要做好初始化。
3. **数组越界**：debug 版数组越界不易察觉；release 版反之。

**Tip** - 在 Debug 模式下，输出信息到 Console：

1. 添加  Console Input/Output 头文件：

   ```c++
   #include "conio.h"
   ```

2. 在函数开始运行处分配一个 console：

   ```c++
   #ifdef _DEBUG
   	AllocConsole();
   #endif
   ```

3. 随后就可以输出到控制台

   ```c++
   _cprintf("Some Debug value: %d", var1);
   ```

## MFC

MFC，Microsoft Foundation Classes，微软基础类库，封装了 Win32 API 等功能，可以开发的具有用户界面的高级程序。

* 参考链接：
  * [微软文档  - MFC 桌面应用程序](https://docs.microsoft.com/en-us/cpp/mfc/mfc-desktop-applications)

[MFC 层级图](https://docs.microsoft.com/en-us/cpp/mfc/hierarchy-chart)：

* `CObject` 类，
  *  `CWnd` ，窗口类，
    * `CDialog`，对话框类，
    * `Cbutton` ，按钮类，
* 

MFC 工程组成：

* **Source** ：源代码，
* **Source** ：源代码，由 `.cpp` 组成。
* **Resource** ：资源，由 `.rs` 和 `.rs2` 组成，用。在 Resource View  窗口下可进行可视化界面设计。

### MFC Class Wizard

Wizard 是对代码自动增/查/删/改类、消息映射、成员变量、成员函数等的工具，免去了手动编写过程。

### 消息响应模型

* Windows 程序是**事件驱动（Event Driven）**的，**鼠标点击/键盘输入/窗口大小调整**等都是事件。
* **事件**被记录为**消息** （Massage），是 `int` 类型，通过宏定义使字面上易于区分。消息包括了自带的**系统消息**和开发者定义的**应用程序消息**，如 `WinUser.h` 中的 `#define WM_LBUTTONDBLCLK 0x0203 ` 定义了鼠标左键点击事件。

### 界面

MFC 创建的 Windows 的应用程序的窗口组成如下：

<img src="窗口构成.png" alt="1568879313742" style="zoom: 67%;" />

#### 菜单栏

#### Dialog

Dialog 的两种显示：

* 模态（禁用 Parent Dialog 的操作），调用 `DoModel()` 。
* 非模态（允许父对话框的操作）。

#### 对话框控件

button、

* 添加事件处理：

* 添加控件变量：
  
* 在 Resource View 右键某
  
* 常用控件
  
  * Rich Edit
  
  1. Rich Edit，富文本编辑器，可以显示**自定义颜色/字体/大小等**的富文本的控件。
  2. 在 `CApp` 类的工程 `CXXXApp` 派生类的 `BOOL CXXXApp::InitInstance()` 中，加入 `AfxInitRichEdit();`，初始化富文本编辑器。

### 实例

#### 设计可调整窗口

在限定范围内可调整窗口大小并约束内部控件位置

1. 使能对话框的调整功能。在 Resource View 中选此对话框，选 `Properties` 的 `Border` 为 `Resizing` 。

2. 在 Resource View 中选此对话框，在 `Message` 添加：

   1. `WM_SIZE`，调整对话框后，调用基类的 [`CWnd::OnSize(...)`](https://docs.microsoft.com/en-us/cpp/mfc/reference/cwnd-class?view=vs-2019#onsize)。重写此函数处理对话框被大小调整。要约束内部控件的位置和大小，使用 `this->GetDlgItem(...)->MoveWindow(...)` 。注意对话框首次创建时也会调用，此时对话框还不是窗口，使用 `this->IsWindowVisible()` 做判断。首次约束窗口应写在 `OnInitDialog()` 内。
   2. `WM_GETMINMAXI`，调整窗口后，调用基类的 [`CWnd::OnGetMinMaxInfo(...)`](https://docs.microsoft.com/en-us/cpp/mfc/reference/cwnd-class?view=vs-2019#ongetminmaxinfo)。重写此函数处理`tagMINMAXINFO` 指针，设置最大和最小

#### 拖放文件到对话框

1. 在 Resource View 中选此对话框，选 `Properties` 的 `Accept Files` 为 `True` 。
2. 在 Resource View 中选此对话框，在 `Message` 添加 

#### 打包资源文件

要在，可通过打包 Dialog 等资源文件实现。

## Winuser.h

#### [MessageBox](https://docs.microsoft.com/en-us/windows/win32/api/winuser/nf-winuser-messagebox)



## Windows API

所有主要的 Windows 函数都在 Windows.h 头文件中进行了声明。

### 常用

#### 

* [WritePrivateProfileString](https://docs.microsoft.com/en-us/windows/win32/api/winbase/nf-winbase-writeprivateprofilestringa) 写 `String` 到 `.ini` 文件。`.ini` 文件内由 sector、key、value 组成。 

## 库

[库](https://en.wikipedia.org/wiki/Library_(computing))是用于开发软件的子程序集合，不是独立程序，向其他程序（如：可执行程序）提供服务的代码。

### 静态库

[静态库](https://docs.microsoft.com/en-us/cpp/build/walkthrough-creating-and-using-a-static-library-cpp?view=vs-2019)有两种：未编译的源代码，源代码有助于 debug，可编译为不同目标平台的二进制文件；预编译的二进制文件，方便快速直接调用。

步骤为：

1. 使用 Visual Studio 新建 C++、windows 的 Static Library Project。
2. 对 project 添加 .h 文件，编写给外部调用的接口，如类声明。对工程添加 .cpp 文件，编写类定义。编译 solution。
3. 创建
4. 调用静态库需要：`.h` 头文件路径，`.lib` 静态库路径。
5. 运行应用程序。

## 动态库

### 动态库



## 设计并行程序

[使用 C++ 和 MFC 进行多线程编程](https://docs.microsoft.com/zh-cn/cpp/parallel/multithreading-with-cpp-and-mfc?view=vs-2019)

简单的任务可直接使用 [CWinThread](https://docs.microsoft.com/en-us/cpp/mfc/reference/cwinthread-class) 类，若需求复杂，则自行设计 `CWinThread` 的派生类。