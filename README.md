# 大一上c语言期末考试
## 第一题
### ※源码
```c
#include<stdio.h>
#include<string.h>
#include<stdlib.h>
#define size 100
void multiply(int (*p)[size],int (*q)[size],int r1,int c1,int r2,int c2)
{
	int i,j,len,k;
	int multiply[size][size];
	int sum[size]={0};

		for(i=0;i<r1;i++)
		{
			for(j=0;j<c2;j++)
			{
				for(k=0;k<c2;k++)
				{
					multiply[i][j]+=(*(*(p+i)+k))*(*(*(q+k)+j));
				
				}
			}
		} 
		printf("\n");
		printf("相乘矩阵为：\n");
		for(i=0;i<r1;i++)
		{
			for(j=0;j<c2;j++)
			{
				printf("%d ",multiply[i][j]);
			}
			printf("\n");
		}
		

}

int main()
{
	int r1,c1,r2,c2;
	int i,j;
	int (*matrixA)[size];
	int (*matrixB)[size];
	matrixA=(int(*)[size])malloc(sizeof(int[size])*5);
	matrixB=(int(*)[size])malloc(sizeof(int[size])*5);
	printf("请输入矩阵A的行和列数：");
	scanf("%d%d",&r1,&c1);
	getchar();
	printf("请输入矩阵A:\n");
	for(i=0;i<r1;i++)
	{
		for(j=0;j<c1;j++)
		{
			scanf("%d",&(*(matrixA+i))[j]);
		}
		printf("\n");
	}
	printf("\n");
	printf("请输入矩阵B的行和列数：");
	scanf("%d%d",&r2,&c2);
	getchar();
	printf("请输入矩阵B：\n");
	for(i=0;i<r2;i++)
	{
		for(j=0;j<c2;j++)
		{
			scanf("%d",&(*(matrixB+i))[j]);
		}
		printf("\n");
	}
	if(c1!=r2)
	printf("两矩阵无法进行相乘");
	else
	multiply(matrixA,matrixB,r1,c1,r2,c2);

	free(matrixA);
	free(matrixB);
	return 0;
	
}

```
### ※运行结果截图
![test](img\1.PNG)

## 第二题
### ※源码
```c
#include<stdio.h>
#include<string.h>
#include<stdlib.h>
typedef struct WordCounter 
{    
	char *word;//可以用来存储单词    
	int word_count; 
} WordCounter;
//这个结构体可以用来存储单词以及出现次数，之后打印也用结构体 

int main()
{
	WordCounter word[50];
	int num=50,size=50,i,j;
	printf("请输入文本:This is the book he wants.This is your book!he likes the book very much!\n");
	char text[]="This is the book he wants.This is your book!he likes the book very much!";
	char word_separators[] = {' ',',',':','?','!','.'}; 
	word[0].word=strtok(text,word_separators);
	word[0].word_count=1;
	char *temp=NULL;
	int word_num=1,flag;
	printf("文本词频统计信息如下：\n");
	while(1)
	{
		flag=0;
		temp=strtok(NULL,word_separators);//temp每一次切的没有错 
		if(temp==0)
		break;
		for(i=0;i<word_num;i++)
		{
			if(strcmp(temp,word[i].word)==0)
			{
				word[i].word_count++;
				flag=1;
				break;
			}
		}
		if(flag==0)
		{
			word[word_num].word=temp;
			word[word_num].word_count=1;
			word_num++;
		}
		
	}
	printf("\n");
	for(i=0;i<word_num;i++)
	{
		printf("%s\t\t%d次\n",word[i].word,word[i].word_count);
	}
	
}
```
### ※运行结果截图
![test](img\2.PNG)
### ※存在问题
- 未完成1：多⾏⽂本⽤char** text来进⾏存储，使⽤动态分配内存为其开辟内存空间，避免内存空间的浪费。
  
  考虑解决方式：
  ```c
  char **text=NULL;
	text=(char **)malloc(size*sizeof(char *));
	printf("请输入文本信息：");
	for(i=0;i<num;i++)
	{
		*(text+i)=(char *)malloc(10000*sizeof(char));
		scanf("%[^\n]",*(text+i));
	}
	printf("打印出文本信息：");
	for(i=0;i<num;i++)
	{
		printf("%s",*(*(text)));
	}
	```
- 未完成2：划分子函数并且指针为其形参之一
- 未完成3：没有输出热门词频，考虑使用找次数最大和找次数第二大的程序方式来实现





