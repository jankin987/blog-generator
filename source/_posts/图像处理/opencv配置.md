---
title: OpenCV3.1.0+VS2013开发环境配置
date: 2018-10-07 13:22:40
tags:
categories: 
- 图像处理
---

###  1.电脑环境
- 电脑系统： win7 x64
- 已安装Visual Studio版本：2013
- 计划安装OpenCV版本：3.1.0。已传至百度网盘

### 2.OpenCV3.1.0的安装
setp1: 双击下载的文件opencv-3.1.0.exe，如下图所示：
![](http://pexakj5n1.bkt.clouddn.com/18-10-7/98605811.jpg)
step2：点击extract，开始安装，其实也是解压，如下图所示：
![](http://pexakj5n1.bkt.clouddn.com/18-10-7/58230028.jpg)
step3：解压结束后，如下图所示：
![](http://pexakj5n1.bkt.clouddn.com/18-10-7/34711476.jpg)

### 3.OpenCV3.1.0的配置
配置主要分两步
- 在电脑中配置环境变量
- 在编程的开发环境（比如VisualStudio）中配置
#### 3.1配置环境变量
【我的电脑】--->【属性】--->【高级系统设置】--->【高级】--->【环境变量】--->【系统变量】--->【Path】--->【编辑】，将OpenCV安装目录的bin目录添加进去，记得加上 ;(分号)，本人电脑上的路径为：E:\OpenCV\opencv\build\x64\vc12\bin
![](http://pexakj5n1.bkt.clouddn.com/18-10-7/19634520.jpg)
备注1：vc14表明了openCV的编译环境为VS2015，vc12表明了openCV的编译环境为VS2013，vc10表示VS是2010，vc11对应VS2012
![](http://pexakj5n1.bkt.clouddn.com/18-10-7/52875569.jpg)
备注2：OpenCV3也可以和Java，Python兼容
![](http://pexakj5n1.bkt.clouddn.com/18-10-7/22266540.jpg)

#### 3.2配置VS2013
step1: 新建一个空项目
setp2: 配置平台
![](http://pexakj5n1.bkt.clouddn.com/18-10-7/69346509.jpg)
![](http://pexakj5n1.bkt.clouddn.com/18-10-7/63794487.jpg)
setp3：VS2013中配置：包含目录 + 库目录 + 链接器
![](http://pexakj5n1.bkt.clouddn.com/18-10-7/85866599.jpg)
（1）包含目录配置
![](http://pexakj5n1.bkt.clouddn.com/18-10-7/849906.jpg)
在弹出的对话框中，添加以下三条路径：
E:\OpenCV\opencv3.1.0\build\include
E:\OpenCV\opencv3.1.0\build\include\opencv
E:\OpenCV\opencv3.1.0\build\include\opencv2

（2）库目录 配置：
![](http://pexakj5n1.bkt.clouddn.com/18-10-7/98468745.jpg)
在【库目录】添加下面一条路径
E:\OpenCV\opencv3.1.0\build\x64\vc12\lib
（3）链接器配置
![](http://pexakj5n1.bkt.clouddn.com/18-10-7/66635453.jpg)
添加如下两个文件:
opencv_world310d.lib 和 opencv_world310.lib


配置完毕

