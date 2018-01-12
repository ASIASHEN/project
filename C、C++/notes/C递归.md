# C递归

1、递归趋势从下往上的进行思维。

2、在使用递归策略时，必须有一个明确地递归结束条件，称为递归出口。

额外要点：

- 递归算法解题通常显得很简洁，但递归算法解题的运行效率较低。所以一般不提倡用递归算法设计程序。
- 在递归调用的过程当中系统为每一层的返回点、局部量等开辟了栈来存储。递归次数过多容易造成栈溢出等，所以一般不提倡用递归算法设计程序。



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

---

# 从递归的经典实例开始

### 计算阶乘

　　计算阶乘是递归程序设计的一个经典示例。计算某个数的阶乘就是用那个数去乘包括 1 在内的所有比它小的数。例如，`factorial(5)` 等价于 `5*4*3*2*1`，而 `factorial(3)` 等价于 `3*2*1`。
　　阶乘的一个有趣特性是，某个数的阶乘等于起始数（starting number）乘以比它小一的数的阶乘。例如，`factorial(5)` 与 `5 * factorial(4)` 相同。您很可能会像这样编写阶乘函数：

```
int factorial(int n){
    return n * factorial(n - 1);
}
```

(*注：本文的程序示例用C语言编写*)
　　不过，这个函数的问题是，它会永远运行下去，因为它没有终止的地方。函数会连续不断地调用 `factorial`。 当计算到零时，没有条件来停止它，所以它会继续调用零和负数的阶乘。因此，我们的函数需要一个条件，告诉它何时停止。
　　由于小于 1 的数的阶乘没有任何意义，所以我们在计算到数字 1 的时候停止，并返回 1 的阶乘（即 1）。因此，真正的递归函数类似于：

```
int factorial(int n){
    if(n == 1)
        return 1;
    else
      return n * factorial(n - 1);
}
```

　　可见，只要初始值大于零，这个函数就能够终止。停止的位置称为 基线条件（base case）。基线条件是递归程序的 最底层位置，在此位置时没有必要再进行操作，可以直接返回一个结果。所有递归程序都必须至少拥有一个基线条件，而且 必须确保它们最终会达到某个基线条件；否则，程序将永远运行下去，直到程序缺少内存或者栈空间。

### 斐波纳契数列

　　[斐波纳契数列](http://zh.wikipedia.org/wiki/%E6%96%90%E6%B3%A2%E9%82%A3%E5%A5%91%E6%95%B0%E5%88%97)(Fibonacci Sequence)，最开始用于描述兔子生长的数目时用上了这数列。从数学上，费波那契数列是以递归的方法来定义：
[![img](http://newtonblogimg.qiniudn.com/Fibonacci%20Sequence.png)](http://newtonblogimg.qiniudn.com/Fibonacci%20Sequence.png)
　　这样斐波纳契数列的递归程序就可以非常清晰的写出来了：#

```
int Fibonacci(int n){
    if (n <= 1)  
        return n;  
    else  
        return Fibonacci(n-1) + Fibonacci(n-2);  
}
```

---

# 递归程序的基本步骤

​	每个递归程序都遵循相同的基本步骤：

```txt
（1）初始化算法。递归程序通常需要一个开始时使用的种子值（seed value）。要完成此任务，可以向函数传递参数，或者提供一个入口函数，这个函数是非递归，但可以为递归计算设置为种子值。
（2）检查要处理的当前值是否已经与基线条件相匹配。如果匹配，则进行处理并返回值。
（3）使用更小的或更简单的子问题（或多个子问题）来重新定义答案。
（4）对子问题运行算法。
（5）将结果合并答案的表达式。
（6）返回结果。
```
---

# 我的练习

```c
//¼ÆËã×ÔÈ»ÊýµÄºÍ
#include<stdio.h>

int addSum(int n);
int main()
{
//¶¨ÒåÒ»¸ö·Ç¸ºÕûÊý£¬²¢ÊäÈë
//ºÍsum
	//int n,sum;Î´³õÊ¼»¯
	int n,sum;
	printf("n = ");
	scanf("%d",&n);

             //forÑ­»·  ÀÛ¼Ó
/*	for(i=0;i<=n;i++)
		sum+=i;
*/

             //WhileÑ­»·
/*	while(i<=n)
	{
		sum+=i;
		i++;
	}
*/

            //Ê¹ÓÃµÝ¹é

	sum=addSum(n);

//Êä³ö½á¹ûsum
	printf("sum = %d\n",sum);

	return 0;
}

//µÝ¹é
int addSum(int n)
{
	if(n==0)
		return 0;
	return n+addSum(n-1);
}

```

