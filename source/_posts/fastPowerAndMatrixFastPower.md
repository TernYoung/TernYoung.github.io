---
title: 快速幂和矩阵快速幂
date: 2019-07-16 13:27:23
mathjax: true
tags: 
	- 快速幂
	- 矩阵快速幂
categories:
	- 技术
author: Tern
authorLink: www.cputern.top
authorAbout: 一个好奇的人
authorDesc: 一个好奇的人
avatar: https://cdn.jsdelivr.net/gh/TernYoung/nicePicture/icon/favicon.png
comments: true
keywords: 矩阵快速幂
description: 快速幂和矩阵快速幂
photos: https://cdn.jsdelivr.net/gh/TernYoung/nicePicture/smallPic/pic004.jpg
---




## 矩阵快速幂


#### 1.快速幂

思考：如何快速求解 $3^{22}$ ?

思想：$3^{16}\times 3^4\times 3^2$

模版代码：

```c++
int pow(int base, int n)//求base^n
{
    int ans = 1;
    while(n){
        if(n&1) ans = ans * base;
        base = base * base;
        n>>=1;
    }
    return ans;
}
```

#### 2.矩阵快速幂

思想：把数换成矩阵，用快速幂求解，再看看下面这张图

![矩阵快速幂图示](/static/images/jzksm/cover.png)

首先来看矩阵乘法与递推式之间的关系

在斐波那契数列之中
$$
f\left( n \right) =\text{1*}f\left( n-1 \right) +\text{1*}f\left( n-2 \right) 
\\
f\left( n-1 \right) =\text{1*}f\left( n-1 \right) +\text{0*}f\left( n-2 \right)
$$
即
$$
\left[ \begin{array}{c}
	f\left( n \right)\\
	f\left( n-1 \right)\\
\end{array} \right] =\left[ \begin{array}{c}
	\text{1 }1\\
	\text{1 }0\\
\end{array} \right] *\left[ \begin{array}{c}
	f\left( n-1 \right)\\
	f\left( n-2 \right)\\
\end{array} \right]
$$
所以有
$$
\left[ \begin{array}{c}
	f\left( n \right)\\
	f\left( n-1 \right)\\
\end{array} \right] =\left[ \begin{array}{c}
	\text{1 }1\\
	\text{1 }0\\
\end{array} \right] ^{\left( n-1 \right)}*\left[ \begin{array}{c}
	f\left( 1 \right)\\
	f\left( 0 \right)\\
\end{array} \right]
$$
上面两幅图完美诠释了斐波那契数列如何用矩阵来实现。

模版代码：

```c++
typedef long long ll;
const ll mod = 1000000007;
const ll N = 4;//n阶矩阵
 
struct Mat
{
    ll m[N+1][N+1];//本模版下标从1开始故定义N+1
 
    Mat(){
        memset(m,0,sizeof(m));
    }
 
    //重载*运算符
    Mat operator * (const Mat& y){
        Mat z;
        for(int i=1;i<=N;++i){
            for(int j=1;j<=N;++j){
                for(int k=1;k<=N;++k){
                    z.m[i][j] += m[i][k]*y.m[k][j]%mod;
                    z.m[i][j] %=mod;
                }
            }
        }
        return z;
    }
};//存储结构体
 
Mat pow(Mat base,ll time)//矩阵快速幂
{
    Mat ans;
    for(int i = 1; i<=N; i++)ans.m[i][i] = 1;//ans初始化为单位矩阵
 
    while(time){
        if(time&1) ans = ans * base;
        base = base * base;
        time>>=1;
    }
    return ans;
}
```



来一个例题 [HDU6185](http://acm.hdu.edu.cn/showproblem.php?pid=6185)

递推式：
$$
f\left( n \right) =f\left( n-1 \right) +\text{5*}f\left( n-2 \right) +f\left( n-3 \right) -f\left( n-4 \right)
$$
第一步：根据
$$
F\left( n \right) = T*F\left( n-1 \right)
$$
即
$$
\left[ f\left( n \right) ,f\left( n-1 \right) ,f\left( n-2 \right) ,f\left( n-3 \right) \right] =T* \left[ f\left( n-1 \right) ,f\left( n-2 \right) ,f\left( n-3 \right) ,f\left( n-4 \right) \right]
$$
写出转移矩阵 *T*

求法：

*T* 的第一列求法：
$$
\text{令}\left[ f\left( n-1 \right) ,f\left( n-2 \right) ,f\left( n-3 \right) ,f\left( n-4 \right) \right] *\left[ T\text{的第一列} \right] =f\left( n \right)
$$

$$
\text{注:}f\left( n \right) =f\left( n-1 \right) +\text{5*}f\left( n-2 \right) +f\left( n-3 \right) -f\left( n-4 \right)
$$

$$
\therefore \left[ \begin{array}{c}
	T\\
	\text{的}\\
	\text{第}\\
	\text{一}\\
	\text{列}\\
\end{array} \right] =\left[ \begin{array}{c}
	1\\
	5\\
	1\\
	-1\\
\end{array} \right]
$$

同理
$$
\text{令}\left[ f\left( n-1 \right) ,f\left( n-2 \right) ,f\left( n-3 \right) ,f\left( n-4 \right) \right] *\left[ T\text{的第二列} \right] =f\left( n-1 \right)
$$

$$
\therefore \left[ \begin{array}{c}
	T\\
	\text{的}\\
	\text{第}\\
	\text{二}\\
	\text{列}\\
\end{array} \right] =\left[ \begin{array}{c}
	1\\
	0\\
	0\\
	0\\
\end{array} \right]
$$

依次类推得
$$
T=\left[ \begin{array}{c}
	\text{1 1 0 0}\\
	\text{5 0 1 0}\\
	\text{1 0 0 1}\\
	-\text{1 0 0 0}\\
\end{array} \right]
$$
第二步：算出前n项，n为矩阵阶数

置初始矩阵init为
$$
\left[ \begin{array}{c}
	f\left( 4 \right) \,\,f\left( 3 \right) \,\,f\left( 2 \right) \,\,f\left( 1 \right)\\
	\text{0 0 0 }0\\
	\text{1 0 0 }0\\
	-\text{1 0 0 }0\\
\end{array} \right]
$$
第三步：求第x项

```
令转移矩阵T = pow(T , x - N)

最终矩阵ansM = 初始矩阵init * T

第x项为 ansM.m[1][1]

防止爆数据取个模 (ansM.m[1][1]+mod)%mod

最终答案 ans = (ansM.m[1][1]+mod)%mod
```

例题代码：

```c++
#include <algorithm>
#include <cstdio>
#include <iostream>
#include <map>
#include <cstring>
using namespace std;
typedef long long ll;
const ll mod = 1000000007;
const ll N = 4;//N阶矩阵
 
struct Mat
{
    ll m[N+1][N+1];//本模版下标从1开始故定义N+1
 
    Mat(){
        memset(m,0,sizeof(m));
    }
 
    //重载*运算符
    Mat operator * (const Mat& y){
        Mat z;
        for(int i=1;i<=N;++i){
            for(int j=1;j<=N;++j){
                for(int k=1;k<=N;++k){
                    z.m[i][j] += m[i][k]*y.m[k][j]%mod;
                    z.m[i][j] %=mod;
                }
            }
        }
        return z;
    }
};//存储结构体
 
Mat pow(Mat base,ll time)//矩阵快速幂
{
    Mat ans;
    for(int i = 1; i<=N; i++)ans.m[i][i] = 1;//ans初始化为单位矩阵
 
    while(time){
        if(time&1) ans = ans * base;
        base = base * base;
        time>>=1;
    }
    return ans;
}
 
int main(){
 
    #ifdef LOCAL
    freopen("in.txt","r",stdin);
    freopen("out.txt","w",stdout);
    #endif // LOCAL
 
    ll x;
    while(cin>>x){
        if(x==1){cout<<1<<endl;continue;}
        if(x==2){cout<<5<<endl;continue;}
        if(x==3){cout<<11<<endl;continue;}
        if(x==4){cout<<36<<endl;continue;}
 
        //输入转移矩阵
        Mat T;
        memset(T.m,0,sizeof(T.m));
        T.m[1][1]=1;    T.m[1][2]=1;
        T.m[2][1]=5;                    T.m[2][3]=1;
        T.m[3][1]=1;                                    T.m[3][4]=1;
        T.m[4][1]=-1;
 
        //输入初始矩阵
        Mat init;
        init.m[1][1]=36; init.m[1][2]=11; init.m[1][3]=5; init.m[1][4]=1;
 
        T = pow(T, x-4);
        Mat ansM;
        ansM = init*T;
        ll ans = (ansM.m[1][1]+mod)%mod;
        cout<<ans<<endl;
    }
 
 
    return 0;
}
```

