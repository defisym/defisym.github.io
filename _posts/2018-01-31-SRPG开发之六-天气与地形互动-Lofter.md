---
layout: post
title: SRPG开发之六-天气与地形互动
date: 2018-01-31 00:01:34
tags: [Project Ktr,ProjectUta,该写什么标签好呢……？]

---
嘛，老实说天气已经做完很久了，不过没有几种就是了，写在这里单纯只是记录实现思路

至于像炎热天气这种需要滤镜的东西，额……我打算直接从插件商店里面买一个水下特效插件，反正把水波波动的速度调慢一些，就和热浪没什么差别了么！

最大的问题就是没办法付款（……），没办法，你不能指望国外网站也有支付宝，信用卡什么的，我还没有（…………）

功能是越做越多，战斗的定义文件也是越来越长，幸好能折叠，不然改一个参数我都得想找点什么东西撞死

![图片](images/_Lofter/emhSNkVpRmJBeitmc0Q2UUs5SExVMGV1UzRkQVFqbTFRS0llNzhrUGhYK1JOVU9USVMvTUpnPT0.png?=imageView&thumbnail=500x0&quality=96&stripmeta=0&type=jpg%7Cwatermark&type=2)

反正比最开始手写AVG脚本要强多了，**战斗场景编辑器制作预定**，应该也是所见即所得鼠标点点点指定各种方块坐标的类型

附带一提在搞了个宏之后AVG脚本编辑器无论是效率上还是……不知道用什么词了，总之已经被爆出渣渣来了，唯一的优势应该就是能所见即所得，不过对话框从头到尾就那几种，记也记住了，CG立绘通常是BB半天也不换一个，说的再多点，填充柄一拽那效率真不是复制粘贴一句一句改能比的  

------------

地形互动是早就构想好的内容，目前只实现了冰-水转换的原型

通常情况下是河流，无法移动

![](http://imglf4.nosdn.127.net/img/emhSNkVpRmJBeitmc0Q2UUs5SExVMk5EQlJkU3V2NWlNMnlsaVoxWkFNNmZZdHpRZWNuV0l3PT0.png?=imageView&thumbnail=500x0&quality=96&stripmeta=0&type=jpg%7Cwatermark&type=2)

当然现在这样丑爆了，最后应该会是挖空，河流边沿这些没有互动的地方直接画在地图上，反正原作就是几张底儿画上动态效果然后轮着播  
可以经由冰属性法术来冻结河流制造通路  

![](http://imglf5.nosdn.127.net/img/emhSNkVpRmJBeitmc0Q2UUs5SExVMG9nb3A2MzRJQUlmUXlGWTdEMEs1Y25EM2dsREYxazRnPT0.png?=imageView&thumbnail=500x0&quality=96&stripmeta=0&type=jpg%7Cwatermark&type=2)  
冻结河流之后的移动力计算一开始出了各种稀奇古怪的毛病，乱改一气以后反而实现了想要的效果（……）

![](http://imglf4.nosdn.127.net/img/emhSNkVpRmJBeitmc0Q2UUs5SExVNi93bWlMTUwvZjFCYWZ1TmlzK1FwY2ErQno1WW55RE9nPT0.jpg?=imageView&thumbnail=500x0&quality=96&stripmeta=0&type=jpg%7Cwatermark&type=2)  
反正这一系列的功能实现照着冰水的格式复制粘贴就行了，应该不会在遇到这种问题了……吧？

总之都是不同条件对对象的选择逻辑与先后顺序不同所导致的问题，看来是时候再认真复习一下帮助文档了

当然敌人也是可以使用我们构建的通路的

![](http://imglf3.nosdn.127.net/img/emhSNkVpRmJBeitmc0Q2UUs5SExVM2grVUlCOWVJSGpsOThsclB4eFhqRSt6T1FBWk9pc3F3PT0.png?=imageView&thumbnail=500x0&quality=96&stripmeta=0&type=jpg%7Cwatermark&type=2)  

想让敌人也会结冰？放弃吧我觉得我还做不出那么厉害的AI……

敌人在水上的时候，你可以一个火球过去，要么把冰桥炸了，让他无路可走

![](http://imglf6.nosdn.127.net/img/emhSNkVpRmJBeitmc0Q2UUs5SExVMjBsRVpubWE1N25oQW0reFNUUDA4SUpaZTFVaDVGdHJRPT0.png?=imageView&thumbnail=500x0&quality=96&stripmeta=0&type=jpg%7Cwatermark&type=2)  
你还可以直接把敌人脚下的冰块用一发火球炸掉，直接把人家淹死（**这才是最终目的！**）

![](http://imglf6.nosdn.127.net/img/emhSNkVpRmJBeitmc0Q2UUs5SExVMC9HOXdOeUxPQ1dJZUFkZ3RkaENic2pOUGhtY000OUpRPT0.png?=imageView&thumbnail=500x0&quality=96&stripmeta=0&type=jpg%7Cwatermark&type=2)  
冰块在炎热天气下会逐渐融化，超过一定回合数之后就会在回合开始时崩解

对没错，**淹死他丫的！**

当然如果你忘记注意这一点的话，角色也是会淹死在河流里面的

地形伤害与战斗伤害不同，会直接判定死亡/游戏失败，没有办法复活

你想，被别人揍趴下了你还可以设定成临时退场

掉岩浆里面掉水里面掉下悬崖还能复活再战明显不对劲，**就算角色不在意，岩浆也是要面子的啊！**

其实不同的地形死法是可以判断出来的，那么掉进岩浆之类的东西烧死请一定要来一张竖着大拇指逐渐沉下去的CG（喂！）

同样的思路还有岩浆-黑曜石，只不过相较于自然融化的冰块黑曜石坚持的回合数更短，更容易烧死就是

另外就是碎砖，碎砖可以通过炸弹/重攻击（特定技能）打破，墙壁类的就可以创造出新的路径，地砖类的，例如前面有个敌人站在碎砖上，一个重攻击下去砸破了可以直接让他掉下去摔死。当然重攻击本身也具有击退效果，摔死还好说，不让敌人卡墙才是最大的问题……

除了这些还有其他的互动构想，例如**火系法术点燃草地、****风系法术吹动角色、****土系法术制造路障等等**，当然草地点着了肯定是能挨着烧起来的，至于下雨天就烧不起来了

本来还有雷电用金属构件电路，千里之外电死你丫的之类的构想，然而发现传颂没有雷系法术，只得作罢

对你没看错，明明有雷神，但是没有雷系法术，有其他的法术啊！咱们可以**风力发电水力发电火力发电地热发电光伏发电和暗物质发电……**实在不行还能**用爱发电**啊！

------------  

天气

**雨天**

![](http://imglf5.nosdn.127.net/img/emhSNkVpRmJBeitmc0Q2UUs5SExVMGpXVW9mQVZOMjBEZnU4VEJqSUFtbVhKL3RSUXlmYm5RPT0.png?=imageView&thumbnail=500x0&quality=96&stripmeta=0&type=jpg%7Cwatermark&type=2)  
雨由四部分组成，首先是只在可视区域刷新的前景雨和后景雨，速度不同，个数一多起来就显得雨大了

地面上的水花是在可视区域随机刷的，但是人物身上的水花是真真正正根据碰撞位点不同创建出来的

**雪**

**![](http://imglf4.nosdn.127.net/img/emhSNkVpRmJBeitmc0Q2UUs5SExVd1JwN3YwSXF1OG5ydlA4dUoxWWg3NzVZdlRSQjNvWlNnPT0.png?=imageView&thumbnail=500x0&quality=96&stripmeta=0&type=jpg%7Cwatermark&type=2)  
**雨的复制粘贴

**浓雾**![](http://imglf3.nosdn.127.net/img/emhSNkVpRmJBeitmc0Q2UUs5SExVOXVPeVdJd0IxejlHOTdzL2V6bVQzYjIzUlhnN24rVi9nPT0.png?=imageView&thumbnail=500x0&quality=96&stripmeta=0&type=jpg%7Cwatermark&type=2)  

用PS做了四个超大的分层云彩，叠在一起，朝着不同的方向运动，营造出云雾升腾的效果

然后咱alpha通道设置反了，本来应该剩下白色才对，结果白色全被扣掉了

![](http://imglf3.nosdn.127.net/img/emhSNkVpRmJBeitmc0Q2UUs5SExVOTBzUWFVV1FZa2ZXMmxqckJzaDc3OHRrNzN3M0IzaWRRPT0.png?=imageView&thumbnail=500x0&quality=96&stripmeta=0&type=jpg%7Cwatermark&type=2)

**结果被吐槽是“硝烟”**  
由于分层云彩只有在图片尺寸以128为倍数的时候才能密铺，所以我很傻的搞了四张2560*1536的……  

明明（1280+128）*（768+128）就足够的说……我真傻，真的，我单知道下雪天——CUT

![](http://www.005.tv/uploads/allimg/160713/22-160G3104531152.gif)  

然后，对，没错，你猜的没错，开始卡了……笔记本上的核心显卡已经开始罩不住了……

稍微做了点优化，比如战略层打开的时候云雾不动了啊，只显示一层啊之类的，多少不会掉帧掉到20了

还好家里台式机独显杠杠的，可以随便浪，啥优化也不做稳稳地稳60，yeah~

![](http://img2.imgtn.bdimg.com/it/u=648743407,1255326668&fm=214&gp=0.jpg)