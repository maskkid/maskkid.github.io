---
layout: post
title: "php框架设计稿"
date: 2015-08-12 21:57
category : tech
---
很简单的框架，适合自己用：）

<pre>
XFrame
	core
		db.class.php
		storage.class.php
		memcache.class.php
	
	helper
		gd.class.php
		form.class.php
		upload.class.php
		http.class.php

	common
		config.frame.php
		config.app.php

	xframe
		Model.class.php
		Controller.class.php 
		View.class.php
		XFrame.class.php run, loader ($controller->action()) 

	XFrame.php autoload, loadconfig, define, global, XFrame.class::run()


index.php
	define('APP_PATH', './simoapp')  
	require XFrame/XFrame.php
</pre>
