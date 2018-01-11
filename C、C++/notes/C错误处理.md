# C错误处理

C语言不提供对错误处理的直接支持，但是作为一种系统编程语言，它以返回值得形式允许你访问底层数据。在发生错误时，大多数的C或UNIX函数调用返回1或NULL，同时会设置一个错误代码errno，该错误代码是全局变量，表示在函数调用期间发生了错误。你可以在<error.h>头文件找到各种各样的错误代码。

所以，C程序员可以通过检查返回值，然后根据返回值决定采取哪种适当的动作。开发人员应该在程序初始化时，把error设置为0，这是一种良好的编程习惯。0值表示程序中没有错误。

---

# errno、perror()和strerror()

C语言提供了perror()和strerror()函数来显示与errno相关的文本消息。

- perror()函数显示你传给它的字符串，后跟一个冒号、一个空格和当前errno值得文本表示形式。
- strerror()函数，返回一个指针，指针指向当前errno值得文本表示。

让我们来模拟一种错误情况，尝试打开一个不存在的文件。你可以使用多种方式来输出错误消息，在这里我们使用函数来演示用法。另外有一点需要注意，你应该使用stderr文件流来输出所有的错误。

```c
#include<stdio.h>
#include<errno.h>
#include<string.h>

extern int errno;//错误代码errno，该错误代码是全局变量，表示在函数调用期间发生了错误。在<error.h>头文件中找到各种各种的错误代码。

int main()
{
	FILE*pf;//初始化类型FILE的一个对象，类型FILe包含了所有用来控制流的必要信息
	
	int errnum;
	pf=fopen("unexist.txt","rb");//r:打开一个已有的文本文件，允许读取文件
								 //rb:如果处理的是二进制文件，则需要使用下面的访问模式来取代上面的访问模式	
	if(pf==NULL)
	{
		errnum=errno;
		fprintf(stderr,"错误号：%d\n",errno);
		perror("通过perror输出错误");//perror()函数显示你传给你的字符串，后跟一个冒号：一个空格和当前errno值的文本表示形式
		fprintf(stderr,"打开文件错误：%s\n",strerror(errnum));//strerror()函数，返回一个指针，指针指向当前errno值的文本表示形式。
	}
	else
	{
		fclose(pf);//关闭文件
	}
	return 0;
}
```

当上面的代码被编译和执行时，它会产生下列结果：

```c
错误号: 2
通过 perror 输出错误: No such file or directory
打开文件错误: No such file or directory
```

---

```c
在进行除法运算时，如果不检查除数是否为零，则会导致一个运行时错误。

为了避免这种情况发生，下面的代码在进行除法运算前会先检查除数是否为零：

#include <stdio.h>
#include <stdlib.h>

main()
{
   int dividend = 20;
   int divisor = 0;
   int quotient;
 
   if( divisor == 0){
      fprintf(stderr, "除数为 0 退出运行...\n");
      exit(-1);
   }
   quotient = dividend / divisor;
   fprintf(stderr, "quotient 变量的值为 : %d\n", quotient );

   exit(0);
}
当上面的代码被编译和执行时，它会产生下列结果：

除数为 0 退出运行...
```

---

## 程序退出状态

通常情况下，程序成功执行完一个操作正常退出的时候会带有值 EXIT_SUCCESS。在这里，EXIT_SUCCESS 是宏，它被定义为 0。

如果程序中存在一种错误情况，当您退出程序时，会带有状态值 EXIT_FAILURE，被定义为 -1。所以，上面的程序可以写成：

```c
#include <stdio.h>
#include <stdlib.h>

main()
{
   int dividend = 20;
   int divisor = 5;
   int quotient;
 
   if( divisor == 0){
      fprintf(stderr, "除数为 0 退出运行...\n");//unix标准输出（设备）文件，对应终端的屏幕。进程将从标准输入文件中得到输入数据，将正常输出数据输出到标准输出文件，而将错误信息送到标准错误文件中。在C中，程序执行时，一直处于开启状态。
      exit(EXIT_FAILURE);
   }
   quotient = dividend / divisor;
   fprintf(stderr, "quotient 变量的值为: %d\n", quotient );

   exit(EXIT_SUCCESS);
}
```

当上面的代码被编译和执行时，它会产生下列结果：

```c
quotient 变量的值为 : 4
```

