## Preface 

Countless programmers have learned C++ from previous editions of *C++ Primer*. During that time, C++ has matured greatly: Its focus, and that of its programming community, has widened from looking mostly at machine efficiency to devoting more attention to programmer efficiency.

In 2011, the C++ standards committee issued a major revision to the ISO C++ standard. This revised standard is latest step in C++’s evolution and continues the emphasis on programmer efficiency. The primary goals of the new standard are to

- Make the language more uniform and easier to teach and to learn
- Make the standard libraries easier, safer, and more efficient to use
- Make it easier to write efficient abstractions and libraries

In this edition, we have completely revised the *C++ Primer* to use the latest standard. You can get an idea of how extensively the new standard has affected C++ by reviewing the New Features Table of Contents, which lists the sections that cover new material and appears on page xxi.

Some additions in the new standard, such as `auto` for type inference, are pervasive. These facilities make the code in this edition easier to read and to understand. Programs (and programmers!) can ignore type details, which makes it easier to concentrate on what the program is intended to do. Other new features, such as smart pointers and move-enabled containers, let us write more sophisticated classes without having to contend with the intricacies of resource management. As a result, we can start to teach how to write your own classes much earlier in the book than we did in the Fourth Edition. We—and you—no longer have to worry about many of the details that stood in our way under the previous standard.

🆕We’ve marked those parts of the text that cover features defined by the new standard, with a marginal icon. We hope that readers who are already familiar with the core of C++ will find these alerts useful in deciding where to focus their attention. We also expect that these icons will help explain error messages from compilers that might not yet support every new feature. Although nearly all of the examples in this book have been compiled under the current release of the GNU compiler, we realize some readers will not yet have access to completely updated compilers. Even though numerous capabilities have been added by the latest standard, the core language remains unchanged and forms the bulk of the material that we cover. Readers can use these icons to note which capabilities may not yet be available in their compiler.

### Why Read This Book?

Modern C++ can be thought of as comprising three parts:

- The low-level language, much of which is inherited from C
- More advanced language features that allow us to define our own types and to organize large-scale programs and systems
- The standard library, which uses these advanced features to provide useful data structures and algorithms

Most texts present C++ in the order in which it evolved. They teach the C subset of C++ first, and present the more abstract features of C++ as advanced topics at the end of the book. There are two problems with this approach: Readers can get bogged down in the details inherent in low-level programming and give up in frustration. Those who do press on learn bad habits that they must unlearn later.

We take the opposite approach: Right from the start, we use the features that let programmers ignore the details inherent in low-level programming. For example, we introduce and use the library `string` and `vector` types along with the built-in arithmetic and array types. Programs that use these library types are easier to write, easier to understand, and much less error-prone.

Too often, the library is taught as an “advanced” topic. Instead of using the library, many books use low-level programming techniques based on pointers to character arrays and dynamic memory management. Getting programs that use these low-level techniques to work correctly is much harder than writing the corresponding C++ code using the library.

Throughout *C++ Primer*, we emphasize good style: We want to help you, the reader, develop good habits immediately and avoid needing to unlearn bad habits as you gain more sophisticated knowledge. We highlight particularly tricky matters and warn about common misconceptions and pitfalls.

We also explain the rationale behind the rules—explaining the why not just the what. We believe that by understanding why things work as they do, readers can more quickly cement their grasp of the language.

Although you do not need to know C in order to understand this book, we assume you know enough about programming to write, compile, and run a program in at least one modern block-structured language. In particular, we assume you have used variables, written and called functions, and used a compiler.

### Changes to the Fifth Edition

New to this edition of *C++ Primer* are icons in the margins to help guide the reader. C++ is a large language that offers capabilities tailored to particular kinds of programming problems. Some of these capabilities are of great import for large project teams but might not be necessary for smaller efforts. As a result, not every programmer needs to know every detail of every feature. We’ve added these marginal icons to help the reader know which parts can be learned later and which topics are more essential.

📖We’ve marked sections that cover the fundamentals of the language with an image of a person studying a book. The topics covered in sections marked this way form the core part of the language. Everyone should read and understand these sections.

📚We’ve also indicated those sections that cover advanced or special-purpose topics. These sections can be skipped or skimmed on a first reading. We’ve marked such sections with a stack of books to indicate that you can safely put down the book at that point. It is probably a good idea to skim such sections so you know that the capability exists. However, there is no reason to spend time studying these topics until you actually need to use the feature in your own programs.

🔍To help readers guide their attention further, we’ve noted particularly tricky concepts with a magnifying-glass icon. We hope that readers will take the time to understand thoroughly the material presented in the sections so marked. In at least some of these sections, the import of the topic may not be readily apparent; but we think you’ll find that these sections cover topics that turn out to be essential to understanding the language.

Another aid to reading this book, is our extensive use of cross-references. We hope these references will make it easier for readers to dip into the middle of the book, yet easily jump back to the earlier material on which later examples rely.

What remains unchanged is that *C++ Primer* is a clear, correct, and thorough tutorial guide to C++. We teach the language by presenting a series of increasingly sophisticated examples, which explain language features and show how to make the best use of C++.

### Structure of This Book

We start by covering the basics of the language and the library together in Parts I and II. These parts cover enough material to let you, the reader, write significant programs. Most C++ programmers need to know essentially everything covered in this portion of the book.

In addition to teaching the basics of C++, the material in Parts I and II serves another important purpose: By using the abstract facilities defined by the library, you will become more comfortable with using high-level programming techniques. The library facilities are themselves abstract data types that are usually written in C++. The library can be defined using the same class-construction features that are available to any C++ programmer. Our experience in teaching C++ is that by first using well-designed abstract types, readers find it easier to understand how to build their own types.

Only after a thorough grounding in using the library—and writing the kinds of abstract programs that the library allows—do we move on to those C++ features that will enable you to write your own abstractions. Parts III and IV focus on writing abstractions in the form of classes. Part III covers the fundamentals; Part IV covers more specialized facilities.

In Part III, we cover issues of copy control, along with other techniques to make classes that are as easy to use as the built-in types. Classes are the foundation for object-oriented and generic programming, which we also cover in Part III. C++ *Primer* concludes with Part IV, which covers features that are of most use in structuring large, complicated systems. We also summarize the library algorithms in Appendix A.

### Aids to the Reader

Each chapter concludes with a summary, followed by a glossary of defined terms, which together recap the chapter’s most important points. Readers should use these sections as a personal checklist: If you do not understand a term, restudy the corresponding part of the chapter.

We’ve also incorporated a number of other learning aids in the body of the text:

- Important terms are indicated in **bold**; important terms that we assume are already familiar to the reader are indicated in ***bold italics***. Each term appears in the chapter’s Defined Terms section.
- Throughout the book, we highlight parts of the text to call attention to important aspects of the language, warn about common pitfalls, suggest good programming practices, and provide general usage tips.
- To make it easier to follow the relationships among features and concepts, we provide extensive forward and backward cross-references.
- We provide sidebar discussions on important concepts and for topics that new C++ programmers often find most difficult.
- Learning any programming language requires writing programs. To that end, the Primer provides extensive examples throughout the text. Source code for the extended examples is available on the Web at the following URL: http://www.informit.com/title/032174113

### A Note about Compilers

As of this writing (July, 2012), compiler vendors are hard at work updating their compilers to match the latest ISO standard. The compiler we use most frequently is the GNU compiler, version 4.7.0. There are only a few features used in this book that this compiler does not yet implement: inheriting constructors, reference qualifiers for member functions, and the regular-expression library.

### Acknowledgments

In preparing this edition we are very grateful for the help of several current and former members of the standardization committee: Dave Abrahams, Andy Koenig, Stephan T. Lavavej, Jason Merrill, John Spicer, and Herb Sutter. They provided invaluable assistance to us in understanding some of the more subtle parts of the new standard. We’d also like to thank the many folks who worked on updating the GNU compiler making the standard a reality.

As in previous editions of *C++ Primer*, we’d like to extend our thanks to Bjarne Stroustrup for his tireless work on C++ and for his friendship to the authors during most of that time. We’d also like to thank Alex Stepanov for his original insights that led to the containers and algorithms at the core of the standard library. Finally, our thanks go to all the C++ Standards committee members for their hard work in clarifying, refining, and improving C++ over many years.

## Chapter 1. Getting Started 

This chapter introduces most of the basic elements of C++: types, variables, expressions, statements, and functions. Along the way, we’ll briefly explain how to compile and execute a program.

After having read this chapter and worked through the exercises, you should be able to write, compile, and execute simple programs. Later chapters will assume that you can use the features introduced in this chapter, and will explain these features in more detail.

The way to learn a new programming language is to write programs. In this chapter, we’ll write a program to solve a simple problem for a bookstore.

Our store keeps a file of transactions, each of which records the sale of one or more copies of a single book. Each transaction contains three data elements:<br>
**0-201-70353-X 4 24.99**<br>
The first element is an ISBN (International Standard Book Number, a unique book identifier), the second is the number of copies sold, and the last is the price at which each of these copies was sold. From time to time, the bookstore owner reads this file and for each book computes the number of copies sold, the total revenue from that book, and the average sales price.

To be able to write this program, we need to cover a few basic C++ features. In addition, we’ll need to know how to compile and execute a program.

Although we haven’t yet designed our program, it’s easy to see that it must

- Define variables
- Do input and output
- Use a data structure to hold the data
- Test whether two records have the same ISBN
- Contain a loop that will process every record in the transaction file

We’ll start by reviewing how to solve these subproblems in C++ and then write our bookstore program.

### 1.1. Writing a Simple C++ Program 

Every C++ program contains one or more **functions**, one of which must be named `main`. The operating system runs a C++ program by calling `main`. Here is a simple version of main that does nothing but return a value to the operating system:

```c++
int main()
{
    return 0;
}
```

A function definition has four elements: a **return type**, a **function name**, a (possibly empty) parameter list enclosed in parentheses, and a function body. Although `main` is special in some ways, we define `main` the same way we define any other function.

In this example, `main` has an empty list of parameters (shown by the () with nothing inside). § 6.2.5 (p. 218) will discuss the other parameter types that we can define for `main`.

The `main` function is required to have a return type of `int`, which is a type that represents integers. The `int` type is a **built-in type**, which means that it is one of the types the language defines.

The final part of a function definition, the function body, is a **block** of **statements** starting with an open curly brace and ending with a **close curly**:

```C++
{
    return 0;
}
```

The only statement in this block is a `return`, which is a statement that terminates a function. As is the case here, a `return` can also send a value back to the function’s caller. When a `return` statement includes a value, the value returned must have a type that is compatible with the return type of the function. In this case, the return type of main is `int` and the return value is 0, which is an `int`.

> 📝**Note**
>
> Note the semicolon at the end of the `return` statement. Semicolons mark the end of most statements in C++. They are easy to overlook but, when forgotten, can lead to mysterious compiler error messages.

On most systems, the value returned from `main` is a status indicator. A return value of 0 indicates success. A nonzero return has a meaning that is defined by the system. Ordinarily a nonzero return indicates what kind of error occurred.

> **Key Concept: Types**
>
> Types are one of the most fundamental concepts in programming and a concept that we will come back to over and over in this Primer. A type defines both the contents of a data element and the operations that are possible on those data.
>
> The data our programs manipulate are stored in variables and every variable has a type. When the type of a variable named `v` is `T`, we often say that “v has type T” or, interchangeably, that “v is a T.”

#### 1.1.1 Compiling and Executing Our Program

Having written the program, we need to compile it. How you compile a program depends on your operating system and compiler. For details on how your particular compiler works, check the reference manual or ask a knowledgeable colleague.

Many PC-based compilers are run from an integrated development environment (IDE) that bundles the compiler with build and analysis tools. These environments can be a great asset in developing large programs but require a fair bit of time to learn how to use effectively. Learning how to use such environments is well beyond the scope of this book.

Most compilers, including those that come with an IDE, provide a command-line interface. Unless you already know the IDE, you may find it easier to start with the command-line interface. Doing so will let you concentrate on learning C++ first. Moreover, once you understand the language, the IDE is likely to be easier to learn.

##### Program Source File Naming Convention

Whether you use a command-line interface or an IDE, most compilers expect program source code to be stored in one or more files. Program files are normally referred to as a **source files**. On most systems, the name of a source file ends with a suffix, which is a period followed by one or more characters. The suffix tells the system that the file is a C++ program. Different compilers use different suffix conventions; the most common include `·`, `.cxx`, `.cpp`, `.cp`, and `.C`.

##### Running the Compiler from the Command Line

If we are using a command-line interface, we will typically compile a program in a console window (such as a shell window on a UNIX system or a Command Prompt window on Windows). Assuming that our `main` program is in a file named `prog1.cc`, we might compile it by using a command such as

```shell
$ CC prog1.cc
```

where `CC` names the compiler and `$` is the system prompt. The compiler generates an executable file. On a Windows system, that executable file is named `prog1.exe`. UNIX compilers tend to put their executables in files named `a.out`.

To run an executable on Windows, we supply the executable file name and can omit the `.exe` file extension:

```powershell
$ prog1
```

On some systems you must specify the file’s location explicitly, even if the file is in the current directory or folder. In such cases, we would write

```powershell
$ .\prog1
```

The “.” followed by a backslash indicates that the file is in the current directory.

To run an executable on UNIX, we use the full file name, including the file extension:

```shell
$ a.out
```

If we need to specify the file’s location, we’d use a “.” followed by a forward slash to indicate that our executable is in the current directory:

```shell
$ ./a.out
```

The value returned from `main` is accessed in a system-dependent manner. On both UNIX and Windows systems, after executing the program, you must issue an appropriate `echo` command.

On UNIX systems, we obtain the status by writing

```shell
$ echo $?
```

To see the status on a Windows system, we write

```powershell
$ echo %ERRORLEVEL%
```

> **Running the GNU or Microsoft Compilers**
>
> The command used to run the C++ compiler varies across compilers and operating systems. The most common compilers are the GNU compiler and the Microsoft Visual Studio compilers. By default, the command to run the GNU compiler is `g++`:
>
> ```powershell
> $ g++ -o prog1 prog1.cc
> ```
>
> Here `$` is the system prompt. The `-o prog1` is an argument to the compiler and names the file in which to put the executable file. This command generates an executable file named `prog1` or `prog1.exe`, depending on the operating system. On UNIX, executable files have no suffix; on Windows, the suffix is `.exe`. If the `-o prog1` is omitted, the compiler generates an executable named a.out on UNIX systems and a.exe on Windows. (Note: Depending on the release of the GNU compiler you are using, you may need to specify `-std=c++0x` to turn on C++ 11 support.)
>
> The command to run the Microsoft Visual Studio 2010 compiler is cl:
>
> ```powershell
> C:\Users\me\Programs> cl /EHsc prog1.cpp
> ```
>
> Here `C:\Users\me\Programs>` is the system prompt and `\Users\me\Programs` is the name of the current directory (aka the current folder). The cl command invokes the compiler, and `/EHsc` is the compiler option that turns on standard exception handling. The Microsoft compiler automatically generates an executable with a name that corresponds to the first source file name. The executable has the suffix .`exe` and the same name as the source file name. In this case, the executable is named `prog1.exe`.
>
> Compilers usually include options to generate warnings about problematic constructs. It is usually a good idea to use these options. Our preference is to use -`Wall` with the GNU compiler, and to use `/W4` with the Microsoft compilers.
>
> For further information consult your compiler’s user’s guide.

> ​	**Exercises Section 1.1.1**
>
> **Exercise 1.1**: Review the documentation for your compiler and determine what file naming convention it uses. Compile and run the `main` program from page 2.
>
> **Exercise 1.2**: Change the program to return `-1`. A return value of `-1` is often treated as an indicator that the program failed. Recompile and rerun your program to see how your system treats a failure indicator from `main`.

### 1.2. A First Look at Input/Output 

The C++ language does not define any statements to do input or output (IO). Instead, C++ includes an extensive **standard library** that provides IO (and many other facilities). For many purposes, including the examples in this book, one needs to know only a few basic concepts and operations from the IO library. 

Most of the examples in this book use the **iostream** library. Fundamental to the iostream library are two types named **istream** and ostream, which represent input and output streams, respectively. A stream is a sequence of characters read from or written to an IO device. The term stream is intended to suggest that the characters are generated, or consumed, sequentially over time. 

##### Standard Input and Output Objects 

The library defines four IO objects. To handle input, we use an object of type `istream` named `cin` 
(pronounced see-in). This object is also referred to as the **standard input**. For output, we use an `ostream` object named `cout` (pronounced see-out). This object is also known as the **standard output**. The library also defines two other `ostream` objects, named `cerr` and `clog` (pronounced see-err and see-log, respectively). We typically use `cerr`, referred to as the **standard error**, for warning and error messages and `clog` for general information about the execution of the program. 

Ordinarily, the system associates each of these objects with the window in which the program is executed. So, when we read from `cin`, data are read from the window in which the program is executing, and when we write to `cout`, `cerr`, or `clog`, the output is written to the same window. 

##### A Program That Uses the IO Library 

In our bookstore problem, we'll have several records that we'll want to combine into a single total. As a simpler, related problem, let's look first at how we might add two numbers. Using the IO library, we can extend our `main` program to prompt the user to give us two numbers and then print their sum: 

```c++
# include <iostream> 
int main() 
{
  std::cout << "Enter two numbers:" << std::endl; 
  int v1 = 0, v2 = 0; 
  std::cin >> v1 >> v2; 
  std::cout << "The sum of " << v1 << " and " << v2 
    << " is " << v1 + v2 << std::endl; 
  return 0; 
} 
```

This program starts by printing 
	**Enter two numbers:** 
on the user's screen and then waits for input from the user. If the user enters
	**37**
followed by a newline, then the program produces the following output: 
	**The sum of 3 and 7 is 10** 
The first line of our program 

```c++
include <iostream>
```

tells the compiler that we want to use the `iostream` library. The name inside angle brackets (`iostream` in this case) refers to a **header**. Every program that uses a library facility must include its associated header. The `#include` directive must be written on a single line'the name of the header and the `#include` must appear on the same line. In general, `#include` directives must appear outside any function. Typically, we put all the `#include` directives for a program at the beginning of the source file. 

##### Writing to a Stream 

The first statement in the body of `main` executes an **expression**. In C++ an expression yields a result and is composed of one or more operands and (usually) an operator. The expressions in this statement use the output operator (the . operator) to print a message on the standard output: 

```C++
std::cout << "Enter two numbers:" << std::endl; 
```

The `<<` operator takes two operands: The left-hand operand must be an `ostream` object; the right-hand operand is a value to print. The operator writes the given value on the given `ostream`. The result of the output operator is its left-hand operand. That is, the result is the `ostream` on which we wrote the given value. 

Our output statement uses the `<<` operator twice. Because the operator returns its left-hand operand, the result of the first operator becomes the left-hand operand of the second. As a result, we can chain together output requests. Thus, our expression is equivalent to 

```c++
(std::cout << "Enter two numbers:") << std::endl; 
```

Each operator in the chain has the same object as its left-hand operand, in this case `std::cout`. Alternatively, we can generate the same output using two statements: 

```c++
std::cout << "Enter two numbers:"; 
std::cout << std::endl; 
```

The first output operator prints a message to the user. That message is a **string literal**, which is a sequence of characters enclosed in double quotation marks. The text between the quotation marks is printed to the standard output. 

The second operator prints `endl`, which is a special value called a **manipulator**. Writing `endl` has the effect of ending the current line and flushing the **buffer** associated with that device. 

Flushing the buffer ensures that all the output the program has generated so far is actually written to the output stream, rather than sitting in memory waiting to be written. 

> ⚠️**Warning** 
>
> Programmers often add print statements during debugging. Such statements should *always* flush the stream. Otherwise, if the program crashes, output may be left in the buffer, leading to incorrect inferences about where the program crashed. 

##### Using Names from the Standard Library 

Careful readers will note that this program uses `std::cout` and `std::endl` rather than just `cout` and `endl`. The prefix std:: indicates that the names cout and endl are defined inside the **namespace** named `std`. Namespaces allow us to avoid inadvertent collisions between the names we define and uses of those same names inside a library. All the names defined by the standard library are in the `std` namespace. 

One side effect of the library's use of a namespace is that when we use a name from the library, we must say explicitly that we want to use the name from the std namespace. Writing `std::cout` uses the scope operator (the **:: operator**) to say that we want to use the name `cout` that is defined in the namespace `std`. § 3.1 
(p. 82) will show a simpler way to access names from the library. 

##### Reading from a Stream 

Having asked the user for input, we next want to read that input. We start by defining two **variables** named `v1` and `v2` to hold the input: 

```c++
int v1 = 0, v2 =0; 
```

We define these variables as type `int`, which is a built-in type representing integers. We also initialize 
them to `0`. When we **initialize** a variable, we give it the indicated value at the same time as the variable is created. 

The next statement 

```c++
std::cin >> v1 >> v2; 
```

reads the input. The input operator (the **>> operator**) behaves analogously to the output operator. It takes an `istream` as its left-hand operand and an object as its right-hand operand. It reads data from the given `istream` and stores what was read in the given object. Like the output operator, the input operator returns its left-hand operand as its result. Hence, this expression is equivalent to 

```c++
(std::cin >> v1) >> v2;
```

Because the operator returns its left-hand operand, we can combine a sequence of input requests into a single statement. Our input operation reads two values from `std::cin`, storing the first in `v1` and the second in `v2`. In other words, our input operation executes as 

```c++
std::cin >> v1; 
std::cin >> v2; 
```

##### Completing the Program 

What remains is to print our result: 

```c++
std::cout << "The sum of " << v1 << " and " << v2 << " is " << v1 + v2 << std::endl; 
```

This statement, although longer than the one that prompted the user for input, is conceptually similar. It prints each of its operands on the standard output. What is interesting in this example is that the operands are not all the same kinds of values. Some operands are string literals, such as "The sum of ". 

Others are int values, such as `v1`, `v2`, and the result of evaluating the arithmetic expression `v1 + v2`. The library defines versions of the input and output operators that handle operands of each of these differing types. 

> ​	**Exercises Section 1.2**
>
> **Exercise 1.3**: Write a program to print Hello, World on the standard output. 
>
> **Exercise 1.4**: Our program used the addition operator, +, to add two numbers. Write a program that uses the multiplication operator, *, to print the product instead. 
>
> **Exercise 1.5**: We wrote the output in one large statement. Rewrite the program to use a separate statement to print each operand. 
>
> **Exercise 1.6**: Explain whether the following program fragment is legal. 
>
> ```c++
> std::cout << "The sum of " << v1; 
> << " and " << v2; 
> << " is " << v1 + v2 << std::endl; 
> ```
>
> If the program is legal, what does it do? If the program is not legal, why not? How would you fix it? 

### 1.3. A Word about Comments 

Before our programs get much more complicated, we should see how C++ handles comments. Comments help the human readers of our programs. They are typically used to summarize an algorithm, identify the purpose of a variable, or clarify an otherwise obscure segment of code. The compiler ignores comments, so they have no effect on the program's behavior or performance. 

Although the compiler ignores comments, readers of our code do not. Programmers tend to believe comments even when other parts of the system documentation are out of date. An incorrect comment is worse than no comment at all because it may mislead the reader. When you change your code, be sure to update the comments, too! 

##### Kinds of Comments in C++ 

There are two kinds of comments in C++: single-line and paired. A single-line comment starts with a double slash (`//`) and ends with a newline. Everything to the right of the slashes on the current line is ignored by the compiler. A comment of this kind can contain any text, including additional double slashes. 

The other kind of comment uses two delimiters (`/*` and `*/`) that are inherited from C. Such comments begin with a `/*` and end with the next `*/`. These comments can include anything that is not a `*/`, including newlines. The compiler treats everything that falls between the `/*` and `*/` as part of the comment. 

A comment pair can be placed anywhere a tab, space, or newline is permitted. Comment pairs can span multiple lines of a program but are not required to do so. When a comment pair does span multiple lines, it is often a good idea to indicate visually that the inner lines are part of a multiline comment. Our style is to begin each line in the comment with an asterisk, thus indicating that the entire range is part of a multiline comment. 

Programs typically contain a mixture of both comment forms. Comment pairs generally are used for multiline explanations, whereas double-slash comments tend to be used for half-line and single-line remarks: 

```c++
# include <iostream>
/*
 * Simple main function: 
 * Read two numbers and write their sum 
*/ 
int main()
{
  // prompt user to enter two numbers 
  std::cout << "Enter two numbers:" << std::endl; 
  int v1 =0, v2 =0; // variables to hold the input we read
  std::cin >> v1 >> v2; // read input
  std::cout << "The sum of " << v1 << " and " << v2
    << " is " << v1 + v2 << std::endl;
  return 0;
}
```

> 📝**Note** 
> In this book, we italicize comments to make them stand out from the normal program text. In actual programs, whether comment text is distinguished from the text used for program code depends on the sophistication of the programming environment you are using. 

##### Comment Pairs Do Not Nest 

A comment that begins with `/*` ends with the next `*/`. As a result, one comment pair cannot appear inside another. The compiler error messages that result from this kind of mistake can be mysterious and confusing. As an example, compile the following program on your system: 

```C++
/*
 * comment pairs /* */ cannot nest. 
 * "cannot nest" is considered source code, 
 * as is the rest of the program
*/ 
int main() 
{ 
  return 0; 
} 
```

We often need to comment out a block of code during debugging. Because that code might contain nested comment pairs, the best way to comment a block of code is to insert single-line comments at the beginning of each line in the section we want to ignore: 

```c++
// /* 
// * everything inside a single-line comment is ignored 
// * including nested comment pairs 
// */ 
```

> ​	**Exercises Section 1.3** 
> **Exercise 1.7**: Compile a program that has incorrectly nested comments. 
> **Exercise 1.8**: Indicate which, if any, of the following output statements are legal: 
>
> ```C++
> std::cout << "/*"; 
> std::cout << "*/"; 
> std::cout << /* "*/" */; 
> std::cout << /* "*/" /* "/*" */; 
> ```
>
> After you've predicted what will happen, test your answers by compiling a program with each of these statements. Correct any errors you encounter. 