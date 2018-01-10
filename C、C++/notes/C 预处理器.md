# C 预处理器

C预处理起不是编译器的组成部分，但是它是编译过程中一个单独的步骤。简而言之，C预处理器只不过是一个文本替换工具而已，它们会指示编译器在实际编译之前完成所需的预处理。我们将把C预处理器（C Preprocessor）简写为CPP。

所有的预处理器命令都是以井号（#）开头。它必须是第一个非空字符，为了增加可读性，预处理器指令应从第一列开始。下面列出了所有重要的 预处理指令：

| 指令       | 描述                               |
| -------- | -------------------------------- |
| #define  | 定义宏                              |
| #include | 包含一个源代码文件                        |
| #undef   | 取消已定义的宏                          |
| #ifdef   | 如果宏已经定义，则返回真                     |
| #ifndef  | 如果宏没有定义，则返回真                     |
| #if      | 如果给定条件为真，则编译下面代码                 |
| #else    | #if 的替代方案                        |
| #elif    | 如果前面的 #if 给定条件不为真，当前条件为真，则编译下面代码 |
| #endif   | 结束一个 #if……#else 条件编译块            |
| #error   | 当遇到标准错误时，输出错误消息                  |
| #pragma  | 使用标准化方法，向编译器发布特殊的命令到编译器中         |

## 预处理器实例

分析下面的实例来理解不同的指令。

```
#define MAX_ARRAY_LENGTH 20
```

这个指令告诉 CPP 把所有的 MAX_ARRAY_LENGTH 替换为 20。使用 *#define* 定义常量来增强可读性。

```
#include <stdio.h>
#include "myheader.h"	
```

这些指令告诉CPP（预处理器）从系统库中获取stdio.h，并添加到文本到当前的源文件中。下一行告诉CPP从本地目录中获取myheader.h，并添加内容到当前的源文件中。

```c
#undef FILE_SIZE
#define FILE_SIZE 42
```

这个指令告诉CPP取消已定义的FILE_SIZE，并定义它为42。

```c
#ifndef MESSAGE
     #define MESSAGE "You wish!"
#endif
```

这个指令告诉CPP只有当MESSAGE未定义是，才定义MESSAGE

```c
#ifdef DEBUG
	/*your debugging statements here*/
#endif
```

这个指令告诉CPP如果定义了DEBUG，则执行处理语句。在编译时，如果你向gcc传递了DEBUG开关量，这个指令就非常有用。它定义了DEBUG，你可以在编译期间随时关闭或开启调试。

---

# 预定义宏

ANSI C 定义了许多宏。在编程中您可以使用这些宏，但是不能直接修改这些预定义的宏。

| 宏        | 描述                                |
| -------- | --------------------------------- |
| __DATE__ | 当前日期，一个以 "MMM DD YYYY" 格式表示的字符常量。 |
| __TIME__ | 当前时间，一个以 "HH:MM:SS" 格式表示的字符常量。    |
| __FILE__ | 这会包含当前文件名，一个字符串常量。                |
| __LINE__ | 这会包含当前行号，一个十进制常量。                 |
| __STDC__ | 当编译器以 ANSI 标准编译时，则定义为 1。          |

让我们来尝试下面的实例：

```c
#include <stdio.h>

main()
{
   printf("File :%s\n", __FILE__ );
   printf("Date :%s\n", __DATE__ );
   printf("Time :%s\n", __TIME__ );
   printf("Line :%d\n", __LINE__ );
   printf("ANSI :%d\n", __STDC__ );//vs 2015 __STDC_WANT_SECURE_LIB__ 

}
```

当上面的代码（在文件 **test.c** 中）被编译和执行时，它会产生下列结果：

```c
File :test.c
Date :Jun 2 2012
Time :03:36:24
Line :8
ANSI :1
```

---

# C预处理器运算符

C预处理器提供了下列的运算符来帮助你创建宏：

> 宏连续运算符（\）

一个宏通常写在一个单行上。但是如果宏太长，一个单行容不下，则使用宏的延续运算符（\）。例如：

```c
#define message_for(a,b) \
    printf(#a " and " #b ": we love you!\n");
```

> 字符串常量化运算符（#）

在