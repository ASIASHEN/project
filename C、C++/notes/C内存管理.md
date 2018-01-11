# C内存管理

C中的动态内存管理。C语言为内存的分配和管理提供了几个函数。这些函数可以在<stdlib.h>头文件中找到。

| 序号   | 函数和描述                                    |
| ---- | ---------------------------------------- |
| 1    | void*calloc(int num,int size)；在内存中动态地分配num个长度为size的连续空间，并将每个字节都初始化为0。所以它的结果是分配了num *size个字节长度的空间，并且每个字节的值都是0。 |
| 2    | void free(void *address);该函数释放address所指向的内存块，释放的是动态分配的内存空间。 |
| 3    | void *malloc(int num)；在堆区分配一块指定大小的内存空间，用来存放数据。这块内存空间在函数执行完成后不会被初始化，它们的值是未知的。 |
| 4    | void *realloc(void *address,int newsize)；该函数重新分配内存，把内存扩展到newsize。 |

---

# 动态分配内存

编程时，如果你预先知道数组的 大小，那么定义数组时就比较容易。例如，一个存储人名的数组，它最多容纳100个字符，所以你可以定义数组，如下所示：

```c
#include<stdio.h>
#include<stdlib.h>
//C语言为内存的分配和管理提供了几个函数
#include<string.h>

int main()
{
	char name[100];
	char *description;

	strcpy(name,"Zara Ali");

	/*动态分配内存*/
	description=calloc(200,sizeof(char));
	//malloc(200*sizeof(char))

	if(description==NULL)
	{
		fprintf(stderr,"Error - unable to allocate required memory\n");
				//unix标准输出（设备）文件，对应终端的屏幕。
	}
	else
	{
		strcpy(description,"Zara ali a Dps student in class 10th");
	}
	printf("Name = %s\n",name);
	printf("Description: %s\n",description);
}
```

当上面的代码被编译和执行时，它会产生下列结果：

```
Name = Zara Ali
Description: Zara ali a DPS student in class 10th
```

上面的程序也可以使用 **calloc()** 来编写，只需要把 malloc 替换为 calloc 即可，如下所示：

```
calloc(200, sizeof(char));
```

当动态分配内存时，您有完全控制权，可以传递任何大小的值。而那些预先定义了大小的数组，一旦定义则无法改变大小。

---

# 重新调整内存的大小和释放内存

当程序退出时，操作系统会自动释放所有分配给程序的内存，但是，建议你在不需要内存时，都应该调用函数free()来释放内存。

或者，你可以通过调用函数realloc()来增加或减小已分配的内存块的大小。让我们使用realloc()和free()函数

```c
#include<stdio.h>
#include<stdlib.h>
#include<string.h>

int main()
{
	char name[100];
	char *description;

	strcpy(name,"Zare Ali");

	/*动态分配内存*/
	description=malloc(30*sizeof(char));
	if(description==NULL)
	{
		fprintf(stderr,"Error - unable to allocate(分配) required memory\n");
	}
	else
	{
		strcpy(description,"Zera ali a DPS student.");
	}
	/*假设你想要储存更大的描述信息*/
	description=realloc(description,100*sizeof(char));
   //该函数重新分配内存，把内存扩展到newsize
	if(description==NULL)
	{
		fprintf(stderr,"Error - unable to allocate required memory\n");
	}
	else
	{
		strcat(description,"She is in class 10th");//连接字符串 s2 到字符串 s1 的末尾。
	}
	printf("Name = %s\n",name);
	printf("Description: %s\n",description);
	
	/* 使用free()函数释放内存*/
	free(description);
}
```

当上面的代码被编译和执行时，它会产生下列结果：

```
Name = Zara Ali
Description: Zara ali a DPS student.She is in class 10th
```

您可以尝试一下不重新分配额外的内存，strcat() 函数会生成一个错误，因为存储 description 时可用的内存不足。