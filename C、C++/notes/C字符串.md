# C字符串

在C语言中，字符串实际上是使用NULL字符‘\0'终止一维字符数组。因此，一个以NULL结尾的字符串，包含了组成字符串的字符。

下面的声明和初始化创建了一个“Hello”字符串。由于在数组的末尾存储了空字符，所以字符数组的大小比单词“Hello”的字符数多一个。

`char greeting[6]={'H','e','l','l','o','\0'};`

依据数组初始化规则，你可以把上面的语句写成一下语句：

`char greeting[]="Hello";`

以下是C/C++中定义的字符串的内存表示：



![C/C++ 中的字符串表示](http://www.runoob.com/wp-content/uploads/2014/08/string_representation.jpg)

其实，你不需要把BULL字符放在字符串常量的末尾。C编译器会在初始化数组时，自动把'\0'放在字符串的末尾。

```c
#include <stdio.h>

int main ()
{
   char greeting[6] = {'H', 'e', 'l', 'l', 'o', '\0'};

   printf("Greeting message: %s\n", greeting );

   return 0;
}
```

当上面的代码被编译和执行时，它会产生下列结果：

```c
Greeting message: Hello
```

C中有大量操作字符串的函数：

| 序号   | 函数&目的                                    |
| ---- | ---------------------------------------- |
| 1    | strcpy（s1,s2）；复制字符串s2到字符串s1              |
| 2    | strcat（s1,s2）；连接字符串s2到字符串s1的末尾。          |
| 3    | strlen（s1）；返回字符串s1的长度。                   |
| 4    | strcmp（s1,s2）；如果s1和s2是相同的，则返回0；如果s1<s2则返回小于0；如果s1<s2则返回大于0. |
| 5    | strchr(s1,ch);返回一个指针，指向字符串s1中字符ch的第一次出现的位置 |
| 6    | strstr(s1,s2);返回一个指针，指向字符串s1中字符串s2的第一次出现的位置。 |

