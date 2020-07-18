---
layout: post
title: Project Ktr:AVG System Demo (Update1021/Build0830)
date: 2018-08-30 22:54:05
tags: [Project Ktr,ProjectUta,传颂之物]

---
![图片](./images/_LofteremhSNkVpRmJBejk0dFhqSzlOZVE2TlJPR3RVNjlKZWlrRnhxWXlOUUxyZGRJT2xDekVzdE5RPT0.png?=imageView&thumbnail=500x0&quality=96&stripmeta=0&type=jpg%7Cwatermark&type=2)  

**Changelogs：**

<span style="text-decoration:underline;">20181021-问题修正-无新版本构建  
</span>

+修正了快进会导致立绘不透明度未被正常保存的bug

+修正了在Bgm音量过小时，跳转指令不会等待遮罩创建的bug

+修正了在某些情况下跳转指令不会正常运行的bug

+修正了跳转指令在对白未显示完全时错误响应的bug

<span style="text-decoration:underline;">20181019-问题修正-无新版本构建  
</span>

修正了在使用其它页面后，返回AVG界面，文本中使用patternfadeout指令，会导致叠化完成后前景图丢失的bug

·其实是没有在叠化完成功能里筛选ID，而导致前景图在叠化完成后获取了错误的图片名，进而被错误的更新

<span style="text-decoration:underline;">20181005-问题修正-无新版本构建</span>  

修正了在跳转回Splash画面时，不会正常完成标题画面加载的bug

·所以那个用于测试的选项我好像是看着能跳转回标题就强退了，从来没等他加载完过

·在跳转时会更新为下一文本块的ID，在返回标题这种特殊条件下会将文本块ID更新为0，然后标题画面loading时会首先做第一个文本块的跳转表，找不到0对应的文本块就懵逼了

·这就和2016年7月发现的存档后返回标题再开新游戏不会正确的从游戏开头开始一样，之前用过的全局变量的参数出了问题

<span style="text-decoration:underline;">20180922-功能更新-无新版本构建</span>  

+换行

现在你可以在文本中使用/n来换行了

![](http://imglf6.nosdn.127.net/img/emhSNkVpRmJBejkxK0R6dFJkVW5oYU1MQmVyRWpUUlRJM0RjVHQwaWhrc1hKeXp3c1FlZ3NnPT0.png?=imageView&thumbnail=500x0&quality=96&stripmeta=0&type=jpg%7Cwatermark&type=2)  

同时兼容存档读档与历史记录![](http://imglf4.nosdn.127.net/img/emhSNkVpRmJBejkxK0R6dFJkVW5oUTlDVmlicUxTellscTQ3WXdlcXovN2NQbDdxRmcwdkFBPT0.png?=imageView&thumbnail=500x0&quality=96&stripmeta=0&type=jpg%7Cwatermark&type=2)（功能只做一半儿不兼容那我可以去死了）  

<span style="text-decoration:underline;">20180914-功能更新-无新版本构建  
</span>

+Pattern Fade优化

现已支援透明对象

![](http://imglf3.nosdn.127.net/img/emhSNkVpRmJBejk0SDBLejFsQ1YvV3dPN29aMi9CbGtnZ0NRblF0RTliUmNvZlBXN0h6ZXZnPT0.png?=imageView&thumbnail=500x0&quality=96&stripmeta=0&type=jpg%7Cwatermark&type=2)  
![](http://imglf4.nosdn.127.net/img/emhSNkVpRmJBejk0SDBLejFsQ1YvUlZRTnFpeUdrTU9sbEU3d0ZpTWRrUldGMDQrWTQ3ZWxnPT0.png?=imageView&thumbnail=500x0&quality=96&stripmeta=0&type=jpg%7Cwatermark&type=2)  
**实际效果：**

不同角色：

![](http://imglf5.nosdn.127.net/img/emhSNkVpRmJBejk0SDBLejFsQ1YvWGVoTzFWWk5qOTVacW0rajk0cDBrK3k3c0FjdDBMdHVRPT0.png?=imageView&thumbnail=500x0&quality=96&stripmeta=0&type=jpg%7Cwatermark&type=2)  
差分：

![](http://imglf5.nosdn.127.net/img/emhSNkVpRmJBejk0SDBLejFsQ1YvYkVvVUgvVnVkTEdyc3FTc1UvYnZrUUh6eVdjdi9KM2N3PT0.png?=imageView&thumbnail=500x0&quality=96&stripmeta=0&type=jpg%7Cwatermark&type=2)  
需要注意的是Pattern并不适用于差分

<span style="text-decoration:line-through;">（而且做立绘切换本来就不太合适，很鬼畜啊喂）</span>

叠化是通过新旧两层遮罩来进行的，如果只叠化前景，几乎看不出来Pattern的作用，如果同时叠化又略鬼畜，两者权衡之下还是留下了鬼畜的版本，用以兼容替换角色的情形（嗯嗯）

昨晚实在是智障了……妄图调一个没初始化的变量作为分支条件肯定会出问题，果然做东西就是一个和Bug斗争的过程，当你觉得做的差不多了的时候，就是出现新坑的时候……

![](http://imglf3.nosdn.127.net/img/emhSNkVpRmJBejk0SDBLejFsQ1YvV0VpUnovU2YvRVd1bjl3VjRDWWxpMFA5QThoUTNuTXVRPT0.jpg?=imageView&thumbnail=500x0&quality=96&stripmeta=0&type=jpg%7Cwatermark&type=2)  
（我是那个小精灵，不是猫眼林克）

<span style="text-decoration:underline;">20180908~20180913-功能更新-无新版本构建</span>  

+Pattern Fade优化

现在存在较为平滑的循环过渡了，不再是最初版本的立即跳变

+Pattern Fade更新

现在允许将Pattern Fade作为贴图来进行图像间的叠化

![](http://imglf3.nosdn.127.net/img/emhSNkVpRmJBejk0SDBLejFsQ1YvY0lGaFJYZGRYYk1iUFFBTWVxdDJIZ2FFckZRSmNGenlBPT0.png?=imageView&thumbnail=500x0&quality=96&stripmeta=0&type=jpg%7Cwatermark&type=2)  

+Pattern Fade更新实装

现在允许你对CG使用Pattern Fade

由于会导致透明对象花屏，故未对立绘对象开放

<span style="text-decoration:underline;">20180908-功能更新-无新版本构建  
</span>

+Performance演出正式回归

通过指定演出字符串，跳转至指定场景，完成特定定义的演出

仅提供旧版本的相关功能，不主要进行维护和更新

+Pattern Fade 实装

使用pattern fade读取picname图像进行叠化，于状态2下进行，但仍旧建议结合#wait指令使用

<span style="text-decoration:underline;">20180906-功能更新-无新版本构建  
</span>

+Pattern Fade 研究

简单的shader编写，根据阈值来筛选像素

<span style="text-decoration:underline;">20180905-功能更新-无新版本构建  
</span>

+现在允许你设定旋转的圈数了

好吧是我试着做了一个“我是梅西慌得一批”的缺德演出，然后发现忘记给旋转做出口了……

<span style="text-decoration:underline;">20180904-功能更新-无新版本构建  
</span>

+现在在使用缩放指令时，允许在缩放途中对其他图像对象进行操作

缩放现已提供强制等待模式，开启后允许缩放在任何状态下执行，翻页等待执行完成，响应强制等待指令，可通过结合等待指令在缩放一段时间后切换图像，再完成强制等待后进入新的文本解析循环

示例：

> @cgchange=春.png
> 
> @backzoom=640:360:640:360:1:0:1
> 
> #wait:1000
> 
> @cgchange=夏.png
> 
> #forcewait:1000

Gif：

![](http://imglf3.nosdn.127.net/img/emhSNkVpRmJBei9YN0JGV2haSDdiSzlCT25YRHFqS1lqSlM5OUhsSjNoSHhQT2VTK1R0cElnPT0.gif?=imageView&thumbnail=500x0&quality=96&stripmeta=0&type=jpg%7Cwatermark&type=2)  

<span style="text-decoration:underline;">20180901-常规维护-无新版本构建</span>  

+修正了在切换差分时，新素材被拉伸的情况下，出现坐标偏移的bug  

怀疑和字符串一样是内部实现的问题，总之是想办法回避了  

+修正了在过渡过程中强制关闭程序，中断存档保存了错误的立绘的bug

演出过程中是不允许开菜单，也无法保存存档，只能说强行关闭存中断方便是方便，就是净给自己找事儿……

+可能修正了立绘没有被正确销毁的bug

之前偶然发生过该类问题，没复现过，追加了一个标志位作保险

<span style="text-decoration:underline;">20180831-常规维护-无新版本构建</span>

+修正了连续使用相应过渡指令，天气未被正确切换的bug

傻乎乎的用了同一个标志位，比如先用了下雨再用过渡天晴，如果等待时间不够，过渡下雨并未执行完成且恢复标志位，此时开始执行过渡天晴，一个创建一个销毁，都以同样的标志位为入口条件，但一个出口是粒子创建至指定数量，一个是粒子完全销毁，两者，用白话说，开始扯皮……就是看谁扯得过谁，当然通常是先执行的比较厉害，先达成出口条件，清空标志位，于是后者的条件也不满足，就导致了过渡指令失效的bug 

+修正了在演出过程中依旧显示翻页提示的bug 

在对白显示结束后，会出现相应对话框颜色的翻页提示，在开始下一句对白演出时，对话框和对白默认是不会消失的，导致其显示条件永远满足 

难怪我在测试需要配合等待的演出的时候一直怀疑卡掉了…… 

**Demo说明：**

*   除UI、标题画面和对话历史界面头像外，全部的美术素材均来自《传颂之物》

*   标题Bgm来自塞尔达传说：风之杖，其余来自网络共享素材

*   本Demo仅供演示，不包含任何剧情内容，不代表最终效果，请勿用于商业用途

*   Windows 8以上版本请关闭DPI缩放以获得更好的显示效果  

*   需要Direct X 9 运行库

**功能说明：**  

*   鉴赏页面仅供展示，并不附带实际功能，No data项为随机生成，页面切换按钮仅“一”有效，点击将生成新的No data项，来模拟页面切换效果

*   在CG鉴赏页，用鼠标悬浮在选项上背景图像会叠化更新，该功能最后会实装至全部鉴赏页面

*   设置页面中，对不同角色设置语音音量的功能并未实装，相应选项部分为空

**已知问题：**

*   在标题画面，将鼠标放置在选项预定出现的位置，出现悬浮效果后立即点击，该次点击无效

*   拖拽进度条中，拖拽按钮悬浮特效可随鼠标短暂离开拖拽范围

*   带有描边效果的字符串对象，会有一定几率随机消失

**当前版本仅供测试，如发现bug请通过评论、私信或邮箱 defisym@outlook.com 反馈****<span style="text-decoration:line-through;">（</span>****<span style="text-decoration:line-through;">不会有人看的）</span>****，****能够稳定复现的恶性bug会最优先****定位**并******修复**  

**本版本中附带半成品战旗系统，并包含未更新UI的分支页面，文本编辑规则请参考[前文](http://defisym.lofter.com/post/1eaddb63_ee7bd251)**

链接：[点我](https://pan.baidu.com/s/1I7bwOUwdTrgfdcYIamfe5Q)

密码：b03n