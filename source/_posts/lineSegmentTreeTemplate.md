---
title: 线段树模板
date: 2019-07-18 22:26:23
tags: 
	- 线段树
categories:
	- 技术
author: Tern
authorLink: www.cputern.top
authorAbout: 一个好奇的人
authorDesc: 一个好奇的人
avatar: https://cdn.jsdelivr.net/gh/TernYoung/nicePicture/icon/favicon.png
comments: true
keywords: 线段树
description: 线段树模板
photos: https://cdn.jsdelivr.net/gh/TernYoung/nicePicture/smallPic/pic008.jpg

---

#### 建树

1.先定义全局变量和一个结构体以便每个节点能存东西

```c++
int x;//单点
int v;//单点更改的值
int a,b;//区间
int t;//区间更改的值
struct node
{
    int l;//区间左端点
    int r;//区间右端点
    int w;//区间保存的值
}tree[400001];//开四倍大小
```

2.递归建树

```c++
inline void build(int k,int l,int r)//建树 
{
    tree[k].l=l,tree[k].r=r;
    if(tree[k].l==tree[k].r)                   //递到叶子节点的时候归
    {
        scanf("%d",&tree[k].w);                //输入各叶子节点的值
        return;                                //出递归
    }
    int m=(l+r)/2;                             //准备生成左右子树
    build(k*2,l,m);                            //递归左子树
    build(k*2+1,m+1,r);                        //左子树递归完递归右子树
    tree[k].w=tree[k*2].w+tree[k*2+1].w;       //向上更新各区间值就是pushup(k)
}
```

#### 基本操作

向上更新

```c++
inline void pushup(int k)
{
    tree[k].w=tree[k*2].w+tree[k*2+1].w;    //父亲的值根据其子孙的值确定
}
```

向下更新

```c++
inline void pushdown(int k)
{
    tree[k*2].f+=tree[k].f;                                      //将更改的单位值传递给左儿子
    tree[k*2+1].f+=tree[k].f;                                    //将更改的单位值传递给右儿子
    tree[k*2].w+=tree[k].f*(tree[k*2].r-tree[k*2].l+1);          //更新左儿子保存的值
    tree[k*2+1].w+=tree[k].f*(tree[k*2+1].r-tree[k*2+1].l+1);    //更新右儿子保存的值
    tree[k].f=0;                                                 //向下更新完毕取消标记值
}
```

单点查询

```c++
inline void ask_point(int k)
{
    if(tree[k].l==tree[k].r)                 //当查到叶子节点时
    {    
        ans=tree[k].w;                       //ans为全局变量传递查询的值
        return ;                             //出递归   
    }
    if(tree[k].f) pushdown(k);               //向下更新
    int m=(tree[k].l+tree[k].r)/2;           //取区间中值，准备递归左右子树查询
    if(x<=m) ask_point(k*2);                 //若查询的单点为区间中值或在区间左边则递归左子树
    else ask_point(k*2+1);                   //否则递归右子树
}
```

单点更新

```c++
inline void change_point(int k)
{
    if(tree[k].l==tree[k].r)
    {
        tree[k].w+=v;
        return;
    }
    if(tree[k].f) pushdown(k);
    int m=(tree[k].l+tree[k].r)/2;
    if(x<=m) change_point(k*2);
    else change_point(k*2+1);
    tree[k].w=tree[k*2].w+tree[k*2+1].w;
}
```

区间查询

```c++
inline void ask_interval(int k)
{
    if(tree[k].l>=a&&tree[k].r<=b)                 //区间在a,b之间
    {
        ans+=tree[k].w;
        return;
    }
    if(tree[k].f) pushdown(k);
    int m=(tree[k].l+tree[k].r)/2;
    if(a<=m) ask_interval(k*2);              //若本区间中值等于a或在a右边（说明左边还能递归）
    if(b>m) ask_interval(k*2+1);             //若本区间中值在b左边（说明右边还能递归）    
}
```

区间更新

```c++
inline void change_interval(int k)
{
    if(tree[k].l>=a&&tree[k].r<=b)
    {
        tree[k].w+=(tree[k].r-tree[k].l+1)*t;
        tree[k].f+=t;
        return;
    }
    if(tree[k].f) pushdown(k);
    int m=(tree[k].l+tree[k].r)/2;
    if(a<=m) change_interval(k*2);
    if(b>m) change_interval(k*2+1);
    tree[k].w=tree[k*2].w+tree[k*2+1].w;
}
```

