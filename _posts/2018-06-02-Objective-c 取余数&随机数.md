---
layout:     post
title:      Objective-c 整数余数 & 随机数
subtitle:   逻辑运算符
date:       2018-6-2
author:     Jin
header-img: img/post-bg-hacker.jpg
catalog: true
tags:
    - Obj-逻辑运算
---



## 取整数

  a=3  b=10
  b%(3)=1
  a/b=3

## 随机数

  1、  获取一个随机整数范围在：[0,100)包括0，不包括100
  
  int x = arc4random() % 100;
  
  2、  获取一个随机数范围在：[500,1000），包括500，包括1000
  
  int y = (arc4random() % 501) + 500;
  
  3、  获取一个随机整数，范围在[from,to），包括from，包括to
  
  -(int)getRandomNumber:(int)from to:(int)to
  
  {
  
  return (int)(from + (arc4random() % (to – from + 1)));
  
  }
  




