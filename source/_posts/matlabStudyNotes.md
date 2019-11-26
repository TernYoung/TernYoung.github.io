---
title: Matlab学习电记
date: 2019-07-29 20:54:36
tags:
	- Matlab
categories:
	- 技术
author: Tern
authorLink: www.cputern.top
authorAbout: 一个好奇的人
authorDesc: 一个好奇的人
avatar: https://cdn.jsdelivr.net/gh/TernYoung/nicePicture/icon/favicon.png
comments: true
keywords: matlab
description: Matlab基础
photos: https://cdn.jsdelivr.net/gh/TernYoung/nicePicture/smallPic/pic012.jpg
---


#### 基本运算与函数

```matlab
>> (1*2+3*4)/2
ans = 7
```

Matlab会将运算结果直接存入一变量ans，并输出显示。

也可以将结果存入一个变量:

```matlab
>> x=(1*2+3*4)/2
x = 7
```

变量命名规则：1.首字符为英文字母 2.字符间无空格 3.最多19个字符

常用的数学运算符号有 +,-,*,/,^,%,等。

Matlab默认将所有变量均存成double的形式

若不想让Matlab每次都显示运算结果，只需在运算式最后加上分号;

```matlab
>> x=(1*2+3*4)/2;
```

若要显示变量的值，直接键入即可

```matlab
>> x
x = 7
```

Matlab常用的基本数学函数：   

`abs(x)`：纯量的绝对值或向量的长度 

`angle(z)`：复 数z的相角(Phase angle) 

`sqrt(x)`：开平方 

`real(z)`：复数z的实部 

`imag(z)`：复数z的虚 部 

`conj(z)`：复数z的共轭复数 

`round(x)`：四舍五入至最近整数 

`fix(x)`：无论正负，舍去小数至最近整数 

`floor(x)`：地板函数，即舍去正小数至最近整数 

`ceil(x)`：天花板函数，即加入正小数至最近整数 

`rat(x)`：将实数x化为分数表示 

`rats(x)`：将实数x化为多项分数展开 

`sign(x)`：符号函数 (Signum function)。   

当x<0时，sign(x)=-1；   

当x=0时，sign(x)=0;   

当x>0时，sign(x)=1。   

Matlab常用的三角函数:

`sin(x)`：正弦函数 

`cos(x)`：馀弦函数 

`tan(x)`：正切函数 

`asin(x)`：反正弦函数 

`acos(x)`：反馀弦函数 

`atan(x)`：反正切函数 

`atan2(x,y)`：四象限的反正切函数 

`sinh(x)`：超越正弦函数 

`cosh(x)`：超越馀弦函数 

`tanh(x)`：超越正切函数 

`asinh(x)`：反超越正弦函数 

`acosh(x)`：反超越馀弦函数 

`atanh(x)`：反超越正切函数   

变量也可以用来存放向量和矩阵，并进行各种运算：

```matlab
>>x = [1 2 3 4];
>>y = 2*x+1
y = 3 5 7 9
```

可以随意更改、增加或删除向量元素：

```matlab
>>y(3) = 11 %更改
y = 3 5 11 9
>>y(6) = 12 %增加
y = 3 5 11 9 0 12
>>y(4) = [] %删除
y = 3 5 11 0 12
```

%为注释符

取元素出来运算：

```matlab
>>2*y(3)
ans = 22
>>2*y(2:4)
ans = 10 22 0
```

若对Matalb函数用法有疑问，可随时使用help查询帮助。

```matlab
>>help
matlab\datafun                 - Data analysis and Fourier transforms.
matlab\datatypes               - Data types and structures.
matlab\elfun                   - Elementary math functions.
matlab\elmat                   - Elementary matrices and matrix manipulation.
matlab\funfun                  - Function functions and ODE solvers.
...
```

将行向量转置后得到列向量：

```matlab
>>y'
ans = 
        3
        5
        11
        0
        12
```

Matlab适用于向量的常用函数： 

`min(x)`: 向量x的元素的最小值 

`max(x)`: 向量x的元素的最大值 

`mean(x)`: 向量x的元素的平均值 

`median(x)`: 向量x的元素的中位数 

`std(x)`: 向量x的元素的标准差 

`diff(x)`: 向量x的相邻元素的差 

`sort(x)`: 对向量x的元素进行排序（Sorting） 

`length(x)`: 向量x的元素个数 

`norm(x)`: 向量x的欧氏（Euclidean）长度 

`sum(x)`: 向量x的元素总和 

`prod(x)`: 向量x的元素总乘积 

`cumsum(x)`: 向量x的累计元素总和 

`cumprod(x)`: 向量x的累计元素总乘积 

`dot(x, y)`: 向量x和y的内 积 

`cross(x, y)`: 向量x和y的外积 （大部份的向量函数也可适用于矩阵，详见下述。）  

若要输入矩阵，则必须在每一列结尾加上分号;

```matlab
>>A = [1 2 3 4;5 6 7 8;9 10 11 12]
A = 
	1 2 3 4
	5 6 7 8
	9 10 11 12
```

同样可对矩阵进行更改，增加，删除等操作：

```matlab
>>A(2,3) = 5
A =
	1 2 3 4
	5 6 5 8
	9 10 11 12
>>B = A(2,1:3) %取出部分矩阵
B =
    5 6 5
```

#### 定义符号变量syms

创建符号表达式$x^2+y^2$ 

```matlab
>> syms x y;
>> f = x^2+y^2;
>> f
f = x^2+y^2
```

创建符号表达式数组

```matlab
>> syms x y;
>> f=[x^2,y^2;x+y,x-y];
>> f
f=
[x^2,y^2]
[x+y,x-y]
```

连续定义20个符号变量$x_1,x_2,x_3...,x_{19},x_{20}$ 

```matlab
>> for i=1;20
		eval(sprintf('syms x%d',i))
   end
>> whos
```

定义单个符号变量，将字符或数字转为符号变量sym

```matlab
>> x1 = sym('x1'),a = sym('sqrt(200)'),v=sym('[100 200]')
```

#### 符号表达式的替换subs

```matlab
>> syms x y z;
>> f = x^2+y^2+z^2;
>> g = subs(f,[x,y],[1,2]) //其它格式g=subs(f,{x,y},{1,2})
g = 1^2+2^2+z^2 = z^2 + 5
```

#### 符号表达式的化简simplify

```matlab
>> syms x y;
>> s1=simplify(cos(x)^2-sin(x)^2)
>> s2=simplify(x^3+3*x^2+3*x+1)
s1=cos(2*x)
s2=(x+1)^3
```

#### 符号计算精度及其数据类型转换

```matlab
vpa(s) 		计算符号表达式s的数值结果
vpa(s,n) 	采用n位有效数字计算精度求s的数值结果
digits 		显示vpa计算结果的有效数字的位数
digits(n) 	设置vpa计算结果的有效数字的位数
double(s) 	将符号表达式s转化为双精度数值
char(s) 	将符号表达式s转化为字符串
```

#### 复合计算函数compose
`compose(f,g)`	返回复合函数f(g(y)),其中f=f(x),g=g(y)
`compose(f,g,z)`	返回复合函数f(g(z)),f=f(x),g=g(y)
`compose(f,g,x,y,z)`	返回复合函数f(g(z)) 将x=g(y)代入f(x)中，最后用指定的变量z代替变量y

```matlab
>> syms x y t;
>> f = 1/(1+x);
>> g = sin(y)^2;
>> h = compose(f,g,x,y,t)
f = 1/(x+1)
g = sin(y)^2
h = 1/(sin(t)^2+1)
```

#### 计算极限函数limit
`limit(f,x,a)`			计算f(x)当x趋于a的极限
`limit(f,x,a,'right')`	计算右极限
`limit(f,x,a,'left')`		计算左极限

求一元函数极限$\underset{x\rightarrow 0}{\lim}\frac{\sin(x)}{x}$ ，并绘图观察函数在x趋于0时函数的变化趋势

```matlab
>>syms x;
>>y = sin(x)/x;
>>s = limit(y,x,0);
>>x = -1:0.02:1;
>>y = sin(x)./x;
>>plot(x,y,'k.');
```

#### 求导计算diff

`diff(s,'v')` 求s对自变量v的1阶导数

`diff(s,'v',n)` 求s对自变量v的n阶导数

注：‘v’可为符号变量

已知$f\left( x,y \right) =x^2y+2xy+y^2$ 求$\frac{\partial f}{\partial x}$ 和$\frac{\partial f}{\partial y}$ 

```matlab
>>syms x y;
>>f = x^2*y+2*x*y+y*y;
>>d1 = diff(f,x,1)
>>d2 = diff(f,y,1)
d1 = 2*y+2*x*y
d2 = x^2+2*x+2*y
```

#### 符号积分函数int

`int(expr,var)` 	以expr表达式中的变量var为积分变量计算不定积分

`int(expr,var,a,b)` 	以expr表达式中的变量var为积分变量计算定积分，积分

求不定积分$\int{x\ln \left( x^2-1 \right) dx}$ 

```matlab
>>syms x a
>>f = int(x*log(x*x-1))
f = (x^2*log(x^2-1))/2-log(x+1)/2-x^2/2-log(x-1)/2
```

泰勒多项式函数taylor

$f\left( x \right) =f\left( x_0 \right) +f^{'}\left( x_0 \right) \left( x-x_0 \right) +\frac{f^{''}\left( x_0 \right)}{\text{2!}}\left( x-x_0 \right) ^2+...+\frac{f^{\left( n \right)}\left( x_0 \right)}{n!}\left( x-x_0 \right) ^n+R_n\left( x \right) $`taylor(f)`	计算f的5阶麦克劳林多项式

`taylor(f,v,Name,Value)`

`taylor(f,v,a)`	计算f在点a展开的麦克考林多项式

`taylor(f,v,a,Name,Value)`	指定属性名称，属性值的调用方法。其中：f为函数的表达式或者符号变量。v为函数自变量，Name为属性名，Value为属性值。

求$e^x$的7阶多项式

```matlab
>>taylor(exp(x),x,0,'order',8)
ans = 
x^7/5040 + x^6/720 + x^5/120 + x^4/24 + x^3/6 + x^2/2 + x + 1
>>taylor(exp(x),x,'expansionpoint',0,'order',8)
ans = 
x^7/5040 + x^6/720 + x^5/120 + x^4/24 + x^3/6 + x^2/2 + x + 1
```

#### 求解方程（组）函数solve

>s = solve(eqn1,eqn2,...,eqnM,var1,var2,...,varN)，输出一个结构体变量，未知数x的解，通过S.x获取
[S1,...,SN]=solve(eqn1,eqn2,...,eqnM,var1,var2,...,varN)，每个参数储存一个未知数解
eqn1,eqn2,...表示方程，用一个包含“==”的等式表示
var1,var2,...表示未知数符号
需先用syms命令定义符号变量

求解方程$x^2+5x+=0$ 

```matlab
>>syms x;
>>s = solve(x^2+5*x+6==0,x)
s=
-2
-3
```

求解含参的方程组$ax+by=10,ax-by=20$ 

```matlab
>>syms x y a b;
>>s=solve(a*x+b*y==10,a*x-b*y==20,x,y)
>>s.x
ans = 
15/a
>>s.y
ans =
-5/b
```

```matlab
>>syms x y a b;
>>[s1,s2]=solve(a*x+b*y==10,a*x-b*y==20,x,y)
>>s1
ans = 
15/a
>>s2
ans =
-5/b
```

#### 求解微分方程函数dsolve

> s=dsolve(eqn1,eqn2,...,eqnD,cond1,cond2,...,condN)	输出一个结构体变量，未知数x的解，通过S.x获取
> [s1,..s2]=dsolve(eqn1,eqn2,...,eqnD,cond1,cond2,...,condN)	每个参数储存一个未知数解
> eqn为包含‘==’的表达式，表示微分方程
> cond为初始条件
> 未知函数，参数应先用syms定义，例：未知函数y(t)  定义：syms y(t)
> 未知函数y的k阶导数用diff(y,k)表示

求解微分方程的特解 $\frac{dy}{dt}=(10-0.02t)t,y(0)=4$ 

```matlab
>>syms y(t)
>>ansy = dsolve(diff(y)==(10-0.02*t)*t,y(0)==4)
ansy = 4 - (t^2*(t - 750))/150
```