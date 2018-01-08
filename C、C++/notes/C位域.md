# C位域

如果出现的结构中包含多个开关量，只有TRUE/FALSE变量，如下：

```c
struct
  {
  unsigned int widthValidated;
  unsigned int heightValidated;
}status;
```

这种结构需要8字节的内存空间，但实际上，在每个变量上，我们只存储0或1。在这种情况下，C语言提供了一种更好的利用内存空间的方式。如果你在结构内使用这样的变量，你可以定义变量的宽度来告诉编译器，你将只使用这些字节，例如，上面的结构可以重写成：

```c
struct
{
  unsigned int widthValidated : 1;
  unsigned int heightValidated : 1;
} status;
```

现在，上面的结构中，status变量将占用4个字节的内存空间，但是只有2位被用来存储值。如果你用了32个变量，每一个变量宽度为1位，那么status结构将使用4个字节，但只要你再多用一个变量，如果使用了33个变量，那么它将分配内存的下一段来存储第33个变量，这个时候就开始使用8个字节。让我们看看下面的实例来理解这个概念：

```c
#include<stdio.h>
#include<string.h>

/*定义简单的结构*/
struct 
{
	unsigned int widthValidated;
	unsigned int heightValidated;
}status1;

/*定义位域结构*/
struct
{
	unsigned int widthValidated : 1;
	unsigned int geightValidated : 1;
}status2;

int main()
{
	printf("Memory size occupied by status1:%d\n", sizeof(status1));
	printf("Memory size occupied by status2:%d\n", sizeof(status2));

	return 0;
}
```

当上面的代码被编译和执行时，它会产生下列结果：

```c
Memory size occupied by status1 : 8
Memory size occupied by status2 : 4
```

## 位域声明

在结构内声明位域的形式如下：

```
struct
{
  type [member_name] : width ;
};
```

下面是有关位域中变量元素的描述：

| 元素          | 描述                                    |
| ----------- | ------------------------------------- |
| type        | 整数类型，决定了如何解释位域的值。类型可以是整型、有符号整型、无符号整型。 |
| member_name | 位域的名称。                                |
| width       | 位域中位的数量。宽度必须小于或等于指定类型的位宽度。            |

带有预定义宽度的变量被称为**位域**。位域可以存储多于 1 位的数，例如，需要一个变量来存储从 0 到 7 的值，您可以定义一个宽度为 3 位的位域，如下：

```c
struct
{
  unsigned int age : 3;
} Age;
```

上面的结构定义指示 C 编译器，age 变量将只使用 3 位来存储这个值，如果您试图使用超过 3 位，则无法完成。让我们来看下面的实例：

```c
#include <stdio.h>
#include <string.h>

struct
{
  unsigned int age : 3;
} Age;

int main( )
{
   Age.age = 4;
   printf( "Sizeof( Age ) : %d\n", sizeof(Age) );
   printf( "Age.age : %d\n", Age.age );

   Age.age = 7;
   printf( "Age.age : %d\n", Age.age );

   Age.age = 8;
   printf( "Age.age : %d\n", Age.age );

   return 0;
}
```

当上面的代码被编译时，它会带有警告，当上面的代码被执行时，它会产生下列结果：

```c
Sizeof( Age ) : 4
Age.age : 4
Age.age : 7
Age.age : 0
```