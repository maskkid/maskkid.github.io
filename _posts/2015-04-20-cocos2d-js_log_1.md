---
layout: post
title: "Cocos2d-js总结笔记"
date: 2015-04-20 21:38
category : game
---

            前两天做了一个canvas的游戏，引擎使用的collie，小巧好用，兼容移动端事件。
            在当时选择引擎的时候，倾向cocos2d。这几天重新温习了一下，记录下学习笔记。

## 关于cocos2d-js

* 1.1 概述

    ![dd](http://cn.cocos2d-x.org/image/logo.png)[【官网】](http://cn.cocos2d-x.org)Cocos2d-JS是Cocos2d-x的JavaScript版本，融合了Cocos2d-HTML5和Cocos2d-x JavaScript Bindings（JSB）。

* 1.2 概念图

    ![概念图](http://cn.cocos2d-x.org/uploads/20140612172346_76249.png)

* 1.3 概念关键词
    * 导演、场景、层、精灵、事件、时钟
    * director、scene、layer、sprite、event、timer

                概念基本和已知的flash动画概念类似，舞台、场景、剪辑、时间轴、事件等等。

* 1.4 游戏流程-对应技术 简单解析
    
    一个游戏基本包含 初始化场景、游戏场景、游戏结束场景。

    初始化场景包含开始游戏事件、切换场景动作（转场动画）；游戏中包含sprite自身动作处理、sprite运行动作处理、多sprite碰撞处理、帧定时器更新动作处理；游戏结束，类似开始，偏静态。

