---
layout: post
title: SRPG开发之⑨·一年之际……
date: 2020-03-09 23:00:56
tags: [独立游戏,传颂之物,Project Ktr,ProjectUta,该写什么标签好呢……？]

---
**前篇：[AVG部分](http://defisym.lofter.com/post/1eaddb63_1c852db7c)**

**SLG部分**

哟，大家好，这个年更系列又回来了。上次写有关它的文章还是[19年5月31日](https://defisym.lofter.com/post/1eaddb63_1c5d6c695)。

从18年底开始，我的精力基本就全放在SLG上了，包括打《风花雪月》这种SLG类游戏在内（笑）。和AVG部分一样，SLG部分我也给起了个名字，White Maple。

![图片](images/_Lofter/emhSNkVpRmJBei9XU1d1SEhMSDZtUGtxZ0xobHFOZnNXaTB2UkpBeGNFaWoyM2hhT1ByVlZnPT0.jpg?=imageView&thumbnail=500x0&quality=96&stripmeta=0&type=jpg%7Cwatermark&type=2)  

工欲善其事，必先利其器。在有了“SLG的本质是连通图上点的关系问题”这样一个指导思想后，过去一直若有若无的笼罩在系统实现上的那层迷雾终于消退掉了，在我面前展露出一个非常清晰的图景。在19年2月的状态系统之后，我陆续比较顺利的实现了许多模块与系统，包括但不限于：

*   按下打开与按住打开
*   简易的光照与阴影
*   击退
*   拖拽镜头
*   危险区域
*   格挡/取消提示
*   攻击取消
*   预计伤害
*   鼠标吸附到网格
*   过载系统
*   战斗中存档
*   高速移动模式
*   可互动地形创建于地形阵亡
*   追击带来伤害补正
*   敌人性格
*   通用区域计算
*   敌人逃跑
*   敌人增援
*   敌人决策
*   提示信息显示
*   支援
*   状态补正
*   通用攻击区域计算
*   单位面板

此外，我还重写了几乎全部系统的逻辑，能够优化的尽量优化，能够敌我通用的全部敌我通用。老规矩，细节的修正和调整就不提了，不然就等于把Changelog复制过来一样。当然，我依然没能够在2019年做完自己觉得2018年就能做完的照着2017年用2016年的点子写的策划案的全部内容。

![](http://imglf4.nosdn.127.net/img/emhSNkVpRmJBei9XU1d1SEhMSDZtQzRPWmYyc3l6WmVNNmMvK0Nrc01pMXpPZXJCc2xZUHF3PT0.jpg?=imageView&thumbnail=500x0&quality=96&stripmeta=0&type=jpg%7Cwatermark&type=2)  

上述系统中大多在实现上没有太多困难，大部分时间还是花在了调试与查缺补漏上。由于系统逐渐复杂且相互影响，常常有某个要素没有考虑到，就会导致出现各种各样稀奇古怪的非预期效果。比如在对象不存在时错误调起了运动方法，引擎自动返回了全部对象列表中的第一项，于是在敌人近战攻击时，整个地图飘走了之类。真正花了我很多时间的，是决策部分。

![](http://imglf6.nosdn.127.net/img/emhSNkVpRmJBei9XU1d1SEhMSDZtQUVKc3RYS1l1em1KL1pNb3VGWFVsT1RYbGQyTXFndzRRPT0.jpg?=imageView&thumbnail=500x0&quality=96&stripmeta=0&type=jpg%7Cwatermark&type=2)  

在旧版本中，敌人AI逻辑十分简单，仅仅是移动→攻击→待机的三步循环。由于本作在设计上是指令拆分的，例如你可以先攻击再移动，（原地攻击后再动，攻击有补正，移动力有衰减），后续实装道具与符卡后整个行动逻辑与补正会变得更加复杂多样。新版的敌人AI不会按照某种顺序调用对应方法，而是会计算所有方法的权值，循环执行权值最高的行动，直到所有操作都不可行，选择结束回合。这种模式下，敌人也可以像玩家控制的单位一样，先砍一刀再跑。

虽然这个新逻辑看起来也并不复杂，但要改造旧有系统并将其实装还是费了我一番脑筋的，思考了数个解决方案都不太合适，最后根据“指导思想”，补充了抵达判据，并将AI中的涉及到的方法改成回调模式，才算是基本实现了想法。当然，这只是开始，距离实际可游玩之间还需要无穷无尽的调参……现在光是攻击位点计算就有着十多项权值，等全要素完成之后权值肯定只多不少，调整一组在各种情况下都比较合适的参数还是比较有难度的，尤其是像我这种脑子不太灵光的……

![](http://imglf5.nosdn.127.net/img/emhSNkVpRmJBei9XU1d1SEhMSDZtQmo4OFVsbmw1eVZ6VlRLNDliUnRhUEd3d2puZjd2Y2JnPT0.png?=imageView&thumbnail=500x0&quality=96&stripmeta=0&type=jpg%7Cwatermark&type=2)  

下一步终于要杀入符卡部分了。在符卡、单位特性与道具完成并实装后，这个SLG框架终于能说是基本搭好了。在那之后将会是无休无止的调试与Bug修正，直到打磨出一个细节上相对没那么粗糙的版本，随后才是关卡设计与无尽的调整……

当然，我得有素材才行，不然就调自己新构思的关卡不调本作的关卡了（笑，破坏团结的话还是少说）

**附录**

*   其实AVG引擎和SLG引擎的名字都是有相互关联的梗的，与流行歌曲有关。
*   AVG引擎名其实还和构思中的另一个故事有关