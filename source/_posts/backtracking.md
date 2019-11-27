---
title: 回溯法
date: 2019-11-27 11:27:23
tags: 
	- 算法
	- 回溯法
categories:
	- 技术
author: Tern
authorLink: www.cputern.top
authorAbout: 一个好奇的人
authorDesc: 一个好奇的人
avatar: https://cdn.jsdelivr.net/gh/TernYoung/nicePicture/icon/favicon.png
comments: true
keywords: 回溯法
description: 回溯法学习
photos: https://cdn.jsdelivr.net/gh/TernYoung/nicePicture/smallPic/pic101.jpg
---



## 一、什么是回溯法？

>  回溯法是一种选优搜索法，按选优条件向前搜索，以达到目标。但当探索到某一步时，发现原先选择并不优或达不到目标，就退回一步重新选择，这种走不通就退回再走的技术为回溯法，而满足回溯条件的某个状态的点称为“回溯点”。  

 许多复杂的，规模较大的问题都可以使用回溯法，有“通用解题方法”的美称。 

## 二、原理

> 在包含问题的所有解的解空间树中，按照**深度优先搜索的策略**，从根结点出发深度探索解空间树。当探索到某一结点时，要先判断该结点是否包含问题的解，如果包含，就从该结点出发继续探索下去，如果该结点不包含问题的解，则逐层向其祖先结点回溯。（其实回溯法就是对隐式图的深度优先搜索算法）。若用回溯法求问题的所有解时，要回溯到根，且根结点的所有可行的子树都要已被搜索遍才结束。而若使用回溯法求任一个解时，只要搜索到问题的一个解就可以结束。

## 三、如何使用回溯法

1. 确定问题的解空间，问题的解空间中应包含解。
2. 确定节点的扩展搜索规则。
3. 以深度优先方式搜索解空间，并在搜索过程中用剪枝函数避免无效搜索。 

算法模版：

```c++
int a[n];
try(int i){
    if(i>n){输出结果}
    else{
        for(int j = 下界; j<= 上界;j++){
            if(ok(j)){
                a[i]=j;
                ...
                try(i+1);
                返回前处理工作
            }
        }
    }
}
```

## 四、例题

* [N皇后](http://acm.hdu.edu.cn/showproblem.php?pid=2553)
* [Prime Ring Problem](http://acm.hdu.edu.cn/showproblem.php?pid=1016)
* [Sudoku](http://acm.hdu.edu.cn/showproblem.php?pid=5547)

