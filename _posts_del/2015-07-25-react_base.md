---
layout: post
title: "ReactJs 总结"
date: 2015-07-24 21:45
category : tech
---

**简介**

Reactjs是facebook开源的一个前端框架，web方向仅处理View层。更大的野心在多端处理上，实现跨端的虚拟标识框架。相比目前我认识的框架，要简单/轻量的多。

**应用**

个人理解，主要解决同样的代码/结构/动作只写一次，复用性，模块化非常方便。可以父子包含/并列组合。配合JSX，清新干爽，你说像什么就是什么：）

**干货**

* 组件创建，creatCLass
* 静态数据传递/获取， 属性/props
* 动态数据传递/获取/设置， state/setSstate，发生变化后，会自动调用render
* 虚拟节点子项获取，ref/refs.ref
* 其他操作同js
* MC层可以组合backbone/spine等框架使用
