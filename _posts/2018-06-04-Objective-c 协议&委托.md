---
layout:     post
title:      协议&委托
subtitle:   常量符号
date:       2018-6-5
author:     Jin
header-img: img/post-bg-hacker.jpg
catalog: true
tags:
    - Obj-语法
---



## 协议&委托
彻底理解Objective-C:协议(protocol),代理(delegate)
杂食 关注
2016.04.09 17:18* 字数 1256 阅读 734评论 1喜欢 9
许多同学在第一次接触Objective-C里面的代理,协议,代理协议这些概念,很容易被搞晕.
再加上初次接触 Objective-C 类的property等写法看着比较陌生,更加剧了理解难度.

本文的目的就是,让你彻底理解协议,代理,以及他们的使用场景.
我将要用一个大家都熟悉的场景来讲解.

导演可以拍电影,调教演员,也可以进入到后期制作.导演也可以招聘"助理",帮他干后期制作的事情.
我们先写看协议.(protocol)协议=protocol

协议是什么? 协议就是一纸协议,听着好像废话,你可以从许多角度来看协议:
协议是某种约定(或许多约定的组合)

协议是双方要遵守的东西.
协议是许多小项的组合.
协议是双方的约定.
协议有个协议名字

那Objective-C里面呢, 协议就是”功能的集合”===>”方法的集合” ,也就是”能力清单”.
协议就是带名字的能力清单
我们先抛开Objective-C里面那些ViewController, DataSource, View那些概念,看上面说的具体的协议例子:
# 影视行政助理协议(协议的名字) # 

功能列表:

1:能寻找合适的胶片冲洗厂,进行胶片的冲洗(必须).

2:后期音频合成,可以将录制好的音频合成到胶片里面(必须).

3:需找海报制作商(必须).

4:负责片场治安秩序(非必须)


所以,这个协议名字叫
”影视行政助理协议”
这是一纸清单.这个清单有4个项目(功能/方法),其中前3个是必须的.
协议有协议名字,有清单(方法列表,或者说功能列表)
协议就是”协议就是带名字的能力清单”.

下面再说代理(人).(delegate)
上面提到”协议是双方的约定”,否则单单只存在一份协议是没有意义的(但是没有错),我们来看看协议涉及到的双方.
导演(Director):导演很忙,(实际上,那份协议就是导演自己编写的),因为他要把主要精力放到”艺术创作”上,把重要的琐事”代理”出去(这里的代理是动词),或者说把重要的琐事让”代理”去干(这里的代理是名词),为了便于理解,我们用名词这种方式.
我们再看看实际情况下,影视圈的情况:

oldStreet:(老街)男,一个长期混迹影视圈的能人,行政能力很强,快50了,
做事老派,不上网,没有微信,喜欢通过人脉干事,上面那4个活他都能干,尤其负责片场治安那个.
newSchool:(新校)女,刚刚毕业的电影学院学生,20出头,新潮人类,离开微信不能活那种,需要找工作.上面那个协议里面的事,她能干3个,负责片场治安秩序?还是算了吧.

现在,这两人都来应聘,都符合条件(就是说这两人都可以干协议里面规定必须能干的事情),在Objective-C里面,我们说”这两人都实现了这个协议”.
而导演这边呢,以前是孤家寡人,累的要死,现在有了助理了,对吧? ,以前导演可以这么自我介绍(导演的属性):
”XX导演,男,35岁,恐怖片导演,只做恐怖片,不是北京人,未婚”.

但是现在你要这么介绍了:
”XX导演,男,35岁,恐怖片导演,只做恐怖片,不是北京人,未婚,我的影视后期制助理是谁谁谁”.
如果导演太忙了,他可能还需要其他的人帮他干活,比如剧本医生,那就要这么介绍:
”XX导演,男,35岁,恐怖片导演,只做恐怖片,不是北京人,未婚,我的行政助理是谁谁谁,我的剧本医生是谁谁谁”.
这段意思是说,导演可以超过一个代理.我们把情况搞简单,先只给他一个代理(影视后期制作).

导演的影视后期制作是"某某某",这句话的复杂版本是:
某某某可以干"影视行政助理协议"这个协议里面规定的必须干的事情,导演的"导演的影视后期制作代理"被设置成"某某某",<br/>

导演可以安排助理干"影视行政助理协议"里面的任何事情了.
我们可以看到, 是 协议 将本来没有关系的两方(导演,某某某)联系了起来.
下面是filmAssistantProtocol.h 文件,就是协议文件.
以
@protocol 开头,
以@end结尾.
//filmAssistantProtocol.h
@protocol filmAssistantProtocol   //协议名字

@required
/*
1:能寻找合适的胶片冲洗厂,进行胶片的冲洗(必须).
2:后期音频合成,可以将录制好的音频合成到胶片里面(必须).
3:需找海报制作商(必须).
4:负责片场治安秩序(非必须)
*/

+(void) filmDeveloped;  //冲洗照片
+(void) audioProcess;   //音频合成
+(void) posterMake ;   //海报制造

@optional
-(void) siteSecurity; //现成安保

@end
我们可以很清楚的看到,协议(protocol)就是一个协议名字+功能列表(实际就是方法列表)
然后看看导演这里的写法(Director.h)
//
//  Director.h

#import <Foundation/Foundation.h>
#import "filmAssistantProtocol.h"

//#import "剧本医生协议.h"

@interface Director : NSObject

@property (strong, nonatomic) NSString   *directorName;  //定义导演的名字

//

/*定义一个后期制作的代理 backAssistant,这个代理遵守 filmAssistantProtocol 这个
协议,即:这个后期制作的代理 应该能干filmAssistantProtocol 这个协议里面定义的
功能集合

与通常我们见到的 
@property(nonatomic, retain)  id <someProtocol>        delegate; 写法其实是一回事.
|                   |
|                   |
V                   V
@property(nonatomic, retain)  id<filmAssistantProtocol> backAssistant;

*/

@property(nonatomic, retain) id<filmAssistantProtocol> backAssistant;

/*我们目前只有一个代理,如果需要其他代理(比如剧本医生),将会是下面的写法*/

//@property(nonatomic, retain) id<剧本医生协议> 剧本代理人;

-(void) posterMake;  //印刷海报,导演自己也可以印刷海报
-(void) introMyself; // 导演自我介绍的方法.

@end
注意:与导演名字directorName并列的另外一个属性是backAssistant,
backAssistant/后期制做代理
再看看一个newSchool的情况:

//
//  newSchool.h
//  Film
//
//  Created by Alex on 4/9/16.
//  Copyright © 2016 Alex. All rights reserved.
//

#import <Foundation/Foundation.h>
#import "filmAssistantProtocol.h"
@interface newSchool : NSObject<filmAssistantProtocol>  //实现了filmAssistantProtocol这个协议
@property (strong, nonatomic) NSString   *girlname;
//冲洗照片
-(void) filmDeveloped;
//音频合成
-(void) audioProcess;
//海报制造
-(void) posterMake;
@end
我们看到, filmAssistantProtocol 出现了两次,
Director.h ,可以理解成:[导演说,我要有个助理,能干后期制作那些事]
newSchool.h ,可以理解成:[一个毕业新手说,干后期制作那些事,我都能干]

最后的组合


//
//  ViewController.m
//

#import "ViewController.h"
#import "Director.h"
#import "newSchool.h"

@interface ViewController ()

@end

@implementation ViewController

- (void)viewDidLoad {
[super viewDidLoad];

NSLog(@"程序开始了");
Director* oneDirector = [[Director alloc] init]; //初始化一个导演

oneDirector.directorName = @"PeterJ";    // PeterJ ,彼得杰克逊,指环王导演,这样让你们读代码好记.

[oneDirector introMyself];   //导演介绍自己,虽然有"assistant"这个属性,但是还么有指定具体人.

[oneDirector posterMake];   //导演自己也可以posterMake,因为他有这个方法.

newSchool* oneGirl = [[newSchool alloc] init];  //定义一个新派的女学生,因为这个newSchool实现了那个协议,所以她就有那些能力.
oneGirl.girlname = @"小花蝴蝶";

//设置代理,把导演的后期制作代理设置成这个'小花蝴蝶',以后印海报那些事就交给小花蝴蝶干.
/*
我们在代码里面常见的那种写法
XXX.delegate=self;
或  

XXX.delegate=yyy;
与下面其实是一个意思.

*/

oneDirector.backAssistant = oneGirl;    //把这个女孩指定为导演的那些干杂事的代理.

[oneDirector introMyself];          //导演再次描述自己,backAssistant已经有人了.

[oneDirector.backAssistant posterMake]; //导演可以让自己的backAssistant 去弄海报这事了.

}

- (void)didReceiveMemoryWarning {
[super didReceiveMemoryWarning];
// Dispose of any resources that can be recreated.
}

@end


