---
title: 在wps中嵌入mathtype
date: 2018-09-21 00:40:28
tags:
---

1. 安装VBA环境。下载WPS VBA 7.0.1568，并安装，然后就可以启用宏了
2. 将wps的宏安全性设置到最低
![](http://pexakj5n1.bkt.clouddn.com/18-9-21/86512317.jpg)
3. 将mathtype安装目录下的 `MathType\MathPage\32\MathPage.wll`拷贝到wps的目录`C:\Users\Administrator\AppData\Local\Kingsoft\WPS Office\10.1.0.6393\office6`下
4. 将\MathType\Office Support\64\目录下的如下三个文件拷贝到`C:\Users\Administrator\AppData\Local\Kingsoft\WPS\ Office\10.1.0.6393\office6\startup`下
![模板](http://pexakj5n1.bkt.clouddn.com/18-9-21/25451933.jpg)
5. 最后效果
![](http://pexakj5n1.bkt.clouddn.com/18-9-21/5408350.jpg)
6. 然后就可以愉快地在wps中将公式转为TeX 了


