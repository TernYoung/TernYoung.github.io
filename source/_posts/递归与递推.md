---
title: 递归与递推
date: 2019-11-19 13:27:23
mathjax: true
tags: 
	- 递归
categories:
	- 递归
cover: static/images/recursion/cover.jpg 
---

# 递归与递推

## 一、递归是什么？

![img](/static/images/recursion/cover.jpg)

### 程序调用自身的编程技巧称为递归（ recursion） 

> 英文的recursion从词源上分析只是"re-  (again)" + "curs- （come, happen）" 也就是重复发生，再次重现的意思。 而对应的中文翻译 ”递归“ 却表达了两个意思："递"＋"归"。 这两个意思，正是递归思想的精华所在。从这层次上来看，中文翻译反而更达意。

### 递归就是有去(递去)有回(归来)

> 没有回来就是无限递归：从前有座山，山里有座庙，庙里有个老和尚和小和尚，老和尚对小和尚说，从前有座山，山里有座庙，庙里有个老和尚和小和尚，老和尚对小和尚说，从前有座山，山里有座庙，庙里有个老和尚和小和尚，老和尚对小和尚说...... 这就是无限递归

![img](/static/images/recursion/b10b80733bd3512d265c69f68f0c6d4c_hd.jpg)

### 那什么是有限递归，即有去（递去）有回（归来）？

> 目前找到的对递归最恰当的比喻，就是查词典。
> 我们使用的词典，本身就是递归，为了解释一个词，需要使用更多的词。
> 当你查一个词，发现这个词的解释中某个词仍然不懂，于是你开始查这第二个词，可惜，第二个词里仍然有不懂的词，于是查第三个词，这样查下去，直到有一个词的解释是你完全能看懂的，那么递归走到了尽头，然后你开始后退，逐个明白之前查过的每一个词，最终，你明白了最开始那个词的意思。

## 二、递归的基本思想

> 递归的基本思想是**把规模大的问题转化为规模小的相似的子问题来解决**。在函数实现时，因为解决大问题的方法和解决小问题的方法往往是同一个方法，所以就产生了函数调用它自身的情况。另外这个解决问题的函数**必须有明显的结束条件**，这样就不会产生无限递归的情况了。 

### 核心思想

>* 把规模大的问题转化为规模小的相似的子问题来解决
>* 必须有明显的结束条件

### 试一试

$f(n)=f(n-1)+f(n-2); f(1)=1,f(2)=1;$

求$f(4)$？

* $f(4)=f(3)+f(2),f(3)=f(2)+f(1)$
* $f(1)=1,f(2)=1,f(3)=f(2)+f(1),f(4)=f(3)+f(2)$

代码：

```c++
//递归版
int Fibonacci(int n){
    if(n == 1 || n == 2)return 1;
    int ans = Fibonacci(n-1)+Fibonacci(n-2);
    return ans;
}
//递推版
int Fibonacci(int n){
    int f[100];
	f[1]=1;f[2]=1;
    for(int i = 3;i<=n;i++){
        f[i]=f[i-1]+f[i-2];
    }
    return f[n];
}
```



![img](/static/images/recursion/1f818b686dc5482cbb8343d8caf65dac_hd.jpg)

### 递归的过程是出入栈的过程

这句话怎么理解？我们以上述代码为例，取 n=4，

 ![img](/static/images/recursion/v2-536f951bc76f4f9107a5bc8e1a9b5008_hd.webp)

**看懂了上面的过程吗？**

> Tips:事实上，每一个递归程序都可以把它改写为非递归版本。我们只需利用栈，通过入栈和出栈两个操作就可以模拟递归的过程。典型代表就是二叉树的非递归遍历。但并不是每个递归程序都是那么容易被改写为非递归的。某些递归程序比较复杂，其入栈和出栈非常繁琐，给编码带来了很大难度，而且易读性极差，所以条件允许的情况下，推荐使用递归。

## 三、不要被递归绕进去

> 在刚接触递归的时候, 看到一个递归实现, 我们总是难免陷入不停的验证之中，比如上面提及的求斐波那契数列，求解`Fibonacci(n)`时，我们总会情不自禁的发问，`Fibonacci(n-1)`可以求出正确的答案么？接着我们就会再用`Fibonacci(n-2)`去验证...不停地往下验证直到`Fibonacci(1)`,这样验证成功之后会发现很神奇，但是要编写的时候却无从下手。

> 对递归这样的不适应，和我们平时习惯的思维方式有关。我们习惯的思维是：已知`Fibonacci(1)`，乘上 1 就等于`Fibonacci(1)`，再乘以 2 就等于`Fibonacci(2)`...直到加到 n。

### 而递归和我们的思维方式不一样。

### 我们要坚信递归计算能得到正确的答案，而不要进入递归去验证。

递归的思维和数学的上一个命题证明方法很相似，如下：

> 如果下面这两点是成立的，我们就知道这个递归对于所有的 n 都是正确的。
>
> 1. 当 n = 1 时，结果正确；
> 2. 假设递归对于 k 是正确的，我们证明对于 k + 1 也是正确的。

没错就是高中学过的数学归纳法，上述的第 1 点称为基本情况，第 2 点称为通用情况。

例如：

> 证明：$ S(n) = 1 + 2 + 3 + …  + n = \frac{n(n + 1)} {2}  $
>
> 第一步：当 n = 1 时，1 = 1，显然成立
>
> 第二步：假设$ n = k $时等式成立,即 $ S(n) =  \frac{n(n + 1)} {2}  $
>
> 当$ n = k+1 $时，
>
> $S(n + 1) =  S(n) + n + 1 = n(n + 1)/2 + n + 1 = (n + 1)(n + 2)/ 2$
>
> 成立

在递归中，我们通常把第 1 点称为终止条件，因为这样更容易理解，其作用就是终止递归，防止递归无限地运行下去。而第二点则是子问题的通用处理方法。

### 下面我们用两个例子来具体感受一下：

#### 例 1 汉诺塔

![img](/static/images/recursion/21233227-fdbdf31ae5fe4ab7915f7b4352075ace.png)

> 第一步确定终止条件：n=1 时，直接把珠子从 A 移到 C.
>
> 第二步确定通用情况：假设有 n 条珠子在 A 上，我们可以调用一条hanoi(n)方法将其移到 C 杠上
>
> ，那么当有 n +1 条珠子在 A 上我们怎么移动 n+1 条珠子到 C 杠上呢？很简单，我们首先用hanoi(n+1)方法将 n 条珠子都移动到 B 上，然后再把第 n+1 个（最后一个）移动到 C 上，再用同样的hanoi(n)方法将在 B 杠上的  n  条珠子移动到 C 上，问题解决。
>

是不是有点感觉了？

#### 例 2 求阶乘

>第一步：确定终止条件 n = 0 时,直接得出 Factorial(0) = 1 。
>
>第二步：要求n的阶乘时，我们假设可以调用一条Factorial(n) 方法得到结果，当要求n+1的阶乘时，Factorial(n+1) = n*Factorial(n) ,问题解决。

是不是有点感觉，又感觉哪里不对劲？

#### 没错！我们不知道那个方法到底是啥，我们需要的是那个方法！

## 四、怎么编写递归算法？

### 先判断能不能用递归

1. 最常用的递归：转化为子问题，递归求解

2. 问题是不是递归定义的
3. 是不是多重循环问题

### 若是第一种情况

> 将原问题分解成规模更小的子问题
>
> 找到终止条件
>
> 提取原子问题处理的相同逻辑，编写子问题的处理方法，递归调用。

[汉诺塔](http://noi.openjudge.cn/ch0202/6261/)

> 解： 
>
> 第一步，转化原问题，找子问题
>
> 1.要将 n 条盘子从 a 移到 c，则先将第 n 条盘子上的 n-1 个盘子借助 c 移到 b 
>
> 2.此时只有第 n 个盘子在 a 杆上，直接将第 n 个盘子从 a 移到 c
>
> 3.将 b 上的 n-1 条盘子用同样的方法借助 a 移到 c
>
> 第二步，找到终止条件
>
> 当只有 1 条盘子的时候可以直接移动。
>
> 第三步，提取原子问题处理的相同逻辑，编写子问题处理方法，递归调用
>
> 相同逻辑：将 x 个盘子借助临时杆从源杆移至目标杆
>
> 确定参数：这里有 x、临时杆、源杆、目标杆四个参数 , 无需返回值
>
> 编写代码

```c++
void hanoi(int x, char source, char temp ,char goal){
    if(x==1){
        cout<<source<<"->"<<x<<"->"<<goal<<endl;
    }
    else{
        hanoi(n-1, source, goal, temp);
        cout<<source<<"->"<<x<<"->"<<goal<<endl;
        hanoi(n-1, temp, source, goal);
    }
}
```

[爬楼梯](http://noi.openjudge.cn/ch0202/3089/)

> 解：
>
> 第一步，转化原问题，找到子问题
>
> 上到第 n 级楼梯，可以从第 n-1 级迈上去，也可以从第 n - 2 级迈上去
>
> 即我们要求原问题f(n),则我们要知到子问题 f(n-1) 和 f(n-2) 
>
> 第二步，找到终止条件
>
> 当 n = 1时，只能从地板迈上来即 f(1)=1
>
> 当 n = 2 时，可以从地板和第一级迈上来即 f(2)=2
>
> 第三步，提取原子问题处理的相同逻辑，编写子问题处理方法，递归调用
>
> 相同逻辑：f(n) = f(n-1) + f(n-2), f(n-1) = f(n-2) + f(n-3)
>
> 确定参数：只有一个参数 n ,即第 n 级楼梯 ，返回值为到第 n 级的走法
>
> 编写代码

```c++
int f(int n ){
    if(n==1)return 1;
    if(n==2)return 2;
    int ans = f(n-1) + f(n-2);
    return ans;
}
```

[2的幂次方表示](http://noi.openjudge.cn/ch0202/8758/)

>解：
>
>第一步，转化原问题，找到子问题
>
>例如 $137=2^7+2^3+2^0$ ，子问题 $7=2^2+2+2^0,3=2+2^0$
>
>第二步，找到终止条件
>
>当幂次方为0或1时终止
>
>第三步，提取原子问题处理的相同逻辑，编写子问题处理方法，递归调用
>
>相同逻辑：将一个数 n 化为 2 的幂次方
>
>确定参数：只有一个参数n, 无返回值
>
>编写代码

```c++
int f[16];//f[0] = 1; for (int i = 1; i < 16; i++) f[i] = f[i-1]*2;

void print(int n) {
    bool first = true;
    int num = n;
    for (int i = 15; i >= 0; i--) {
        if (f[i] <= num) {
            if (!first) cout << "+";
            else first = false;
            
            if (i == 1) cout << "2";
            else if (i == 0) cout << "2(0)";
            else {
                cout << "2(";
                cout<<i;
                cout << ")";
            }
            num -= f[i];
        }
    }
}
```

### 若是第二种情况 : 问题递归定义

这种情况则不需自己找子问题，直接根据定义即可编写。

举例：

[逆波兰表达式](http://noi.openjudge.cn/ch0202/1696/)

> 逆波兰表达式的定义：
>
> 1. 一个数是一个逆波兰表达式，值为该数
> 2. "运算符 逆波兰表达式 逆波兰表达式" 也是一个逆波兰表达式，值为两个逆波兰表达式的值运算的结果
>
> 子问题：求逆波兰表达式
>
> 终止条件：逆波兰表达式为一个数时
>
> 重复逻辑：求逆波兰表达式
>
> 编写代码

```c++
double exp(){
    char s[100];
    cin>>s;
    if(s[0] != '+' && s[0] != '-' && s[0]!='*' && s[0]!='/'){
        return atof(s);
    }
    else if(s[0] == '+'){
        return exp() + exp();
    }
    else if(s[0] == '-'){
        return exp() - exp();
    }
    else if(s[0] == '*'){
        return exp() * exp();
    }
    else if(s[0] == '/'){
        return exp() / exp();
    }
}
```

### 若是第三种情况 ：多重循环

> 这种情况就不是子问题了，而是搜索

[全排列](http://noi.openjudge.cn/ch0202/1750/)

```c++
void p(){
    for(int i = 1;i<=3;i++){
        for(int j = 1;j<=3;j++){
            for(int k = 1; k<=3;k++){
                if(i!=j&&i!=k&&j!=k)
                cout<<i<<j<<k<<endl;
            }
        }
    }
}

char num[1000];
int mark[1000];
void permutation(int d,int n){
	if(d==n+1){
		for(int i = 1;i<=n;i++){
            cout<<num[i];
            if(i!=n)cout<<" ";
            else cout<<endl;
        }
    }
    else{
        for(int i = 1; i<=n;i++){
            if(mark[i] == 0){
                num[d] = '0'+i;
                mark[i] = 1;
                permutation(d+1);
                mark[i] = 0;
            }
        }
    }
}
```

 [八皇后问题](http://noi.openjudge.cn/ch0205/1700/)

[N皇后问题](http://acm.hdu.edu.cn/showproblem.php?pid=2553)

```c++
const int N=20;   //最多放皇后的个数
int q[N];         //各皇后所在的行号
int cont = 0;     //统计解得个数
void print(int n)
{
	int i,j;
	cont++;
	printf("第%d个解：",cont);
	for(i=1;i<=n;i++)
		printf("(%d,%d) ",i,q[i]);
	printf("\n");
	for(i=1;i<=n;i++)        //行
	{                
		for(j=1;j<=n;j++)    //列
		{
			if(q[i]!=j)
				printf("x ");
			else 
				printf("Q "); 
		}
		printf("\n");
	}
}

//检验第i行的k列上是否可以摆放皇后
int can_place(int i,int k)  
{
	int j=1;
	while(j<i)  //j=1~i-1是已经放置了皇后的行
	{
		//第j行的皇后是否在k列或(j,q[j])与(i,k)是否在斜线上
		if(q[j]==k || abs(j-i)==abs(q[j]-k)) 
			return 0;
		j++;
	}
	return 1;
}

void place(int k, int n){
    if(k==n+1){
        print(n);
        return;
    }
    else{
        for(int i = 1;i<=n;i++){
            if(can_place(k,i)){
                q[k] = i;
                place(k+1,n);
            }
        }
    }
}
```



## 五、递推

###　几个例题

#### [hdu2044](http://acm.hdu.edu.cn/showproblem.php?pid=2044)

> f[n] = f[n-1] + f[n-2]

#### [hdu2045](http://acm.hdu.edu.cn/showproblem.php?pid=2045)

> f[n] = f[i-1] + 2*f[i-2]

#### [hdu2046](http://acm.hdu.edu.cn/showproblem.php?pid=2046)

> f[n] = f[n-1] + f[n-2]

####　[hdu2047](http://acm.hdu.edu.cn/showproblem.php?pid=2047)

> f[n] = 2\*f[n-1] + 2\*f[n-2]

#### [hdu2048](http://acm.hdu.edu.cn/showproblem.php?pid=2048)


> f[n]=(n-1)*(f[n-1]+f[n-2])

#### [hdu2049](http://acm.hdu.edu.cn/showproblem.php?pid=2049)

> f[n]=(n-1)*(f[n-1]+f[n-2])

#### [hdu2050](http://acm.hdu.edu.cn/showproblem.php?pid=2050)

> f[n] = 2\*f[n]\*f[n]-f[n]+1