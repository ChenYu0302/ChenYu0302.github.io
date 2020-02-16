---
layout: blog
title: C++
permalink: /blog/Cpp.html
date: 2020-02-14 01:06:00 +0800
category: 开发
tags: 
---

# C++ 11 编程语言

> 参见
>
> [Standard C++](https://isocpp.org/) ，标准 C++ 官方网站。
>
> [Microsoft Docs - C++ Language Reference](https://docs.microsoft.com/en-us/cpp/cpp/cpp-language-reference) ，微软的 C++ 参考文档。
>
> Stanley B Lippman - C++ Primer 5th Edition，。

C++ 11 是继 C++ 98 后的语言版本。

## Lexical Conventions 词法规则

Token，令牌，构成 C++ 程序的最小单位。

> 一个输出 ”Hello Word“ 的 C++ 语句：
>
> ```c++
> std::cout << "Hello World!" << std::endl;
> ```
>
> 可拆解为以下令牌：
>
> 1. `std` - 命名空间
> 2. 
> 3. 

### Keyword 关键字

> 继承自 C 语言的：
>
> |                           Keyword                            | 描述                                                         |
> | :----------------------------------------------------------: | ------------------------------------------------------------ |
> | [bool](https://docs.microsoft.com/en-us/cpp/cpp/bool-cpp?view=vs-2019) | 内置布尔类型。只有 True 和 False 两种可能值，对应变量存储 **非0** 和 **0**。 |
> |                             int                              |                                                              |
> |                                                              |                                                              |
> |                                                              |                                                              |
> |                                                              |                                                              |

> C 语言之外的：
>
> |                           Keyword                            | 描述                                         |
> | :----------------------------------------------------------: | -------------------------------------------- |
> | [auto](https://docs.microsoft.com/en-us/cpp/cpp/auto-keyword?view=vs-2019) | C++11 新特性，让编译器自动推断其类型的类型。 |
> |                                                              |                                              |
> |                                                              |                                              |
> |                                                              |                                              |
> |                                                              |                                              |
> |                                                              |                                              |
> |                                                              |                                              |
> |                                                              |                                              |
> |                                                              |                                              |
> |                                                              |                                              |
> |                                                              |                                              |
> |                                                              |                                              |
> |                                                              |                                              |
> |                                                              |                                              |
> |                                                              |                                              |
> |                                                              |                                              |
> |                                                              |                                              |
> |                                                              |                                              |
> |                                                              |                                              |
> |                                                              |                                              |
> |                                                              |                                              |
> |                                                              |                                              |

### Identifier 标识符



### Literal 字面值

Literal，字面值，直接用字符描述的数据常量，常被用于给变量赋值。

> 整数字面值：直接写数字为十进制，加入前缀表示为其他进制。默认是 `int` 型。
>
> ```c++
> 10;		// 十进制10 
> 0x10;	// 十六进制10 ，等于十进制16
> 0b10;	// 二进制10 ，等于十进制2
> -10		// 带有负号运算符的字面值10，因为严格意义上字面值不会是负数。
> ```

> 小数字面值：。默认是 `double` 型。
>
> ```c++
> 
> ```

> 文本字面值：' ' 内为字符；" " 内为字符串。
>
> ```C++
> 
> ```

，指定字面值的类型，而不是使用默认类型。

> ```
> 
> ```
>
> 如果不指定字面值类型，可能会因为默认类型的限制发生运算错误。
>
> ```c++
> 
> ```

开发者可以自定义字面值，

### Punctuator 标点

### Comment 注释

```c++
// comment a line

/*
comment
a 
block
*/
```

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

在 C++ 程序的三个生命周期：预处理（preprocessing）、编译（compile）、运行时（runtime），分别有以下。

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
   1. 计算机—属性---高级系统设置---环境变量，
   2. 在系统变量中找到 Path 变量，
   3. 在后面加入 min-gw的安装目录，如 [C:\MinGw\bin](file:///C:/MinGw/bin)
4. 验证：如果在cmd输入“mingw-get”能弹出MinGw     sinstallation manager 窗口，则安装成功
5. 安装gcc：cmd中输入“mingw-get install     gcc”，gcc用于编译.c文件
6. 安装g++：cmd中输入“mingw-get install g++”，g++用于编译.cpp文件
7. 安装gdb：cmd中输入“mingw-get install gdb”，gdb用于编译时调试
8. 编译.c文件：cmd中输入“gcc XXX.c”，将当前文件夹下XXX.c编译成a.exe文件
9. 调试程序：cmd中输入“gdb a.exe”，就可以是用gdb常用的命令进行调试程序了
10. 更新MinGW：cmd中输入“mingw-get update”,cmd中输入“mingw-get upgrade”

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

# Standard Library 标准库

> **参考**
>
> [Microsoft Docs - C++ Standard Library](https://docs.microsoft.com/en-us/cpp/standard-library/cpp-standard-library-reference) 
>
> [Microsoft Docs - C++ standard library header files](https://docs.microsoft.com/en-us/cpp/standard-library/cpp-standard-library-header-files)

C++ Standard Library ，C++ 标准库。命名空间位于 `namespace std` 。

## C 标准库

C 标准库是 C++ 标准库的子集。

### "string.h" 字符数组

 头文件 "string.h"。定义了 `sting` 结构体，以 `\0` 结尾的字符数组。 

```c++
sizeof("ABC"); // = 4, beacuse of ending with `\0`;
memset();
```

### "time.h" 时间



## String 字符串



### \<string\> 字符串模板类

头文件 [\<string\>](https://docs.microsoft.com/en-us/cpp/standard-library/string) 。

```c++
std::string myName = "";
```



`char*` 与 `std::string` 的转换

|                        | to `string` | to `const char*` | to `char*` | to `char[]` |
| ---------------------- | ----------- | ---------------- | ---------- | ----------- |
| **from** `string`      |             |                  |            |             |
| **from** `const char*` |             |                  |            |             |
| **from** `char*`       |             |                  |            |             |
| **from** `char[]`      |             |                  |            |             |



# I/O Stream 输入输出流

stream，流，具有输入/输出功能。stream 对象是一串有方向的字节包裹，具有 source 源头、destination 目的地。文件、控制台、字符串变量的读/写，会对 stream 对象进行操作。

## string stream 字符串流

```

```

## file stream 文件流

头文件 \<fstream\>  。 `class ifstream` 支持将 stream 输入/输出到文件，

# Iterators 迭代器

[Iterators](https://docs.microsoft.com/en-us/cpp/standard-library/iterators)，迭代器，

## Container 容器

Container，容器，是用于管理和组织其他对象的对象，基于 Template 实现。

### Sequence Containers 顺序容器

Sequence Containers ，顺序容器，根据**位置**管理元素。

#### vector

头文件 [\<vector\>](https://docs.microsoft.com/en-us/cpp/standard-library/vector) 。可变大小，可任意位置增删成员，综合性能最好。

```c++
/** 初始化 **/
 // 空
std::vector<int> v1;
 // C++ 11 new: 初始化并赋值
std::vector<int> v1 = {1,2,3,4,5};
// 用迭代器初始化
std::set<int> s1 = {9, 8, 7, 6, 5, 4, 3};   // 3 4 5 6 7 8 9
std::vector<int> v1(s1.begin(), s1.end());  // 3 4 5 6 7 8 9

/** 更新 **/


/****************************
 * 
****************************/
```



### Associative Containers 关联容器

Associative Containers，根据**键（Key）**管理元素。共计8种类型，从3个维度区分：

* 是可通过 key 访问 value 的 `map` 还是 value 就是 key 本身的 `set` 。
* `multi`前缀表示 key 能否重复。
* `unordered`前缀表示成员是否有序。

头文件 [\<set\>](https://docs.microsoft.com/en-us/cpp/standard-library/set)  \<[map](https://docs.microsoft.com/en-us/cpp/standard-library/map)\>  \<[unordered_set](https://docs.microsoft.com/en-us/cpp/standard-library/unordered-set)\>  \<[unordered_map](https://docs.microsoft.com/en-us/cpp/standard-library/unordered-map)\> 

iterator 是 const 的：这意味着不能用诸如 `std::copy` 等算法他们操作。

严格若序的，

#### set

`std::set` 存储已排序对象，默认对 Key 依据 `<` 运算符排序。

```c++
// define a set object

std::vector<int> v1 = {9, 9, 8, 8, 8, 7, 7, 6, 5, 4, 3, 3};
std::set<int> s1(v1.begin(), v1.end());		// {9, 8, 7, 6, 5, 4, 3}



// define a map object
set::map<pair<std::string, int>> 
```

若成员是自定义类型 ，必须对 Key 重载`<`运算符。若成员有 `a < b == false && b < a == false` ，则 `a == b` 。所以通过重载 `<` 运算符实现唯一性。

```c++
struct Box
{
    double length;
    double width;
    double height;
    double volume;
    Box(double l, double w, double h) : length(l), width(w), height(h)
    {
        volume = l * w * h;
    }
    bool operator<(const Box &other) const { return volume < (other.volume); }
};

std::set<Box> SomeBoxes;
Box box1(5, 7, 8);
SomeBoxes.insert(box1);
Box box2(8, 7, 5);
SomeBoxes.insert(box2); // box1 == box2 in the set according to operator<
Box box3(7, 7, 7);
SomeBoxes.insert(box3);
Box box4(10, 14, 16);
SomeBoxes.insert(box4);
Box box5(3, 3, 3);
SomeBoxes.insert(box5);
```

自定义比较函数

```c++

```

#### 遍历

#### find 查找

```c++
std::set<int> evenNumber = {0,2,4,6,8,10};
if (evenNumber.find(5) == evenNumber.end())
    std::cout << "Can't find 5 in evenNumber" << std::endl;
else
    std::cout << "Can find 5 in evenNumber" << std::endl;
```

#### count 计数

#### insert 添加

#### erase 删除

#### map

#### multi set/map

```c++
typedef std::string Poet;    
typedef std::string Poem;    
std::multimap<Poet, Poem> poemCollection;
   
poemCollection.insert(std::pair<"李白", "将进酒">);
poemCollection.insert(std::pair<"李白", "蜀道难">);
poemCollection.insert(std::pair<"白居易", "琵琶行">);
poemCollection.insert(std::pair<"", "">);
```

### ordered vs unordered

无序关联容器是 C++ 11 标准。

若有序，按 `<` 对成员排列；

```c++

```

若无序，需定义成员的哈希函数。

```

```



## Algorithms 算法

Algorithms ，算法，由 100+ 个函数组成。泛型编程使算法函数可应用于多种数据结构。头文件 [\<algorithm\>](https://docs.microsoft.com/en-us/cpp/standard-library/algorithm) 。

### sort 排序

[sort](https://docs.microsoft.com/en-us/cpp/standard-library/algorithm-functions?view=vs-2019#sort) ，两种函数重载，可缺省使用 `<` 运算符作排序的比较；或传入比较函数变量，依据此函数排序。

1. 默认使用 `<` 运算符进行排序

```c++
std::vector<int> v1 = {8, 10, 15, 23, 55, 22, 78, 11, 28};
std::sort(v1.begin(), v1.end()); // 8 10 11 15 22 23 28 55 78
```

对于自定义类型，必须定义类型的 `<` 运算符。对于容器成员，若 `a < b == false && b < a == false` ，则 `a == b` 。

```c++
struct Box
{
    double length;
    double width;
    double height;
    double volume;
    Box(double l, double w, double h) : length(l), width(w), height(h)
    {
        volume = l * w * h;
    }
    bool operator<(const Box &other) const { return volume < (other.volume); }
};

std::vector<Box> SomeBoxes;
Box box1(5, 7, 8);
Box box2(1, 3, 5);
Box box3(7, 7, 7);
Box box4(10, 14, 16);
Box box5(3, 3, 3);
SomeBoxes.push_back(box1);
SomeBoxes.push_back(box2);
SomeBoxes.push_back(box3);
SomeBoxes.push_back(box4);
SomeBoxes.push_back(box5);

// SomeBoxes's volume sequence before sorted: 280 15 343 2240 27

std::sort(SomeBoxes.begin(), SomeBoxes.end());

// SomeBoxes's volume sequence after sorted: 15 27 280 343 2240
return 0;
```

2. 使用自定义比较函数进行排序

```c++
bool GreaterInt(int integer1, int integer2)
{
    return integer1 > integer2;
}
```

```c++
std::vector<int> v1 = {8, 10, 15, 23, 55, 22, 78, 11, 28};
std::sort(v1.begin(), v1.end(), GreaterInt); // 78 55 28 23 22 15 11 10 8
```

 [is_sorted](https://docs.microsoft.com/en-us/cpp/standard-library/algorithm-functions?view=vs-2019#is_sorted) 

 [is_sorted_until](https://docs.microsoft.com/en-us/cpp/standard-library/algorithm-functions?view=vs-2019#is_sorted_until)

### copy 复制

### find 寻找

### fill 填充

### replace 替换

### Lexicographical 字典序

字典排序规则：从首位比较，若相等，则比较下一位。

### permutation 全排列

[next_permutation](https://docs.microsoft.com/en-us/cpp/standard-library/algorithm-functions?view=vs-2019#next_permutation) 与 [prev_permutation](https://docs.microsoft.com/en-us/cpp/standard-library/algorithm-functions?view=vs-2019#prev_permutation) 可用于获取上一个/下一个全排列。以 {A,B,C} 为例理解 next 与 previous 的含义：按字符 A<B<C 为小到大顺序的三者，排列数有 $A_3^3=\frac{3!}{(3-3)!}=6$ 种。这 6 种小到大排序为：ABC<ABC<BAC<BCA<CAB<CBA，这种排序称为**字典排序（lexicographical order）** 。

参数 first iteration、last iteration 指明在此 iterator 之间计算上/下个全排列，必须是顺序类型的 iterator。`bool` 型返回值，`true` 表示还有下一个全排列，`false` 表示已经没有下一个。 若缺省了比较函数，则默认使用 `<` 运算符比较，否则需传入比较函数。

```c++
std::string strABC = "ABC";
do{
    std::cout << strABC << " ";        
}while(std::next_permutation(strABC.begin(), strABC.end()));
// output: ABC ACB BAC BCA CAB CBA
```

## memory management 内存管理 

### Smart Pointer 智能指针

## Time 时间

头文件 [\<ctime\>](https://docs.microsoft.com/en-us/cpp/standard-library/ctime) 源于 C 标准库 time.h；头文件 [\<chrono\>](https://docs.microsoft.com/en-us/cpp/standard-library/chrono) 属于 C++ 标准库。

### ctime

```

```



### chrono