# 序

Visual C++ 是微软的 C/C++ 开发环境，用于开发 Windows 平台的桌面应用程序。

首先，直接使用 Windows 操作系统 API（Win32 API）开发简单程序，可以理解其工作原理。

随后，使用  Microsoft Foundation Classes（MFC， 封装了 Win32 API 等功能）开发高级程序。

* 学习资源 ：
  * [微软官方文档 - Windows 平台 C++ 语言开发应用程序](https://docs.microsoft.com/en-us/cpp/windows/overview-of-windows-programming-in-cpp)
  * [微软官方文档  - MFC 桌面应用程序](https://docs.microsoft.com/en-us/cpp/mfc/mfc-desktop-applications)
  * *Ivor Horton's Beginning Visual C++ 2013* 中/英文版 ISBN: 978-1-118-84571-4
  * MFC_类库中文手册.chm

# Visual Studio

Visual Studio 是微软的集成开发环境。[solution 与 project](https://docs.microsoft.com/en-us/visualstudio/ide/solutions-and-projects-in-visual-studio) 的区别为：一个 solution 可以包含一个或多个 project。

# Windows 应用程序

Windows 的应用程序的窗口组成如下：

<img src="窗口构成.png" alt="1568879313742" style="zoom: 67%;" />



## 消息映射机制

* Windows 程序是**事件驱动（Event Driven）**的，**鼠标点击/键盘输入/窗口大小调整**都是事件。
* 事件被记录为消息 （Massage），虽然是 `int` 类型，但是通过宏定义使字面上易于区分。消息包括了自带的**系统消息**和开发者定义的**应用程序消息**，如 `WinUser.h` 中的 `#define WM_LBUTTONDBLCLK 0x0203 ` 定义了鼠标左键点击。
* 

 WM_



## 补充

*  win32 API 的主要设置用于开发32位或64位应用程序（虽然都叫 Win32 API）。
* API 后缀 `W` / 后缀 `A` / 无后缀，表示 双字节字符/ 单字节字符 / 根据当前字符环境选择字节字符。

# [MFC](https://docs.microsoft.com/en-us/cpp/mfc/mfc-desktop-applications)

Windows 应用程序API函数是通过C语言实现的，所有主要的 Windows 函数都在 Windows.h 头文件中进行了声明。Windows 操作系统提供了 1000 多种 API 函数。其中 win32 API 的主要设置用于开发32位或64位应用程序。

MFC 是微软把 win32 API 的封装类所构成的框架。

## 层级构成 / 类继承关系

根据 MFC [层级图](https://docs.microsoft.com/en-us/cpp/mfc/hierarchy-chart)，

* 

* 分为继承自 `CObject` 类

* 继承自 `CWnd` 的对象都是**窗口**，这不仅包括了显示的、有边框的对象（`CDialog`），还有按钮（C）

## 概念

* Resource：资源由 .rs 和 构成。
* Wizard：方便增/查/删/改新功能的工具，不用开发者手动写代码。如增/查/删/改消息映射、成员变量、成员函数等。

## 控件使用

### Rich Edit

1. Rich Edit （富文本编辑器）可以显示**自定义颜色/字体/大小等**的富文本。
2. 在 `CApp` 类的工程 `CXXXApp` 派生类的 `BOOL CXXXApp::InitInstance()` 中，加入 `AfxInitRichEdit();`，初始化富文本编辑器。

## 功能实现

### 在限定范围内可调整窗口大小并约束内部控件位置

1. 在 Resource View 中选此对话框，选 `Properties` 的 `Border` 为 `Resizing` 。
2. 在 Resource View 中选此对话框，在 `Message` 添加：
   1. `WM_SIZE`，调整对话框后，调用基类的 [`CWnd::OnSize(...)`](https://docs.microsoft.com/en-us/cpp/mfc/reference/cwnd-class?view=vs-2019#onsize)。重写此函数处理对话框被大小调整。要约束内部控件的位置和大小，使用 `this->GetDlgItem(...)->MoveWindow(...)` 。注意对话框首次创建时也会调用，此时对话框还不是窗口，使用 `this->IsWindowVisible()` 做判断。首次约束窗口应写在 `OnInitDialog()` 内。
   2. `WM_GETMINMAXI`，调整窗口后，调用基类的 [`CWnd::OnGetMinMaxInfo(...)`](https://docs.microsoft.com/en-us/cpp/mfc/reference/cwnd-class?view=vs-2019#ongetminmaxinfo)。重写此函数处理`tagMINMAXINFO` 指针，设置最大和最小
3. 

### 对话框拖放文件

1. 在 Resource View 中选此对话框，选 `Properties` 的 `Accept Files` 为 `True` 。
2. 在 Resource View 中选此对话框，在 `Message` 添加 

# 库

根据[维基百科](https://en.wikipedia.org/wiki/Library_(computing))，库是用于开发软件的子程序集合。库不是独立程序，库向其他程序（如：可执行程序）提供服务的代码。

Windows 系统下的静态链接库（Static Libary）为 .lib 文件，动链接库（Shared library）为 .dll 文件。连接阶段，静态库编译成的 .o 会合并到 .exe ，运行时摆脱对库依赖；动态库反之。

## 静态库

静态库有两种：未编译的源代码，源代码有助于 debug，可编译为不同目标平台的二进制文件；预编译的二进制文件，方便快速直接调用。

参考[微软官方](https://docs.microsoft.com/en-us/cpp/build/walkthrough-creating-and-using-a-static-library-cpp?view=vs-2019)，步骤为：

1. 使用 Visual Studio 新建 C++、windows 的 Static Library Project。
2. 对 project 添加 .h 文件，编写给外部调用的接口，如类声明。对工程添加 .cpp 文件，编写类定义。编译 solution。
3. 创建
4. 使用静态库需要：.h 头文件路径，.lib 静态库路径。
5. 运行应用程序。

## 动态库

# Win32 APIs



| API                                                          | 描述               |
| ------------------------------------------------------------ | ------------------ |
| [WritePrivateProfileStringA](https://docs.microsoft.com/en-us/windows/win32/api/winbase/nf-winbase-writeprivateprofilestringa) <br/>[WritePrivateProfileStringW](https://docs.microsoft.com/en-us/windows/win32/api/winbase/nf-winbase-writeprivateprofilestringw) | 写数据到 .ini 文件 |
|                                                              |                    |
|                                                              |                    |



# [并行程序设计](https://docs.microsoft.com/en-us/cpp/parallel/parallel-programming-in-visual-cpp?view=vs-2019)

简单的任务可直接使用 [CWinThread](https://docs.microsoft.com/en-us/cpp/mfc/reference/cwinthread-class) 类，有复杂需求则自行设计 CWinThread 的派生类。

## C win32 多线程

## C++ MFC 多线程

[使用MFC中的AfxBeginThread创建多线程](https://www.cnblogs.com/liangxiaofeng/p/5607042.html)

[使用 C++ 和 MFC 进行多线程编程](https://docs.microsoft.com/zh-cn/cpp/parallel/multithreading-with-cpp-and-mfc?view=vs-2019)

# 数据访问

# 微软[匈牙利命名法](https://en.wikipedia.org/wiki/Hungarian_notation)

匈牙利命名法广泛存在于

| 变量类型 | 前缀 |
| -------- | ---- |
| int      | n    |
|          |      |
|          |      |



# 苹果驼峰命名法