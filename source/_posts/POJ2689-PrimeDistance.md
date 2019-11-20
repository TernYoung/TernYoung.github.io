---
title: POJ2689-PrimeDistance
date: 2019-07-23 21:38:22
tags:
	- 素数
	- POJ
categories:
	- 数论题集
cover:  static/images/number_theory/poj2689.png
---

### 知识点：素数

### 算法：素数区间筛法

> 题意： 给出一个区间 $[L,R]$ ,范围为 $1\le L<R \le 2^{31}-1$ ,区间长度不超过 $10^6$ ,求相邻差最小和相邻差最大的素数对。当存在多个时输出小的。

> 题解：范围太大，所以不能直接筛，需要用到区间筛法，注意不能用int,中间处理会爆数据,注意1不是素数。

代码：

```c++
#include<cstdio>
#include<iostream>
#include<algorithm>
#include<cstring>
using namespace std;
typedef long long ll;

const int MAXN = 1e6+1e3;   //待筛的区间[L,R]长度
const int N = 50001;//保证大于(2^31-1)的算数平方根
bool prime[MAXN];
bool seive[N];
ll ans[MAXN];
ll ansSize;

void segmentSeive(ll L,ll R)   //区间筛法
{
    for(ll i=2;i<N;i++) seive[i]=1;
    for(ll i=2;i*i<=R;i++)
        if(seive[i])
            for(int j=2*i;j<N;j+=i)
                seive[j]=false;

    ll len=R-L+1;
    for(ll i=0;i<len;i++) prime[i]=1;
    if(L<=1) prime[1-L]=0;

    for(ll i=2; i*i<=R ;i++)
    {
        if(seive[i])
        {
            for(ll j=max((ll)2,(L-1+i)/i)*i;j<=R;j+=i)
                prime[j-L]=false;
        }
    }
    ansSize=0;
    for(ll i = 0; i < len ;i++){
        if(prime[i]){
            ans[ansSize++]=i+L;
        }
    }
}

int main()
{
    ll L,R;
    while(~scanf("%lld%lld",&L,&R))
    {
        segmentSeive(L,R);
        ll len = R-L+1;
        ll minl=R,minr=R,maxl=-1,maxr=-1;
        ll minnum=R,maxnum=-1;
        for(ll i=0;i<ansSize-1;i++){
            ll temp=ans[i+1]-ans[i];
            if(temp>maxnum){
                maxnum=temp;
                maxl=ans[i];maxr=ans[i+1];
            }
            if(temp<minnum){
                minnum=temp;
                minl=ans[i];minr=ans[i+1];
            }
        }

        if(ansSize>=2) printf("%lld,%lld are closest, %lld,%lld are most distant.\n",minl,minr,maxl,maxr);
        else puts("There are no adjacent primes.");
    }
    return 0;
}

```

