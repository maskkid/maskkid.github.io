---
layout: post
title: "docker总结"
date: 2018-11-1 21:38
category : tech
---
## 背景

很看好一些可预见发展强势的业务场景下的微服务架构，从硬件到软件，从技术架构到业务隔离，彻底解耦，并且从软硬两层制定了严格的耦合场景标准。

之前一直用PHP做项目，语言本身可选择性很低，因为需要配合nginx和php-fpm等，基于虚拟化的微服务架构，显得特别复杂和臃肿。有一段时间，想彻底转到golang（主要是早期七牛全go架构和用golang做过一个跨平台的监控系统, 玩的爽到不要不要的）,另外一个选择就是nodejs（这货，从一出来，就不看好，之前一直基于v8解析，另外那时候js的工程化生态非常弱）,但在天津这个国际化大都市的互联网环境里，go的生存空间太小了，也只能当工具。

这几天，正好有时间，抛开语言，重新从架构垂直分层的底层开始准备，大概跟踪了docker最新的一些生态玩法。

---
## 基础

* docker image
* docker container
* commit/push/save
* *DockerFile*
* network 
* link
* volume
* ports
* docker-compose
   - services
   - links
   - networks
   - image
   - build
       - context

---
## 集群

* k8s

---
## 知识逻辑

* 一个docker颗粒度
* 多个docker通信
    - 基于网络
        - 基本四种，直连，桥接，none，container
    - 基于io共享
    - 网络和io继承
* docker基本管理，变更、组合(docker file, compose)
* 分布式docker管理工具**(k8s)

---
## 问题

* 大量docker容器内软件的数据规划没有标准，比如日志、文件、数据等等
* 问题定位、跟踪、调试工具

---


