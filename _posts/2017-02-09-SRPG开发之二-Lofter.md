---
layout: post
title: SRPG开发之二
date: 2017-02-09 21:42:54
tags: [该写什么标签好呢……？,ProjectUta]

---
今天是移动范围的计算……

嗯，实现并不是很难，但是问题是优化……

现在虽然看起来没什么问题，但是实际上堆叠了好多判定物体，如果移动范围大的话会很卡……

![图片](./images/_LofteremhSNkVpRmJBejgxK01GYXljQTlNMWhLaytlNS9DR0NNUnFKUjBUOXU1elo1NEtJZFBTSzNnPT0.png?=imageView&thumbnail=500x0&quality=96&stripmeta=0&type=jpg%7Cwatermark&type=2)  

而且指示必须是不透明的否则堆叠在一起透明度就变了摔！

所以说直接写程序代码判断起来宽搜什么的还是蛮简单的，一个if就完事了

但是引擎不行啊，只能够通过创建物体的方式来，但是创建物体的时候没办法获知物体下面有什么

当然用三种不同的判定物体去判断可以解决，，物体A是炮灰，判断完了就 销毁的那一种，不过那就太麻烦了……

不过最大移动力7已经能够走半个屏幕了

日后如果扩大格子大小，这个问题就没那么明显了（冠冕堂皇的偷懒）

然后就是边界的判断，基本上是没问题了吧……

![](http://imglf2.nosdn.127.net/img/emhSNkVpRmJBejgxK01GYXljQTlNOUV3OWI2TmF1NUx4cWVCdU9RUnEvWVlkWHdDUkxsS0t3PT0.png?=imageView&thumbnail=500x0&quality=96&stripmeta=0&type=jpg%7Cwatermark&type=2)  

虽然偶尔会有走的时候路线不经过格子的问题……2333……

嗯，接下来只要添加移动序列之类的就可以了……

![](http://imglf0.nosdn.127.net/img/emhSNkVpRmJBejgxK01GYXljQTlNNG82d1h4UVk3TkZxd0RFNWt1YUkxeGNaNGNPT0R5ejZ3PT0.png?=imageView&thumbnail=500x0&quality=96&stripmeta=0&type=jpg%7Cwatermark&type=2)  

那个才是最恶心的……要一直调啊调啊测试啊测试啊……

不能出任何的问题呀……

另外就是AIAIAIAIAIAI……

别的都做好了AI不行纯粹就是扯淡……

现在的想法就是

先判断攻击范围，主角在攻击范围之内的话，打之，不管了  

不在的话AI判断是循环一下可移动区域（算法和主角的一样不过当然不显示就是了），找到离主角最近的，然后直接走过去……

再判断攻击范围，主角在攻击范围之内的话，打之……

很弱智啊……

哈哈哈哈哈哈……

---
> ### 评论区：
>**defisym：** 不能一开始就偷懒的太过火了啊，况且还是在设计阶段(ಥ_ಥ)  *[2017-02-10 23:20:49]*
>
>**七月七日遊中書：** 把地图简单化不就好了_(:з)∠)_  *[2017-02-10 19:06:16]*
>
>**defisym：** 但是想一想，直接把寻路终点设成主角，然后走行动力大小的步数就行了。
<br />反而缺点就是如果过河的路有两条，主角对岸中间位置左右绕圈，然后由于AI总是会选择最短的路径，于是一开始往左走，后来又选择了往右走，之后无限循环死活不过河……(눈_눈)  *[2017-02-10 18:59:07]*
>
>**七月七日遊中書：** hhhhh画面感满分  *[2017-02-10 16:51:27]*
>
>**defisym：** 现在我的算法太简单，如果场景里面有一条河，需要从场景左边绕过去，而ai开场在对岸中间的话，估计他就待在那里不动了就_(:з)∠)_  *[2017-02-10 16:46:27]*
>
>**七月七日遊中書：** 其实二三代游戏里ai也挺弱智的，最高难度没有智商（。  *[2017-02-10 00:28:02]*
>
>