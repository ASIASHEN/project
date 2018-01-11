# C递归

递归指的是在函数的定义中使用函数自身的方法。

> 举个例子：
> 从前有座山，山里有座庙，庙里有个老和尚，正在给小和尚讲故事呢！故事是什么呢？"从前有座山，山里有座庙，庙里有个老和尚，正在给小和尚讲故事呢！故事是什么呢？'从前有座山，山里有座庙，庙里有个老和尚，正在给小和尚讲故事呢！故事是什么呢？……'"
>

语法格式如下：

```c
void recursion()
{
   recursion(); /* 函数调用自身 */
}
 
int main()
{
   recursion();
}
```

C语言支持递归，即一个函数可以调用其自身。但是使用递归时，程序员需要注意定义一个函数退出的条件，否则会进入死循环。

递归函数在解决许多数学问题上起了至关重要的作用，比如计算一个数的阶乘、生成裴波那契数列，等等。

# 数的阶乘

```c
#include<stdio.h>

double factorial(unsigned int i)
{
	if (i <= 1)
		return 1;
	else
		return i*factorial(i - 1);
}

int main()
{
	int i = 15;
	printf("15! = %lf\n", factorial(i));//%lf=1307674368000.000000精度的问题
  										//	%d=1971322880
	return 0;
}
```

---

# 裴波那契数列

下面的实例使用递归函数生成一个给定的数的斐波那契数列

```c
#include<stdio.h>

int fibonaci(int i)
{
	if(i==0)
		return 0;
	if(i==1)
		return 1;
	return fibonaci(i-2)+fibonaci(i-1);//若fibonaci(i)+fibonaci(i-1)会死循环
}

int main()
{
	int i;
	for(i=0;i<10;i++)
		printf("%d\n",fibonaci(i));
	
	return 0;
}

```

