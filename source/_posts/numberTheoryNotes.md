---
title: 数论笔记
date: 2019-8-24 23:45:00
tags:
	- 数论
categories:
	- 技术
author: Tern
authorLink: www.cputern.top
authorAbout: 一个好奇的人
authorDesc: 一个好奇的人
avatar: https://cdn.jsdelivr.net/gh/TernYoung/nicePicture/icon/favicon.png
comments: true
keywords: 数论
description: 数论笔记
photos: https://cdn.jsdelivr.net/gh/TernYoung/nicePicture/Wallpapers/a5.jpg
---


### 素数

> 定义：在大于1的自然数中，除了1和它本身没有其它约数，这样的数称为素数；否则称为合数。 例如：2、3、5、7、11、13、17、19...

判定：

* 试除法：如果自然数$n$不能被$[2, 𝑛]$ 内的所有素数整除，那么n是素数

  * ```C++
    bool isPrime( long long n )
    {
    	for(long long i = 2; i*i <= n; i++)
    	{
    		if(n%i == 0) return false;
    	}
    	return true;
    }
    ```

  * 加速：大于4的素数总是等于 $6x+1$ 或 $6x-1$ （约数一定是成对出现的，$d$ 和 $n/d$）

  * ```c++
    bool isPrime(int num) 
    {
    	if (num <= 3) return num>1; 
    	// 不在6的倍数两侧的一定不是质数
    	if (num % 6 != 1 && num % 6 != 5) 
    		return false;
    	int s = (int) sqrt(num);
    	for (int i = 5; i <= s; i += 6) {
    		if (num % i == 0 || num % (i+2) == 0) {
    			return false; 
    		} 
    	}
    	return true; 
    }
    ```

    

* Miller-Rabin算法

筛法：[素数筛法](http://www.cputern.top/2019/07/24/%E7%B4%A0%E6%95%B0%E7%AD%9B%E6%B3%95/)

例题：[素数距离](https://www.acwing.com/problem/content/198/)

### 反素数

> 定义：对于正整数x，其约数的个数记作$g(x)$。例如 $g(1)=1,g(6)=4$。 如果某个正整数x满足：对任意正整数$ i(0<i<x)$，都有$g(x)>g(i)$，那么称x为反素数。

>x 是小于 n 的最大的反素数的情况： $1………….x….n $
>* x一定是 小于n的 约数最多的 数 
>* 当约数个数相同时，x一定是最小的数

> 性质：反素数$x = 𝑝_1^{e_1}𝑝_2^{e_2} … 𝑝_𝑟^{e_𝑟}$
>* 质因子 𝑝1, 𝑝2, …, 𝑝𝑟 是从2开始连续的素数. 
>* 质因子的指数递减 $𝑒_1 ≥ 𝑒_2 ≥ 𝑒_3 … ≥ 𝑒_𝑟$

### 约数

> 定义：若整数n除以整数d的余数为0，即d能整除n，则称d是n的约数，n是d的倍数，记为$d|n$ 

> 唯一分解定理：任一大于1的自然数𝑁 ，都可以唯一分解为有限个素数之积：$𝑁 = 𝑝_1^{𝑐_1}𝑝_2^{𝑐_2} … 𝑝_𝑟^{𝑐_𝑟} $

```C++
map <int , int > prime_factor(int n){
    map <int, int>ans;
    for(int i = 2; i*i <= n; i++){
        while(n % i == 0){
        ++ans[i];
        n /= i;
       }
    }
 
    if(n != 1) ans [n] = 1;
 
    //输出
    map<int, int>::iterator iter;
    int flag = 0;
    for(iter = ans.begin(); iter != ans.end(); iter++)
    {
        if(flag == 1)cout<<"*";
        if(flag == 0)flag = 1;
        cout<<iter->first<<'^'<<iter->second;
    }
    return ans ;
}
```

### 模运算

> 定义：a % b = m , 5 % 2 = 1​

性质：
>* (a + b) % p = (a % p + b % p) % p 
>* (a – b) % p = (a % p – b % p) % p 
>* (a * b) % p = (a % p * b % p) % p 
>* (ab) % p = ((a % p)b) % p 
>* (a / b) % p **≠** (a % p / b % p) % p 
>* 交换律：(a + b) % m = (b + a) % m 
  ​				(a * b) % m = (b * a) % m 
>* 结合律：((a+b) % p + c) % p = (a + (b+c) % p) % p  
  ​				((a*b) % p * c)% p = (a * (b*c) % p) % p  
>* 分配律：((a +b)% p * c) % p = ((a * c) % p + (b * c) % p) % p

### 同余

> 定义：给定一个正整数m和两个整数a和b，如果$((a-b) mod m)=0$，则称a和b模m同余，记为 $a≡b(mod\ m)$。 $((a-b) mod m)=0$ 当且仅当存在整数k，$a=b+km$。

例如，$-7≡-3≡1≡5≡9(mod 4) \\ -5≡-1≡3≡7≡11(mod 4)$

> 同余类：整数被正整数m除后，余数有m种情形：0,1,2,3,…,m-1，他们彼此之间的余数不同。按模m是否同余对整数集进行分类，可以将整数集分成m个两两不相交的子集。我们把所有对模m同余的整数构成的一个集合,叫做模m的一个同余类（剩余类）。

>性质：
>* 自反性：a≡a(% p) 
>* 对称性：a≡b(% p) → b≡a(% p) 
>* 传递性：(a≡b(% p), b≡c(% p)) → a≡c(% p) 
>* 消去律：ac≡bc(% p) → a≡b(% p/GCD(c,p) ） 
>* a≡b(% d) → a≡b(% d) 
>* (a≡b(% d),a≡b(% c)) → a≡b(% LCM(c,d)) 
>* 若a≡b (% p)，则对于任意的c，都有 (a + c) ≡ (b + c) (%p) 
>* 若a≡b (% p)，则对于任意的c，都有 (a * c) ≡ (b * c) (%p) 
>* 若a≡b (% p)，则对于任意的c，都有 (ac) ≡ (bc) (%p) 
>* 若a≡b (% p)，c≡d (% p)，则 (a +c) ≡ (b +d) (%p) 
  ​												(a - c) ≡ (b - d) (%p) 
  ​												(a * c) ≡ (b * d) (%p) 

例题：[余数之和](https://www.acwing.com/problem/content/description/201/)

### 线性同余方程

> 定义: $ax≡c(mod\ b)$,（未知数指数为1故叫一次同余方程也称线性同余方程）。等价于 $ax - c$ 是 b的倍数，设为-y倍,即 $ax + by = c$.当且仅当$gcd（a,b）$整除$c$有解。

>解题步骤：
1、化简方程为一次同余方程标准式：$ax≡b(mod\ n)$
2、利用$d = exgcd(a,b,x,y)$求线性同余方程$ax + by = gcd(a,b)$的解$x_0$以及公式 $x_1 = x_0*\frac{c}{d}$求出原方程$ax+by=c $的解$x_1$,前提是d|c.
3、最小非负整数解 公式：$x_1 = (x_1 \% (\frac{b}{d}) + (\frac{b}{d}) ) \% (\frac{b}{d})$
若方程的$ax + by = c $的一组整数解为$(x_1 , y_1)$，则它的任意整数解为$(x_1 + k * (\frac{b}{d}) , y_1 - k * (\frac{a}{d}) )$ ( k取任意整数 ), $T = \frac{b}{d}$就为 $x_1$ 增长的周期;

### 扩展gcd

>已知:$ax+by = gcd(a,b)$,求出一组特解，$x_0，y_0$。其他解为：$x=x_0+kb; y=y_0-ka;$
对于更为一般的方程$ax+by = c$,它有解当且仅当$d|c（d=gcd(a,b))$。
通解：$x = (\frac{c}{d})*x_0+k*(\frac{b}{d}) , y = (\frac{c}{d})*y_0 - k*(\frac{a}{d})（k∈Z）$。
最小正整数解：$x_1 = ((x_0*\frac{c}{d})\%(\frac{b}{d})+(\frac{b}{d}))\%(\frac{b}{d})$。
用途：求乘法逆元，不定方程，线性同余方程。

代码：

```c++
long long exgcd(long long a, long long b, long long &x, long long &y){
    if(b == 0){ x = 1,y = 0;return a; }
    long long d = exgcd(b , a%b, x, y);
    long long z = x; x =y; y = z - y * (a/b);
    return d;
}
```

### 乘法逆元

> 满足$ax≡1 (mod\ p)$的$x$值$(gcd(a,p)=1)$
> 通俗理解：$(\frac{1}{a})mod\ p$ 和 ($a$的逆元)$mod\ p$ 一样
> 作用：求$(\frac{a}{b})\%p$，当$a$过大，导致$\frac{a}{b}$无法直接求得时可以先求$b$对$p$的逆元$x$  ($b\%p$与b对p的逆元是一样的)，再乘$(a\%p)=n$，即
> $(n*x)\%p$和$(a/b)\%p$结果是一样的
> 求法:
> $a*x≡1 (mod\ p)$
> $a*x\%p = 1$
> $ax = yp +1$
> $ax - yp = 1$
> $gcd（a,p）= 1$,用$exgcd（）$求x最小正整数解

代码：

```c++
long long inverse(long long num,long long mod)  
{  
    long long x,y;  
    exgcd(num,mod,x,y);  
    while(x<0) x+=mod,y-=num;  
    return x;  
} 
```

扩展GCD&同余方程&乘法逆元 例题：[hdu2104](http://acm.hdu.edu.cn/showproblem.php?pid=2104) [hdu2669](http://acm.hdu.edu.cn/showproblem.php?pid=2669) [hdu1576](http://acm.hdu.edu.cn/showproblem.php?pid=1576) [poj1061](http://poj.org/problem?id=1061) [poj2115](http://poj.org/problem?id=2115) [poj2891](http://poj.org/problem?id=2891) [poj1845](http://poj.org/problem?id=1845) 


### 最大公约数（gcd）

> 定义：两个或多个整数共有约数中最大的一个。

求法：

* 欧几里得算法（辗转相除法）：如果d和r是a除以b的商和余数，那么a和b的最大公因数等于b和r的最大公因数，即 $gcd(a,b)=gcd(b,a\%b)$

  ```c++
  int gcd(int a, int b){ 
      while(b>0){ 
          int r = a % b; 
          a = b; b = r; 
      } 
      return a; 
  }
  ```

>性质：
>* 若$gcd(a,b)==1$ 则a,b互质
>* $gcd(a, b) = gcd(a-b, b)， 其中 a>b $
>* $gcd(a, b) = k*gcd(a_1 , b_1)， 其中 a=k*a_1，b=k*b_1$
>* 如果$a=p*a_1$，$p$是素数，且$b$和$p$互质，那么$gcd(a, b) = gcd(p*a_1 , b) = gcd(a_1 , b) $
>* 取$p=2$，有以下性质：
  * 如果a，b都是偶数，那么 $gcd(a, b) = gcd(a>>1, b>>1) *2 $
  * 如果a是偶数，b是奇数，那么 $gcd(a, b) = gcd(a>>1, b)$
  * 如果a，b都是奇数，那么 $gcd(a, b) = gcd( (a-b)>>1, b)$

### 最小公倍数（lcm）

> 定义：两个或多个整数公有的倍数叫做它们的公倍数，其中除0以外最小的一 个公倍数就叫做这几个整数的最小公倍数。

> 计算：$lcm(𝑎, 𝑏) = \frac{a*b}{gcd(𝑎, 𝑏)} $

例题: [LCM Walk](http://acm.hdu.edu.cn/showproblem.php?pid=5584)

### 贝祖定理：

> 定理：对于非零正整数$a、b$，令$d=gcd(a,b)$.则存在整数$x和y$ 使得$ax+by=d$ .

> 扩展：如果 $ax+by=n$ 有解，充要条件是$n是gcd(a,b)$的倍数

### 中国剩余定理

>定义：设 $k$ 组数 $(a_i , n_i )$, 其中 $n_i$两两互素，要找到最小的正整数$x$，满足方程组 $x≡a_i (mod\ n_i ) (i=1,2...k) $

> 算法步骤：
>
> * 令 $n=n_1n_2 ...n_k , m_i=\frac{n}{n_i} $
> * 显然 $gcd(m_i ,n_i )=1$，采用扩展欧几里德算法计算出 $x_i$ 满足$m_ix_i≡1(mod\ n_i )$  
>
> * 方程组的解 $x = (a_1x_1m_1+a_2x_2m_2+...+a_kx_km_k ) mod\ n  $
> * 此方程组任意两个解模n同余，因此x就是最小的

例题：[poj1006](http://poj.org/problem?id=1006) 

### 欧拉函数

> 定义：给定正整数n，欧拉函数 φ(n)=不大于n且和n互质的正整数的 个数(包括1)。 
>* $\varphi(1)=1$
>* $\varphi(n)=\varSigma _{i=1}^{n}\left[ gcd\left( i,n \right) ==1 \right]$

> 完全余数集合：$Z_n=\{不大于且和n互质的数\}$ ,$|Z_n|=\varphi(n)$ 

> 性质：
>
> * $p$为素数，则 $φ(p)=p-1 $ (因为质数与小于它的每一个数，都构成互质关系)
>
> * $p$为素数，正整数 $n=p^k$，则 $φ(n) = p^k - p^{k-1} $， 或写为 $φ(n) = p^{k-1} (p-1) = p^k (1- \frac{1}{p}) $
>
> * 两个素数 $p,q，n=pq$，则 $φ(n)=(p-1)(q-1)$
>
> * 正整数 $p,q$互质，$n=pq$，则 $φ(n)=φ(p)φ(q) $,推论：当$p=2，q$是奇数时，则 $φ(2q)=φ(q)$
>
> * 当$b$是质数，$a\%b=0$，则 $φ(ab)=φ(a)b$
>
> * 任意正整数$ n：n = p_1^{a1}p_2^{a2} ... p_m^{am} (p_i为素数) $, $φ(n) = n(1-\frac{1}{p_1}
> )(1-\frac{1}{p_2}
> )...(1-\frac{1}{p_m})$
>
> * 欧拉函数计算公式：$\varphi \left( n \right) =n\varPi _{i=1}^{m}\left( 1-\frac{1}{p_i} \right) $
>
> * 欧拉函数递推式：给定质数 $p$ 满足 $p|x$，若 $p^2 |x$ 不成立，则 $φ(x)=φ(\frac{x}{p})*(p-1) $，若 $p^2 |x$ 成立，则 $φ(x)=φ(\frac{x}{p})*p$； (可用于线性求1∼n所有数的欧拉函数)
>
>   * 代码：
>
>   * ```c++
>        int primes[N], euler[N], cnt;
>        bool st[N];
>        void get_eulers(int n) 
>        {
>            euler[1] = 1;
>            for (int i=2; i <= n; i++ ){
>                if ( !st[i] ){
>                primes[cnt++] = i;
>                euler[i] = i-1;
>                }
>                for ( int j=0; primes[j] <= n/i; j++ ){
>                    st[ primes[j]*i ] = true;
>                    if ( i % primes[j] == 0 ) {
>                    euler[ i*primes[j] ] = euler[i] * primes[j];
>                    break;
>                    } 
>                    euler[ i*primes[j] ] = euler[i] * ( primes[j]-1 );
>                }
>            } 
>        }
>        ```
>  *  整数n 等于n的所有约数（包括1和n）的欧拉函数之和 $𝑛 = \varSigma_{d|n}\varphi \left( d \right)$
> 
>  * 给定整数n，所有小于n且与n互质的数的和是$n∗φ(n)/2$ 
>
> *  给定两个整数a,b，令$d=gcd(a,b)$，则$\varphi(ab)=\frac{\varphi(a)\varphi(b)d}{\varphi(d)}$ 


例题：[hdu6322](http://acm.hdu.edu.cn/showproblem.php?pid=6322) [poj2478](http://poj.org/problem?id=2478) Longge的问题 (BZOJ-2705)  LCM SUM

### 欧拉定理

> 定理：正整数a和n互质，有 $a^{φ(n)} ≡ 1\ mod\ n$ 

> 模运算消去律：若 $gcd(c,p)=1$，则 $ac ≡ bc\ mod\ p → a ≡ b\ mod\ p $

### 费马小定理

> 定理：若正整数a与素数p互质，则有 $a^{p-1} ≡ 1 (mod\ p)$ ，或写为 $a^p ≡ a (mod\ p)$，$φ(p) = p-1$，代入欧拉定理即证.

### 求逆元

> 欧拉定理求逆元：若$a,p$互素，$a^{φ(p)}≡1 (mod\ p) → aa^{φ(p)-1} ≡ 1 (mod\ p)$

> 费马小定理求逆元：若$p$为素数，$a^{p-1}≡1 (mod\ p) → aa^{p-2} ≡ 1 (mod\ p) $

例题：[poj3696](http://poj.org/problem?id=3696)

### 计算大数取模

> 求$ (a^b)\%m $的值，其中 $a,b$ 都可能很大.
快速幂求$(a^b)\%m = ((a\%m)^b)\%m$ 

### 欧拉降幂

>欧拉降幂公式：
$$
a^b=\begin{cases}
	a^{b\%\varphi \left( m \right)}\left( mod\,\,m \right) ,          a,m\text{互质}\\
	a^b\left( mod\,\,m \right) ,                b\leqslant \varphi \left( m \right)\\
	a^{b\%\varphi \left( m \right) +\varphi \left( m \right)}\left( mod\,\,m \right) ,   b>\varphi \left( m \right)\\
\end{cases}
$$
> 求$(a^b)\%m$，其中$1≤a,m≤10^9，1≤b≤10^{1000000}$
> 若$gcd(a,m)=1$，由欧拉定理$a^{φ(m)}≡1(mod\ m)$:$a^b ≡a^{b\%φ(m)}(mod\ m)$
> 若$gcd(a,m)>1$，且$b≤φ(m)，则 a^b(mod m) $用快速幂计算
> 若$gcd(a,m)>1$，且$b>φ(m)，则 a^b≡a^{b\%φ(m)+φ(m)}(mod\ m) $

例题 [hdu4704](http://acm.hdu.edu.cn/showproblem.php?pid=4704)

### 莫比乌斯函数

> 定义：
$$
\mu \left( n \right) =\begin{cases}
	\text{1,  }if\,\,n=1\\
	\left( -1 \right) ^k, if\,\,n=p_1\times p_2\times ...\times p_k\\
	\text{0, 其它情况}\\
\end{cases}
$$
>其它情况是，n大于1且有平方因子时$\mu(n)=0$ 
 $(-1)^k，\mu(n)$ 按n的唯一分解的质因子的个数的奇偶计算。

> 性质：
>
> * 对于任意正整数n,$
> \varSigma _{d|n}\mu \left( d \right) =\begin{cases}
> 	\text{1, }n=1\\
> 	\text{0, }n>1\\
> \end{cases}
> $ 
>
> * 对于任意正整数n, $\varSigma _{d|n}\frac{\mu \left( d \right)}{d}=\frac{\varphi \left( n \right)}{n}$ 
>
> * 莫比乌斯函数是积性函数，对于任意两个互质的正整数a,b,满足$\mu(ab)=\mu(a)\mu(b)$ 
>
>   * 因此，可以用线性筛对莫比乌斯函数打表
>
>   * ```c++
>    void mus(int n)
>    {
>    tot = 0; mu[1]=1;
>    for(int i=2; i<n; i++) {
>    if( !vis[i] ) { pri[++tot]=i; mu[i]=-1; }
>    for(int j=1; j<=tot && i*pri[j]<n; j++) {
>        vis[ i*pri[j] ] = 1;
>        if( i%pri[j]==0 ) {
>            mu[ i*pri[j] ] = 0;
>            break;
>        }
>        mu[ i*pri[j] ] = -mu[i];
>    } 
>    } 
>    }
>    ```
>  ```
> 
>  ```
>
> ```
> 
> ```
>
> ```
> 
> ```
>
> ```
> 
> ```

例题： 完全平方数（BZOJ-2420）

> 莫比乌斯反演：
>
> 形式一：$F\left( n \right) =\varSigma _{d|n}f\left( d \right) \Longrightarrow f\left( n \right) =\varSigma _{d|n}\mu \left( d \right) F\left( \frac{n}{d} \right) ,\text{其中}\mu \left( d \right) \text{是莫比乌斯函数。}$ 
>
> 形式二：$F\left( n \right) =\varSigma _{n|d}f\left( d \right) \Longrightarrow f\left( n \right) =\varSigma _{n|d}\mu \left( \frac{d}{n} \right) F\left( d \right) $ 

例题：Problem B(BZOJ_2301)

### 积性函数

> 数论函数：若f(n)的定义域为正整数域，值域为复数，即 $f:Z^+ \rightarrow C$，则称f(n)为数论函数。 

> 积性函数：若f(n)为数论函数，且f(1)=1，对于任意两个互质的正整数a,b，均满足f(ab)=f(a)f(b)，则称其为积性函数。 

> 完全积性函数：若f(n)为积性函数，且对于任意整数a,b 都有f(ab)=f(a)f(b)，则称其为完全积性函数。 

> 性质：
>
> * 对于任意积性函数f，均有f(1)=1 
> * 对于一个大于1的正整数N，设$N=\varPi _{i=1}^{r}p_i^{a_i}$ ，其中$p_i$ 为互不相同的素数。那么，积性函数f有：$f(N)=f(\varPi _{i=1}^{r}p_i^{a_i})=\varPi _{i=1}^{r}f(p_i^{a_i})$ ,若函数f具有完全积性，则$f(N)= \varPi _{i=1}^{r}f(p_i)^{a_i}$

例题：[hdu2879](http://acm.hdu.edu.cn/showproblem.php?pid=2879)

### 积性函数线性筛

若f(x)是一个积性函数，那么我们可以在线性时间内计算出f(x)的前n项的值。

> 原理:
>
> * 采用计算最小质因子算法，可以线性时间计算出 不大于n的所有数的最 
>
> 小质因子。 
>
> * 与计算最小质因子同步计算f(x)，也就可以线性时间计算出 不大于n的所 
>
> 有数的f(x)。 

> 前提：要能快速计算$ f(1), f(p)和f(𝑝^𝑐) $
>
> * 利用计算最小质因子算法，找到x的最小质因子p，幂次为c，且$𝑝^𝑐 ≠ 𝑥$， 
>
>   那么$p^c$和$\frac{x}{p^c}$互质,$f(x)=f(p^c\frac{x}{p^c})=f(p^c)f(\frac{x}{p^c})$

计算最小质因子算法：

* 对于一个大于1的正整数n 
* 1) 从2开始枚举 i 直到n，令 $low_i$ 是 i 的最小质因子$p^c $

* 2) 若当前 i 的 $low_i$ 还未计算，那么 i 是素数（将i加入素数列表），同时 $low_i =i $

* 3) 在素数列表中枚举不超过 $low_i$ 的素数$p_j（i∙p_j≤n）$，计算$low_{i∙p_j}=p_j $；若$p_j$是i的约数，终止枚举，$low_{i∙p_j}= low_i ∙p_j$ 。 

  * 当 $p_j$是 i的约数；若$low_i=i$，此时 i一定是素数的幂， 

  * 否则，$i$可以分解为互质的两个部分 。 

* 因为每个数都只会被其最小的质因子筛去，所以该算法的时间复杂度是 $O(n)$。 

通用代码算法：

```c++
void sieve(){
    st[1]=low[1]=1; cnt=0;
    f[1]=对1直接计算;
    for (ll i=2; i<=n; i++) {
        if (!st[i]) low[i]=p[++cnt]=i, f[i]=对质数直接计算;
        for (ll j=1; j<=cnt&&i*p[j]<=n; j++) {
            st[ i*p[j] ]=1;
            if ( i%p[j]==0 ) { 
                low[ i*p[j] ]=low[i]*p[j];
                if (low[i]==i) f[ i*p[j] ]=对质数的若干次幂进行计算，即f(pc)
                else
                	f[ i*p[j] ]=f[ i/low[i] ] * f[ low[i]*p[j] ];
                break;
            }
            low[ i*p[j] ]=p[j]; 
            f[ i*p[j] ]=f[i]*f[p[j]];
        } 
    } 
}
```

线性筛约数和 $\sigma \left( i \right) =\varPi _{i=1}^{k}\left( \varSigma _{j=0}^{a_i}p_{i}^{j} \right) $

```c++
int main() {
    GetSumD(1e3);
    for(int i=1; i<=tot; i++)
    	printf("%d ", SD[i]);
    return 0;
}

const int N = 1e4+10;
int N, prime[N], vis[N], SD[N], sum[N], low[N], tot;
void GetSumD(int N) {
    vis[1]=SD[1]=low[1]=sum[1]=1;
    for( int i = 2; i<=N; i++ ) {
        if(!vis[i]) prime[++tot]=i, sum[i]=SD[i]=i+1, low[i]=i;
        for( int j=1; j<=tot && i*prime[j]<=N; j++ ) {
            vis[ i*prime[j] ] = 1;
            if( !(i % prime[j]) ) {
                low[ i*prime[j] ] = low[i] * prime[j];
                sum[ i*prime[j] ] = sum[i] + low[ i*prime[j] ];
                SD[ i*prime[j] ] = SD[i] / sum[i]*sum[ i*prime[j] ];
                break;
            }
            low[ i*prime[j] ] = prime[j];
            sum[ i*prime[j] ] = prime[j] + 1;
            SD[ i*prime[j] ] = SD[i]*SD[prime[j]];
        } 
    }
}
```

例题： tsy's number 2019南昌邀请赛网络赛

### 杜教筛

