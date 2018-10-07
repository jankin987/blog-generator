---
title: 将Hexo部署到github和个人服务器
date: 2018-09-12 12:12:12
tags: 
- Hexo
- Github
categories: 
- Hexo配置
---

### **安装和配置Hexo**
1. 下载安装git
2. 下载node.js并安装，默认会安装npm
3. `npm -v` 查看npm版本，若没出错，表示安装成功
4. `npm install -g hexo-cli` ,安装 Hexo
5. `hexo -v` 产看hexo版本信息
6. `cd /` 进入根目录（git的安装目录下）
7. `hexo init myBlog` 自动创建和初始化博客文件
8. `cd myBlog` 进入myBlog目录，对博客的操作都在这个路径下完成
9. `npm i`
10. `hexo new firstblog` ，生成 /myBlog/source/_posts/firstblog.md 文件

----------
### **配置Git**

1. 在github上新建空repo，命名为 *jankin987.github.io* 
2. 设置 /myBlog/_config.yml 文件，配置如下：
把最后一行 type 改为 `type: git`
在最后一行后面新增一行，左边与 type 平齐，内容为 `repo: github: git@github.com:jankin987/jankin987.github.io.git`
其他设置可自行修改
3. 在 /myBlog 目录下执行 `npm install hexo-deployer-git --save` ，
4. `hexo deploy` ，将博客发布到github
5. 访问 https://jankin987.github.io/ ，即可查看第一篇博客

----------
### **修改Hexo主题**

1. 配置好Hexo和Git后，使用 `hexo new xx` 新建博客，再使用 `hexo generate` 和 `hexo deploy` 发布到相应的服务器。如果需要对 Hexo 进行相应的配置，可修改 /myBlog/_config.yml 文件,以更改主题为例。
2. `cd /myBlog/themes` ，进入与主题相应的目录
3. `git clone git@github.com:iissnan/hexo-theme-next.git` ，下载相应的主题
4. 将 _config.yml 的第 75 行改为 `theme: hexo-theme-next`，保存
5. `hexo generate` and `hexo deploy`

----------
### **将博客源码保存在GitHub仓库**

1. GitHub 创建 blog-generator 空仓库并初始化
2. 进入 /myBlog 目录， `git@github.com:jankin987/blog-generator.git` 克隆项目
3. 在对 Hexo 的 md 文件进行修改后，`git add .` and `git commit -am "add"` and `git push` ，这样所有的源码就保存到 github 上了

----------
### **将博客发布到个人服务器**
#### **服务器配置**
1. 个人服务器是centos7.4的版本，默认安装了 git。先声明的是，我将私人仓库放在 /home/git/hexo.git 目录下，将最后生成的预览网页直接放在 /home/git 目录下

2. `yum install -y nginx` ，安装nginx
3. `systemctl start nginx.service` ,开启 nginx 服务
4. `ss -tnlp`，看 80 端口有没有在监听状态
5. 访问 http://118.25.52.244/ ，默认是一个 nginx 的欢迎界面，由于域名备案未完成，先用IP代替了。如果不能访问，检查 iptables 和 selinux
6. `adduser git` ，新建用户 git，同时可以给用户设置密码
7. `su git` ，所有的操作使用 git 用户操作，避免权限的相关问题
8. `su ~` ，进入自己的家目录
9. `mkdir hexo.git` 创建目录，用于git仓库搭建，hexo.git 目录的属组和数组要为 git ，另外将各个的用户的权限改为 755
10. `cd /home/git/hexo.git` and `git init --bare hexo.git` 进入目录并初始化裸库
11. `vim /home/git/hexo.git/hooks/post-receive` 创建git钩子，内容如下：
```bash
#!/bin/sh
git --work-tree=/home/git --git-dir=/home/git/hexo.git checkout -f
```
12. 保存并退出后, 给post-receive文件添加可执行权限，`chmod +x /home/git/hexo.git/hooks/post-receive`

13. 修改ngnix配置文件 /etc/nginx/nginx.conf，将 server 下的 root 改为 /home/git，表示网页的根目录存放路径，location 改为 index index.html index.htm;表示默认打开index.html文件
14. `systemctl restart nginx.service` 重启 nginx 服务
#### **win配置**
修改Hexo的配置文件 _config.yml，将 repo 修改为：
```
repo: 
&emsp;&emsp;&emsp;github: git@github.com:jankin987/jankin987.github.io.git
&emsp;&emsp;&emsp;jankin987: git@118.25.52.244:/home/git/hexo.git
```

----------


### **在另外电脑上同步源码及Hexo**
1. `cd /` 在根目录下进行操作
2. `git clone git@github.com:jankin987/blog-generator.git` 从 GitHub 中下载博客的源代码
3. 将 blog-generator 重命名为 myBlog
4. `cd /myBlog` 进入 myBlog目录下操作
5. 测试本地仓库
``` 
git add .
git commit -m "add"
```
6. 本地仓库与远程仓库绑定
```
git remote add origin git@github.com:jankin987/blog-generator.git
git push -u origin master
```
7. `npm i` 安装模块组件
8. `npm install hexo-deployer-git --save` 安装组件
9. 配置完成，可通过 `hexo new xxx` ， `hexo generate`  ， `hexo deploy` 进行测试

----------

### **配置Hexo，访问生成的静态页面**
1. `npm install hexo-server --save`，安装hexo-server包
2. `hexo s`，运行服务
3. 在浏览器使用`http://localhost:4000/`访问


### **额外说明**
1. 操作主要参考[Hexo官方文档][1]
2. 说明中并没有Q和ssh的介绍
