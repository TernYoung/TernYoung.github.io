---
title: 素数筛法
date: 2019-07-24 21:06:36
tags:
	- 素数
	- 数论
categories:
	- 技术
author: Tern
authorLink: www.cputern.top
authorAbout: 一个好奇的人
authorDesc: 一个好奇的人
avatar: https://cdn.jsdelivr.net/gh/TernYoung/nicePicture/icon/favicon.png
comments: true
keywords: 素数筛法
description: 素数筛法
photos: https://cdn.jsdelivr.net/gh/TernYoung/nicePicture/Wallpapers/b2.png
---


### 朴素筛法（试除法）

复杂度：$O(n\sqrt{n})$

最简单的素数筛法，耗时长

```c++
bool judge(int n){
    for(int i = 2; i <= sqrt(n); i++){
        if(n%i==0)return false;
    }
    return true;
}

void easyPrimesieve(int n){
    for(int i = 2; i <= n; i++){
        if(judge(i))cout<<i<<endl;
    }
}
```



### 埃氏筛法

复杂度：$O(nloglogn)$ 

埃拉托斯特尼筛法，利用当前已经找到的素数，从后面的数中筛去当前素数的倍数，当前素数已经是筛去数的质因子，如此下去能筛除所有之后的合数，是一种比较快的筛法,缺点是会重复筛一些数。

代码：

```c++
void ElatostnySeive(int n){
    bool isPrime[1000];
    int prime[1000],p=0;
    memset(isPrime,true,sizeof(isPrime));
    isPrime[0]=isPrime[1]=false;
    for(int i=2; i<=n;i++){
        if(isPrime[i]){
            prime[p++]=i;
            for(int j = i+i;j<=n;j+=i){ //此方法会重复筛8 16等数
                isPrime[j]=false;
            }
        }
    }
    for(int i = 0; i< p;i++){
        cout<<prime[i]<<endl;
    }
}
```



### 欧几里得筛法

复杂度：$O(n)$

非常好的线性筛法，与埃筛法相比，欧筛法不重复筛。理解不了的话，手动模拟下。

```c++
void EulerSeive(int n)
{
    int prime[1000];//保存素数
	bool vis[1000];//初始化
	int cnt=0;
	memset(vis,0,sizeof(vis));
	for(int i=2;i<n;i++)
	{
		if(!vis[i])
		prime[cnt++]=i;
		for(int j=0;j<cnt&&i*prime[j]<n;j++)
		{
			vis[i*prime[j]]=1;
			if(i%prime[j]==0)//关键
			break;
		}
	}
	for(int i = 0; i< cnt;i++){
        cout<<prime[i]<<endl;
    }
}
```



### 区间筛法

对于超大区间，比如$a<b\le2^{31}-1,b-a\le10^6$这种情况下，数组开不到这么大，所以需要特殊处理，先筛出$2-\sqrt{b}$的表，再根据此表，用埃氏筛法筛目标区间的表。

代码：

```c++
//区间筛法
typedef long long ll;
const int MAXN = 1e6+1e3;   //待筛的区间[L,R]长度
const int N = 50001;//保证大于(2^31-1)的算数平方根
bool prime[MAXN];
bool seive[N];
ll ans[MAXN];
ll ansSize;

//输入区间，输出区间内所有素数
void segmentSeive(ll L,ll R)
{
    //预处理
    for(ll i=2;i<N;i++) seive[i]=1;
    for(ll i=2;i*i<=R;i++)
        if(seive[i])
            for(int j=2*i;j<N;j+=i)
                seive[j]=false;

    ll len=R-L+1;
    for(ll i=0;i<len;i++) prime[i]=1;
    if(L<=1) prime[1-L]=0;   //0和1不是素数

    for(ll i=2; i*i<=R ;i++)
    {
        if(seive[i])
        {
            for(ll j=max((ll)2,(L-1+i)/i)*i;j<=R;j+=i)  //易错点，j必须从大于1，因为L可能小于i，但是seive[i]是素数。
                prime[j-L]=false;
        }
    }
    ansSize=0;
    for(ll i = 0; i < len ;i++){
        if(prime[i]){
            ans[ansSize++]=i+L;
        }
    }
    for(int i = 0;i < ansSize;i++){
        cout<<ans[i]<<endl;
    }
}
```

