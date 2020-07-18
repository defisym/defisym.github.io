---
layout: post
title: SRPG开发之三
date: 2017-02-10 18:52:51
tags: [该写什么标签好呢……？,ProjectUta]

---
·修复了停止之后朝向不正确的BUG

·（现在你往哪儿看都可以了）

![图片](./images/_LofteremhSNkVpRmJBei9NUXVEWFZhZVZCMXdNbTY2bnBNM3FtZXlCL1N5V0pGK091S0Z3UlExd2RRPT0.png?=imageView&thumbnail=500x0&quality=96&stripmeta=0&type=jpg%7Cwatermark&type=2)  

·优化了算法，现在不会出现堆叠判定点的问题了，最高可以寻路20层

·图里面移动范围指示是半透明的而没有出现透明度不正确的现象<span style="text-decoration:line-through;">，yeah！</span>

·（这张地图还记得么？当时大白都走到快终点了艾露露还没过一半儿XD）

·从这个角落来看基本上没啥大问题了，但是因为坐标偏移等等因素，在测试的时候曾经卡死在角落出不来，但是修改了地图尺寸以后就没事了，神奇。

·估计是角色当时默认站位直接卡进了障碍区里，所以系统判定你出不去XD

·我很庆幸一开始是用了一张平坦地图（周围有点树木）来测试的，不然我会疯掉的：P

**·找到BUG原因了。说来可笑，是因为我抠图不细致导致障碍边缘比较大，然后判定点也比较大，所以导致比较窄的路口出不去XD**

**·之前这里就是因为判定点叠上了背景所以判定这里不能通行，但是一开始创建的引导点指示这里可以通行，这就是卡死的原因XD**

**![](http://imglf1.nosdn.127.net/img/emhSNkVpRmJBei9NUXVEWFZhZVZCMndOT3Z6VnV2czBLTkhpSlp2N1JhODF0U0x4SmUvN3B3PT0.jpg?=imageView&thumbnail=500x0&quality=96&stripmeta=0&type=jpg%7Cwatermark&type=2)  
****<span style="text-decoration:line-through;">·判定点什么的果然还是一个像素越小越好（大雾）</span>**

![](http://imglf2.nosdn.127.net/img/emhSNkVpRmJBei9NUXVEWFZhZVZCM0FPd2FxMWNCeEt0QzI2U3FRb0NZNTJ4d1BHWnZBaHJ3PT0.png?=imageView&thumbnail=500x0&quality=96&stripmeta=0&type=jpg%7Cwatermark&type=2)  

·（其实由于优化并不是极致十二层以上就开始卡了，现在的算法是在刷新出来之后循环一遍把堆叠的销毁掉）

·（而且由于引擎限制二十层以上需要的判定点个数已经超出了一帧之内允许循环的最大次数，所以再做下去就只能换数组实时动态了）

·（换数组实时动态==重写<span style="text-decoration:line-through;">==之前的全白搞了==懒的搞==懒蛋一个</span>）

·地图边缘判定正常

![](http://imglf0.nosdn.127.net/img/emhSNkVpRmJBei9NUXVEWFZhZVZCd3o5M09RUko4TVB2WjU2cFJyYkJ0Zlg1ZGdQTS9xWVNnPT0.png?=imageView&thumbnail=500x0&quality=96&stripmeta=0&type=jpg%7Cwatermark&type=2)  
·这个投机取巧了，地图大小刚好是格子大小的整倍数。

·不是整倍数也可以啊，地图边缘全不可通行绕一圈儿出来就好了XD（←同样的投机取巧）

·最后就是判定方格会叠掉背景上面去的问题……

·其实也不是问题，最后隐藏掉就行了XD，显示出来只是为了debug

·像这样子：

![](http://imglf2.nosdn.127.net/img/emhSNkVpRmJBei9NUXVEWFZhZVZCMWsxaDkvWGFQSmo3d1p6blpkMW95UnJidnY1Y2Z2akNRPT0.png?=imageView&thumbnail=500x0&quality=96&stripmeta=0&type=jpg%7Cwatermark&type=2)  
·抵达终点！（大雾）

![](http://imglf1.nosdn.127.net/img/emhSNkVpRmJBei9NUXVEWFZhZVZCOWpkbzhCajVHLzU2c3hYdFBuSHoydWtmMWw0WHU5L2J3PT0.png?=imageView&thumbnail=500x0&quality=96&stripmeta=0&type=jpg%7Cwatermark&type=2)  
·暂时系统开发要告一段落了，我得滚回去码字了XD

---
> ### 评论区：
>**defisym：** 就是不从格子里面走XD
<br />而且走的乱七八糟，总之自带鬼畜那一种……  *[2017-02-13 23:57:21]*
>
>**七月七日遊中書：** 哈哈哈哈哈哈有点想看效果（。）  *[2017-02-12 22:01:06]*
>
>**defisym：** 我放弃斜四十五度了……
<br />因为寻路还是非斜四十五度的
<br />所以结果角色移动会很鬼畜XD  *[2017-02-12 16:43:43]*
>
>**七月七日遊中書：** 吃瓜群众默默围观  *[2017-02-11 12:46:01]*
>
>**defisym：** 等等你这里启发我了，突然有个思路，只要将格子变成斜四十五度的，然后相应的坐标变换一下，再把寻路的部分网格变细，（目前寻路网格和移动网格是一一对应的，只要寻路网格足够小就能够避免变为斜四十五度以后寻路网格和移动网格不对应的问题），点击以后记录被点击的方格的坐标，移动结束是按照寻路网格来的，走过去以后坐标的差不会很大，行动结束以后直接把角色坐标移动对过去就行了。  *[2017-02-11 10:54:34]*
>
>**七月七日遊中書：** 看起来有点搞笑2333333  *[2017-02-10 19:47:18]*
>
>**defisym：** 我没有素材啊(ಥ_ಥ) 而且斜四十五需要坐标变换，好麻烦啊（懒）  *[2017-02-10 19:28:51]*
>
>**七月七日遊中書：** 所以地图是倾斜的但人物移动是垂直的？XD  *[2017-02-10 19:16:03]*
>
>