---
title: 如何在hexo中支持Mathjax
date: 2018-09-23 12:52:20
tags:
- Mathjax
categories: Hexo配置
---
在 hexo 中，可以通过安装第三方库来解决公式的问题。
###  第一步： 使用Kramed代替 Marked
hexo 默认的渲染引擎是 marked，但是 marked 不支持 mathjax。 kramed 是在 marked 的基础上进行修改。我们在工程目录下执行以下命令来安装 kramed
```bash
npm uninstall hexo-renderer-marked --save
npm install hexo-renderer-kramed --save
```
然后，更改`/node_modules/hexo-renderer-kramed/lib/renderer.js`，更改：
```
// Change inline math rule
function formatText(text) {
    // Fit kramed's rule: $$ + \1 + $$
    return text.replace(/`\$(.*?)\$`/g, '$$$$$1$$$$');
}
```
为
```
// Change inline math rule
function formatText(text) {
    return text;
}
```
### 第二步：停止使用 hexo-math
如果已经安装 hexo-math, 请卸载：`npm uninstall hexo-math --save`
然后安装`hexo-renderer-mathjax`包：`npm install hexo-renderer-mathjax --save`

### 第三步: 更新 Mathjax 的 CDN 链接
首先，打开`/node_modules/hexo-renderer-mathjax/mathjax.html`，然后，把<script>更改为：
`<script src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.1/MathJax.js?config=TeX-MML-AM_CHTML"></script>`
### 第四步: 更改默认转义规则
因为 hexo 默认的转义规则会将一些字符进行转义，比如 _ 转为 <em>, 所以我们需要对默认的规则进行修改.
首先， 打开`path-to-your-project/node_modules/kramed/lib/rules/inline.js`，把
```
escape: /^\\([\\`*{}\[\]()#$+\-.!_>])/,
```

更改为 
```
escape: /^\\([`*\[\]()# +\-.!_>])/,
```

然后把
`em: /^\b_((?:__|[\s\S])+?)_\b|^\*((?:\*\*|[\s\S])+?)\*(?!\*)/,`
更改为
`em: /^\*((?:\*\*|[\s\S])+?)\*(?!\*)/,`
###  第五步: 开启mathjax
在主题的配置文件`_config.yml`中开启开启 Mathjax， 找到 `mathjax` 字段添加如下代码：
```
mathjax:
    enable: true
```
这一步可选，在博客中开启 Mathjax，， 添加以下内容：
```
---
title:
category: 
mathjax: true
---
```
这样就能在hexo中使用公式了。
