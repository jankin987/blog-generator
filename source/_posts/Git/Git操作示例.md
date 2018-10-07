---
title: Git操作示例
date: 2018-09-19 23:15:01
tags:
categories: 
- Git
---
### 初始化的两种方式
```
$ git init myBlog
$ cd myBlog

# 初次使用需要设置姓名和邮箱
$ git config --global user.name "[name]"
$ git config --global user.email "[email]"
```

```
git clone git@github.com:jirengu/blog.git
cd blog
```
### 更新和推送
```
# 把当前目录下的新增和修改的文件添加到暂存区
$ git add .
$ git status
# 把暂存区的更新提交到本地库
$ git commit -am "add file"
# 把远程仓库的变动更新合并到本地仓库
$ git pull
# 如果之前执行过git push origin master，可直接用git push
$ git push origin master
```


