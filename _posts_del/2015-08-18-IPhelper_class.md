---
layout: post
title: "IPhelper简类"
date: 2015-08-18 14:00
category : tech
---

基础助手类，设计包含配置加载/ip数字互转/ip归属地查询/访问者ip获取/ip的段归属验证。


			<?php 

			class IPhelper {

			    private static $banlist = array();

			    private static $banedlist = array();

			    static function loadConfig($banlist=array()) {
				self::$banlist = $banlist;
			    }

			    static function ip2num($ip) {
				if(strpos($ip,'.')===false) return 0;
				return bindec( decbin( ip2long($ip)));
			    }

			    static function getip() {
				if (getenv('HTTP_CLIENT_IP')) {
				    $ip = getenv('HTTP_CLIENT_IP');
				} elseif (getenv('HTTP_X_FORWARDED_FOR')) {
				    $ip = getenv('HTTP_X_FORWARDED_FOR');
				} elseif (getenv('HTTP_X_FORWARDED')) {
				    $ip = getenv('HTTP_X_FORWARDED');
				} elseif (getenv('HTTP_FORWARDED_FOR')) {
				    $ip = getenv('HTTP_FORWARDED_FOR');

				} elseif (getenv('HTTP_FORWARDED')) {
				    $ip = getenv('HTTP_FORWARDED');
				} else {
				    $ip = $_SERVER['REMOTE_ADDR'];
				}
				return $ip;
			    }
			    static function isBannedByiP($ip) {
				if(empty(self::$banlist)) return false;
				foreach(self::$banlist as $item) {
				    $_item = explode('.',$item);
				    $_sip = $_eip = null;
				    if(count($_item)==3) { // xx.xx.xx
					$_sip = self::ip2num($item.'.0');
					$_eip = self::ip2num($item.'.255');
				    }
				    if(strpos($item,'-')) { // xx.xx.xx.xx-yy.yy.yy.yy
					$_item = explode('-', $item);
					$_sip = self::ip2num($_item[0]);
					$_eip = self::ip2num($_item[1]);
				    }
				    if($_sip && $_eip) {
					$_ip = self::ip2num($ip);
					if ($_ip>=$_sip && $_ip<=$_eip) {
					    return true;
					    break;
					}
				    }
				    if(count($_item)==4 && $item==$ip) { // xx.xx.xx.xx
					return true;
					break;
				    }
				    $_item = null;
				}
				return false;
			    }

			    static function isBannedClient () {
				$_ip = self::getip();
				if(isset(self::$banedlist[$_ip])) return true;
				$_isban = self::isBannedByiP($_ip);
				if($_isban) self::$banedlist[$_ip] = 1;
				return $_isban;
			    }
			}


			// example
			$banlist = array(
			    '192.168.0.1',  // 单ip
			    '192.168.1',    // 网段
			    '127.0.0.2',    // 单ip
			    '127.0.0.0-127.0.0.255' // 网段
			);

			// 初始化加载配置
			IPhelper::loadConfig($banlist);

			$isban = IPhelper::isBannedClient();

			if($isban) {
			    echo 'IP:' . IPhelper::getip() . ' is baned';
			}
			?>
