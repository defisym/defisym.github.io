---
layout: post
title: SRPG开发之一
date: 2017-02-08 21:00:52
tags: [该写什么标签好呢……？,ProjectUta]

---
![图片](./images/_LofteremhSNkVpRmJBei94UTV0MTFoQS9lSnY2bUs4RkN6QnFvS3BOSlM5aVdMRENnNmZPMDJLaW1nPT0.png?=imageView&thumbnail=500x0&quality=96&stripmeta=0&type=jpg%7Cwatermark&type=2)  
![](http://imglf2.nosdn.127.net/img/emhSNkVpRmJBei94UTV0MTFoQS9lRk93WXBseWtmeTJYQkxXWG5nNnBTUHdmM0lsM1lGa093PT0.png?=imageView&thumbnail=500x0&quality=96&stripmeta=0&type=jpg%7Cwatermark&type=2)  
寻路就算是搞定了……

然后就是朝向不知道为啥永远向下XD……

等回头再处理吧……

接下来只要加上移动范围判定基本的走格子移动就搞定了……

大概只是一个深搜吧，嗯，大概……

可是深搜的话就出现附近有阻挡但是移动力强的话，可以绕到敌人后边的问题……

嗯，这个只是设计上的一点点偏差罢了……

究竟采用面前一个敌人那边走不动道还是可以绕过去呢……

没准实现的时候一个bug就变成feature了呢（逃

万一思路错了就惨了XD

至于为啥不是传颂那种斜四十五度……

啊因为那样涉及到坐标变换，以及我懒得去算坐标变换公式…………

而且斜四十五度测试放物件的时候不好对坐标的啊（其实还是懒）

（虽然最后肯定是关卡外文件写好让它自动生成的说……）

另外AI还是大问题啊啊啊啊啊啊……

---
> ### 评论区：
>**defisym：** 真的做起来才发现问题好多……我已经是一条咸鱼了.JPEG  *[2017-02-09 22:02:35]*
>
>**七月七日遊中書：** 向程序猿大佬低头  *[2017-02-09 03:10:35]*
>
>