---
title: 概率统计期末总结
date: 2020-01-04 21:59:36
tags:
	- 概率统计
categories:
	- 技术
author: Tern
authorLink: cputern.top
authorAbout: 一个好奇的人
authorDesc: 一个好奇的人
avatar: https://cdn.jsdelivr.net/gh/TernYoung/nicePicture/icon/favicon.png
comments: true
keywords: 关键字
description: 描述
photos: https://cdn.jsdelivr.net/gh/TernYoung/nicePicture/smallPic/pic013.jpg
---



## 第一章  随机事件及其概率

### 1.排列组合公式

> 排列：$A_{n}^{m}=\frac{n!}{\left( n-m \right) !}$
组合：$C_{n}^{m}=\frac{A_{n}^{m}}{m!}=\frac{n!}{m!\left( n-m \right) !};C_{n}^{m}=C_{n}^{n-m}$

### 2.基本概念

$$
\begin{aligned}
	E\phantom{=}\text{随机试验}\\
	S\phantom{=}\text{随机试验}E\text{的样本空间}\\
	A,B,C\phantom{=}\text{事件，样本空间}S\text{的子集}\\
	x,y\phantom{=}\text{采样点，随机试验的可能取值}\\
	\bar{A}\phantom{=}\text{事件}A\text{的逆事件}\\
\end{aligned}
$$

事件：
$$
A=\left( 5,\;5 \right) ,\;B=\left( 3,\;7 \right) ,
$$
$$
S=\left\{ \left( x,\;y \right) \left| x=1,\;2,...,19,\;y=1,\;2,...,\;19 \right. \right\} ,
$$
$$
A\subset S,\;B\subset S
$$

### 3.随机事件的关系

$设试验 E 的样本空间为 S，A,B,A_k(k=1,2,...)是 S 的子集$ .

* 子事件：$A\subset B\;\text{or }A\Rightarrow B$
* 和事件：$C=A\cup B=\left\{ x\left| x\in A\;\text{or }x\in B \right. \right\}$ ;  $C=\bigcup_{i=1}^n{A_i}$
* 相等：$\left. \begin{array}{r}A\subset B\\ B\subset A\\ \end{array} \right\} \Rightarrow A=B$
* 积事件：$C=AB=A\cap B=\left\{ x\left| x\in A\;\text{and}x\in B \right. \right\} $ ； $C=\bigcap_{i=1}^n{A_i}$
* 差事件：$
  C=A-B=\left\{ x\left| x\in A\;\text{and} x \notin B \right. \right\} 
  $
* 互不相容：$
  A\cap B=\varnothing 
  $
* 对立事件：$A\cap B=\varnothing\;\text{and}\;A\cup B=S$　;　$A=\bar{B},\;B=\bar{A},\;\bar{B}=S-B$

### 4.事件的运算

与集合运算一样

交换律：$
A\cup B=B\cup A  ; A\cap B=A\cap B
$

结合律：$
A\cup \left( B\cup C \right) =\left( A\cup B \right) \cup C
\\
A\cap \left( B\cap C \right) =\left( A\cap B \right) \cap C
$

分配律：$
A\cup \left( B\cap C \right) =\left( A\cup B \right) \cap \left( B\cup C \right) 
\\
A\cap \left( B\cup C \right) =\left( A\cap B \right) \cup \left( B\cap C \right) 
$

摩根律：$
\overline{A\cup B}=\overline{A}\cap \overline{B}
;
\overline{A\cap B}=\overline{A}\cup \overline{B}
$

### 5.频率与概率

频率的定义：$
f_n\left( A \right) =\frac{n_A}{n}
$

频率的性质：

* $
  0\le f_n\left( A \right) \le 1
  $
* $
  0\le f_n\left( A \right) \le 1f_n\left( S \right) =1
  $
* $
  A\cap B=\varnothing \Rightarrow f_n\left( A+B \right) =f_n\left( A \right) +f_n\left( B \right) 
  $

概率与频率的关系：$
P\left( A \right) =\lim_{n\rightarrow \infty}f_n\left( A \right) 
$

概率的性质：

* $
  P\left( \varnothing \right) =0,\;P\left( S \right) =1
  $
* $
  \forall A\in S,\;P\left( A \right) \ge 0
  $
* $
  \text{若}A_iA_j=\varnothing \left( i\ne j,\;\;i,j=1,2,3,... \right) ,\;\text{则有}
  \\
  P\left( A_1\cup A_2\cup \cdots \cup A_n\cdots \right) =P\left( A_1 \right) +P\left( A_2 \right) +\cdots P\left( A_n \right) +\cdots 
  \\
  \text{或者}
  \\
  P\left( \bigcup_{i=1}^{+\infty}{A_i} \right) =\prod_{i=1}^{+\infty}{P\left( A_i \right)}
  $
* $
  \forall A,\;B\in S,P\left( A-B \right) =P\left( A \right) -P\left( AB \right) 
  $
* 若$A \in B$ , 有 $ P(B)\ge P(A)$ 且 $P\left( A-B \right) =P\left( A \right) -P\left( B \right) $
* $ \forall A\in S,
  P\bigl( \bar{A} \bigr) =1-P\bigl( A \bigr) 
  $
* $
  \forall A,B\in S,
  P\left( A\cup B \right) =P\left( A \right) +P\left( B \right) -P\left( AB \right) 
  $

### 6.古典概型和几何概型

古典概型：$
P\left( A \right) =\frac{A\text{包含的基本事件数}n\left( A \right)}{S\text{中基本事件的总数}n}
$

几何概型：$
P\left( A \right) =\frac{m\left( G_A \right)}{m\left( G \right)}
$

### 7.条件概率

$$
\overset{A}{\overbrace{\bigcirc \bigcirc \bigcirc \bigcirc \overset{AB}{\overbrace{\phantom{\bigcirc \bigcirc \bigcirc }}}}}\!\!\!\!\!\!\!\!\!\!\!\!\!\!\!\!\!\!\!\!\!\!\!\!\underset{B}{\underbrace{\bigcirc \bigcirc \bigcirc \bigcirc \bigcirc }}
$$
定义在事件B已经发生情况下，事件A发生的条件概率为$P\left( A\mid B \right) =\frac{P\left( AB \right)}{P\left( B \right)}，P\left( B \right) >0$

性质：

* 非负性：对于每一事件B,有 $P(B|A)\ge 0$ 
* 规范性：对于必然事件S,有 $P(S|A)=1$ 
* 可列可加性：设$ B_1,B_2,...$是两两互不相容的事件，则有 $
  P\left( \bigcup_{i=1}^{\infty}{B_i}|A \right) =\sum_{i=1}^{\infty}{P\left( B_i|A \right)}
  $

注意：条件概率P(B|A)与一般概率P(B)是有区别的! P(B)是在试验条件下,样态空间是$\varOmega $;而P(B|A)以A发生为条件,样本空间缩小为A,相当于把A看作新的样本空间求AB发生的概率。

乘法公式：$
P\left( AB \right) =P\left( A \right) P\left( B\mid A \right) 
\\
P\left( ABC \right) =P\left( A \right) P\left( B\mid A \right) P\left( C\mid AB \right) 
$

### 8.全概率公式和贝叶斯公式

$P(A)=P(AB)+P(A\bar B))$

全概率公式：$
P\left( A \right) =P\left( A|B \right) P\left( B \right) +P\left( A|\bar{B} \right) P\left( \bar{B} \right) 
$

贝叶斯公式：$
P\left( B|A \right) =\frac{P\left( AB \right)}{P\left( A \right)}=\frac{P\left( A|B \right) P\left( B \right)}{P\left( A|B \right) P\left( B \right) +P\left( A|\bar{B} \right) P\left( \bar{B} \right)}
$
$
P\left( B_k\mid A \right) =\frac{P\left( B_k \right) \cdot P\left( A\mid B_k \right)}{\sum_{i=1}^n{P\left( B_i \right) \cdot P\left( A\mid B_i \right)}}
$

### 9.事件的独立性

独立性原理：$
P\left( A\mid B \right) =P\left( B \right) 
$

相互独立的事件：$
P\left( AB \right) =P\left( A \right) \cdot P\left( B \right) 
$

三事件相互独立：$
\left. \begin{array}{r}
	P\left( AB \right) =P\left( A \right) \cdot P\left( B \right)\\
	P\left( AC \right) =P\left( A \right) \cdot P\left( C \right)\\
	P\left( BC \right) =P\left( B \right) \cdot P\left( C \right)\\
	P\left( ABC \right) =P\left( A \right) \cdot P\left( B \right) \cdot P\left( C \right) \\
\end{array}\,\, \right\} \Rightarrow A,B,C三事件相互独立
$

关于独立性的一些结论：

* $P\left( AB \right) =P\left( A \right) P\left( B \right)\\P(B)=P(B|A)\\P(B|A)=P(B| \bar A)\\P(B|A)=P(B| \bar A)$
* $A$和$\bar B$ $\bar A$和$B$ $ \bar A$和$\bar B$ 也相互独立
* A 和 B 相互独立 与 A和B互不相容不能同时成立，$
  \text{AB}=\varnothing \Longleftrightarrow \ \text{P}\left( \text{AB} \right) =0\ \text{与 P}\left( \text{AB} \right) =\text{P}\left( \text{A} \right) \text{P}\left( \text{B} \right) >0\text{矛盾}
  $
* $P(SA)=P(S)P(A)=P(A)\\P(\varnothing A)=P(\varnothing)P(A)=0$

## 第二章 随机变量及其分布

### 1.随机变量
$$
\begin{array}{c}
	S\phantom{=}\text{样本空间}\\
	E\phantom{=}\text{随机试验}\\
	e\phantom{=}\text{样本空间}S\text{中的一个样本点}\\
	X\left( e \right) \phantom{=}\text{与每一个}e\text{对应的实数，随机变量}\\
	p_k\phantom{=}\text{随机变量}X\text{的概率分布律，简称分布律}\\
\end{array}
$$

### 2.离散型随机变量及其分布

$
\text{定义：}p_k=P\left( X=x_k \right) 
\\
\text{其中}p_k\ge 0,\;k=1,\;2,\;3,\;...\;+\infty ,\ \text{且有}
\\
\sum_{k=1}^{+\infty}{p_k}=1
$

常用分布

|   名称   |             符号             |                            分布律                            |                             说明                             |
| :------: | :--------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: |
| 0-1分布  |           $b(1,p)$           | $P\left( X=1 \right) =p,\\P\left( X=0 \right) =1-p,\\(0<p<1)$ |    只有两个可能结果0和1，比如抛<br/>硬币，产品是否合格等     |
| 二项分布 |           $b(n,p)$           | $P\left( X=k \right) =C_{n}^{k}p^kq^{n-k},\\\left( 0<p<1,q=1-p\right)\\k=0,1,2,...,n$ | n重伯努利试验中A发生的次数服<br/>从二项分布,其中P表示每次试验中<br/>A发生的概率,比如抛n次硬币正面<br/>出现的次数。 |
| 泊松分布 | $\pi \left( \lambda \right)$ | $P\left( X=k \right) =\frac{e^{-\lambda}\lambda ^k}{k\;!},\\ \lambda >0,k=0,1,2,...,n$ | 表示一段时间间隔或一定范围内A<br/>发生的次数服从泊松分布,比如加油<br/>站一小时内来的汽车数量,一天内某<br/>个路段发生交通事故的次数等。 |

泊松定理

$设 X 服从二项分布B(n,p),当n较大,p较小时,X近似服从泊松分布P(np),即$
$$
\text{P}\left\{ \text{X}=\text{k} \right\} =\text{C}_{\text{n}}^{\text{k}}\text{p}^{\text{k}}\text{q}^{\text{n}-\text{k}}\approx \frac{\left( \text{np} \right) ^{\text{k}}\text{e}^{-\text{np}}}{\text{k!}}
$$
这个定理在二项分布计算中,当遇到n很大,P很小,不好计算时,可以用泊松分布近似计算。

离散型随机变量的分布函数
$$
\begin{aligned}
	X\phantom{=}\text{随机变量}\\
	F\left( x \right) \phantom{=}\text{随机变量}X\text{的分布函数}\\
\end{aligned}
$$

定义：$
\;F\left( x \right) =P\left( X\le x \right) ,\;x\in \left( -\infty ,\;+\infty \right) 
$

性质：

* $
  若 -\infty <x_1<x_2<+\infty \;则\;F\left( x_1 \right) \le F\left( x_2 \right) 
  $
* $
  \text{P}\left\{ \text{a}<\text{X}\le \text{b} \right\} =\text{F}\left( \text{b} \right) -\text{F}\left( \text{a} \right) 
  $
* $0\le F\left( x \right) \le 1\\F\left( +\infty \right) \triangleq \lim_{x\rightarrow +\infty}F\left( x \right) =1\\F\left( -\infty \right) \triangleq \lim_{x\rightarrow -\infty}F\left( x \right) =0$
* $F(x)右连续，F\left( x_{+0} \right) =F\left( x \right) $

### 3.连续型随机变量及其分布

$$
\begin{aligned}
	X\phantom{=}\text{随机变量}\\
	F\left( x \right) \phantom{=}\text{随机变量}X\text{的概率分布律}\\
	f\left( x \right) \phantom{=}\text{随机变量}X\text{的概率密度}\\
\end{aligned}
$$

与离散型区别：

* 离散型为散点，图中散点长度相加为1
* 连续型为密集连续，图中所有线相加为1，即积分为1

连续型随机变量的概率密度函数

定义：$
\text{对于}X\sim F\left( x \right) 
\text{若有}\exists f\left( x \right) \ge 0,\;x\in \left( -\infty ,\;+\infty \right) \text{，则}
F\left( x \right) =\int_{-\infty}^x{f\left( t \right) \text{d}t}
$

性质：

* $
  f\left( x \right) \ge 0
  $
* $
  \int_{-\infty}^{+\infty}{f\left( x \right) \text{d}x}=1
  $
* $
  \forall a,\;b\left( a\le b \right) ,
  P\left( a<X\le b \right) =\int_a^b{f\left( x \right) \text{d}x}=F\left( b \right) -F\left( a \right) 
  $
* 若 $
  f\left( x_- \right) =f\left( x \right) =f\left( x_+ \right) 
  $ ,则有 $F^`(x)=f(x)$
* 对任意一点 $a$ , 始终有 $P(X=a)=0$

常用分布

|   名称   |                符号                |                           概率密度                           |                           分布函数                           |
| :------: | :--------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: |
| 均匀分布 |              $U(a,b)$              | $f\left( x \right) =\begin{cases}	\frac{1}{b-a},&		a\le x\le b\\	0&		\text{其他}\\\end{cases}$ | $F\left( x \right) =\begin{cases}	0,&		x<a\\\\	\frac{x-a}{b-1},&		a\le x<b\\\\	1,&		x\ge b\\\end{cases}  $ |
| 指数分布 |    $ e\left( \lambda \right) $     | $f\left( x \right) = \begin{cases}	\frac{1}{\lambda}e^{-x/\lambda}&		x>0\\	0&		x\le 0\\\end{cases} $ | $F\left( x \right) =\begin{cases}	1-e^{-x/\lambda}&		x>0\\	0&		x\le 0\\\end{cases}$ |
| 正态分布 | $N\left( \mu ,\;\sigma ^2 \right)$ | $f\left( x \right) =\frac{1}{\sqrt{2\pi}\sigma}e^{-\frac{\left( x-\mu \right) ^2}{2\sigma ^2}},\;x\in \left( -\infty ,\;+\infty \right) $ | $F\left( x \right) =\varPhi \left( \frac{x-\mu}{\sigma} \right)$ |

正态分布：

* 当 $\mu =0,\;\sigma =1$ 时称 X 服从标准正态分布 $N(0,1)$
* 以 $x=\mu$ 对称,当 $x<\mu$ 时单调上升,当 $x>\mu$ 时单调下降,当$x=\mu$ 处取到最大值
* 在 $x=\mu \pm \sigma$ 处有拐点；并以 $ y=0 $ 为水平渐进线
* 标准正态分布概率密度满足 $f(-x)=f(x)$ ,分布函数满足 $\Phi \left( -\text{x} \right) =1-\Phi \left( \text{x} \right) $
* 若 $X\sim N\left( \mu ,\;\sigma ^2 \right) $ ，则 $
  \text{Z}=\frac{X-\mu }{\sigma }~\text{N}\left( 0,1 \right) 
  $

正态分布概率的计算公式：

$
\text{P}\left\{ \text{X}<\text{x} \right\} =\text{P}\left\{ \text{X}\le \text{x} \right\} =\text{P}\left\{ \frac{\text{X}-\mu }{\sigma }\le \frac{\text{x}-\mu }{\sigma } \right\} =\text{P}\left\{ \text{Z}\le \frac{\text{x}-\mu }{\sigma } \right\} =\Phi \left( \frac{\text{x}-\mu }{\sigma } \right) 
$

$P\left\{ X\ge x \right\}=P\left\{X>x\right\}=\text{P}\left\{ \frac{\text{X}-\mu }{\sigma }> \frac{\text{x}-\mu }{\sigma } \right\}=1-F(x)=1-\Phi  \frac{\text{x}-\mu }{\sigma }$

$\text{P}\left\{ \text{x}_1<\text{X}<\text{x}_2 \right\} =\Phi \left( \frac{\text{x}_2-\mu }{\sigma } \right) -\Phi \left( \frac{\text{x}_1-\mu }{\sigma } \right) $

### 4.随机变量的函数的分布

离散型：

* 第一步，求出Y所有可能的值
* 第二步，对Y相同取值的概率进行合并，得到Y的分布列

连续型：

* 第一步，求出Y的分布函数$F_Y(y)$
* 第二步，两边同时对 y 求导
* 第三步，根据 $f_x$ 求出 $f_y$

> 例，假设魔方边长 $X~N(10,1^2)$,试求它的体积 $Y=X^3$ 的概率密度
>
> 第一步,$
> \text{F}_{\text{Y}}\left( \text{y} \right) =\text{P}\left( \text{Y}\le \text{y} \right) =\text{P}\left( \text{X}^3\le \text{y} \right) =\text{P}\left( \text{X}\le \sqrt[3]{\text{y}} \right) =\text{F}_{\text{x}}\left( \sqrt[3]{\text{y}} \right) 
> $
>
> 第二步,$
> \text{f}_{\text{Y}}\left( \text{y} \right) =\text{f}_{\text{X}}\left( \sqrt[3]{\text{y}} \right) \cdot \left( \sqrt[3]{\text{y}} \right) \text{`}=\frac{1}{3\sqrt[3]{\text{y}^2}}\cdot \text{f}_{\text{x}}\left( \sqrt[3]{\text{y}} \right) 
> $
>
> 第三步，代入

## 第三章 多维随机变量及其分布

### 1.二维随机变量

$$
\begin{aligned}
	S\phantom{=}\text{样本空间}\\
	\boldsymbol{X}\phantom{=}\text{随机变量（向量）}\\
	F\left( x,y \right) \phantom{=}\text{二维随机变量的分布函数}\\
\end{aligned}
$$

$S=\left\{ e \right\} ,\;X=X\left( e \right) ,\;Y=Y\left( e \right) \boldsymbol，{X}=\left( \begin{array}{c}
	X\left( e \right)\\
	Y\left( e \right)\\
\end{array} \right) $

### 2.二维离散型随机变量及其分布

联合分布律

|           X/Y           |  1   |  2   |  3   | $P\left\{X=x_i\right\}$ |
| :---------------------: | :--: | :--: | :--: | :---------------------: |
|            1            | 0.12 | 0.21 | 0.07 |           0.4           |
|            2            | 0.42 | 0.06 | 0.02 |           0.5           |
|            3            | 0.06 | 0.03 | 0.01 |           0.1           |
| $P\left\{Y=y_i\right\}$ | 0.6  | 0.3  | 0.1  |            1            |

P{X=2,Y=1}=0.42

联合分布函数

$
F\left( x,\;y \right) =P\left( \left\{ X\le x \right\} \cap \left\{ Y\le y \right\} \right) \triangleq P\left( X\le x,\;Y\le y \right) ,\;
\\
x\in \left( -\infty ,\;+\infty \right) ,\;y\in \left( -\infty ,\;+\infty \right) 
$

F(2,1)=0.54

X的边缘分布律：

|  X   |  1   |  2   |  3   |
| :--: | :--: | :--: | :--: |
|  P   | 0.4  | 0.5  | 0.1  |

Y的边缘分布律：

|  Y   |  1   |  2   |  3   |
| :--: | :--: | :--: | :--: |
|  P   | 0.6  | 0.3  | 0.1  |

$F_X\left( x \right) =P\left( X\le x \right) =P\left( X\le x,Y\le +\infty \right) =F\left( x,+\infty \right) \\
F_Y\left( y \right) =P\left( Y\le y \right) =P\left( X\le +\infty ,Y\le y \right) =F\left( +\infty ,y \right) $

条件分布：

$P\left( Y=y_i \right)>0
，P\left( X=x_i\mid Y=y_i \right) =\frac{P\left\{ X=x_i,Y=y_i\right\}}{P\left\{Y=y_i\right\}}$

$P\left( X=x_i \right)>0
，P\left( Y=y_i\mid X=x_i \right) =\frac{P\left\{ X=x_i,Y=y_i\right\}}{P\left\{X=x_i\right\}}$

### 3.二维连续型随机变量及其分布

一维：$F\left( x \right) = P\left\{X\le x\right\}=\int_{-\infty}^x{f\left( t \right) \text{d}t}$

二维：$F\left( x,y \right) =P\left( X\le x,\;Y\le y \right)=\int_{-\infty}^x{\int_{-\infty}^y{f\left( u,v \right) \text{d}u\text{d}v}}$

性质：

* $
  f\left( x,y \right) \ge 0
  $
* $\int_{-\infty}^{+\infty}{\int_{-\infty}^{+\infty}{f\left( x,y \right) \text{d}x\text{d}y}}=\text{F}\left( +\infty ,+\infty \right) =1$
* $
  \text{P}\left\{ \left( \text{X,Y} \right) \in \text{G} \right\} =\iint_{\text{G}}{\text{f}\left( \text{x,y} \right)}\text{dxdy}
  $

边缘分布

$
F_X\left( x \right) =P\left( X\le x \right)
	=P\left( X\le x,Y<+\infty \right)\\
	=\int_{-\infty}^x{\int_{-\infty}^{+\infty}{f\left( u,v \right) \text{d}u\text{d}v}}\\
	=\int_{-\infty}^x{\left[ \int_{-\infty}^{+\infty}{f\left( u,v \right) \text{d}v} \right] \text{d}u}\\
	=\int_{-\infty}^x{f_X\left( x \right) \text{d}u}\\
$

其中 $
f_X\left( x \right) =\int_{-\infty}^{+\infty}{f\left( x,y \right) \text{d}y},\;x\in \left( -\infty ,\;+\infty \right) 
$

同理：$
F_{\text{Y}}\left( \text{y} \right) =P\left( \text{Y}\le \text{y} \right) =\int_{-\infty}^{\text{y}}{\left[ \int_{-\infty}^{+\infty}{f\left( \text{x,y} \right) \text{dx}} \right] \text{dy}}=\int_{-\infty}^{\text{y}}{f_{\text{Y}}\left( \text{y} \right) \text{dy}}
$

其中 $
f_Y\left( y \right) =\int_{-\infty}^{+\infty}{f\left( x,y \right) \text{d}x},\;y\in \left( -\infty ,\;+\infty \right) 
$

条件概率密度

$
f_{\text{X}\mid \text{Y}}\left( \text{x}\mid \text{y} \right) =\frac{f\left( x,y \right)}{f_{\text{Y}}\left( \text{y} \right)},\;\text{x}\in \left( -\infty ,\;+\infty \right) 
$

$
f_{Y\mid X}\left( y\mid x \right) =\frac{f\left( x,y \right)}{f_X\left( x \right)},\;y\in \left( -\infty ,\;+\infty \right) 
$

二维常用分布：

| 名称         | 符号                                      | 概率密度                                                     |
| ------------ | ----------------------------------------- | ------------------------------------------------------------ |
| 均匀分布     |                                           | $\text{f}\left( \text{x,y} \right) =\left\{ \begin{array}{l}	\frac{1}{\text{A}},\left( \text{x,y} \right) \in \text{G}\\	0,\text{其它}\\\end{array} \right. $ |
| 二维正态分布 | $N( \mu_1 ,\mu_2,\sigma_1,\sigma_2,\rho)$ | $f\left( x,y \right) =\frac{1}{2\pi \sigma _1\sigma _2\sqrt{1-\rho ^2}}e^{-\frac{1}{2\left( 1-\rho ^2 \right)}\left[ \frac{\left( x-\mu _1 \right) ^2}{\sigma _1^2}-2\rho \frac{\left( x-\mu _1 \right) \left( y-\mu _2 \right) ^2}{\sigma _1\sigma _2}+\frac{\left( x-\mu _2 \right) ^2}{\sigma _2^2} \right]}\\x\in \left( -\infty ,\;+\infty \right) ,\;y\in \left( -\infty ,\;+\infty \right) $ |

### 4.二维随机变量的独立性

$$
\begin{aligned}
	F_X\left( x \right) \phantom{=}\text{边缘分布函数}\\
	F\left( x,y \right) \phantom{=}\text{二维随机变量的分布函数，联合分布函数}\\
\end{aligned}
$$

$
\forall x,y\in \mathbb{R},\;
P\left( X\le x,Y\le y \right) =P\left( X\le x \right) \cdot P\left( Y\le y \right) 
\\
F\left( x,y \right) =F_X\left( x \right) \cdot F_Y\left( y \right) 
$

独立条件

离散型：$P\left( X\le x_i,Y\le y_i \right) =P\left( X\le x_i \right) \cdot P\left( Y\le y_i \right) $

连续型：$f(x,y)=f_X(x)f_Y(y)$

### 5.两个随机变量函数的分布

(1)Z=X+Y的分布

$
\text{f}_{\text{X}+\text{Y}}\left( \text{z} \right) =\int_{-\infty}^{\infty}{\text{f}\left( \text{z}-\text{y,y} \right) \text{dy}}\\\text{f}_{\text{X}+\text{Y}}\left( \text{z} \right) =\int_{-\infty}^{\infty}{\text{f}\left( \text{x,z}-\text{x} \right) \text{dx}}$

独立则

$\text{f}_{\text{X}+\text{Y}}\left( \text{z} \right) =\int_{-\infty}^{\infty}{\text{f}_{\text{X}}\left( \text{z}-\text{y} \right) \text{f}_{\text{Y}}\left( \text{y} \right) \text{dy}}\\\text{f}_{\text{X}+\text{Y}}\left( \text{z} \right) =\int_{-\infty}^{\infty}{\text{f}_{\text{X}}\left( \text{x} \right) \text{f}_{\text{Y}}\left( \text{z}-\text{x} \right) \text{dx}}$

卷积公式：$f_Z\left( z \right) =\int_{-\infty}^{+\infty}{f\left( x,z-x \right)}\text{d}x=\int_{-\infty}^{+\infty}{f\left( z-y,y \right)}\text{d}y,\;z\in \left( -\infty ,\;+\infty \right) $

分布函数：

有限个相互独立的正态随机变量的线性组合仍然服从正态分布 P77

(2)Z=Y/X,Z=XY的分布

$
\text{f}_{\text{Y/X}}\left( \text{z} \right) =\int_{-\infty}^{\infty}{|\text{x|f}\left( \text{x,xz} \right) \text{dx}}
\\\text{f}_{\text{XY}}\left( \text{z} \right) =\int_{-\infty}^{\infty}{\frac{1}{|\text{x|}}\text{f}\left( \text{x,}\frac{\text{z}}{\text{x}} \right) \text{dx}}$

独立则

$
\text{f}_{\text{Y/X}}\left( \text{z} \right) =\int_{-\infty}^{\infty}{|\text{x|f}_{\text{X}}\left( \text{x} \right) \text{f}_{\text{Y}}\left( \text{xz} \right) \text{dx}}\\\text{f}_{\text{XY}}\left( \text{z} \right) =\int_{-\infty}^{\infty}{\frac{1}{|\text{x|}}\text{f}_{\text{X}}\left( \text{x} \right) \text{f}_{\text{Y}}\left( \frac{\text{z}}{\text{x}} \right) \text{dx}}
$

分布函数

(3)M=max{X,Y}及N=min{X,Y}的分布

$F_M(z)=P\left( M\le z \right) =P\left\{ X\le z , Y\le z \right\} $

$F_N(z)=P\left( N\le z \right) =1-P\left\{ X> z , Y> z \right\} $

独立则

$
F_M\left( z \right) =F_X\left( z \right) \cdot F_Y\left( z \right) 
$

$
F_N\left( z \right) 
	=1-\left[ 1-F_X\left( z \right) \right] \cdot \left[ 1-F_Y\left( z \right) \right]\\
$

具有相同分布函数F(x)则

$
F_M\left( z \right) =\left[ F\left( z \right) \right] ^2\\F_N\left( z \right) =1-\left[ 1-F\left( z \right) \right] ^2$

## 第四章 随机变量的数字特征

$$
\begin{aligned}
	E\left( X \right) \phantom{=}\text{随机变量}X\text{的数学期望}\\
	E\left( g\left( X \right) \right) \phantom{=}\text{随机变量}X\text{的函数的数学期望}\\
	C\phantom{=}\text{常数}\\
\end{aligned}
$$

### 1.期望

离散型: $
P\left( X=x_i \right) =p_i,i=1,2,3,...,\\
E\left( X \right) =\sum_{i=1}^{+\infty}{x_ip_i}$

连续型: $
E\left( X \right) =\int_{-\infty}^{+\infty}{xf\left( x \right) \text{d}x}
$

期望的性质：

* $E(C)=C$
* $E(X+C)=E(X)+C$
* $
  E\left( CX \right) =CE\left( X \right) 
  $
* $
  E\left( X+Y \right) =E\left( X \right) +E\left( Y \right) 
  $
* $
  F\left( x,y \right) =F_X\left( x \right) \cdot F_Y\left( y \right) \Rightarrow E\left( XY \right) =E\left( X \right) \cdot E\left( Y \right) 
  $
* 

随机变量函数的期望

离散型：$
P\left( X=x_i \right) =p_i,i=1,2,3,...,\\
Y=g\left( X \right) \\
E\left( Y \right) =E\left( g\left( X \right) \right) =\sum_{i=1}^{+\infty}{g\left( x_i \right) \cdot p_i}
$

连续型：$
Y=g\left( X \right) \\
E\left( Y \right) =E\left( g\left( X \right) \right) =\int_{-\infty}^{+\infty}{g\left( x \right) f\left( x \right) \text{d}x}
$

二维随机变量的期望

离散型:$
P\left( X=x_i,Y=y_i \right) =p_{ij},i,j=1,2,3,...,\\
Z=g\left( X,Y \right) \\
E\left( Z \right) =E\left( g\left( X,Y \right) \right) =\sum_{i=1}^{+\infty}{\sum_{j=1}^{+\infty}{g\left( x_i,y_i \right) p_{ij}}}
$

连续型:$
Z=g\left( X,Y \right) \\
E\left( Z \right) =E\left( g\left( X,Y \right) \right) =\int_{-\infty}^{+\infty}{\int_{-\infty}^{+\infty}{g\left( x,y \right) f\left( x,y \right)}}\text{d}x\text{d}y
$

### 2.方差

$$
\begin{aligned}
	X\phantom{=}\text{随机变量}\\
	E\left( X \right) ,\;\mu \phantom{=}\text{随机变量}X\text{的数学期望}\\
	D\left( X \right) ,\;\sigma ^2\phantom{=}\text{随机变量}X\text{的函数的方差}\\
	\sigma \left( X \right) \phantom{=}\text{随机变量}X\text{的均方差或标准差}\\
	p_k\phantom{=}\text{离散型随机变量的分布律}\\
	f\left( x \right) \phantom{=}\text{连续型随机变量的概率密度}\\
	C\phantom{=}\text{常数}\\
\end{aligned}
$$

方差:$
D\left( X \right) =E\left\{ \left[ X-E\left( X \right) \right] ^2 \right\}\\D\left( X \right) =E\left( X^2 \right) -\left[ E\left( X \right) \right] ^2
$



标准差:$
\sigma \left( X \right) =\sqrt{D\left( X \right)}
$

$
D\left( X \right) =\left\{ \begin{array}{l}
	\sum_{k=1}^{+\infty}{\left[ x_k-E\left( X \right) \right] ^2\cdot p_k,X\text{为离散型随机变量}}\\
	\int_{-\infty}^{+\infty}{\left[ x-E\left( X \right) \right] ^2\cdot f\left( x \right) \text{d}x,X\text{为连续型随机变量}}\\
\end{array} \right. 
$

性质：

* $
  D\left( C \right) =0
  $
* $
  D\left( X+C \right) =D\left( X \right) 
  $
* $
  D\left( CX \right) =C^2D\left( X \right) 
  $
* $
  D\left( X\pm Y \right) =D\left( X \right) +D\left( Y \right) \pm 2E\left\{ \left[ X-E\left( X \right) \right] \cdot \left[ Y-E\left( Y \right) \right] \right\}\\F\left( x,y \right) =F_X\left( x \right) \cdot F_Y\left( y \right) \Rightarrow D\left( X+Y \right) =D\left( X \right) +D\left( Y \right) 
  $
* $
  P\left( X=E\left( X \right) \right) =1\Leftrightarrow D\left( X \right) =0
  $

切比雪夫不等式

$
\forall \varepsilon >0\\
P\left( \left| X-\mu \right|\ge \varepsilon \right) \le \frac{\sigma ^2}{\varepsilon ^2}\\
P\left( \left| X-\mu \right|<\varepsilon \right) \ge 1-\frac{\sigma ^2}{\varepsilon ^2}
$

### 3.常用分布的期望与方差

常用分布的期望与方差

|               分布               |     参数      |                       分布律或概率密度                       |      期望       |                方差                |
| :------------------------------: | :-----------: | :----------------------------------------------------------: | :-------------: | :--------------------------------: |
|      $B\left( 1,p \right) $      |      $p$      |     $P\left( X=1 \right) =p,\;P\left( X=0 \right) =1-p$      |       $p$       |              $p(1-p)$              |
|      $B\left( n,p \right) $      |     $n,p$     |          $P\left( X=k \right) =C_{n}^{k}p^kq^{n-k}$          |      $np$       |             $np(1-p)$              |
|              $G(p)$              |      $p$      |   $P\left( X=k \right) =\left( 1-p \right) ^{k-1}\cdot p$    |  $\frac{1}{p}$  |         $\frac{1-p}{p^2}$          |
| $Por\pi \left( \lambda \right)$  |   $\lambda$   |  $P\left( X=k \right) =\frac{e^{-\lambda}\lambda ^k}{k\;!}$  |    $\lambda$    |             $\lambda$              |
|  $\text{U}\left( a,\;b \right)$  |     $a<b$     | $f\left( x \right) =\begin{cases}	\frac{1}{b-a},&		a\le x\le b\\	0&		\text{otherwise}\\\end{cases}$ | $\frac{a+b}{2}$ | $\frac{\left( b-a \right) ^2}{12}$ |
| $N\left( \mu ,\sigma ^2 \right)$ | $\mu ,\sigma$ | $f\left( x \right) =\frac{1}{\sqrt{2\pi}\sigma}e^{-\frac{\left( x-\mu \right) ^2}{2\sigma ^2}}$ |      $\mu$      |             $\sigma^2$             |
|     $e\left( \theta \right)$     |   $\theta$    | $f\left( x \right) =\left\{ \;\begin{cases}	\frac{1}{\theta}e^{-x/\theta}&		x>0\\	0&		x\le 0\\\end{cases} \right. $ |    $\theta$     |             $\theta^2$             |

### 4.协方差

$$
\begin{aligned}
	X,Y\phantom{=}\text{随机变量}\\
	\text{Cov}\left( X,Y \right) \phantom{=}\text{随机变量}X\text{与}Y\text{的协方差}\\
	\rho _{XY}\phantom{=}\text{随机变量}X\text{与}Y\text{的相关系数或标准协方差}\\
	a,b\phantom{=}\text{常数}\\
\end{aligned}
$$

$
\text{Cov}\left( X,Y \right) =E\left\{ \left[ X-E\left( X \right) \right] \cdot \left[ Y-E\left( Y \right) \right] \right\} 
$

> 注:1.协方差是两变量与其各自期望值的偏差乘积的期望
> 2.协方差的值可正可负也可为零;

计算式：$
\text{Cov}\left( X,Y \right) =E\left( XY \right) -E\left( X \right) \cdot E\left( Y \right) 
$

性质：

* $
  \text{Cov}\left( X,Y \right) =\text{Cov}\left( Y,X \right) 
  $
* $Cov(X,a)=Cov(b,Y)=0$
* $
  \text{Cov}\left( aX,bY \right) =ab\text{Cov}\left( X,Y \right) 
  $
* $
  \text{Cov}\left( X+Y,Z \right) =\text{Cov}\left( X,Z \right) +\text{Cov}\left( Y,Z \right) 
  $
* X,Y独立，$Cov(X,Y)=0$
* $
  D\left( X\pm Y \right) =D\left( X \right) +D\left( Y \right) \pm 2Cov\left( X,Y \right) 
  $

### 5.相关系数

$
\rho _{XY}=\frac{\text{Cov}\left( X,Y \right)}{\sqrt{D\left( X \right) \cdot D\left( Y \right)}}
$

$
\rho _{XY}=\text{Cov}\left[ \frac{X-E\left( X \right)}{\sqrt{D\left( X \right)}},\frac{Y-E\left( Y \right)}{\sqrt{D\left( Y \right)}} \right] 
$

$
\rho _{XY}=\begin{cases}
	1&		\text{正相关}\\
	-1&		\text{负相关}\\
	0&		\text{独立不相关}\\
\end{cases}
$

$
\rho _{XY}\le 1
$

X，Y不相关时，有$
\rho _{XY}=0\Longleftrightarrow Cov\left( X,Y \right) =0\\E(X,Y)=E(X)E(Y)\\D(X\pm Y)=D(X)+D(Y)
$

## 第5章 大数定律及中心极限定理

大数定律

频率依概率收敛于概率

$
\forall \varepsilon \in \mathbb{R}^+,\;\lim_{n\rightarrow \infty}P\left( \left| f_A-p \right|<\varepsilon \right) =1\\f_A\xrightarrow{P}p$

均值依概率收敛于期望

$
\forall \varepsilon \in \mathbb{R}^+,\;\lim_{n\rightarrow \infty}P\left( \left| \bar{X}-\mu \right|<\varepsilon \right) =1\\
\bar{X}\xrightarrow{P}\mu 
$

中心极限定理1

$
\lim_{n\rightarrow +\infty}P\left( \frac{\sum_{i=1}^n{X_i-n\mu}}{\sqrt{n}\sigma}\le x \right) =\int_{-\infty}^x{\frac{1}{\sqrt{2\pi}}e^{-\frac{t^2}{2}}\text{d}t}
$

n充分大时，$
\frac{\sum_{i=1}^n{X_i-n\mu}}{\sqrt{n}\sigma}
$ 近似 $N(0,1)$

$
\sum_{i=1}^n{X_i}
$ 近似 $N(n\mu,n\sigma^2)$

中心极限定理2

$
\text{若有}\eta_n\sim B\left( n,p \right) ,q=1-p\text{，则}\\
\lim_{n\rightarrow +\infty}P\left( \frac{\eta _n-np}{\sqrt{npq}}\le x \right) =\int_{-\infty}^x{\frac{1}{\sqrt{2\pi}}e^{-\frac{t^2}{2}}\text{d}t}=\varPhi(x)
$

n充分大时可用

## 第六章 样本及抽样分布

### 1.基本概念

总体:试验的全部可能的观察值;

个体:每一个可能观察值;

容量:总体中所包含的个体的个数;

简单随机样本:在相同条件下对总体X进行n次重复的、独立的观察,将这n次的观察结果按试验的次序记为$X_1,X_2,…,X_n$,显然$X_1,X_2…,X_n$彼此之间是独立的,并且它们来自于同样的总体,与$X$服从相同的分布,就称随机变量$X_1,X_2,…,X_n$。为来自总体$X$的一个简单随机样本;

样本值:柚样结束后,就得到了n个实数$x_1,x_2,…,x_n$,它们依次是随机变量$X_1,X_2…,X_n$的观察值,称为样本值统计量:设$X_1,X_2…,X_n$。是来自总体X的一个样本,$g(X_1,X_2…,X_n$)是$X_1,X_2…,X_n$的函数,若g中不含未知参数,则称g($X_1,X_2…,X_n$)是一统计量

样本均值：$
\bar{X}=\frac{1}{n}\sum_{i=1}^n{X_i}$

样本方差：$
S^2=\frac{1}{n-1}\sum_{i=1}^n{\left( X_i-X \right) ^2}
$

样本标准差：$
S=\sqrt{\frac{1}{n-1}\sum_{i=1}^n{\left( X_i-X \right) ^2}}
$

样本k阶原点矩：$
A_k=\frac{1}{n}\sum_{i=1}^n{X_{i}^{k}},k=1,2,...
$

样本k阶中心距：$
B_k=\frac{1}{n}\sum_{i=1}^n{\left( X_i-X \right) ^k},k=1,2,...
$

> 注:统计量本身是一个随机变量,当柚样结束了,将柚样结果$x_1,x_2…,x_n$代入这些函数,就可以得到统计量具体的取值了

### 2.抽样分布

$\chi ^2$ 分布

设$X_1,X_2…,X_n$是来自总体N(0,1)的样本那么我们称这n个
随机变量的平方和$\chi ^2=X_{1}^{2}+X_{2}^{2}+...+X_{n}^{2}$是服从自由度为n的$\chi ^2$分
布,记为$\chi ^2$~$\chi ^2(n)$

性质：

* $
  \text{若}\chi _{1}^{2} \chi ^2\left( n_1 \right) ,\chi _{2}^{2}~\chi ^2\left( n_2 \right) ,\text{且}X,Y\text{相互独立，则有}\chi _{1}^{2}+\chi _{2}^{2}~\chi ^2\left( n_1+n_2 \right) 
  $
* $
  \text{若}\chi ^2~\chi ^2\left( n \right) ,\text{则}E\left( \chi ^2 \right) =n,D\left( \chi ^2 \right) =2n
  $

t分布

$
X~N\left( 0,1 \right) ,Y~\chi ^2\left( n \right) ,\text{且}X,Y\text{相互独立，则}t=\frac{X}{\sqrt{Y/n}}\text{为服从自由度为}n\text{的}t\text{分布,记为}t~t\left( n \right) 
$

F分布

$
\text{若}U~\chi ^2\left( n_1 \right) ,V~\chi ^2\left( n_2 \right) ,\text{且}U,V\text{相互独立，则称}\\F=\frac{U/n_1}{V/n_2}\text{服从自由度为}\left( n_1,n_2 \right) \text{的}F\text{分布记为}F~F\left( n_1,n_2 \right) 
$

$
\frac{1}{F}~F\left( n_2,n_1 \right) 
$

正态总体的样本均值和样本方差的分布
设$X_1,X_2…,X_n$,是来自正态总体$N(\mu,\sigma^2)$的样本,$X,S^2$分别
是样本均值和样本方差那么有下面的结论成立:

* 样本均值服从正态分布:$\bar X~N(\mu,\sigma^2/n)$
* 样本方差服从卡方分布:$
  \frac{\left( n-1 \right) S^2}{\sigma ^2}~\chi ^2\left( n-1 \right) 
  $
* $\bar X 与 S^2$相互独立
* $
  \frac{\bar{X}-\mu}{S/\sqrt{n}}~t\left( n-1 \right) 
  $

## 第七章 参数估计

### 1.点估计

假设总体分布中的待估参数为$\theta,X_1,X_2…,X_n$是来自总体的个样本$x_1,x_2,…,x_n$是相应的一个样本值点估计问题就是要构造一个适当的统计量,用$\hat{\theta}\left( X_1,X_2…,X_n \right) $它的观察值
$\hat{\theta}\left( x_1,x_2…,x_n \right) $作为未知参数O的近似值随机变量$\hat{\theta}\left( X_1,X_2…,X_n \right) $叫做$\theta$的估计量
$\hat{\theta}\left( x_1,x_2…,x_n \right) $叫做估计值
常用的点估计方法有两种矩估计和最大似然估计

### 2.矩估计

 做题步骤： 

(1) 写总体k阶矩：$
\mu _k=E\left( X^k \right) 
$ ，显然$\mu _k$含有未知参数$\theta$

(2)写出样本k阶矩：$
A_k=\frac{1}{n}\sum_{i=1}^n{X^k}
$

(3)令总体k阶矩=样本k阶矩，解$\theta$

### 3.最大似然估计

 做题步骤： 

(1)构造最大似然函数：$
L\left( \theta \right) =\left\{ \begin{array}{l}
	\prod_{i=1}^n{p\left\{ x_i;\theta \right\} ,\text{离散}}\\
	\prod_{i=1}^n{f\left\{ x_i;\theta \right\} ,\text{连续}}\\
\end{array} \right. 
$

(2)对$L(\theta)$ 取对数：$
\ln L\left( \theta \right) =\left\{ \begin{array}{l}
	\sum_{i=1}^n{\ln p\left\{ x_i;\theta \right\} ,\text{离散}}\\
	\sum_{i=1}^n{\ln f\left\{ x_i;\theta \right\} ,\text{连续}}\\
\end{array} \right. 
$

(3)令$
\frac{d}{d\theta}\ln L\left( \theta \right) =0
$，解$\theta$

### 4.估计量的评选标准

| 评选标准 |                             定义                             |             说明             |
| :------: | :----------------------------------------------------------: | :--------------------------: |
|  无偏性  | $若E\left( \hat{\theta} \right) =\theta,则称\hat{\theta}为\theta 的无偏估计量$ |  $\theta$的无偏估计量不唯一  |
|  有效性  | $若D\left( \hat{\theta}_1 \right) \le D\left( \hat{\theta}_2 \right) ,则称\hat{\theta}_1\text{比}\hat{\theta}_2更有效$ | 在无偏的条件下才能比较有效性 |
|  相合性  | $若\hat{\theta}\xrightarrow{P}\theta ,则称\hat{\theta}为\theta 的相合估计量$ |                              |

### 5.区间估计

**背书上的表**

## 第八章 假设检验

基本概念
对于假设检验问题,提出关于总体的一个假设,称为原假设,记做$H_0$;与原假设相对立的假设,称为备择假设,记做$H_1$,假设检验中用到的统计量,称为检验统计量检验统计量把样本空间分成
两个区域,使$H_0$被拒绝的样本观察值所组成的区域为拒绝域此时,检验统计量落入拒绝域的概率是给定的小概率$\alpha$,$\alpha$称为显著水平

设θ是总体的位置参数,$\theta_0$是已知常数,关于$\theta_0$的假设检验，

类型有：

|   类型   |         $H_0$         |         $H_1$         |
| :------: | :-------------------: | :-------------------: |
| 双边检验 |  $\theta = \theta_0$  | $\theta \ne \theta_0$ |
|   右边   | $\theta \le \theta_0$ |  $\theta > \theta_0$  |
|   左边   | $\theta \ge \theta_0$ |  $\theta < \theta_0$  |

假设检验中的两类错误

|    类型    |                   含义                    |                         犯错的概率                         |                             说明                             |
| :--------: | :---------------------------------------: | :--------------------------------------------------------: | :----------------------------------------------------------: |
| 第一类错误 | 原假设$H_0$为真,却拒绝$H_0$，即为弃真错误 | $\alpha =P\left\{ \text{拒绝}H_0|H_0\text{为真} \right\}$ | 仅控制犯第一类错误的概率的检验称为显著性检验，称为显著性水平 |
| 第二类错误 | 原假设$H_0$不真,却接受$H_0$，即为取伪错误 | $\beta =P\left\{ \text{接受}H_0|H_0\text{不真} \right\}$  | 当样本容量固定时,$\alpha$和$\beta$ 中任意一个减小,另一个必然增大;如果使a和同时减小只能增大样本容量 |

> 注:显著性水平$\alpha$其实是犯第一类错误的概率的上界即P{拒绝$H_0$|$H_0$为真}≤$\alpha$,通常按“=”成立时确定拒绝域

假设检验的步骤:
(1)据题意写出原假设H0和备择假设H1;
(2)选择检验方法,写出检验统计量及其分布
(3)根椐给定的显著性水平确定柜绝域;
(4)计算检验统计量的值,做出推断.

**背书上的表**

> 注：检验统计量的分布是指在原假设中等号成立时它所服从的分布拒绝域中的$\alpha$为显著性水平