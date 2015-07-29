---
layout: post
title: "ThinkPHP 源码分析"
date: 2015-07-30 21:45
category : tech
---

			ThinkPHP 3 源码简析说明:主要对Tk框架进行分析，简单适配个人定制化需求。

* 目录结构[官方文档部分内容和文件结构和3.*版有偏差]
    - 框架基本结构

			├─ThinkPHP.php     框架入口文件
			 ├─Common 框架公共文件
			 ├─Conf 框架配置文件
			 ├─Extend 框架扩展目录
			 ├─Lang 核心语言包目录
			 ├─Lib 核心类库目录
			 │  ├─Behavior 核心行为类库
			 │  ├─Core 核心基类库
			 │  ├─Driver 内置驱动
			 │  │  ├─Cache 内置缓存驱动
			 │  │  ├─Db 内置数据库驱动
			 │  │  ├─TagLib 内置标签驱动
			 │  │  └─Template 内置模板引擎驱动
			 │  └─Template 内置模板引擎
			 └─Tpl 系统模板目录


    - 应用的基本结构

			├─index.php     项目入口文件
			 ├─Common 项目公共文件目录
			 ├─Conf 项目配置目录
			 ├─Lang 项目语言目录
			 ├─Lib 项目类库目录
			 │  ├─Action Action类库目录
			 │  ├─Behavior 行为类库目录
			 │  ├─Model 模型类库目录
			 │  └─Widget Widget类库目录
			 ├─Runtime 项目运行时目录
			 │  ├─Cache 模板缓存目录
			 │  ├─Data 数据缓存目录
			 │  ├─Logs 日志文件目录
			 │  └─Temp 临时缓存目录
			 └─Tpl 项目模板目录


* 主流程
    - index.php - 入口文件
        + ThinkPHP.php [Think::start()] - 主类，define主要变量
            * ThinkPHP.class.php [App::run()] - 核心类库，注册autoload/错误处理/加载系统和应用配置文件
                - App.class.php [ run -> init[Dispatch::dispatch 解析url] + exec ] - 应用主类，解析MVC，解析过滤参数，反射调用对应的action

* 主要文件说明[待续]
	* functions.php
	* Model.class.php
	* Controller.class.php
	* Action.class.php
	* Cache

* 定制化
	* 修改模板调用方式。view层只原生php代码。添加自定义模板方法,模仿目前公司框架的形式。 functions.php添加 simotpl(),simoview()两个方法











