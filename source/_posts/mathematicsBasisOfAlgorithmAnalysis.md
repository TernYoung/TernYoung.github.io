---
title: 算法分析的数学基础
date: 2019-08-11 11:54:36
tags:
	- 算法
categories:
	- 技术
author: Tern
authorLink: www.cputern.top
authorAbout: 一个好奇的人
authorDesc: 一个好奇的人
avatar: https://cdn.jsdelivr.net/gh/TernYoung/nicePicture/icon/favicon.png
comments: true
keywords: 算法
description: 算法分析的数学基础
photos: https://cdn.jsdelivr.net/gh/TernYoung/nicePicture/Wallpapers/a6.png
---


#### 计算的定义

> 可由一个给定计算模型机械地执行的规则或计算步骤序列称为该计算模型的一个计算
>
> 注意：
>
> * 一个计算机程序是一个计算（计算模型是计算机）
> * 计算可能永远不停止——不是算法

#### 算法的定义

> 算法是一个满足下列条件的计算：
>
> * 有穷性、确定性、能行性、输入、输出

#### 算的正确性分析

> 算法正确性：一个算法是正确的，如果它对于每一个输入都最终停止，而且产生正确的输出。
>
> 不做正确算法：
>
> * 不停止（在某个输入上）
> * 对所有输入都停止，但对某输入产生不正确的结果
>
> 算法正确性证明
>
> * 证明算法对所有输入都停止
> * 证明对每个输入都产生正确结果

#### 算法复杂性分析

> 目的：预测算法对不同输入所需资源量
>
> 复杂性测度：时间，空间，I/O等，是输入大小的函数
>
> 用途：为求解一个问题选择最佳算法、最佳设备
>
> 需要的数学基础：离散数学，组合数学，概率论，代数等
>
> 需要的数学能力：建立算法复杂性的数学模型，数学模型化简

算法复杂性分析的度量

* 输入的大小
* 时间复杂性：一个算法对特定输入的时间复杂性是该算法对该输入产生结果需要的原子操作或“步”数
* 空间复杂性：一个算法对特定输入的空间复杂性是该算法对该输入产生结果所需要的存储空间大小
* 最坏复杂性
* 最小复杂性
* 平均复杂性

#### 算法分析的模型

> 随机访问模型（Random-Access-Model，RAM）
>
> * 单处理机，串行执行，无并发
> * 基本数据类型
> * 基本操作（每个操作常数时间）
>
> 并行多处理机模型（PRAM）

插入排序的分析：

| INSERTION-SORT(A)                                        | 代价  | 次数                          |
| :------------------------------------------------------- | ----- | ----------------------------- |
| 1. for j = 2 to length[A]                                | $c_1$ | n                             |
| 2.      do key <--- A[j]                                 | $c_2$ | n-1                           |
| 3.           //insert A[j] to sorted sequence A[1...j-1] | 0     | n-1                           |
| 4.            i <--- j-1                                 | $c_4$ | n-1                           |
| 5.            while i>0 and A[i]>key                     | $c_5$ | $\varSigma _{j=2}^{n}t_j$     |
| 6.                   do A[i+1] <--- A[i]                 | $c_6$ | $\varSigma _{j=2}^{n}(t_j-1)$ |
| 7.                         i <--- i-1                    | $c_7$ | $\varSigma _{j=2}^{n}(t_j-1)$ |
| 8.            A[i+1] <--- key                            | $c_8$ | n-1                           |

$t_j$ 是对j来说循环中执行的次数

总时间代价T(n)=代价的和*每次执行次数

$T(n)=c_1n+c_2(n-1)+c_4(n-1)+c_5\varSigma _{j=2}^{n}t_j+c_6\varSigma _{j=2}^{n}(t_j-1)+c_7\varSigma _{j=2}^{n}(t_j-1)+c_8(n-1)$

最好代价：有序的数组

* $t_j=1$, 且6和7行执行0次
* $T(n)=c_1n+c_2(n-1)+c_4(n-1)+c_5(n-1)+c_8(n-1)\\\ \ \ \ \ \ \ \ =(c_1+c_2+c_4+c_5+c_8)n-(c_2+c_4+c_5+c_8)=cn+c'$ 

最坏代价：逆序数组

* $t_j=j$
* $\varSigma _{j=2}^{n}t_j=\varSigma _{j=2}^{n}j=\frac{n\left( n+1 \right)}{2}-\text{1,且 }\varSigma _{j=2}^{n}\left( t_j-1 \right) =\varSigma _{j-2}^{n}\left( j-1 \right) =\frac{n\left( n-1 \right)}{2}$
* $T(n)=c_1n+c_2(n-1)+c_4(n-1)+c_5(\frac{n(n+1)}{2}-1)+c_6(\frac{n(n-1)}{2}-1)+c_7(\frac{n(n-1)}{2})+c_8(n-1)\\\ \ \ \ \ \ \ \ =(\frac{(c_5+c_6+c_7)}{2})n^2+(c_1+c_2+c_4+\frac{c_5}{2}-\frac{c_6}{2}-\frac{c_7}{2}+c_8)n-(c_2+c_4+c_5+c_8)\\\ \ \ \ \ \ \ \ =an^2+bn+c$

平均代价：随机数

* 平均来看，$t_j=\frac{j}{2}.T(n)$ 与 $n^2$ 同阶，和最坏情况相同

#### 算法设计模式

* 暴力搜索
* 分治法
* 图搜索与枚举
  * 分支界限
  * 回溯
* 随机化方法

#### 算法实现方法

* 递归与迭代
* 顺序、并行与分布式
* 确定性与非确定性
* 近似求解与精确求解
* 量子算法

#### 最优化算法设计方法

* 线性规划
* 动态规划
* 贪心法
* 启发式方法


#### 增长的阶

* 用增长率描述算法的效率
* 忽略低阶项，保留最高阶项
* 忽略常系数
* 利用$\varTheta (n^2)$表示插入排序的最坏运行时间
* $\varTheta (1),\varTheta (lgn),\varTheta (\sqrt{n}),\varTheta (n),\varTheta (nlgn),\varTheta (n^2),\varTheta (n^3),\varTheta (2^n),\varTheta (n!)$
* 增长的记号：$O,\varTheta,\varOmega,o,\omega$ 

#### 同阶函数集合

$\varTheta(g(n))=\{f(n)|\exists c_1,c_2>0,n_0,\forall n>n_0,c_1g(n)\leqslant f(n)\leqslant c_2g(n)\}$称为与$g(n)$同阶的函数集合。

* 如果$f(n)\in \varTheta (g(n)),g(n)$ 与$f(n)$ 同阶
* $f(n)\in \Theta(g(n))$ ,记作$f(n)=\Theta(g(n))$ 

![同阶函数集合](/static/images/algorithm/同阶函数集合.png)

$\Theta(g(n))$函数的例子

* 证明 $\frac{1}{2n^2}-3n=\Theta(n^2)$
  - $c_1n^2 \leqslant \frac{1}{2}n^2-3n \leqslant c_2n^2$
  - $c_1\leqslant \frac{1}{2}-\frac{3}{n} \leqslant c_2$
  - 对于任意 $n \geqslant1 ,c_2 \geqslant \frac{1}{2},$ 且对于任意$n \geqslant 7,c_1 \leqslant \frac{1}{14}$ 
  - 因此，$c_1=\frac{1}{14},c_2=\frac{1}{2},n_0=7$ 
* 证明$6n^3\ne \Theta(n^2)$
  * 如果存在$c_1、c_2>0,n_0$使得当$n\geqslant n_0$时，$c_1n^2\leqslant 6n^3 \leqslant c_2n^2$。
  * 当$n>\frac{c_2}{6}$时，$n \leqslant \frac{c_2}{6}$,矛盾。
* 通常$f(n)=an^2+bn+c=\Theta(n^2)$ ,其中$a,b,c$是常数且$a>0$
* $p(n)=\varSigma _{i=0}^{d}a_in^i,$ 其中$a_i$ 是常数且$a_d>0$
  * $p(n)=\Theta (n^d)$
* $\Theta (n^0)$或者$\Theta (1)$,常数时间复杂性。

#### 低阶函数集合

对于给定的函数$g(n)$

*  $ O(g(n))=\{f(n) $:存在正常数$c$和$n_0$满足对于所有$n \geqslant n_0, 0 \leqslant f(n) \leqslant cg(n)\}$
* 记作$f(n)\in O(g(n))$,或简记为$f(n)=O(g(n)).$

![低阶函数集合](/static/images/algorithm/低阶函数集合.png)

> $\Theta(g(n))$和$O(g(n))$的关系
>
> * $f(n)=\Theta(g(n))\Rightarrow f(n)=O(g(n))$
> * $\Theta$ 标记强于 $O$ 标记
> * $\Theta(g(n)) \subseteq O(g(n))$
> * $an^2+bn+c=\Theta(n^2),且 =O(n^2)$
> * $an+b = O(n^2).$ 为什么？
> * $ n = O(n^2)$!!!
> * $O$标记，表示渐进上界
> * $\Theta$标记，表示渐进紧界

#### 高阶函数集合

对于给定的函数g(n)

* $\varOmega(g(n))=\{f(n):$ 存在正常数 $c$ 和 $n_0$,使得对于所有$n \geqslant n_0,0\leqslant cg(n) <f(n)\}$
* 记作$f(n)\in \varOmega(g(n)),$ 或简记为$f(n)=\varOmega(g(n)).$ 

![高阶函数集合](/static/images/algorithm/高阶函数集合.png)

> $O,\Theta,\varOmega$ 标记的关系
>
> * 对于$f(n)$和$g(n),f(n)=\Theta(g(n))$ 当且仅当$f(n)=O(g(n))且f(n)=\varOmega(g(n)).$
> * $O:$ 渐进上界
> * $\Theta:$ 渐进紧界
> * $\varOmega:$ 渐进下界 

> 关于$\varOmega$ 标记
>
> * 用来描述运行时间的最好情况 
> * 对所有输入都正确 
> * 比如，对于插入排序
>   * 最好运行时间是$\varOmega(n)$
>   * 或者说，运行时间是$\varOmega(n)$
>   * 最坏运行时间是 $\varOmega(n^2)$  
>   * 但是说运行时间是 $\varOmega(n^2)$ 则有误
> * 可以用来描述问题
>   * 排序问题的时间复杂性是$\varOmega(n)$

#### 严格低阶函数

给定一个函数$g(n)$

* $o(g(n))=\{f(n):$ 对于任意正常数 $c$ ,存在一个正数$n_0$,从而对所有$n \geqslant n_0$ ,满足$0 \leqslant f(n) < cg(n)\}$
* 记作$f(n)\in o(g(n)),$ 或者简写为$f(n)=o(g(n))$.

![严格低阶函数](/static/images/algorithm/严格低阶函数.png)

$o(g(n))$ 函数的例子

* 证明$2n=o(n^2)$
  * 对 $\forall c>0$,欲 $2n<cn^2$ ,必 $2<cn$,即$\frac{2}{c}<n$.
  * 所以，当$n_0=\frac{2}{c}$ 时，$2n<cn^2$对$\forall c>0,n \geqslant n_0$.
* 证明 $2n^2 \ne o(n^2)$
  * 当$c=1>0$ 时，对于任何$n_0$ ,当$n \geqslant n_0,2n^2<cn^2$ 都不成立

> 关于o标记
>
> * O标记可能是或不是紧的
>   * $2n^2=O(n^2)$ 是紧的，但$2n=O(n^2)$ 不是紧的
> * o标记用于标记上界但不是紧的情况
>   * $2n=o(n^2)$,但是$2n^2 \ne o(n^2)$ 
> * 区别：某个正常数c在O标记中， 但所有正常数c在o标记中.
>
> $f(n)=o(g(n)) \Rightarrow \underset{n\rightarrow \infty}{\lim}\frac{f\left( n \right)}{g\left( n \right)}=0$
>
> 证：由于$f(n)=o(g(n))$,对任意$\varepsilon >0$,存在$n_0$,当$n\leqslant n_0$ 时，即$0 \leqslant \frac{f(n)}{g(n)} \leqslant \varepsilon$.于是，$\underset{n\rightarrow \infty}{\lim}\frac{f\left( n \right)}{g\left( n \right)}=0$

#### 严格高阶函数集合

对于给定函数$g(n)$

* $\omega(g(n))=\{f(n):$  对于任意正常数*c*, 存在正数$n_0$ 对于$n \geqslant n_0, 0\leqslant cg(n)<f(n)\}$
* 记作$f(n)\in \omega(g(n))$, 或者简记为$f(n)=\omega (g(n))$.
* $\omega$标记,类似o标记,表示不紧的下界。
  * $\frac{n^2}{2}=\omega(n)$,但$\frac{n^2}{2} \ne \omega(n^2)$
* $f(n)=\omega (g(n))$当且仅当$g(n)=o(f(n))$
* $\underset{n\rightarrow \infty}{\lim}\frac{f\left( n \right)}{g\left( n \right)}=\infty$

#### 渐进符号的性质

* 传递性：所有五个标记
  * $f(n)=\Theta(g(n))且g(n)=\Theta(h(n))\rightarrow f(n)=\Theta(h(n))$
* 自反性：$O,\Theta,\varOmega$
  * $f(n)=\Theta(f(n))$
* 对称性：$\Theta$
  * $f(n)=\Theta(g(n))当且仅当g(n)=\Theta(f(n))$
* 反对称性: 
  * $f(n)=O(g(n))当且仅当g(n)=\varOmega(f(n))$
  * $f(n)=o(g(n))当且仅当g(n)=\omega(f(n))$

> 注意：并非所有函数都是可比的，即对于函数$f(n)$和$g(n)$,可能$f(n)\ne O(g(n)),f(n)\ne \varOmega(g(n))$.例如，$n和n^{1+sinn}$

#### 增长的阶

* 用增长率描述算法的效率
* 忽略低阶项，保留最高阶项
* 忽略常系数
* 利用$\varTheta (n^2)$表示插入排序的最坏运行时间
* $\varTheta (1),\varTheta (lgn),\varTheta (\sqrt{n}),\varTheta (n),\varTheta (nlgn),\varTheta (n^2),\varTheta (n^3),\varTheta (2^n),\varTheta (n!)$
* 增长的记号：$O,\varTheta,\varOmega,o,\omega$ 

#### 同阶函数集合

$\varTheta(g(n))=\{f(n)|\exists c_1,c_2>0,n_0,\forall n>n_0,c_1g(n)\leqslant f(n)\leqslant c_2g(n)\}$称为与$g(n)$同阶的函数集合。

* 如果$f(n)\in \varTheta (g(n)),g(n)$ 与$f(n)$ 同阶
* $f(n)\in \Theta(g(n))$ ,记作$f(n)=\Theta(g(n))$ 

![同阶函数集合](/static/images/algorithm/同阶函数集合.png)

$\Theta(g(n))$函数的例子

* 证明 $\frac{1}{2n^2}-3n=\Theta(n^2)$
  - $c_1n^2 \leqslant \frac{1}{2}n^2-3n \leqslant c_2n^2$
  - $c_1\leqslant \frac{1}{2}-\frac{3}{n} \leqslant c_2$
  - 对于任意 $n \geqslant1 ,c_2 \geqslant \frac{1}{2},$ 且对于任意$n \geqslant 7,c_1 \leqslant \frac{1}{14}$ 
  - 因此，$c_1=\frac{1}{14},c_2=\frac{1}{2},n_0=7$ 
* 证明$6n^3\ne \Theta(n^2)$
  * 如果存在$c_1、c_2>0,n_0$使得当$n\geqslant n_0$时，$c_1n^2\leqslant 6n^3 \leqslant c_2n^2$。
  * 当$n>\frac{c_2}{6}$时，$n \leqslant \frac{c_2}{6}$,矛盾。
* 通常$f(n)=an^2+bn+c=\Theta(n^2)$ ,其中$a,b,c$是常数且$a>0$
* $p(n)=\varSigma _{i=0}^{d}a_in^i,$ 其中$a_i$ 是常数且$a_d>0$
  * $p(n)=\Theta (n^d)$
* $\Theta (n^0)$或者$\Theta (1)$,常数时间复杂性。

#### 低阶函数集合

对于给定的函数$g(n)$

*  $ O(g(n))=\{f(n) $:存在正常数$c$和$n_0$满足对于所有$n \geqslant n_0, 0 \leqslant f(n) \leqslant cg(n)\}$
* 记作$f(n)\in O(g(n))$,或简记为$f(n)=O(g(n)).$

![低阶函数集合](/static/images/algorithm/低阶函数集合.png)

> $\Theta(g(n))$和$O(g(n))$的关系
>
> * $f(n)=\Theta(g(n))\Rightarrow f(n)=O(g(n))$
> * $\Theta$ 标记强于 $O$ 标记
> * $\Theta(g(n)) \subseteq O(g(n))$
> * $an^2+bn+c=\Theta(n^2),且 =O(n^2)$
> * $an+b = O(n^2).$ 为什么？
> * $ n = O(n^2)$!!!
> * $O$标记，表示渐进上界
> * $\Theta$标记，表示渐进紧界

#### 高阶函数集合

对于给定的函数g(n)

* $\varOmega(g(n))=\{f(n):$ 存在正常数 $c$ 和 $n_0$,使得对于所有$n \geqslant n_0,0\leqslant cg(n) <f(n)\}$
* 记作$f(n)\in \varOmega(g(n)),$ 或简记为$f(n)=\varOmega(g(n)).$ 

![高阶函数集合](/static/images/algorithm/高阶函数集合.png)

> $O,\Theta,\varOmega$ 标记的关系
>
> * 对于$f(n)$和$g(n),f(n)=\Theta(g(n))$ 当且仅当$f(n)=O(g(n))且f(n)=\varOmega(g(n)).$
> * $O:$ 渐进上界
> * $\Theta:$ 渐进紧界
> * $\varOmega:$ 渐进下界 

> 关于$\varOmega$ 标记
>
> * 用来描述运行时间的最好情况 
> * 对所有输入都正确 
> * 比如，对于插入排序
>   * 最好运行时间是$\varOmega(n)$
>   * 或者说，运行时间是$\varOmega(n)$
>   * 最坏运行时间是 $\varOmega(n^2)$  
>   * 但是说运行时间是 $\varOmega(n^2)$ 则有误
> * 可以用来描述问题
>   * 排序问题的时间复杂性是$\varOmega(n)$

#### 严格低阶函数

给定一个函数$g(n)$

* $o(g(n))=\{f(n):$ 对于任意正常数 $c$ ,存在一个正数$n_0$,从而对所有$n \geqslant n_0$ ,满足$0 \leqslant f(n) < cg(n)\}$
* 记作$f(n)\in o(g(n)),$ 或者简写为$f(n)=o(g(n))$.

![严格低阶函数](/static/images/algorithm/严格低阶函数.png)

$o(g(n))$ 函数的例子

* 证明$2n=o(n^2)$
  * 对 $\forall c>0$,欲 $2n<cn^2$ ,必 $2<cn$,即$\frac{2}{c}<n$.
  * 所以，当$n_0=\frac{2}{c}$ 时，$2n<cn^2$对$\forall c>0,n \geqslant n_0$.
* 证明 $2n^2 \ne o(n^2)$
  * 当$c=1>0$ 时，对于任何$n_0$ ,当$n \geqslant n_0,2n^2<cn^2$ 都不成立

> 关于o标记
>
> * O标记可能是或不是紧的
>   * $2n^2=O(n^2)$ 是紧的，但$2n=O(n^2)$ 不是紧的
> * o标记用于标记上界但不是紧的情况
>   * $2n=o(n^2)$,但是$2n^2 \ne o(n^2)$ 
> * 区别：某个正常数c在O标记中， 但所有正常数c在o标记中.
>
> $f(n)=o(g(n)) \Rightarrow \underset{n\rightarrow \infty}{\lim}\frac{f\left( n \right)}{g\left( n \right)}=0$
>
> 证：由于$f(n)=o(g(n))$,对任意$\varepsilon >0$,存在$n_0$,当$n\leqslant n_0$ 时，即$0 \leqslant \frac{f(n)}{g(n)} \leqslant \varepsilon$.于是，$\underset{n\rightarrow \infty}{\lim}\frac{f\left( n \right)}{g\left( n \right)}=0$

#### 严格高阶函数集合

对于给定函数$g(n)$

* $\omega(g(n))=\{f(n):$  对于任意正常数*c*, 存在正数$n_0$ 对于$n \geqslant n_0, 0\leqslant cg(n)<f(n)\}$
* 记作$f(n)\in \omega(g(n))$, 或者简记为$f(n)=\omega (g(n))$.
* $\omega$标记,类似o标记,表示不紧的下界。
  * $\frac{n^2}{2}=\omega(n)$,但$\frac{n^2}{2} \ne \omega(n^2)$
* $f(n)=\omega (g(n))$当且仅当$g(n)=o(f(n))$
* $\underset{n\rightarrow \infty}{\lim}\frac{f\left( n \right)}{g\left( n \right)}=\infty$

#### 渐进符号的性质

* 传递性：所有五个标记
  * $f(n)=\Theta(g(n))且g(n)=\Theta(h(n))\rightarrow f(n)=\Theta(h(n))$
* 自反性：$O,\Theta,\varOmega$
  * $f(n)=\Theta(f(n))$
* 对称性：$\Theta$
  * $f(n)=\Theta(g(n))当且仅当g(n)=\Theta(f(n))$
* 反对称性: 
  * $f(n)=O(g(n))当且仅当g(n)=\varOmega(f(n))$
  * $f(n)=o(g(n))当且仅当g(n)=\omega(f(n))$

> 注意：并非所有函数都是可比的，即对于函数$f(n)$和$g(n)$,可能$f(n)\ne O(g(n)),f(n)\ne \varOmega(g(n))$.例如，$n和n^{1+sinn}$

