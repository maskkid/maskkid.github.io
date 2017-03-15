---
layout: post
title: "docker 使用记录"
date: 2017-03-15 11:15
category : tech
---
            

## Docker 个人基本理解

* 镜像 静态的资源文件，用于容器中动态加载
* 容器 动态的文件，用于承载镜像。类似操作系统之于应用软件
* pull commit 之类，将镜像通过类似git的方式管理起来，方便分发和版本管理
* 能做什么？一致化的模块功能，方便的组合，跨平台部署

## Docker commands

* docker pull // 获取镜像， 可以先通过git search 查找
* docker images // 获取所有镜像
* docker run -v hostpath:vmpath -v hostpath2:vmpath2 --privileged -p 80:8080 --name renameTest centos:latest -it /sbin/init
 - -v和volume配置有不同。主要是文件夹的共享范围。宿主和容器、容器和容器之间是否可以同步修改。[参考此文](https://segmentfault.com/q/1010000004107293)
 - -it 
 - --privileged 部分命令需要宿主root权限
 - -p 和宿主端口映射
 - --name 起个小名

* docker commit // 可以将容器打包成镜像
* docker ps -a // 所有容器
* dockerfile配置详解，[参考该网址](http://www.cnblogs.com/jackluo/p/5388189.html) 
