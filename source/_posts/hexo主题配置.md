---
title: Hexo主题配置
date: 2018-09-19 09:03:38
tags: 
- Hexo
categories: 
- Hexo配置
---

### **修改侧边栏到左边** ###
首先，先更改`\themes\next\source\css\_common\components\sidebar\sidebar.styl`，把第三行的right改成left,如下:
```
.sidebar {
  position: fixed;
  left: 0;
```
然后，打开 `\themes\next\source\js\src\motion.js` ，把101行和167行的 `paddingRight` 全改成 `paddingLeft` 

然后找到类似如下的代码（大约在54行），并替换成如下代码:
```
var sidebarToggleLine1st = new SidebarToggleLine({
  el: '.sidebar-toggle-line-first',
 	status: {
   	arrow: {width: '50%', rotateZ: '45deg', top: '2px', left: '5px'},
   	close: {width: '100%', rotateZ: '45deg', top: '5px', left: 0}
 	}
});
var sidebarToggleLine2nd = new SidebarToggleLine({
 	  el: '.sidebar-toggle-line-middle',
 	status: {
   	arrow: {width: '90%'},
   	close: {opacity: 0}
 	}
});
var sidebarToggleLine3rd = new SidebarToggleLine({
 	  el: '.sidebar-toggle-line-last',
 	status: {
   	arrow: {width: '50%', rotateZ: '-45deg', top: '-2px', left: '5px'},
   	close: {width: '100%', rotateZ: '-45deg', top: '-5px', left: 0}
 	}
});
```

### **修改Scheme Settings** ###
打开 `/myBlog/themes/hexo-theme-next/_config.yml`，修改110行，将scheme 改为`Pisces`
```
# Schemes
#scheme: Muse
#scheme: Mist
scheme: Pisces
#scheme: Gemini
```

### **修改导航菜单** ###


1. 打开 `/myBlog/themes/hexo-theme-next/_config.yml`，修改94行
```
menu:
  home: / || home
  about: /about/ || user
  tags: /tags/ || tags
  categories: /categories/ || th
  archives: /archives/ || archive
  #schedule: /schedule/ || calendar
  #sitemap: /sitemap.xml || sitemap
  #commonweal: /404/ || heartbeat
```
2. 创建归档页面 `hexo new page categories`
修改内容：
```
title: categories
date: 2018-05-14 23:34:12
type: "categories"
---
```
3. 创建标签页 `hexo new page tags`
修改内容：
```
title: tags
date: 2018-05-14 23:36:18
type: "tags"
---
```
4. 创建个人主页 `hexo new page about`，可以配置title（实际没有配置）
```
title: 个人简介
date: 2018-05-14 23:38:55
---
```
### **设置语言（实际没有设置）** ###
默认语言在 ~/Blog/next/languages 下面，而设置在 ~/Blog/_config.yml下 

### **隐藏网页底部powered By Hexo 强力驱动** ###
打开`themes/next/layout/_partials/footer.swig`,删除下面一段代码
![](http://pexakj5n1.bkt.clouddn.com/18-9-23/97405411.jpg)

### **设置网站的图标Favicon**
具体方法实现
找一张（32*32）的ico图标,或者去别的网站下载或者制作，并将图标名称改为favicon.ico，然后把图标放在`/themes/next/source/images`里，并且修改主题配置文件：
![](http://pexakj5n1.bkt.clouddn.com/18-9-23/39990924.jpg)


