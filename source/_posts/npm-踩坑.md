---
title: npm 踩坑
date: 2018-09-23 12:25:08
tags: npm
categories: 踩坑锦集
---
### npm ERR! code ETIMEDOUT
使用npm安装软件包报错：
![](http://pexakj5n1.bkt.clouddn.com/18-9-23/25343742.jpg)

原因：软件包的域名换成别的了
解决办法：执行`npm cache verify`

