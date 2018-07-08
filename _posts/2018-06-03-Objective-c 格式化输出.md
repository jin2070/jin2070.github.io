---
layout:     post
title:      Objective-c 格式化输出
subtitle:   常量符号
date:       2018-6-3
author:     Jin
header-img: img/post-bg-hacker.jpg
catalog: true
tags:
    - Obj-逻辑运算
---



## 常量对应符号

1,  %@     对象

2,  %d, %i 整数

3, %u     无符整形

%f     浮点/双字

%x, %X 二进制整数

%o     八进制整数

%zu    size_t

%p     指针

%e     浮点/双字 （科学计算）

%g     浮点/双字

%s     C 字符串

%.*s   Pascal字符串

%c     字符

%C     unichar

%lld   64位长整数（long long）

%llu   无符64位长整数

%Lf    64位双字

%e 是实数，用科学计数法计的

格式字符 说明
%a 一个浮点值(仅C99有效)

%A 同上

%c 一个字符

%d 十进制整数

%i 十进制，八进制，十六进制整数
%o 八进制整数

%x 十六进制整数

%X 同上
%c 一个字符
%s 一个字符串，遇空格、制表符或换行符结束。

%f 实数，可以用小数形式或指数形式输入。
%F 同上
%e 同上

%E 同上
%g 同上
%G 同上

%p 一个指针

%u 一个无符号十进制整数
%[] 扫描字符集合

%% %符号

类型                                    NSlog字符

char                                    %c

short                                   %hi, %hx, %ho

unsigned short                      %hu, %hx, %ho

int                                       %i, %x, %o

unsigned                              %u, %x, %o

long                                    %li, %lx, %lo

unsigned long                       %lu, %lx, %lo

long long                             %lli, %llx, %llo

unsigned long long                %llu, %llx, %llo

float                                    %f, %e, %g, %a

double                                 %f, %e, %g, %a

long double                          %Lf, %Le, %Lg

id                                        %p


