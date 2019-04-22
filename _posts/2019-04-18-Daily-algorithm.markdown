---
layout:     post
title:      "一日算法"
subtitle:   " \"Daily algorithm\""
date:       2019-04-18 15:40:00
author:     "王琼弟"
catalog: true
tags:
    - 算法
---

## 棋盘覆盖问题

在一个2^k * 2^k （k≥0）个方格组成的棋盘中，恰有一个方格与其他方格不同，称该方格为特殊方格。显然，特殊方格在棋盘中可能出现的位置有4 ^ k种，因而有4^k种不同的棋盘，图4.10(a)所示是k=2时16种棋盘中的一个。棋盘覆盖问题（chess cover problem）要求用图4.10(b)所示的4种不同形状的L型骨牌覆盖给定棋盘上除特殊方格以外的所有方格，且任何2个L型骨牌不得重叠覆盖。

![](https://gss2.bdstatic.com/-fo3dSag_xI4khGkpoWK1HF6hhy/baike/c0%3Dbaike80%2C5%2C5%2C80%2C26/sign=0ef6e2befbf2b211f0238d1cabe90e5d/fd039245d688d43f995a153f7d1ed21b0ff43b0f.jpg)

思路：利用分治法将大问题一步步分解为可以直接解决的小问题,将2的K次方的问题转换为2的K-1次方然后继续简化。

![](https://github.com/MouMangTai/moumangtai.github.io/blob/master/img/chess.jpg?raw=true)

假设如图a所示为4*4的棋盘，特殊方块在第0行第1列，先将棋盘一分为四(如图1），观察到左上部分有特殊方块，则在另外三个部分的交界线处补上方块(如图2)，这时候随着递归棋盘范围缩小到左上部分,继续一分为四，观察到右上角为特殊方块，则将其余部分交界线上的方块补上(如图3)，以此类推，覆盖完剩余棋盘(如图4).

C++代码实现：

```c++
int tile = 0;
int board[8][8];  //棋盘的大小一定要满足2^k*2^k

void ChessBoard(int tr,int tc,int dr,int dc,int size){
    if(size==1) return ;    //边界条件
    int s=size/2;
    int t=++tile;
    //判断左上角部分
    if(dr<tr+s&&dc<tc+s){
        //若特殊方块在左上角部分,则继续缩小范围
        ChessBoard(tr,tc,dr,dc,s);
    }else{
        //若特殊方块不在左上角部分,则用t号骨牌覆盖(左上角的相反方向)右下角的部分
        board[tr+s-1][tc+s-1] = t;
        //继续缩小范围 这时候右下角的部分看作新范围内的特殊方块
        ChessBoard(tr,tc,tr+s-1,tc+s-1,s);
    }

    //剩下的以此类推 右上角
    if(dr<tr+s && dc>=tc+s){
        ChessBoard(tr,tc+s,dr,dc,s);
    }else{
        board[tr+s-1][tc+s] = t;
        ChessBoard(tr,tc+s,tr+s-1,tc+s,s);
    }
    //左下角
    if(dr>= tr+s && dc<tc+s){
        ChessBoard(tr+s,tc,dr,dc,s);
    }else{
        board[tr+s][tc+s-1] = t;
        ChessBoard(tr+s,tc,tr+s,tc+s-1,s);
    }
    //右下角
    if(dr>= tr+s && dc>=tc+s){
        ChessBoard(tr+s,tc+s,dr,dc,s);
    }else{
        board[tr+s][tc+s] = t;
        ChessBoard(tr+s,tc+s,tr+s,tc+s,s);
    }
}
```



