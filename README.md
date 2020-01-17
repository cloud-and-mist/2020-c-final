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

### ※运行结果截图
