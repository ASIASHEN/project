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

---

```c
double firstNumber,secondNumber,product;
printf("输入两个浮点数：");

//用户输入两个浮点数
scanf("%lf %lf",&firstNumber,&secondNumber);
/*%f和%lf分别是float类型和double类型用于格式化输入输出时对应的格式符号。
其中：
float，单精度浮点型，对应%f.
double,双精度浮点型，对应%lf.
在用于输出时:
float类型可以使用%lf格式，但不会有任何好处。
double类型如果使用了%f格式可能会导致输出错误。
在用于输入时:
double 类型使用了%f格式，会导致输入值错误。
float类型使用double类型不仅会导致输入错误，还可能引起程序崩溃。
所以在输入输出时，一定要区分好double和float，而使用对应的格式符号。*/

//两个浮点数相乘
product=firstNumber*secondNumber;

//输出结果，%。2lf保留两位小数
printf("结果 = %.2lf\n",product);

return 0;
```
---

ASCII 定义了 128 个字符。

**分类：**

- 一：0-31、127（删除键）是控制字符
- 二：空白字符：空格（32）、 制表符、 垂直制表符、 换行、 回车。
- 三：可显示字符：a-z、A-Z、0-9、~、！、@、、%、^、&、#、$、*、（、）、-、+、{、}、[、]、'、"、<、>、，、？、/、|、\、_、：、;、.，还有顿号、。

**ASCII 表：**

| ASCII值 | 控制字符 | ASCII值 | 控制字符    | ASCII值 | 控制字符 | ASCII值 | 控制字符 |
| ------ | ---- | ------ | ------- | ------ | ---- | ------ | ---- |
| 0      | NUT  | 32     | (space) | 64     | @    | 96     | 、    |
| 1      | SOH  | 33     | !       | 65     | A    | 97     | a    |
| 2      | STX  | 34     | "       | 66     | B    | 98     | b    |
| 3      | ETX  | 35     | #       | 67     | C    | 99     | c    |
| 4      | EOT  | 36     | $       | 68     | D    | 100    | d    |
| 5      | ENQ  | 37     | %       | 69     | E    | 101    | e    |
| 6      | ACK  | 38     | &       | 70     | F    | 102    | f    |
| 7      | BEL  | 39     | ,       | 71     | G    | 103    | g    |
| 8      | BS   | 40     | (       | 72     | H    | 104    | h    |
| 9      | HT   | 41     | )       | 73     | I    | 105    | i    |
| 10     | LF   | 42     | *       | 74     | J    | 106    | j    |
| 11     | VT   | 43     | +       | 75     | K    | 107    | k    |
| 12     | FF   | 44     | ,       | 76     | L    | 108    | l    |
| 13     | CR   | 45     | -       | 77     | M    | 109    | m    |
| 14     | SO   | 46     | .       | 78     | N    | 110    | n    |
| 15     | SI   | 47     | /       | 79     | O    | 111    | o    |
| 16     | DLE  | 48     | 0       | 80     | P    | 112    | p    |
| 17     | DCI  | 49     | 1       | 81     | Q    | 113    | q    |
| 18     | DC2  | 50     | 2       | 82     | R    | 114    | r    |
| 19     | DC3  | 51     | 3       | 83     | S    | 115    | s    |
| 20     | DC4  | 52     | 4       | 84     | T    | 116    | t    |
| 21     | NAK  | 53     | 5       | 85     | U    | 117    | u    |
| 22     | SYN  | 54     | 6       | 86     | V    | 118    | v    |
| 23     | TB   | 55     | 7       | 87     | W    | 119    | w    |
| 24     | CAN  | 56     | 8       | 88     | X    | 120    | x    |
| 25     | EM   | 57     | 9       | 89     | Y    | 121    | y    |
| 26     | SUB  | 58     | :       | 90     | Z    | 122    | z    |
| 27     | ESC  | 59     | ;       | 91     | [    | 123    | {    |
| 28     | FS   | 60     | <       | 92     | /    | 124    | \|   |
| 29     | GS   | 61     | =       | 93     | ]    | 125    | }    |
| 30     | RS   | 62     | >       | 94     | ^    | 126    | `    |
| 31     | US   | 63     | ?       | 95     | _    | 127    | DEL  |

---

```c
#include <stdio.h>
int main()
{
    char c;
    printf("输入一个字符: ");
 
    // 读取用户输入
    scanf("%c", &c);  
    
    // %d 显示整数
    // %c 显示对应字符
    printf("%c 的 ASCII 为 %d", c, c);
  	//A,a相差32
    return 0;
}
```

---

```c
#include <stdio.h>
#include<stdlib.h>
int main(){
 
    int dividend, divisor, quotient, remainder;
 
    printf("输入被除数: ");
    scanf("%d", &dividend);
 
    printf("输入除数: ");
    scanf("%d", &divisor);
 	
	if(divisor==0)
	{
		fprintf(stderr,"ÊäÈë´íÎó£¡\n");
      /*fprintf是C/C++中的一个格式化写—库函数，位于头文件<stdio.h>中，其作用是格式化输出到一个流/文件中；函数原型为int fprintf( FILE *stream, const char *format, [ argument ]...)，fprintf()函数根据指定的格式(format)向输出流(stream)写入数据(argument)。*/
      //stderr: unix标准输出(设备)文件，对应终端的屏幕。进程将从标准输入文件中得到输入数据，将正常输出数据输出到标准输出文件，而将错误信息送到标准错误文件中。在C中，程序执行时，一直处于开启状态。

		exit(-1);
	}
  
    // 计算商
    quotient = dividend / divisor;
 
    // 计算余数
    remainder = dividend % divisor;
 
    printf("商 = %d\n", quotient);
    printf("余数 = %d", remainder);
 
    return 0;
}
```

---

```c
#include <stdio.h>
 
int main()
{
    char c;
   //scanf("%c",&c);
  /*在VC中编译c程序，在一个大括号括起的范围内，如果变量声明放在了函数调用的后面，那么编译的时候就会报错：
syntax error : missing ';' before 'type'

然后你可以修改为把变量声明放在函数调用之前。就会顺利通过编译。

这个问题在vc编译c++程序，或者gcc编译c程序的时候都不会出现，仅仅在vc编译c程序的时候才会出现.*/
    int isLowercaseVowel, isUppercaseVowel;
 
    printf("输入一个字母: ");
    scanf("%c",&c);
 
    // 小写字母元音
    isLowercaseVowel = (c == 'a' || c == 'e' || c == 'i' || c == 'o' || c == 'u');
 
    // 大写字母元音
    isUppercaseVowel = (c == 'A' || c == 'E' || c == 'I' || c == 'O' || c == 'U');
 
    // if 语句判断
    if (isLowercaseVowel || isUppercaseVowel)
        printf("%c  是元音", c);
    else
        printf("%c 是辅音", c);
    return 0;
}
```

