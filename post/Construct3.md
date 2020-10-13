---
date: 2020-09-15T22:30:49+08:00
description: "Construct3 Gaming"
featured_image: ""
tags: []
title: "Construct3小游戏项目"
markup: mmark
---

# 用Construct3做一个LOL走a练习小游戏

演示视频：[Bilibili](https://www.bilibili.com/video/BV1vD4y1R7Kh/)

## 背景

英雄联盟(League of Legends，简称LOL)，也叫撸啊撸，是当代最热门的Moba类游戏。据不完全统计，至2015年7月为止，超过1亿名玩家每个月至少玩一次《英雄联盟》，而每天都玩的玩家超过2700万，高峰时段有超过750万人同时在线。2015年7月，该公司估计全世界每个月有超过1亿5千万名的活跃玩家。LOL已经成为当今史诗级的一款游戏，深受全球玩家喜爱。每年拳头公司举办的英雄联盟全球总决赛，更是成为了一个重量级的电竞赛事，吸引了大量的英雄联盟爱好者前往线下观赛。在现今，不可否认的是，英雄联盟正逐渐成为像篮球、足球一样家喻户晓、老少皆宜的运动项目

ADC(Attack Damage Carry)，是这个游戏中很重要的一个位置，他们主要造成远程物理伤害，能够提供稳定和较高的每秒伤害，是游戏中破坏防御塔的主力和持续伤害输出的主要来源。而玩家需要熟练掌握ADC这个位置，一个很重要的基本功便是走a

”走A“通俗理解便是：边移动边攻击敌人。在LOL这个游戏中，游戏角色发出一个普通攻击(也叫平a)大致需要经过三个过程：攻击前摇，攻击发生，攻击后摇。攻击前摇便是在角色发出普通攻击之前的抬手动作，攻击后摇是角色在发出普通攻击之后的收手动作。攻击前摇和攻击后摇需要一定的施法时间，而这三个过程被成为普通攻击的一个周期。根据游戏机制，我们可以在攻击后摇的时候进行移动，因此我们可以利用这个时间间隔控制游戏角色进行走位，以拉开与敌人的距离或者躲避敌方角色的技能

伊泽瑞尔（Ezreal）是一个需要在当今版本非常强势的ADC英雄，它需要掌控者协调好平a和技能的衔接，因此我用Construct3做了一个EZ的走a练习小游戏，可以提供给广大ADC玩家用来训练自己的走a技巧

## 游戏玩法

游戏一开始的界面如下：
![](https://tva1.sinaimg.cn/large/007S8ZIlgy1gjhpq12xf6j319s0ty7wi.jpg)

玩家可以通过A+鼠标左键的方式对敌方英雄（劫）进行普通攻击，也可以通过Q键向鼠标方向施放技能，每个劫的血量为5,每个普通攻击可以给予劫1点伤害，每个技能可以给予劫2点伤害。劫的血量降到0以下后会被击杀，系统每3秒会在地图中随机产生一个劫，并劫会持续向着玩家（EZ）的方向靠近。玩家可以通过右击鼠标点击地板进行移动，但是在攻击的时候会停止移动。每击杀一个劫，记分板上会增加分数，看看你能拿到多少分数吧！

## 游戏制作

### 创建工程

首先进入[以下网址](https://editor.construct.net/)：

![](https://tva1.sinaimg.cn/large/007S8ZIlgy1gjhppahj6nj31h00u019c.jpg)

然后点击New Project,会弹出来以下框框：
![](https://tva1.sinaimg.cn/large/007S8ZIlgy1gjhpbv6i5wj30ng0ik400.jpg)

然后我们点击Creat，便可以创建一个工程：
![](https://tva1.sinaimg.cn/large/007S8ZIlgy1gjhpddwnhlj31gt0u0aiq.jpg)

### 创建背景图

我们需要创建一个类似召唤师峡谷中的地图，于是我们可以进入英雄联盟训练模式中截取下路兵线交汇处的地图：
![](https://tva1.sinaimg.cn/large/007S8ZIlgy1gjhpgv41snj30mk0d8h3t.jpg)

然后点击工程界面的空白处，会弹出：
![](https://tva1.sinaimg.cn/large/007S8ZIlgy1gjhphth89kj30y60sgjud.jpg)

我们点击Tiled Background，发现指针变成了十字的模式，点击工程画布的空白处，会弹出：
![](https://tva1.sinaimg.cn/large/007S8ZIlgy1gjhpjf86aej31cp0u0dr3.jpg)

在这里我们可以选择背景的样式，我们选择上面工具栏的第二个按钮来导入我们先前截取得到的背景图，可以得到以下结果：
![](https://tva1.sinaimg.cn/large/007S8ZIlgy1gjhplayk9wj31d50u01kx.jpg)

然后就可以关闭这个窗口啦，因为背景图我们一般是不移动的，我们可以背景，选择把这个背景锁住：
![](https://tva1.sinaimg.cn/large/007S8ZIlgy1gjhpn4wvlij30p00sialr.jpg)

这样子我们的背景就已经创建完毕了

### 创建人物

与创建背景图一样，我们双击画布空白处（因为背景图已经锁定了，双击背景图也是可以的），弹出以下窗口：
![](https://tva1.sinaimg.cn/large/007S8ZIlgy1gjhphth89kj30y60sgjud.jpg)

我们点击Sprite进行创建，同样会弹出一个空白的模版，与创建背景图相同，我们只需要把抠好的图导入变好啦

在这个游戏中需要的物体模型只有四个，分别是：
* EZ
* 劫
* Q技能
* 平a

这些模型的图片都可以召唤师峡谷中通过截屏找到^-^

除了将这些模型进行导入之外，我们还需要设置模型的碰撞体积和重心点，系统会根据前者来判断是否会发生碰撞事件，后者决定该物体的Position

以EZ为例：
![](https://tva1.sinaimg.cn/large/007S8ZIlgy1gjhpysphdrj312k0sidj6.jpg)

我们点击左边工具拦的最后一个，然后会出现一个由多个小正方形连接而成的方框，我们调整这些小正方形的位置，使它们紧贴着EZ的身体，便可以将EZ的碰撞体积缩小到模型本身的身体范围

然后是重心点的位置，我们点击左边工具栏的倒数第二个：
![](https://tva1.sinaimg.cn/large/007S8ZIlgy1gjhq2dxdm4j312i0nk0vd.jpg)

可以看到出现一个小棱形，我们把这个小棱形的位置放到人物的中心中会更加合理

以同样方法可以创建另外3个模型，方法很简单，难的只是找到好看的素材

### 给模型添加动作方式

不同的模型可能会有不同的运动方式，比如EZ的运动方式是点到点的，因为我们是用鼠标右键来控制他的移动；而Q技能的运动方式是直线的，因为我们不应该保证Q一定能命中

以EZ为例，我们点击EZ这个模型，然后在左侧的状态栏里找到Behaviours这一栏，然后在最后有一个Add/edit Behaviours的选项，我们点击它：
![](https://tva1.sinaimg.cn/large/007S8ZIlgy1gjhq8fbu3kj30n20h40ty.jpg)

然后点击Add new behaviour，弹出：
![](https://tva1.sinaimg.cn/large/007S8ZIlgy1gjhq9a1f5jj30y40sktbq.jpg)

滑倒Movement部分中，我们可以看到这里有很多的运动方式可以添加，对于这些运动方式的区别请到官网查询文档，在这里EZ需要的运动方式是Move To方式，我们点击它，发现就会加入到已有的behaviours里面了

当然这里只是添加了一种移动的方式，如何控制它是在后面的事件触发行为中设置

以同样方式可以给另外3个对象也添加对应的移动方式

### 给模型添加事件

添加事件是游戏的一个最重要的部分，它给游戏与玩家的交互设置了对应的事件发生结果

一个游戏的多个事件构成一个实践表，我们看一下一个事件的基本组成结构：
![](https://tva1.sinaimg.cn/large/007S8ZIlgy1gjhqipedjuj31as0cyjus.jpg)

一个完整的事件由一个事件触发条件和一个事件触发结果构成。事件触发条件定义了在什么情况下事件会发生；事件触发结果定义了在满足事件触发条件后会发生些什么

我们现在来添加一个很基础的事件，就是让EZ一直朝向玩家鼠标指向的位置：
![](https://tva1.sinaimg.cn/large/007S8ZIlgy1gjhqlp7pfrj318c034dgf.jpg)

这个事件表明，系统每一拍都会触发这个事件，也就是系统每一拍都会让EZ朝向玩家鼠标指向的位置，这样子就实现了让EZ一直朝向玩家鼠标执行玩家位置的效果

我们来看看如何添加这个事件，首先点击事件表最下面的Add Event，会自动弹出添加触发条件的窗口:
![](https://tva1.sinaimg.cn/large/007S8ZIlgy1gjhqoao7ytj30y40s6dil.jpg)

然后我们选择System，选择Every tick：
![](https://tva1.sinaimg.cn/large/007S8ZIlgy1gjhqp6emtkj30ya0smdjv.jpg)

然后点击后面的Add action:
![](https://tva1.sinaimg.cn/large/007S8ZIlgy1gjhqpy7wlmj319201m0sy.jpg)

然后选择EZ，在弹出来的Action表中选择Set angle totward position:
![](https://tva1.sinaimg.cn/large/007S8ZIlgy1gjhqr3i88bj30y00s4n0j.jpg)

分别在X,Y栏中输入Mouse.X和Mouse.Y:
![](https://tva1.sinaimg.cn/large/007S8ZIlgy1gjhqsgrhxgj30s80gkt9w.jpg)

然后点击Done就可以了

然后可以通过相同的方式来完善这个事件表，就可以作出一个功能完善的走A小游戏了

#### 实现平A

如何实现平A的效果呢？事件表如下：
![](https://tva1.sinaimg.cn/large/007S8ZIlgy1gjhqujxnzij319u0can0h.jpg)

在我们按下键盘A建的时候，我们会将鼠标光标的模式改为十字，然后将Director的一个属性值E_on_click改为True

在这里说一下Director（导演）的用处，我使用这个空对象来存储一些状态值，以便控制一些动作

在这里E_on_click便是判断A键是否被按下，如果按下，那么E_on_click便会变为True，代表现在可以进行平a操作，我们的下一个事件便是检测E_on_click是否为True,并且玩家是否按下鼠标左键以及鼠标的位置是否在劫的身上，如果是，那么我们便产生一个平a并将鼠标光标的样式恢复，并将E_on_click恢复为False

在这里还有一些细节：
* AttackInterval控制攻击间隔
* 在玩家进行平a的时候不能移动

在完成EZ的事件之后，我们还需要完成平a的事件，因为平a是不可躲避的，我们也需要使用Move To的方式控制平a的运动，平a的事件表为：
![](https://tva1.sinaimg.cn/large/007S8ZIlgy1gjhr313pnrj31a809ignl.jpg)
![](https://tva1.sinaimg.cn/large/007S8ZIlgy1gjhr4a35qpj317k036q3o.jpg)

* 当一个平a对象被创建的时候，它会移动到劫的位置
* 当一个平a对象与一个劫对象碰撞的时候，它对这个劫对象造成伤害
* 也会出现平a落空的情况（没a到地方已经死了），那么当它的速度为0时将它摧毁
* 最后一个事件是让一个平a跟踪鼠标指向的那个劫对象，因为劫对象可能有多个，如果不添加这个事件可能你想攻击劫A但攻击了劫B

#### 劫对象的创建和摧毁

一个走a练习游戏，一个劫对象是明显不够的，我们可以让系统每隔一段事件创建一个劫对象：
![](https://tva1.sinaimg.cn/large/007S8ZIlgy1gjhr9boby8j31a40440to.jpg)

而且劫对线产生的位置是随机的，这意味着你需要时刻小心劫的位置，他可能突然刷到你脸上->_<-

我们给劫设置一个生命值，我们点击劫，点击左侧状态栏的的Instance variables：
![](https://tva1.sinaimg.cn/large/007S8ZIlgy1gjhrcc52vwj30jq04qdg5.jpg)

在这里可以给对象添加血量等属性：
![](https://tva1.sinaimg.cn/large/007S8ZIlgy1gjhrcsmvdrj30mw0hgt9w.jpg)

然后回到事件表，我们之前已经设置了一个事件：当一个平a对象与一个劫对象碰撞的时候，它对这个劫对象造成伤害

当然技能也可以：
![](https://tva1.sinaimg.cn/large/007S8ZIlgy1gjhreb9vptj319c03aq3i.jpg)

然后当劫的生命值降到0以下时便会被击杀：
![](https://tva1.sinaimg.cn/large/007S8ZIlgy1gjhrf09qm0j319y03et95.jpg)

到这便完成了劫对象的创建和摧毁啦

#### 攻击间隔和技能CD

技能当然不能随便放啦，两个独立的攻击之间当然也需要攻击间隔

我们可以在Director中设置两个变量：
![](https://tva1.sinaimg.cn/large/007S8ZIlgy1gjhrha32iyj30jm076jrw.jpg)

当我们发出一次平a或者技能的时候，可以将它们设为一个特定的值，然后只有当这些值小于或等于0时，才允许发出下一次攻击：
![](https://tva1.sinaimg.cn/large/007S8ZIlgy1gjhrl68zmgj317m0380tk.jpg)

当它们被设值的时候，我们开启一个系统计数器，每过一秒将它们减1:
![](https://tva1.sinaimg.cn/large/007S8ZIlgy1gjhrma24zqj319405ywg1.jpg)

这样子我们便可以实现攻击间隔和技能CD了

#### 记分板

同样创建一个Text游戏对象：
![](https://tva1.sinaimg.cn/large/007S8ZIlgy1gjhrn46nzxj30y60sadj3.jpg)

然后给这个记分板加上一个Anchor行为，这样它会固定在屏幕的某一个地方：
![](https://tva1.sinaimg.cn/large/007S8ZIlgy1gjhrnzuqj7j30jq0b875b.jpg)

然后给它加一个score属性，初始化为0:
![](https://tva1.sinaimg.cn/large/007S8ZIlgy1gjhrpczy2dj30jm04oq38.jpg)

然后添加事件，理所当然是一个劫被击杀的时候记分板会加1:
![](https://tva1.sinaimg.cn/large/007S8ZIlgy1gjhrox3vr8j319g05qjse.jpg)

那么记分板也完成了

## 总结

用Construct3制作小游戏的关键是如何去管理事件表。制作好的小游戏演示视频已经放到[Bilibili](https://www.bilibili.com/video/BV1vD4y1R7Kh/)了

