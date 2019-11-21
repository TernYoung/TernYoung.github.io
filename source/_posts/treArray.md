---
title: 树状数组
date: 2019-08-17 17:54:36
tags:
	- 数据结构
	- 树状数组
categories:
	- 数据结构
cover:  static/images/BIT/树状数组.jpg
---





公式看不了请刷新一下！！！



#### 树状数组简介

树状数组，顾名思义，它还是一个数组，但是是树状的。

树状数组是能够完成下述操作的数据结构。

- 给定$i$，计算$a_1+a_2+...+a_i$
- 给定$i$和$x$，执行$a_i+=x$

#### 为什么要用树状数组？

- 修改和查询区间和复杂度均为$O(logn)$
- 代码简短

#### 树状数组讲解

这是普通数组，修改复杂度为$O(1)$,查询区间和复杂度为$O(n)$ 

![](/static/images/BIT/数组.jpg)

这是大家知道的二叉树，大神把叶子节点代表 A 数组 A[1]~A[8]

![二叉树](/static/images/BIT/二叉树.png)

然后变形一下

![右歪二叉树](/static/images/BIT/右歪二叉树.png)

接下来大神定义每一列的顶端节点为 C[] 数组，这个数组就是大神搞出来的树状数组。

![](/static/images/BIT/树状数组.jpg)

从这个图里面，大神发现了

> C[1]=A[1];
C[2]=A[1]+A[2];
C[3]=A[3];
C[4]=A[1]+A[2]+A[3]+A[4];
C[5]=A[5];
C[6]=A[5]+A[6];
C[7]=A[7];
C[8]=A[1]+A[2]+A[3]+A[4]+A[5]+A[6]+A[7]+A[8];

然后大神把节点的序号变成二进制

>1=(0001)      C[1]=A[1];
2=(0010)      C[2]=A[1]+A[2];
3=(0011)      C[3]=A[3];
4=(0100)      C[4]=A[1]+A[2]+A[3]+A[4];
5=(0101)      C[5]=A[5];
6=(0110)      C[6]=A[5]+A[6];
7=(0111)      C[7]=A[7];
8=(1000)      C[8]=A[1]+A[2]+A[3]+A[4]+A[5]+A[6]+A[7]+A[8];

大神又发现了 $C[i]=A[i-2^k+1]+A[i-2^k+2]+...+A[i]$ （ $k$ 为 $i$ 的二进制中从最低位到高位连续零的长度）例如$i=8(1000)$时，$k=3$; 

> tips: 快速求$C[i]$ , 首先 $A[i]$ 肯定有，然后往前写够 $lowbit(i)$ 个数，比如求$C[4]$, $A[4]$肯定有,往前写够$lowbit(4)=4$ 个数 $A[4],A[3],A[2],A[1],则C[4]=A[1]+A[2]+A[3]+A[4]$

然后大神引入一个神仙操作 $lowbit(x)$,大神说 $lowbit(x)$ 其实就是取出 $x$ 二进制中的最低位1  换言之  $lowbit(x)=2^k$  $k$的含义与上面相同。

$lowbit()$代码：

```c++
int lowbit(int t)
{
	return t&(-t);
}
//-t 代表t的负数 计算机中负数使用对应的正数的补码来表示
//例如 :
// t=6（0110） 此时 k=1
//-t=-6=(1001+1)=(1010)
// t&(-t)=(0010)=2=2^1
```

$C[i]=A[i-2^k+1]+A[i-2^k+2]+......A[i]$

$C[i]=A[i-lowbit(i)+1]+A[i-lowbit(i)+2]+......A[i]$



---

下面是树状数组的作用，树状数组代码超短，必须会用。

#### 区间查询(查询区间1~x的和)

用 $C[i]$ 这个树状数组，求 $A[i]$ 这个普通数组中前 $i$ 项的和。

假设$i=7$

$sum[7]=A[1]+A[2]+A[3]+A[4]+A[5]+A[6]+A[7]$

$C[4]=A[1]+A[2]+A[3]+A[4] \\  C[6]=A[5]+A[6] \\  C[7]=A[7]$

$sum[7]=C[4]+C[6]+C[7]$

序号写为二进制: $sum[(111)]=C[(100)]+C[(110)]+C[(111)]$

代码：

```c++
    int getsum(int x)
    {
        int ans=0;
        for(int i=x;i>0;i-=lowbit(i))
        	ans+=C[i];
        return ans；
    }

```

对于 $i=7$ 进行演示 

| $7(111)$             | $ans+=C[7]$ |
| -------------------- | ----------- |
| $7-lowbit(7)=6(110)$ | $ans+=C[6]$ |
| $6-lowbit(6)=4(100)$ | $ans+=C[4]$ |
| $4-lowbit(4)=0(000)$ |             |

#### 单点更新

修改A[]数组中的某一个值时  应当如何更新C[]数组?

代码：

```c++
    void add(int x,int y)
    {
        for(int i=x;i<=n;i+=lowbit(i))
        	C[i]+=y;
    }
    //可以发现 更新过程是查询过程的逆过程
    //由叶子结点向上更新C[]数组

```

![](C:\Users\asus\Desktop\树状数组\树状数组.jpg)

当更新$A[1]$时  需要向上更新$C[1] ,C[2],C[4],C[8]$

写为二进制 $ C[(001)],C[(010)],C[(100)],C[(1000)]$

| $1(001)$              | $C[1]+=A[1]$ |
| --------------------- | ------------ |
| $1+lowbit(1)=2(010)$  | $C[2]+=A[1]$ |
| $2+lowbit(2)=4(100)$  | $C[4]+=A[1]$ |
| $4+lowbit(4)=8(1000)$ | $C[8]+=A[1]$ |

模版：

```c++
//树状数组修改值，求某区间的和
#include <iostream>
#include <cstring>
#include <algorithm>
#include <cstdio>
#include <cmath>
#include <string>
#include <deque>
#include <map>
#define INF 0x3f3f3f3f
#define FRE() freopen("in.txt","r",stdin)
 
using namespace std;
typedef long long ll;
const int maxn = 1e5 + 5;
int a[maxn],c[maxn];
int T,n;
 
int lowbit(int x)
{
    return x & -x;
}
 
void upDate(int i, int x)
{
    while(i <= n)
    {
        c[i] += x;
        i += lowbit(i)
    }
}
 
int toSum(int x)
{
    int sum = 0;
    while(x > 0)
    {
        sum += c[x];
        x -= lowbit(x);
    }
    return sum;
}
 
int getSum(int st,int en)
{
    return toSum(en) - toSum(st - 1);
}
 
 
 
 
int main()
{
    memset(a, 0, sizeof(a));
    memset(c, 0, sizeof(c));
    scanf("%d",&T);
    while(T--)
    {
        scanf("%d",&n);
        for(int i = 1; i <= n; i++)
        {
            scanf("%d",&a[i]);
            upDate(i, a[i]);//修改i位置的值
        }
        int st,en;
        scanf("%d%d",&st,&en);
        printf("%d\n",getSum(st, en));//输出st到en之间的和
    }
    return 0;
}
```

#### 树状数组求逆序数

逆序数：逆序数就是数中各位在它前面有多少个数比它大，求出这些元素个数之和。

普通方法需要$O(n^2)$复杂度,用树状数组只需要$O(nlogn)$

思路：可以把数一个个插入到树状数组中， 每插入一个数， 统计比他小的数的个数，对应的逆序为$ i- getsum( data[i] )$，其中$ i $为当前已经插入的数的个数，$ getsum( data[i] ）$为比 $data[i] $小的数的个数，$i- getsum( data[i] )$ 即比 $data[i]$ 大的个数， 即逆序的个数。最后需要把所有逆序数求和，就是在插入的过程中边插入边求和。

代码：

```c++
#include <iostream>
using namespace std;

#define  N  10

struct Node{
	int data;
	int pos;
};

Node d[N+1];
int inverse[N+1]; 
int count[N]; 

int cmp(const void*a,const void*b)
{
	Node *pa=(Node*)a;
	Node *pb=(Node*)b;
	return pa->data-pb->data;
}

int lowbit(int t){ 
	return t & (t^(t-1)); 
}
void modify(int pos,int num)
{
	while (pos<=N) {
		inverse[pos]+=num;
		pos+=lowbit(pos);
	}
}
int sum(int end)
{
	int sum=0;
	while (end>0) {
		sum+=inverse[end];
		end-=lowbit(end);
	}
	return sum;
}


int main()
{
	memset(inverse,0,sizeof(inverse)); //初始化
	memset(count,0,sizeof(count));

	char* a="9854623870";  //长度N
	for(int i=0;i<strlen(a);i++)
	{
		d[i+1].data =a[i]-'0';
		d[i+1].pos=i+1;
	}
	
	qsort(d+1,N,sizeof(Node),cmp);
	
	int id=1;
	count[d[1].pos]=1;
	for(int i=2;i<=N;i++)
	{
		if(d[i].data==d[i-1].data)
			count[d[i].pos]=id;
		else
			count[d[i].pos]=++id;
	}
	int num=0;
	for(int i=1;i<=N;i++)
	{
		modify(count[i],1);
		num+=i-sum(count[i]);
	}
	
	cout<<num<<endl;

	return 0;
}

```

