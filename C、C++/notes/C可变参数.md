# C可变参数

有时，你可能会碰到这样的情况，你希望函数带有可变数量的参数，而不是预定义数量的参数。C语言为这种情况提供了一个解决方案，它允许你定义一个函数，能根据具体的需求接受可变数量的参数。下面的实例演示了这种函数的定义。

```c
int func(int,...)
{
 .
 .
 .  
}

int main()
{
  func(2,2,3);
  func(3,2,3,4);
}
```

请注意，函数func()最后一个参数写成省略号，即三个点号(...)，省略号之前的那个参数是int，代表了要传递的可变参数总数。为了使用这个功能，你需要使用stdarg.h头文件，该文件提供了实现可变参数功能的函数 与宏。具体步骤如下：

- 定义一个函数，最后一个参数为省略号，省略号前面可以设置自定义参数。
- 在函数定义中创建一个va_list类型变量，该类型是在stdarg.h头文件中定义的。
- 使用int参数和va_start宏来初始化va_list变量为一个参数列表。宏va_start是在stdarg.h头文件中定义
- 使用va_ar宏和va_list变量来访问参数列表中的每个项。
- 使用宏va_end来清理赋予va_list变量的内存。

```c
#include<stdio.h>
#include<stdarg.h>
//该文件提供了实现可变参数的功能的函数和宏
double average(int num,...)//1、定义一个函数，最后一个参数为省略号，省略号前面可以设置自定义参数。
{
	va_list valist;//2、在函数定义中创建一个va_list类型变量，该类型是在stdarg.h头文件中定义的。
	double sum=0.0;
	int i;

	/*为num个参数初始化*/
	va_start(valist,num);//使用int参数和va_start宏来初始化va_list变量为一个参数列表。宏va_start是在stdarg.h头文件中定义的

	/*访问所有赋给valist的参数*/
	for(i=0;i<num;i++)
	{
		sum+=va_arg(valist,int);//使用va_arg 宏 和va_list 变量 来访问参数列表中的每个项。
	}
	/*清理为valist保留的内存*/
	va_end(valist);//使用宏va_end来清理赋予va_list变量的内存

	return sum/num;
}

int main()
{
	printf("average: %f\n",average(4,2,3,4,5));//4表示可变参数的总数
	printf("average: %f\n",average(3,5,10,15));//3表示可变参数的总数
}


```