---
layout: post
title: "基于ReactJs的单页应用框架设计"
date: 2015-08-19 12:01
category : tech
---

**基本设计**

基于hash的请求处理->映射返回数据流->逻辑层->更新客户端

**第三方**

* store 本地存储
* router 基于hash的路由系统
* promise 请求回调萌萌哒
* react 显示层组件框架

**代码**

<pre>
simoD = {
	_us = { // api urls
		'get_users' : 'http://xxxx.xxx'
	},

	A : {
		'get_users' : function(){
			ajax.get/post -> this._us['get_users'] -> backfn // Promise.js
		}
	}
}

simoV = {
	'a' : react.createClass(a)
}; // react widget

simoC = {
	'index' : function(d) {}
}

simoR = {
	R : q.js, // 需要回传地址解析 尤其是参数回传，需要写一套路由系统
	conf : {
		'r1' : fn1,
		...
		return this;
	},
	r : function() {
		var R = this.R;
		_.map(this.conf, function(){
			R.reg(x)
		})
	},
	u : function(u){
		this.R.use(u)
	}
}
</pre>
