---
title: opencv踩坑
date: 2018-10-07 16:24:51
tags:
- OpenCv
- 图像处理
categories: 踩坑锦集
---

###  1.cvCvtPixToPlane & cvCvtPlanetoPix
![](http://pexakj5n1.bkt.clouddn.com/18-10-7/14193468.jpg)

### 2. OpenCV：无法启动此程序，因为计算机中丢失opencv_world310.dll
出错：
![](http://pexakj5n1.bkt.clouddn.com/18-10-7/34118316.jpg)
解决：
将bin目录(E:\OpenCV\opencv\build\x64\vc12\bin)中的3个dll文件复制在（C:\Windows\System32）或者(C:\Windows\SysWOW64)
![](http://pexakj5n1.bkt.clouddn.com/18-10-7/19634520.jpg)