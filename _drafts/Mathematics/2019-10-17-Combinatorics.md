---
layout: post
title:  "组合数学 学习笔记"
date:   2019-10-17 02:03:56 +0800
categories: Algorithm
---

> **参考**
>
> [维基百科 - 组合数学](https://zh.wikipedia.org/wiki/%E7%BB%84%E5%90%88%E6%95%B0%E5%AD%A6)
>
> wiki - 
>
> [清华大学 - 组合数学](https://next.xuetangx.com/course/THU08091000450/1075957)
>
> [小与米 - next_permutation(全排列算法)](https://blog.csdn.net/c18219227162/article/details/50301513)
>
> [Shao Voon Wong - Combinations in C++](https://www.codeproject.com/articles/4675/combinations-in-c)
>
> [Shao Voon Wong - Combinations in C++, Part 2](https://www.codeproject.com/Articles/21335/Combinations-in-C-Part)
>
> [cppowboy - 求组合数的算法](https://segmentfault.com/a/1190000005072018)

## 数学定义

$U_n^r=\frac{n!}{(n-r)!}$ 

arrangement ，**排列**，数学上所有排列可能性： $A_n^r=\frac{n!}{(n-r)!}$ ， $A_n^0=1$ ，$A_n^1=n$ ，$A_n^n=n!$。 中国大陆的教科书通常称排列为 Arrangement ，记为 $A$ 。

combination ，**组合**，数学上所有组合可能性： $C_n^r=C_n^{n-r}=\frac{n!}{(n-r)!r!}$ ， $C_n^0=1$ ，$C_n^1=n$ ， $C_n^n=1$。

## 标准库 API

### C++

#### 全排列

全排列有 $A_n^n=n!$ 种可能。以 {A,B,C} 为例理解上一个/下一个字典序的含义。按字符 A<B<C 为小到大顺序的三者，排列数有 $A_3^3=\frac{3!}{(3-3)!}=6$ 种。这 6 种小到大排序为：ABC<ABC<BAC<BCA<CAB<CBA，此种排序称为 lexicographical order ，字典排序。字典排序规则：从首位比较，若相等，则比较下一位。

C++ 标准库提供的 [next_permutation](https://docs.microsoft.com/en-us/cpp/standard-library/algorithm-functions?view=vs-2019#next_permutation) 与 [prev_permutation](https://docs.microsoft.com/en-us/cpp/standard-library/algorithm-functions?view=vs-2019#prev_permutation) 可用于获取下一个/上一个按字典序的全排列，头文件 [\<algorithm\>](https://docs.microsoft.com/en-us/cpp/standard-library/algorithm) 。两种函数重载。参数 first iteration、last iteration 指明在此 iterator 之间计算上/下个全排列，必须是顺序容器类型的 iterator。`bool` 型返回值，`true` 表示因为还有下/上一个全排列，并替换了原来序列的排序；`false` 表示因为已经是最大/小字典序，已经没有下/上一个，原来序列的排序没有发生改变。 若缺省了比较函数，则默认使用 `<` 运算符比较，否则需传入比较函数。

```c++
std::string strABC = "ABC";
do{
    std::cout << strABC << " ";
}while(std::next_permutation(strABC.begin(), strABC.end()));
// output: ABC ACB BAC BCA CAB CBA
```

### Python

### MATLAB



## 实现 API

### 全排列



#### 全排列算法的原理与实现

计算下一个全排列的步骤如下：

1. 首先从最尾端开始往前寻找两个位置相邻元素，令第一元素为 `i` ，第二元素为 `ii` ，且满足 `i<ii` 。
2. 找到这样一组相邻元素后，再从最尾端开始往前检验，找出第一个大于 `i` 的元素，令为 `j` ，将 i , `j` 元素对调(swap)。
3. 再将 `ii` 之后的所有元素按 `<` 排序（反向排序）。

> 例如 {0, 1, 2, 3 ,4} 序列，黑体表示 `i` 和 `ii` ：
>
>  012**34** → 01**24**3→ 013**24**→ 01**34**2→ 014**23** → 0**14**32 → 021**34** → ...

 C++ 实现，需调用 [iter_swap](https://docs.microsoft.com/en-us/cpp/standard-library/algorithm-functions?view=vs-2019#iter_swap) 实现交换；调用 [reverse](https://docs.microsoft.com/en-us/cpp/standard-library/algorithm-functions?view=vs-2019#reverse) 实现反向排序。

```c++
template<calss BidirectionalIterator>
bool next_permutation(BidirectionalIterator first,BidirectionalIterator last)
{
	if(first == lase) return false; /* empty space */    
	if(first + 1 == last) return false;  /* only one element */
    
	for(BidirectionalIterator i = last - 1;;)
	{
		BidirectionalIterator ii = i;
		i--;
		if(*i < *ii)
		{
			BidirectionalIterator j = last;
			while(!(*i < *--j));
			std::iter_swap(i,j);
			std::reverse(ii,last);
			return true;
		}
		if(i == first)
		{
			std::reverse(first,last);
			return false;
		}
	}
}
```

### 组合

#### 基于字典序实现 next_combination 函数

以 $C_{10}^4=\frac{10!}{(10-4)!4!}$ 为例，所有的组合按字典序排列，{0,1,2,3} 为最小字典序的合组索引，{6,7,8,9} 为最大字典序的组合索引：

```c++
[A] [B] [C] [D]  E   F   G   H   I   J  
[A] [B] [C]  D  [E]  F   G   H   I   J  
[A] [B] [C]  D   E  [F]  G   H   I   J  
[A] [B] [C]  D   E   F  [G]  H   I   J  
[A] [B] [C]  D   E   F   G  [H]  I   J
[A] [B] [C]  D   E   F   G   H  [I]  J
[A] [B] [C]  D   E   F   G   H   I  [J] 
[A] [B]  C  [D] [E]  F   G   H   I   J
[A] [B]  C  [D]  E  [F]  G   H   I   J
[A] [B]  C  [D]  E   F  [G]  H   I   J  
[A] [B]  C  [D]  E   F   G  [H]  I   J
[A] [B]  C  [D]  E   F   G   H  [I]  J
[A] [B]  C  [D]  E   F   G   H   I  [J] 
[A] [B]  C   D  [E] [F]  G   H   I   J  
[A] [B]  C   D  [E]  F  [G]  H   I   J
[A] [B]  C   D  [E]  F   G  [H]  I   J
[A] [B]  C   D  [E]  F   G   H  [I]  J
[A] [B]  C   D  [E]  F   G   H   I  [J] 
[A] [B]  C   D   E  [F] [G]  H   I   J
[A] [B]  C   D   E  [F]  G  [H]  I   J
[A] [B]  C   D   E  [F]  G   H  [I]  J
[A] [B]  C   D   E  [F]  G   H   I  [J] 
[A] [B]  C   D   E   F  [G] [H]  I   J
[A] [B]  C   D   E   F  [G]  H  [I]  J
[A] [B]  C   D   E   F  [G]  H   I  [J]
[A] [B]  C   D   E   F   G  [H] [I]  J  
[A] [B]  C   D   E   F   G  [H]  I  [J]
[A] [B]  C   D   E   F   G   H  [I] [J]
[A]  B  [C] [D] [E]  F   G   H   I   J
[A]  B  [C] [D]  E  [F]  G   H   I   J  
[A]  B  [C] [D]  E   F  [G]  H   I   J
[A]  B  [C] [D]  E   F   G  [H]  I   J  
[A]  B  [C] [D]  E   F   G   H  [I]  J
[A]  B  [C] [D]  E   F   G   H   I  [J]
[A]  B  [C]  D  [E] [F]  G   H   I   J
[A]  B  [C]  D  [E]  F  [G]  H   I   J
[A]  B  [C]  D  [E]  F   G  [H]  I   J  
[A]  B  [C]  D  [E]  F   G   H  [I]  J  
[A]  B  [C]  D  [E]  F   G   H   I  [J]
[A]  B  [C]  D   E  [F] [G]  H   I   J
[A]  B  [C]  D   E  [F]  G  [H]  I   J
[A]  B  [C]  D   E  [F]  G   H  [I]  J
[A]  B  [C]  D   E  [F]  G   H   I  [J] 
[A]  B  [C]  D   E   F  [G] [H]  I   J
[A]  B  [C]  D   E   F  [G]  H  [I]  J
[A]  B  [C]  D   E   F  [G]  H   I  [J]
[A]  B  [C]  D   E   F   G  [H] [I]  J
[A]  B  [C]  D   E   F   G  [H]  I  [J] 
[A]  B  [C]  D   E   F   G   H  [I] [J]
[A]  B   C  [D] [E] [F]  G   H   I   J  
[A]  B   C  [D] [E]  F  [G]  H   I   J
[A]  B   C  [D] [E]  F   G  [H]  I   J
[A]  B   C  [D] [E]  F   G   H  [I]  J
[A]  B   C  [D] [E]  F   G   H   I  [J]
[A]  B   C  [D]  E  [F] [G]  H   I   J  
[A]  B   C  [D]  E  [F]  G  [H]  I   J  
[A]  B   C  [D]  E  [F]  G   H  [I]  J
[A]  B   C  [D]  E  [F]  G   H   I  [J]
[A]  B   C  [D]  E   F  [G] [H]  I   J
[A]  B   C  [D]  E   F  [G]  H  [I]  J
[A]  B   C  [D]  E   F  [G]  H   I  [J] 
[A]  B   C  [D]  E   F   G  [H] [I]  J
[A]  B   C  [D]  E   F   G  [H]  I  [J]
[A]  B   C  [D]  E   F   G   H  [I] [J] 
[A]  B   C   D  [E] [F] [G]  H   I   J
[A]  B   C   D  [E] [F]  G  [H]  I   J
[A]  B   C   D  [E] [F]  G   H  [I]  J
[A]  B   C   D  [E] [F]  G   H   I  [J] 
[A]  B   C   D  [E]  F  [G] [H]  I   J
[A]  B   C   D  [E]  F  [G]  H  [I]  J
[A]  B   C   D  [E]  F  [G]  H   I  [J] 
[A]  B   C   D  [E]  F   G  [H] [I]  J
[A]  B   C   D  [E]  F   G  [H]  I  [J]
[A]  B   C   D  [E]  F   G   H  [I] [J] 
[A]  B   C   D   E  [F] [G] [H]  I   J
[A]  B   C   D   E  [F] [G]  H  [I]  J
[A]  B   C   D   E  [F] [G]  H   I  [J]
[A]  B   C   D   E  [F]  G  [H] [I]  J
[A]  B   C   D   E  [F]  G  [H]  I  [J] 
[A]  B   C   D   E  [F]  G   H  [I] [J]
[A]  B   C   D   E   F  [G] [H] [I]  J
[A]  B   C   D   E   F  [G] [H]  I  [J] 
[A]  B   C   D   E   F  [G]  H  [I] [J]
[A]  B   C   D   E   F   G  [H] [I] [J]
 A  [B] [C] [D] [E]  F   G   H   I   J
 A  [B] [C] [D]  E  [F]  G   H   I   J
 A  [B] [C] [D]  E   F  [G]  H   I   J  
 A  [B] [C] [D]  E   F   G  [H]  I   J
 A  [B] [C] [D]  E   F   G   H  [I]  J  
 A  [B] [C] [D]  E   F   G   H   I  [J]
 A  [B] [C]  D  [E] [F]  G   H   I   J
 A  [B] [C]  D  [E]  F  [G]  H   I   J
 A  [B] [C]  D  [E]  F   G  [H]  I   J  
 A  [B] [C]  D  [E]  F   G   H  [I]  J
 A  [B] [C]  D  [E]  F   G   H   I  [J]
 A  [B] [C]  D   E  [F] [G]  H   I   J
 A  [B] [C]  D   E  [F]  G  [H]  I   J
 A  [B] [C]  D   E  [F]  G   H  [I]  J  
 A  [B] [C]  D   E  [F]  G   H   I  [J]
 A  [B] [C]  D   E   F  [G] [H]  I   J
 A  [B] [C]  D   E   F  [G]  H  [I]  J  
 A  [B] [C]  D   E   F  [G]  H   I  [J]
 A  [B] [C]  D   E   F   G  [H] [I]  J
 A  [B] [C]  D   E   F   G  [H]  I  [J] 
 A  [B] [C]  D   E   F   G   H  [I] [J]
 A  [B]  C  [D] [E] [F]  G   H   I   J
 A  [B]  C  [D] [E]  F  [G]  H   I   J  
 A  [B]  C  [D] [E]  F   G  [H]  I   J
 A  [B]  C  [D] [E]  F   G   H  [I]  J
 A  [B]  C  [D] [E]  F   G   H   I  [J]
 A  [B]  C  [D]  E  [F] [G]  H   I   J  
 A  [B]  C  [D]  E  [F]  G  [H]  I   J
 A  [B]  C  [D]  E  [F]  G   H  [I]  J  
 A  [B]  C  [D]  E  [F]  G   H   I  [J]
 A  [B]  C  [D]  E   F  [G] [H]  I   J
 A  [B]  C  [D]  E   F  [G]  H  [I]  J
 A  [B]  C  [D]  E   F  [G]  H   I  [J]
 A  [B]  C  [D]  E   F   G  [H] [I]  J  
 A  [B]  C  [D]  E   F   G  [H]  I  [J]
 A  [B]  C  [D]  E   F   G   H  [I] [J]
 A  [B]  C   D  [E] [F] [G]  H   I   J
 A  [B]  C   D  [E] [F]  G  [H]  I   J  
 A  [B]  C   D  [E] [F]  G   H  [I]  J
 A  [B]  C   D  [E] [F]  G   H   I  [J]
 A  [B]  C   D  [E]  F  [G] [H]  I   J
 A  [B]  C   D  [E]  F  [G]  H  [I]  J  
 A  [B]  C   D  [E]  F  [G]  H   I  [J]
 A  [B]  C   D  [E]  F   G  [H] [I]  J
 A  [B]  C   D  [E]  F   G  [H]  I  [J]
 A  [B]  C   D  [E]  F   G   H  [I] [J]
 A  [B]  C   D   E  [F] [G] [H]  I   J  
 A  [B]  C   D   E  [F] [G]  H  [I]  J
 A  [B]  C   D   E  [F] [G]  H   I  [J] 
 A  [B]  C   D   E  [F]  G  [H] [I]  J
 A  [B]  C   D   E  [F]  G  [H]  I  [J]
 A  [B]  C   D   E  [F]  G   H  [I] [J]
 A  [B]  C   D   E   F  [G] [H] [I]  J
 A  [B]  C   D   E   F  [G] [H]  I  [J] 
 A  [B]  C   D   E   F  [G]  H  [I] [J]
 A  [B]  C   D   E   F   G  [H] [I] [J] 
 A   B  [C] [D] [E] [F]  G   H   I   J
 A   B  [C] [D] [E]  F  [G]  H   I   J
 A   B  [C] [D] [E]  F   G  [H]  I   J
 A   B  [C] [D] [E]  F   G   H  [I]  J
 A   B  [C] [D] [E]  F   G   H   I  [J] 
 A   B  [C] [D]  E  [F] [G]  H   I   J
 A   B  [C] [D]  E  [F]  G  [H]  I   J
 A   B  [C] [D]  E  [F]  G   H  [I]  J
 A   B  [C] [D]  E  [F]  G   H   I  [J] 
 A   B  [C] [D]  E   F  [G] [H]  I   J
 A   B  [C] [D]  E   F  [G]  H  [I]  J  
 A   B  [C] [D]  E   F  [G]  H   I  [J]
 A   B  [C] [D]  E   F   G  [H] [I]  J
 A   B  [C] [D]  E   F   G  [H]  I  [J] 
 A   B  [C] [D]  E   F   G   H  [I] [J]
 A   B  [C]  D  [E] [F] [G]  H   I   J
 A   B  [C]  D  [E] [F]  G  [H]  I   J  
 A   B  [C]  D  [E] [F]  G   H  [I]  J
 A   B  [C]  D  [E] [F]  G   H   I  [J]
 A   B  [C]  D  [E]  F  [G] [H]  I   J
 A   B  [C]  D  [E]  F  [G]  H  [I]  J
 A   B  [C]  D  [E]  F  [G]  H   I  [J] 
 A   B  [C]  D  [E]  F   G  [H] [I]  J
 A   B  [C]  D  [E]  F   G  [H]  I  [J]
 A   B  [C]  D  [E]  F   G   H  [I] [J] 
 A   B  [C]  D   E  [F] [G] [H]  I   J
 A   B  [C]  D   E  [F] [G]  H  [I]  J  
 A   B  [C]  D   E  [F] [G]  H   I  [J]
 A   B  [C]  D   E  [F]  G  [H] [I]  J
 A   B  [C]  D   E  [F]  G  [H]  I  [J]
 A   B  [C]  D   E  [F]  G   H  [I] [J] 
 A   B  [C]  D   E   F  [G] [H] [I]  J  
 A   B  [C]  D   E   F  [G] [H]  I  [J]
 A   B  [C]  D   E   F  [G]  H  [I] [J]
 A   B  [C]  D   E   F   G  [H] [I] [J]
 A   B   C  [D] [E] [F] [G]  H   I   J
 A   B   C  [D] [E] [F]  G  [H]  I   J
 A   B   C  [D] [E] [F]  G   H  [I]  J  
 A   B   C  [D] [E] [F]  G   H   I  [J]
 A   B   C  [D] [E]  F  [G] [H]  I   J
 A   B   C  [D] [E]  F  [G]  H  [I]  J
 A   B   C  [D] [E]  F  [G]  H   I  [J] 
 A   B   C  [D] [E]  F   G  [H] [I]  J
 A   B   C  [D] [E]  F   G  [H]  I  [J]
 A   B   C  [D] [E]  F   G   H  [I] [J] 
 A   B   C  [D]  E  [F] [G] [H]  I   J
 A   B   C  [D]  E  [F] [G]  H  [I]  J
 A   B   C  [D]  E  [F] [G]  H   I  [J]
 A   B   C  [D]  E  [F]  G  [H] [I]  J
 A   B   C  [D]  E  [F]  G  [H]  I  [J] 
 A   B   C  [D]  E  [F]  G   H  [I] [J]
 A   B   C  [D]  E   F  [G] [H] [I]  J  
 A   B   C  [D]  E   F  [G] [H]  I  [J]
 A   B   C  [D]  E   F  [G]  H  [I] [J]
 A   B   C  [D]  E   F   G  [H] [I] [J]
 A   B   C   D  [E] [F] [G] [H]  I   J
 A   B   C   D  [E] [F] [G]  H  [I]  J
 A   B   C   D  [E] [F] [G]  H   I  [J]
 A   B   C   D  [E] [F]  G  [H] [I]  J
 A   B   C   D  [E] [F]  G  [H]  I  [J]
 A   B   C   D  [E] [F]  G   H  [I] [J]
 A   B   C   D  [E]  F  [G] [H] [I]  J
 A   B   C   D  [E]  F  [G] [H]  I  [J]
 A   B   C   D  [E]  F  [G]  H  [I] [J]
 A   B   C   D  [E]  F   G  [H] [I] [J]
 A   B   C   D   E  [F] [G] [H] [I]  J
 A   B   C   D   E  [F] [G] [H]  I  [J]
 A   B   C   D   E  [F] [G]  H  [I] [J]
 A   B   C   D   E  [F]  G  [H] [I] [J]
 A   B   C   D   E   F  [G] [H] [I] [J]
```

参考上面的规律，仿照 `std::next_permutation`，设计一个 `next_combination_indexes` 函数：

* `std::vector` 型参数  `vi` 保存n的索引组合；
* 参数 `n_count` 表示 n 的个数；
* `bool` 型返回值，`true` 表示能为 `vi` 找到下一个组合，并替换了原来序列的排序；`false` 表示因为已经是最大字典序，已经没有下一个组合，原来序列的排序没有发生改变。

```c++
inline bool next_comnbination_indexes(std::vector<unsigned int> &vi, const unsigned int n_count)
{
    if (vi.size() == 0)
        return false;

    unsigned int m_ArrSize = vi.size();
    unsigned int m_LastIdx = vi.size() - 1;

    unsigned int m_SetSize = n_count;
    unsigned int m_LastSetIdx = n_count - 1;

    // Check if the last element is at the end
    if (vi[m_LastIdx] == m_LastSetIdx)
    {
        if (m_ArrSize == 1) // Completed
            return false;

        // Check if the subsequent elements(counted from back)
        // is also at their subsequent positions
        //////////////////////////////////////////////////////
        bool Completed = true;
        // Incomplete Index, init value not used
        unsigned int IncompIdx = m_LastIdx - 1;

        bool FirstIdx = false;
        unsigned int ArrIdx = m_LastIdx - 1;

        unsigned int SetIdx = m_LastSetIdx - 1;

        while (!FirstIdx)
        {
            if (vi[ArrIdx] != SetIdx)
            {
                Completed = false;
                IncompIdx = vi[ArrIdx] + 1;
                break;
            }

            if (SetIdx)
                --SetIdx;

            if (!ArrIdx)
                FirstIdx = true;
            else
                --ArrIdx;
        }

        if (Completed)
            return false;
        else
        {
            for (unsigned int i = ArrIdx; i <= m_LastIdx; ++i, ++IncompIdx)
            {
                vi[i] = IncompIdx;
            }
        }
    }
    else if (vi[m_LastIdx] < m_LastSetIdx)
    {
        (vi[m_LastIdx])++;
    }
    else // bigger than the m_LastIdx! Impossible!
    {
        return false;
    }

    return true;
}
```



 

泛型迭代器的通用版代码

```c++
template <class BidIt>
inline bool next_combination(BidIt n_begin, BidIt n_end,
                             BidIt r_begin, BidIt r_end)
{

    bool boolmarked = false;
    BidIt r_marked;

    BidIt n_it1 = n_end;
    --n_it1;

    BidIt tmp_r_end = r_end;
    --tmp_r_end;

    for (BidIt r_it1 = tmp_r_end; r_it1 != r_begin || r_it1 == r_begin; --r_it1, --n_it1)
    {
        if (*r_it1 == *n_it1)
        {
            if (r_it1 != r_begin) //to ensure not at the start of r sequence
            {
                boolmarked = true;
                r_marked = (--r_it1);
                ++r_it1; //add it back again
                continue;
            }
            else // it means it is at the start the sequence, so return false
                return false;
        }
        else //if(*r_it1!=*n_it1 )
        {
            //marked code
            if (boolmarked == true)
            {
                //for loop to find which marked is in the first sequence
                BidIt n_marked; //mark in first sequence
                for (BidIt n_it2 = n_begin; n_it2 != n_end; ++n_it2)
                    if (*r_marked == *n_it2)
                    {
                        n_marked = n_it2;
                        break;
                    }

                BidIt n_it3 = ++n_marked;
                for (BidIt r_it2 = r_marked; r_it2 != r_end; ++r_it2, ++n_it3)
                {
                    *r_it2 = *n_it3;
                }
                return true;
            }
            for (BidIt n_it4 = n_begin; n_it4 != n_end; ++n_it4)
                if (*r_it1 == *n_it4)
                {
                    *r_it1 = *(++n_it4);
                    return true;
                }
        }
    }

    return true; //will never reach here
}
```

整型数组的简化版代码

```

```

#### 基于递归实现

```c++

```

### 排列

#### 基于字典序实现

结合标准库的 next_permutation 与编写的 next_combination ，可以求排列。

```c++

```

#### 基于递归实现
