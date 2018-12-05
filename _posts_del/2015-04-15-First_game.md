---
layout: post
title: "一个基于canvas的小游戏"
date: 2015-04-15 21:53
category : tech
tag : game
---

朋友公司的一个小游戏，几年前自己做过一套基于坐标的事件框架，等准备碰撞检测的时候，分神去学算法了，后来就是玩cocos2d-js，然后经过这几年，跟很多技术一样，又荒废了，只剩下一个解决问题的方向。

这个用了2个晚上，2个中午做的，选引擎选了很久，cocos2d太重，后来看上了韩国人写的collie，自己用，不错。碰撞、事件和概念类的layer、object。

这版完成版本，有些细节没做，包括按钮的动画、文字特效、loading美化，分数算法也有些小问题，可能跟setInterval、事件并发延迟有关。

[***Demo地址***](http://onrd.net/game)