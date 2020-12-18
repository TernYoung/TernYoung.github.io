---
title: 数据库期末总结
date: 2020-01-07 21:00:36
tags:
	- 数据库
categories:
	- 技术
author: Tern
authorLink: cputern.top
authorAbout: 一个好奇的人
authorDesc: 一个好奇的人
avatar: https://cdn.jsdelivr.net/gh/TernYoung/nicePicture/icon/favicon.png
comments: true
keywords: 数据库
description: 数据库期末总结
photos: https://cdn.jsdelivr.net/gh/TernYoung/nicePicture/smallPic/pic023.jpg
---

## 2019数据库原理考试大纲

### 一、简答题(本题共4小题,每小题5分,共20分)
主要考核第一童到第七章的基本概念

#### 1.

#### 2.

#### 3.

#### 4.



### 二、SQL操作题(每小题3分,共24分)

主要考核学生对于给出的若干关系模式,用SQL语句表达式作答,主要操作包括,增、删、改和创建基本表和视图。

#### 1.创建基本表

```sql
CREATE TABLE Student(
	Sno CHAR(9) PRIMARY KEY, 
    Sname CHAR(20) UNIQUE,
    Ssex CHAR(2),
    Sage SMALLINT,
    Sdept CHAR(20)
);
```

```sql
CREATE TABLE Course(
	Cno CHAR(4) PRIMARY KEY,
    Cname CHAR(40) NOT NULL,
    Cpno CHAR(4),
    Ccredit SMALLINT,
    FOREIGN KEY(Cpno) REFERENCES Course(Cno)
);
```

```sql
CREATE TABLE SC(
	Sno CHAR(9), 
    Cno CHAR(4),
    Grade SMALLINT,
    PRIMARY KEY(Sno,Cno),
    FOREIGN KEY(Sno) REFERENCES Student(Sno),
    FOREIGN KEY(Cno) REFERENCES Course(Cno)
);
```

```sql
CREATE TABLE tablename 
( 
 column datatype [NULL|NOT NULL] [列级完整性约束], 
 column datatype [NULL|NOT NULL] [CONSTRAINTS], 
 表级完整性约束
);
```

#### 2.改

```sql
UPDATE tablename 
SET columname = value, ... 
[WHERE ...];
```

#### 3.删

```sql
DELETE FROM tablename 
[WHERE ...];
```

#### 4.查

```sql
SELECT columnname, ... 
FROM tablename, ... 
[WHERE ...] 
[UNION ...] 
[GROUP BY ...] 
[HAVING ...] 
[ORDER BY ...];
```

#### 5.查

#### 6.查

#### 7.增

```sql
INSERT INTO tablename [(columns, ...)] 
VALUES(values, ...);
```

#### 8.创建视图

```sql
CREATE VIEW viewname AS 
SELECT columns, ... 
FROM tables, ... 
[WHERE ...] 
[GROUP BY ...] 
[HAVING ...];
```



### 三、证明题(每小题10分,共20分)

Armstrong公理系统设关系模式R<U,F>，其中U为属性集，F是U上的一组函数依赖，那么有如下推理规则：
```text
    A1自反律：若Y⊆X⊆U，则X→Y为F所蕴涵；
    A2增广律：若X→Y为F所蕴含，且Z⊆U，则XZ→YZ为F所蕴涵；
    A3传递律：若X→Y，Y→Z为F所蕴含，则X→Z为F所蕴涵。
```
根据上面三条推理规则，又可推出下面三条推理规则：
```text
    合并规则：若X→Y，X→Z，则X→YZ为F所蕴涵；
    伪传递规则：若X→Y，WY→Z，则XW→Z为F所蕴涵；
    分解规则：若X→Y，Z⊆Y，则X→Z为F所蕴涵。
```
引理：$X→A_1A_2…A_k$成立的充分必要条件是$X→A_i$成立$(i=1,2,…,k)$。

#### 1.证明 Armstrong公理规则

**A1自反律**

```text
A1自反律：若Y⊆X⊆U，则X→Y为F所蕴含
证明1
设Y⊆X⊆U。
对R<U,F>的任一关系r中的任意两个元组t,s：
若t[X]=s[X]，由于Y⊆X，则有t[Y]=s[Y]，所以X→Y成立，自反律得证。
```
**A2增广律**

```text
A2增广律：若X→Y为F所蕴含，且Z⊆U，则XZ→YZ为F所蕴含
证明2
设X→Y为F所蕴含，且Z⊆U。
对R<U,F>的任一关系r中的任意两个元组t,s：
若t[XZ]=s[XZ]，由于X⊆XZ，Z⊆XZ，根据自反律，则有t[X]=s[X]和t[Z]=s[Z]；
由于X→Y，于是t[Y]=s[Y]，所以t[YZ]=s[YZ]；所以XZ→YZ为F所蕴涵，增广律得证。
```
**A3传递律**

```text
A3传递律：若X→Y，Y→Z为F所蕴涵，则X→Z为F所蕴涵
证明3
设X→Y及Y→Z为F所蕴涵。
对R<U,F>的任一关系r中的任意两个元组t,s：
若t[X]=s[X]，由于X→Y，有t[Y]=s[Y]；
再由于Y→Z，有t[Z]=s[Z]，所以X→Z为F所蕴含，传递律得证。
```
**合并规则**

```text
合并规则：若X→Y，X→Z，则X→YZ为F所蕴含
证明4
因X→Y ，所以X→XY （增广律 XX→XY即X→XY）
因X→Z ，所以XY→YZ （增广律）
因X→XY，XY→YZ
故X→YZ （传递律）
```
**伪传递规则**

```text
伪传递规则：若X→Y，WY→Z，则XW→Z为F所蕴含
证明5
因X→Y ，所以WX→WY （增广律）
因WY→Z ，所以XW→Z （传递律）
```
**分解规则**

```text
分解规则：若X→Y，Z⊆Y，则X→Z为F所蕴含
证明6
因Z⊆Y 　所以Y→Z （自反律）
因X→Y 所以X→Z （传递律）
```


#### 2.证明在给定函数依赖集中,逻辑蕴涵了给定的函数依赖

```text
例1 根据Armstrong公理的A1，A2，A3证明X→Y，X→Z，有X→YZ。
因为X→Y,  根据A2规则 可知X→XY
因为X→Z,   根据A2规则 可知XY→YZ
又根据A3规则 可以得到  X→YZ
```

```text
例2 根据Armstrong公理的A1，A2，A3证明由X→Y，WY→Z，有XW→Z。
因为X→Y,  根据A2规则 可知 XW→WY
因为WY→Z,  根据A3规则 可以得到 XW→YZ
```

```text
例3 设F={AB→E,AGJ,BE→I,E→G,GI→H}
试证:F|=AB→GH
1.已知AB→E,E→G		 则:AB→G;传递律
2.已知AB→E			 则:AB→BE;(增广律)
3.已知BE→I,又AB→BE		则:AB→I(传递律)
4.由1和3有AB→G,AB→I 	则:AB→GI(合成规则)
5.由4有AB→GI,又GI→H 	则:AB→H(传递律)
6.由1和5有AB→H,AB→G 	则AB→GH (合成规则)
```



### 四、简单应用题(每小题6分,共24分)

本大题共4小题,分别考核学生对于关系数据库理论中的以下综合应用,
求①候选关键字,②最小覆盖,③判定给定模式分解是否满足无损连接性和依赖保持性,④判定给定关系模式符合哪种范式条件,并在此基本上分解到3NF或BCNF

##### 算法6.1 求闭包

#### 1.①候选关键字（候选码）

第一步：求最小函数依赖集

第二步：写出$L,R,N,LR$ 

定理：$L,N$必为任一候选关键字的成员，$R$ 必不是

第三步：若$X$是$L$类和$N$类组成的属性集,且 $X ≠\varnothing $,则计算$X$的闭包$X^{+}_F$，若$X+F = U$ ,则$X $为关系模式$R$ 的唯一的候选码,算法结束. 若$X+F≠U$ ,转第4 步. 若$X = \varnothing $,转第5 步.

第四步：将$X$ 依次与$LR$ 中的属性分别组合, 判断该组合属性是否是候选码; 找出所有的候选码后,算法结束.

第五步：对$LR$ 中的属性及属性组合依次进行判断;找出所有的候选码后,算法结束.



#### 2.②最小覆盖（最小函数依赖）

口诀：先拆右非单，依赖依次删，后拆左非单
套路：
$
R=\left( A,B,C \right) ，F=\left\{ A\rightarrow BC,B\rightarrow C,A\rightarrow B,AB\rightarrow C \right\} 
$

第一步：先拆右非单
即 $A\rightarrow BC\Longrightarrow A\rightarrow B,A\rightarrow C$ ，$F=\left\{ A\rightarrow B,A\rightarrow C,B\rightarrow C,A\rightarrow B\left( \text{重复删除} \right) ,AB\rightarrow C \right\} $

第二步：依赖依次删
即考虑将 $F$ 中各个依赖依次删除,是否还能推出还原,能还原即可删去。

* 考虑到有 $A\rightarrow C$ , $AB\rightarrow C$ 中 $B$ 为多余属性，去掉 $AB\rightarrow C$ 
* 考虑到 $A\rightarrow C$ 可由 $
  A\rightarrow B,B\rightarrow C
  $ 导出，去掉 $A\rightarrow C$ 

$F_{min}=\left\{ A\rightarrow B,B\rightarrow C \right\} $ 

第三步：后拆左非单
由于此时左侧已经全为单元素,故不用执行此步,若左侧还有非单元素,考虑能否将其拆成单元素



#### 3.③判定给定模式分解是否满足无损连接性和依赖保持性

##### 算法6.2判别一个分解是否无损连接

矩阵法

第一步：画矩阵，各属性为列，分解为行，初步填表

第二步：求最小函数依赖

第三步：根据依赖补充表

##### 是否依赖保持

第一步：根据分解拆分依赖

第二步：验证 $F^+=\left( \bigcup_{i=1}^k{F_i} \right) ^+$



#### 4.④判定给定关系模式符合哪种范式条件,并在此基本上分解到3NF或BCNF

##### 3NF分解

##### 算法6.3 转换为3NF的保持函数依赖的分解

口诀：保函依赖分解题，先求最小依赖集。依赖两侧未出现，分成子集放一边，剩余依赖变子集。若要连接成无损，再添候选做子集。

下面通过几道例题讲解口诀： 

 **例1**.已知$R\left( A,B,C,D,E \right) ,F=\left\{ A\rightarrow D,E\rightarrow D,D\rightarrow B,BC\rightarrow D,DC\rightarrow A \right\} $求保持函数依赖的3NF分解，和具有无损连接性及保持函数依赖的3NF分解 

第一步：保函依赖分解题，先求最小依赖集。

 先求出 $R$ 的最小依赖集，可得$
F_{min}=\left\{ A\rightarrow D,E\rightarrow D,D\rightarrow B,BC\rightarrow D,DC\rightarrow A \right\} 
$ 

第二步：依赖两侧未出现，分成子集放一边。

首先可以发现没有不出现在两侧的元素不用单独分出一个子集，“剩余依赖变子集”然后我们将各依赖分别划分为子集得到：$
\left\{ AD \right\} ,\left\{ ED \right\} ,\left\{ DB \right\} ,\left\{ BCD \right\} ,\left\{ DCA \right\} 
$ ，即为所求保持函数依赖的3NF分解

##### 算法6.4 转换为3NF既有无损连接性又保持函数依赖的分解

第三步：若要连接成无损，再添候选做子集。

求候选码。候选码为$\{CE\}$。故所求具有无损连接性及保持函数依赖的3NF分解为$\{AD\},\{ED\},\{DB\},\{BCD\},\{DCA\},\{CE\}$ 

**例2**.关系模式$R$,有$U=\{A,B,C,D,E,G\},F=\{B\rightarrow G,CE\rightarrow B,C\rightarrow A,CE\rightarrow G,B\rightarrow D,C\rightarrow D\}$，将关系模式分解为3NF且保持函数依赖

第一步：保函依赖分解题，先求最小依赖集。

先求出R的最小依赖集，可得 $F_{min}=\{ B\rightarrow G,CE\rightarrow B,C\rightarrow A,B\rightarrow D,C\rightarrow D  \}$

第二步：依赖两侧未出现，分成子集放一边，剩余依赖变子集。

首先可以发现没有不出现在两侧的元素，然后我们将各依赖分别划分为子集得$\{BG\}, \{CEB\}, \{CA\}, \{BD\}, \{CD\}$，即为所求保持函数依赖的3NF分解

第三步：若要连接成无损，再添候选做子集。

找到R的一个候选码为$\{ACE\}$。故所求具有无损连接性及保持函数依赖的3NF分解为$\{BG\}, \{CEB\}, \{CA\}, \{BD\}, \{CD\},\{ACE\}$ 

(注：范式分解并不唯一，正确即可)

##### 算法6.5 转换为BCNF的无损连接分解

法一：

口诀：先求最小依赖集，候码非码成子集，余下左侧全候码。

例.关系模式$R$,有$U=\{A,B,C,D,E,G\},F=\{B\rightarrow G,CE\rightarrow B,C\rightarrow A,CE\rightarrow G,B\rightarrow D,C\rightarrow D\}$，将关系模式分解为3NF且保持函数依赖

第一步：先求最小依赖集。

最小依赖集为$F_{min}=\{B\rightarrow G,CE\rightarrow B,C\rightarrow A,B\rightarrow D,C\rightarrow D\}$。

第二步：候码非码成子集。

由于候选码为$(CE)$因此将$CE\rightarrow B$划分出子集$(BCE)$，而$B\rightarrow G，B\rightarrow D$左侧均不含主属性$(C、E)$中的任何一个故划分出$(BG),(BD)$ 

第三步：此时剩余依赖$F=\{C\rightarrow A,C\rightarrow D\}$剩余元素$\{A,C,D\}$检查发现函数依赖左侧都是候选码即完成BCNF分解，如果不满足则继续分解余下的。 

于是BCNF分解的最后结果为$\{(BG),(BD),(ACD),(BCE)\}$。

法二：

第一步：写出R,极其$F$，任取一项非候选键项写至左子树设为$R_1,F_1$ ,剩余写至右子树为$R_2,F_2$

第二步：同理分解，最后会留候选键，分解为$R_1...R_n$



### 五、设计题(本题12分)

本大题考核学生对于给定的实际数据库系统的综合应用,要求能根据题目给定的

#### 1.语义描述完成如下应用
(1)设计该理系统的E一R图；(2)将该ER图转换为关系横型结构；(3)指出转换结果中每个关系模式的主码和外码(如果有)。

