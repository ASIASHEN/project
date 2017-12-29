# C++

面向对象的方法

	1. 类的的抽象 成员变量和成员函数
	2. 实例化 类的对象
	3. A.面向过程加工的是 一个一个的函数
	B.面向对象加工的是：一个一个的类
	4. main集成测试

//思考：类的调用 执行过程分析==>类代码不是一步一步指向
//类是一个数据类型（固定大小内存块的别名）；定义一个类，是一个抽象的概念，不会给你分配内存
//用数据类型定义变量才会分配内存

#include<iostream>
Using namespace std;
Class circle
{
Public:
       double r;

       double pi=3.1415926;
       double area=pi*r*r;
};
//2010编译不通过，但2013可以
Int main()
{
       circle c1;
       cout<<"please enter c1's radius: ";
      cin>>c1.r;
    
      cout<<c1.area<<endl;
     system("pause");
    return 0;
}


area

	1. 初始化的时候已经执行了，当时r是随机数
	2. 结果：造成area变量是一个乱码

Double area = pi*r*r

pi

3.1415926

但c1.area的时候，只是从变量所示的内存空间中拿值；并没有执行pi*r*r    

r

10

	1. 当使用<iostream>的时候，该头文件没有定义全局命名空间，必须使用namespace std；
	这样才能使用cout。若不引入using namespace std，需要这样做。std：cout
	2. C++标准为了和c区别开，也为了正确使用命名空间，规定头文件不使用后缀.h。
	3. C++命名空间的定义：namespace name{…}
	4. Using namespace NamespaceA;
	5. Namespace 定义可嵌套。
	
	1. c语言返回变量的值  c++语言是返回变量本事
	c返回变量中的三目运算符返回的是变量值，不能作为左值使用
	C++中的三目运算符可直接返回变量本身，因此可以出现在程序的任何地方。
	2. 注意：三目运算符可能返回的值中如果有一个是常量值，则不能作为左值使用
	(a<b?1:b)=30;
	3. c语言如何支持类似c++的特性呢？
	====》当左值的条件：要有内存空间；c++编译器帮助程序员取了一个地址而已

c语言中const是一个冒牌货
结论：
c语言中的const变量
       c语言中的const变量是只读变量，有自己的存储空间
C++中的const常量
       可能分配存储空间，也可能不分配储存空间
       当const常量为全局，并且需要在其它文件中使用
       当使用&操作符取const常量的地址

#define 和 const作用域可能不同

Typed&name=var;//普通引用必须初始化
Int&c（错误）

	1. 引用在C++中的内部实现是一个常指针
	TyPe&name<-->Type*constname
	2. C++编译器在编译过程中使用常指针作为引用的内部实现，因此引用所占用的空间大小与指针相同
	3. 从使用的角度，引用会让人误会其只是一个别名，没有自己的内存空间。这是C++为了实用性而做出的细节隐藏。
	Void func(int &a)                    void func(int *const a)
	                                         
	{                                    {  
	    a=5;                                    *a=5;
	}                                    }

​	

#include<stdio.h>
Void main()
{
Int a[]={1,2,3,4,5},*p,i;
P=a;
For(i=4;i>-1;--i)
  printf("\n");

P=&a[4];//把a[4]作为了p[0]首地址,倒序输出，属于越界。
For(i=4;i>-1;--i)
  printf("\n");


申请内存时，要注意判别是否申请成功。在使用完动态内存之后，应该使用语句
Free（p）；
释放内存，这条语句放在程序结束之前即可。

int a[3][3], i, *p;
	/*
	p=a[0]这里的a[0]是地址
	p = &a[0][0];
	p=(int *)a;
	*/

#接口是一个共享的框架，供两个系统交互时使用。
对于类，我们说公共接口

#定义成员函数时，使用作用域解析运算符（：：）来标识函数所属的类

#如果愿意，也可以在类声明之外定义成员函数，并使其成为内联函数，为此，只需在类实现部分定义函数时使用inline限定即可

#构造函数的参数表示的不是类成员，而是赋给类成员的值，因此，参数名不能与类成员相同，否则最终的代码将是shares=shares
为了避免这种混乱，一种常见的做法是在数据域成员名中使用m_前缀：
另一种常见的做法是，在成员中使用后缀

#typedef为一个已有的类型取一个新名字
语法：typedef type newname
             typedef int feet;
             feet distance;//该声明是完全合法，它创建了一个整型变量distance

#枚举类型
枚举类型声明一个可选的类型名称和一组标识符，用来作为该类型的值
创建枚举， 关键字enum
Enum enum-name {list of names }var-list
Enum-name是枚举类型的名称，名称列表{list of names}是用逗号分开
例：enum color{red,green,blue}c;
C=blue;

#type variable_list
type必须是一个有效的C++数据类型
Int I,j;
Float c,cha;
**不带初始化的定义，带有静态存储持续时间的变量会被隐式初始化为NULL（所有字节的值都是0），其他所有变量的初始值是未定义的。
变量的声明只在编译的时候有它的意义。

#右值是不能对其进行赋值的表达式

#c++变量的作用域
	在函数或一个代码块内部声明的变量，称为局部变量
	在函数参数的定义中声明的变量，称为形式参数
	在所有函数外部声明的变量，称为全局变量

#局部变量和全局变量名称可以相同，在函数内，局部变量的值会覆盖全局变量的值

#~
二进制补码运算符是一元运算符，具有"翻转"位效果。	(~A ) 将得到 -61，即为 1100 0011，2 的补码形式，带符号的二进制数

#逗号运算符会顺序执行一系列运算。整个逗号表达式的值是以逗号分隔的列表中的最后一个表达式的值。

#
逗号运算符会顺序执行一系列运算。整个逗号表达式的值是以逗号分隔的列表中的最后一个表达式的值。


#引用变量是一个别名，也就是说，它是某个已存在变量的另一个名字。一旦把引用初始化为某个变量，就可以使用该引用名称或变量名称来指向变量。
C++ 引用 vs 指针
引用很容易与指针混淆，它们之间有三个主要的不同：
不存在空引用。引用必须连接到一块合法的内存。
一旦引用被初始化为一个对象，就不能被指向到另一个对象。指针可以在任何时候指向到另一个对象。
引用必须在创建时被初始化。指针可以在任何时间被初始化。


#
结构作为函数参数
把结构作为函数参数，传参方式与其他类型的变量或指针类似
// 输出 Book1 信息
   printBook( Book1 );
// 输出 Book2 信息
   printBook( Book2 );
return 0;
}
void printBook( struct Books book )//可以起别名
{
   cout << "Book title : " << book.title <<endl;
   cout << "Book author : " << book.author <<endl;
   cout << "Book subject : " << book.subject <<endl;
   cout << "Book id : " << book.book_id <<endl;
}

#include <iostream>
#include <cstring>

using namespace std;
void printBook( struct Books *book );
struct Books
{
   char  title[50];
   char  author[50];
   char  subject[100];
   int   book_id;
};

int main( )
{
   struct Books Book1;        // 声明 Book1，类型为 Book
   struct Books Book2;        // 声明 Book2，类型为 Book */

   // Book1 详述
   strcpy( Book1.title, "Learn C++ Programming");
   strcpy( Book1.author, "Chand Miyan"); 
   strcpy( Book1.subject, "C++ Programming");
   Book1.book_id = 6495407;
// Book2 详述
   strcpy( Book2.title, "Telecom Billing");
   strcpy( Book2.author, "Yakit Singha");
   strcpy( Book2.subject, "Telecom");
   Book2.book_id = 6495700;

   // 通过传 Book1 的地址来输出 Book1 信息
   printBook( &Book1 );
// 通过传 Book2 的地址来输出 Book2 信息
   printBook( &Book2 );
return 0;
}
// 该函数以结构指针作为参数
void printBook( struct Books *book )
{
   cout << "Book title : " << book->title <<endl;//指针
   cout << "Book author : " << book->author <<endl;
   cout << "Book subject : " << book->subject <<endl;
   cout << "Book id : " << book->book_id <<endl;
}


#
多继承
多继承即一个子类可以有多个父类，它继承了多个父类的特性。
C++ 类可以从多个类继承成员，语法如下：
class <派生类名>:<继承方式1><基类名1>,<继承方式2><基类名2>,…
{
<派生类类体>

#c++重载运算符和重载函数
C++允许在同一作用域的某个函数和运算符指定多个定义，分别称为函数重载和运算重载
函数重载：
C++ 中的函数重载
在同一个作用域内，可以声明几个功能类似的同名函数，但是这些同名函数的形式参数（指参数的个数、类型或者顺序）必须不同。您不能仅通过返回类型的不同来重载函数。
下面的实例中，同名函数 print() 被用于输出不同的数据类型：
#include <iostream>
using namespace std;

class printData 
{
   public:
      void print(int i) {
        cout << "Printing int: " << i << endl;
      }
void print(double  f) {
        cout << "Printing float: " << f << endl;
      }
void print(char* c) {
        cout << "Printing character: " << c << endl;
      }
};
int main(void)
{
   printData pd;

   // Call print to print integer
   pd.print(5);
   // Call print to print float
   pd.print(500.263);
   // Call print to print character
   pd.print("Hello C++");

   return 0;
}

C++ 中的运算符重载
您可以重定义或重载大部分 C++ 内置的运算符。这样，您就能使用自定义类型的运算符。
重载的运算符是带有特殊名称的函数，函数名是由关键字 operator 和其后要重载的运算符符号构成的。与其他函数一样，重载运算符有一个返回类型和一个参数列表。
Box operator+(const Box&);
声明加法运算符用于把两个 Box 对象相加，返回最终的 Box 对象。大多数的重载运算符可被定义为普通的非成员函数或这被定义为类成员函数。如果我们定义上面的函数为类的非成员函数，那么我们需要为每次操作传递两个参数，如下所示：
Box operator+(const Box&, const Box&);
下面的实例使用成员函数演示了运算符重载的概念。在这里，对象作为参数进行传递，对象的属性使用 this 运算符进行访问，如下所示：
#include <iostream>
using namespace std;
class Box
{
   public:
double getVolume(void)
      {
         return length * breadth * height;
      }
      void setLength( double len )
      {
          length = len;
      }
void setBreadth( double bre )
      {
          breadth = bre;
      }
void setHeight( double hei )
      {
          height = hei;
      }
      // 重载 + 运算符，用于把两个 Box 对象相加
      Box operator+(const Box& b)
      {
         Box box;
         box.length = this->length + b.length;
         box.breadth = this->breadth + b.breadth;
         box.height = this->height + b.height;
         return box;
      }
   private:
      double length;      // 长度
      double breadth;     // 宽度
      double height;      // 高度
};
// 程序的主函数
int main( )
{
   Box Box1;                // 声明 Box1，类型为 Box
   Box Box2;                // 声明 Box2，类型为 Box
   Box Box3;                // 声明 Box3，类型为 Box
   double volume = 0.0;     // 把体积存储在该变量中

   // Box1 详述
   Box1.setLength(6.0); 
   Box1.setBreadth(7.0); 
   Box1.setHeight(5.0);

   // Box2 详述
   Box2.setLength(12.0); 
   Box2.setBreadth(13.0); 
   Box2.setHeight(10.0);

   // Box1 的体积
   volume = Box1.getVolume();
   cout << "Volume of Box1 : " << volume <<endl;

   // Box2 的体积
   volume = Box2.getVolume();
   cout << "Volume of Box2 : " << volume <<endl;
// 把两个对象相加，得到 Box3
   Box3 = Box1 + Box2;
// Box3 的体积
   volume = Box3.getVolume();
   cout << "Volume of Box3 : " << volume <<endl;
return 0;
}


数据类型	描述
ofstream	该数据类型表示输出文件流，用于创建文件并向文件写入信息。
ifstream	该数据类型表示输入文件流，用于从文件读取信息。
fstream	该数据类型通常表示文件流，且同时具有 ofstream 和 ifstream 两种功能，这意味着它可以创建文件，向文件写入信息，从文件读取信息。

从文件读取信息或者向文件写入信息之前，必须先打开文件。ofstream 和 fstream 对象都可以用来打开文件进行写操作，如果只需要打开文件进行读操作，则使用 ifstream 对象。
下面是 open() 函数的标准语法，open() 函数是 fstream、ifstream 和 ofstream 对象的一个成员。
void open(const char *filename, ios::openmode mode);
在这里，open() 成员函数的第一参数指定要打开的文件的名称和位置，第二个参数定义文件被打开的模式。
模式标志	描述
ios::app	追加模式。所有写入都追加到文件末尾。
ios::ate	文件打开后定位到文件末尾。
ios::in	打开文件用于读取。
ios::out	打开文件用于写入。
ios::trunc	如果该文件已经存在，其内容将在打开文件之前被截断，即把文件长度设为 0。



getline()函数从外部读取一行，ignore() 函数会忽略掉之前读语句留下的多余字符。

#include<fstream>
#include<iostream>
using namespace std;

int main()
{
	char data[100];

	//以写模式打开文件
	ofstream outfile;
	outfile.open("afile.dat");
	
	cout << "writing to the file" << endl;
	cout << "enter your name: ";
	cin.getline(data, 100);
	
	//向文件写入用户输入的数据
	outfile << data << endl;
	
	cout << "Enter your age: ";
	cin >> data;
	cin.ignore();
	
	// 再次向文件写入用户输入的数据
	outfile << data << endl;
	
	// 关闭打开的文件
	outfile.close();
	
	//以读模式打开文件
	ifstream infile;
	infile.open("afile.dat");
	
	cout << "Reading from the file" << endl;
	infile >> data;
	
	//在屏幕上写入数据
	cout << data << endl;
	
	// 再次从文件读取数据，并显示它
	infile >> data;
	cout << data << endl;
	
	//关闭打开文件
	infile.close();
	
	system("pause");
	return 0;
}




抛出异常
您可以使用 throw 语句在代码块中的任何地方抛出异常。throw 语句的操作数可以是任意的表达式，表达式的结果的类型决定了抛出的异常的类型。
以下是尝试除以零时抛出异常的实例：
double division(int a, int b)
{
   if( b == 0 )
   {
      throw "Division by zero condition!";
   }
   return (a/b);
}
捕获异常
catch 块跟在 try 块后面，用于捕获异常。您可以指定想要捕捉的异常类型，这是由 catch 关键字后的括号内的异常声明决定的。
try
{
   // 保护代码
}catch( ExceptionName e )
{
  // 处理 ExceptionName 异常的代码
}
上面的代码会捕获一个类型为 ExceptionName 的异常。如果您想让 catch 块能够处理 try 块抛出的任何类型的异常，则必须在异常声明的括号内使用省略号 ...，如下所示：
try
{
   // 保护代码
}catch(...)
{
  // 能处理任何异常的代码
}
• 栈：在函数内部声明的所有变量都将占用栈内存。
• 堆：这是程序中未使用的内存，在程序运行时可用于动态分配内存。



• # 和 ## 运算符
• # 和 ## 预处理运算符在 C++ 和 ANSI/ISO C 中都是可用的。# 运算符会把 replacement-text 令牌转换为用引号引起来的字符串。
• 请看下面的宏定义：
• #include <iostream>
using namespace std;
• #define MKSTR( x ) #x
• int main ()
{
    cout << MKSTR(HELLO C++) << endl;
• return 0;
} 
• 当上面的代码被编译和执行时，它会产生下列结果：
• HELLO C++
• 

C++ 多线程
多线程是多任务处理的一种特殊形式，多任务处理允许让电脑同时运行两个或两个以上的程序。在一般情况下，有两种类型的多任务处理：基于进程和基于线程。
基于进程的多任务处理处理的是程序的并发执行。基于线程的多任务处理的是同一程序的片段的并发执行。
多线程程序包含可以同时运行的两个或多个部分。这样的程序中的每个部分称为一个线程，每个线程定义了一个单独的执行路径。





