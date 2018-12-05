---
layout: post
title: "微信api微框架设计"
date: 2015-08-11 14:52
category : tech
---

最近公司做微信帐号绑定，时间紧没有做完所有接口，仅实现了一个可扩展的类库。按照个人理解，比较合理的weixin.frame设计如下：


<pre>
WeixinApi.class 实现所有原生api
	api_method1
	api_method2
	...
	helper_post
	helper_get

WeixinCache.class 实现缓存机制
	config
	set
	get

WeixinLogic.class
	通用的weixin业务逻辑，比如自动回复，关注回复，解绑回复，模板消息等等
	logic_method1
	logic_method2

Weixin.frame
	weixin web框架，实现简单的功能演示

	$action_pre = "Simo_";
	$action = $_GET['action'];
	function_exist($action_pre.$actioin) {
		$action();
	} or {
		Simo_index();
	}

	Simo_index() {
		echo "index";
	}
</pre>
