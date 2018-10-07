---
title: Mathjax踩坑
date: 2018-09-23 12:37:48
tags:
- Mathjax
categories: 踩坑锦集
mathjax: true
---
在另外一篇文章里，详细介绍了如何在 hexo 中支持 Mathjax，这篇文章里，主要介绍两个大坑
 ###  1.不要安装 hexo-math
 当说明如何在hexo使用公式时，在很多文章里都介绍了`npm install hexo-math --save`这种方式，甚至在hexo的官方文档也介绍了这种方式，结果就是解决了几个小时的错误还没解决完。主要原因是依赖包`hexo-inject`已被作者弃用，不会再使用在hexo中。
 ### 2.Unhandled rejection Template render error: (unknown path) [Line 1, Column 35]
 报错如下：
 ![](http://pexakj5n1.bkt.clouddn.com/18-9-23/7323949.jpg)
 这个问题想了很久也没明白，既没告诉路径，也没告诉错在哪，原因在于，当配置好Mathjax后，使用TeX ![](http://pexakj5n1.bkt.clouddn.com/18-9-23/13625794.jpg)可以在其他的markdown编辑器显示出$O(\log_2 N)$，但在hexo上就不行，在hexo上要这样写：`$O(\log_2 N)$`。奇耻大坑。
