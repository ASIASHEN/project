# C语言学习笔记第一部分

### 枚举

~~~c
enum color{black,red=5,green,yellow};

enum color b=black;
printf("black=%d\n",b);

enum color r=red;
printf("red=%d\n",r);

enum color g=green;
printf("greeen=%d\n",g);

enum color y=yellow;
printf("yellow=%d\n",y);
~~~

#### 输出：

```c
black=0
red=5
green=6
yellow=7
```

枚举成员的值可以相同

~~~c
enum {BLACK=1,RED,GREEN=1,YELLOW};

printf("black=%d\n",BLACK);
printf("red=%d\n",RED);
printf("gree=%d\n",GREEN);
printf("yellow=%d\n",YELLOW);
~~~

### 整数常量

常量类型很重要，可以通过后缀来区分类型

```c
0x200->int
0x200 -> int
200U -> unsigned int

0L -> long
0xf0f0UL -> unsigned long

0777LL -> long long
0xFFULL -> unsigned long long
```

### 语句块

语句块代表了一个作用域，在语句块内声明的自动变量超出范围后立即释放。除了用“{...}”表示一个常规语句块外，还可以直接用于复杂的赋值操作，这在宏中经常使用。

```c
int =({char a='a';a++;a;});
printf("%d\n",i);
```

