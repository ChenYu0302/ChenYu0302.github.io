---
layout: post
title:  "C++ 编程语言"
date:   2020-01-13 02:03:56 +0800
categories: C++

---

## Basic 基础

### Type 类型



### Scope 作用域

`{}` 

### Header File 头文件

### Lvalue & Rvalue 左值 & 右值

## Build-In Types 内置类型

C++ 内置类型不依赖头文件，编译器自动支持。

### void 无类型

### integral 整型

存储整数型原理：没有 `unsigned` 修饰的整型

|         类型         | 描述 |       占用        |       取值范围       |
| :------------------: | ---- | :---------------: | :------------------: |
|        `bool`        |      | 1 Byte \| 1 bits  |                      |
|        `char`        |      | 1 Byte \| 1 bits  |      -127 ~ 127      |
|   `unsigned char`    |      | 1 Byte \| 1 bits  |        0~256         |
|        `int`         |      |     机器位长      | 64位机器：32位机器： |
|    `unsigned int`    |      |     机器位长      |      64位机器：      |
|       `short`        |      |                   |                      |
|   `unsigned short`   |      |                   |                      |
|        `long`        |      | 8 Byte \| 64 bits |                      |
|   `unsigned long`    |      |                   |                      |
|     `long long`      |      |                   |                      |
| `unsigned long long` |      |                   |                      |



### floating point 浮点型

存储小数型原理：

## Declaration & Definition 声明 & 定义

Variable，变量，由 Type 类型、Name 变量名、Value 值 组成。

### `const` 修饰符

定义并初始化常量。`const` 修饰的常量，相比 `#define` 宏定义的文本替换，具有类型检查的优点。

```c++
const double PI = 3.141592653;
```

### `typedef` 类型别名

## casting 类型转换

## Build-In Operation  内置运算符

| 优先级 |   符号   | 中/英                                                        | 描述             |
| :----: | :------: | ------------------------------------------------------------ | ---------------- |
| **1**  |   `::`   | 作用域解析 / [Scope Resolution](https://docs.microsoft.com/en-us/cpp/cpp/scope-resolution-operator?view=vs-2019) | 类/命名空间      |
| **2**  |   `.`    | 访问对象成员 / [Object Member Access)](https://docs.microsoft.com/en-us/cpp/cpp/member-access-operators-dot-and?view=vs-2019) |                  |
|   2    |   `->`   | 访问指针成员 / [Pointer Member Access](https://docs.microsoft.com/en-us/cpp/cpp/member-access-operators-dot-and?view=vs-2019) |                  |
|   2    |   `[]`   | 下标运算符 / [Subscript](https://docs.microsoft.com/en-us/cpp/cpp/subscript-operator?view=vs-2019) |                  |
|   2    |   `()`   | 函数调用 / [Function call](https://docs.microsoft.com/en-us/cpp/cpp/function-call-operator-parens?view=vs-2019) |                  |
|   2    |   `++`   | 后置递增 / [Postfix increment](https://docs.microsoft.com/en-us/cpp/cpp/postfix-increment-and-decrement-operators-increment-and-decrement?view=vs-2019) |                  |
|   2    |   `--`   | 后置递减 / [Postfix decrement](https://docs.microsoft.com/en-us/cpp/cpp/postfix-increment-and-decrement-operators-increment-and-decrement?view=vs-2019) |                  |
|   2    |          |                                                              |                  |
|   2    |          |                                                              |                  |
|   2    |          |                                                              |                  |
|   2    |          |                                                              |                  |
|   2    |          |                                                              |                  |
| **3**  | `sizeof` | 对象或类型占用字节 / [Size of object or type](https://docs.microsoft.com/en-us/cpp/cpp/sizeof-operator?view=vs-2019) |                  |
|   3    |  `new`   | 创建对象 / [Create object](https://docs.microsoft.com/en-us/cpp/cpp/new-operator-cpp?view=vs-2019) | 在动态内存中划分 |
|   3    | `delete` | 销毁对象 / [Destroy object](https://docs.microsoft.com/en-us/cpp/cpp/delete-operator-cpp?view=vs-2019) |                  |
|   3    |          |                                                              |                  |
| **4**  |          |                                                              |                  |
|        |          |                                                              |                  |
| **5**  |          |                                                              |                  |
| **6**  |          |                                                              |                  |
| **7**  |          |                                                              |                  |
| **8**  |          |                                                              |                  |
| **9**  |          |                                                              |                  |
| **10** |          |                                                              |                  |
| **11** |          |                                                              |                  |
| **12** |          |                                                              |                  |
| **13** |          |                                                              |                  |
| **14** |          |                                                              |                  |
| **15** |          |                                                              |                  |
| **16** |          |                                                              |                  |
| **17** | `throw`  |                                                              |                  |
| **18** |   `,`    |                                                              |                  |

## Expression 表达式

类型转换

```c++

```



## Statement 语句

### Selection (Branch) 选择（分支）

### Iteration (Loop) 迭代（循环）

## Pointer 指针



### `void` pointer

### `NULL` pointer

### pointer to pointer

## Array 数组

内存上，数组成员，配合指针的偏移访问数组成员。

## Reference 引用

引用，Reference，是 C++ 语法做的优化，编译后，**本质还是靠指针**来实现的。引用相当于变量的别名。

## Function 函数

* 函数的**类型**取决于**参数列表与返回类型**。
* 函数的实例对象**名称**取决于**函数名**。
* 函数的**定义**取决于**函数体**。

函数声明，功能为：给外部提供调用接口，参数列表可以省略参数名，但不建议。

函数定义，参数列表可以省略参数名，但不建议。

### Argument List  参数表



> **拓展**：C 标准库头文件 `<stdarg.h>` 或 C++ 标准库头文件 `<initializer_list>` 可用于实现**参数个数可变**。

### overload 重载



### inline 内联

### Pointer to Function 函数指针

### Callback Function 回调函数

通过函数指针

## Lambda (Closure) 闭包

lambda 就是一种匿名函数，没有函数名的某种，又称为 closure，闭包。

## Enumeration 枚举

枚举用于定义只有几种有限可能的类型。

 ```c++
enum Suit // Suit is Enumeration
{
    // heart etc. is Enumerator
    heart,   /*♥️*/ 
    spade,   /*♠️*/
    club,    /*♣️*/
    diamond  /*♦️*/
}

void checkSuit(Suit suit)
{
    // Enumeration always match with switch brach.
    switch (suit)
    {
        case heart:
            /**/
            break;
            
            
            
    }
}
 ```

## Union 联合

Union 联合，继承自 C 语言。

## Class & Struct 类 & 结构

### Define Class/Struct 定义类/结构



在 C 中，定义一个结构实例需写 `struct TypeName instanceName` ；在 C++ 中，可省略 `struct` 关键字写 `TypeName instanceName` 。

### member 成员

### member function 成员函数



#### `this` 指针

`this` 指针指向 

### Constructor & Initialization 构造函数 & 初始化

构造函数用于

```c++
struct Fahrenheit
{
    double temperature;
    Fahrenheit(double Celsius)
}
```

#### 初始化列表

```c++
{
    
}
```



#### Copy Constructor 拷贝构造函数



#### Move Constructor 移动构造函数

C++ 11 新特性。

### Destructor 析构函数

因为被系统调用，无参数表，所以无重载。

### Access Control 访问控制

### Inheritance 继承



#### Override 重写



#### Virtual Function 虚函数

开发者希望在派生类中被重新定义的成员函数应被声明为虚函数。



虚函数表

#### Abstract Class 抽象类



#### Single Base Class Inheritance 单基类继承



#### Multiple Base Classes Inheritance 多基类继承



### Static 静态 

## Operator Overloading 运算符重载

设计运算符重载是，应遵循逻辑。语法如下：

```c++
type operator operator-symbol ( parameter-list )
```

### Unary 一元运算符

可被重载的一元运算符： `!` ` &` ` ~` ` *` ` +` ` -` ` ++`  `--` 。

### Binary 二元运算符

```c++
struct Box
{
    unsigned int length;
    unsigned int height;
    unsigned int width;
};

bool operator<(const Box &lhs, const Box &rhs)
{
    return (lhs.length * lhs.height * lhs.width) < (rhs.length * rhs.height * rhs.width);
}

bool operator>(const Box &lhs, const Box &rhs)
{
    return (lhs.length * lhs.height * lhs.width) > (rhs.length * rhs.height * rhs.width);
}

int main()
{
    Box myBox, yourBox;
    myBox.length = 2;
    myBox.height = 2;
    myBox.width = 2;
    yourBox.length = 1;
    yourBox.height = 1;
    yourBox.width = 1;

    myBox < yourBox; // false
    myBox > yourBox; // true

    return 0;
}
```



## Templates 模板

### Class Templates 类模板

### Function Templates 函数模板

```c++
template< class T > void MySwap( T& a, T& b ) {
   T c(a);
   a = b;
   b = c;
}
```

## Exception 异常

## Assertion & Debug 断言与调试

在 C++ 程序的三个生命周期：preprocessing 预处理、compile 编译、runtime 运行时，分别有以下。

* 
* 

`Assert(oughtToBeTrueExpression)` 是一个宏定义，

## Preprocessor 预处理

[C/C++ 预处理](https://docs.microsoft.com/en-us/cpp/preprocessor/c-cpp-preprocessor-reference) 

### 条件编译

## Compile 编译

编译器将 `.cpp` 和 `.h` 的 C++ 文本代码历经4个步骤： Preprocessing 预处理 →  Compilation → Assemble → Linking 链接，生成可执行文件（Executable File）或库（Library）。

### Environment 环境

#### GCC

[GCC](https://gcc.gnu.org/)，下载 。Windows 通过 MinGW 安装；macOS 通过 Homebrew 安装。

1. 下载MinGW：[官网地址](http://www.mingw.org/)

2. 安装MinGW：[默认位置](file:///C:/MinGW)

3. 修改环境变量：

4. 1. 计算机—属性---高级系统设置---环境变量，
   2. 在系统变量中找到 Path 变量，
   3. 在后面加入 min-gw的安装目录，如 [C:\MinGw\bin](file:///C:/MinGw/bin)

1. 验证：如果在cmd输入“mingw-get”能弹出MinGw     sinstallation manager 窗口，则安装成功
2. 安装gcc：cmd中输入“mingw-get install     gcc”，gcc用于编译.c文件
3. 安装g++：cmd中输入“mingw-get install g++”，g++用于编译.cpp文件
4. 安装gdb：cmd中输入“mingw-get install gdb”，gdb用于编译时调试
5. 编译.c文件：cmd中输入“gcc XXX.c”，将当前文件夹下XXX.c编译成a.exe文件
6. 调试程序：cmd中输入“gdb a.exe”，就可以是用gdb常用的命令进行调试程序了
7. 更新MinGW：cmd中输入“mingw-get update”,cmd中输入“mingw-get upgrade”

> 备注
>
> * 如果出现 Windows 平台下控制台乱码，则前往 `MinGW\share\locale` ，删除中文环境。

#### Clang & LLVM

1. ~~下载LLVM：[官网地址](http://releases.llvm.org/download.html)，选择Pre-Built     Binaries中的Clang for Windows (64-bit)，获得exe文件~~
2. ~~运行exe文件，勾选Add LLVM to the     system PATH for all users（即第二项）。[默认位置](file:///C:/Program Files/LLVM)~~
3. ~~验证：cmd中输入“clang -v”，显示clang版本，则安装成功~~
4. ~~编译.c文件：cmd中输入“clang XXX.c”，将当前文件夹下XXX.c编译成a.exe文件~~

#### Microsoft Visual C++

#### Apple Xcode

Xcode IED 使用 LLVM 编译 C 家族语言。

### Multiple Files Project 多文件工程

