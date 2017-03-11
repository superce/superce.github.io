---
title: 创建 Github 项目
---

创建一个新的 Github 项目，本地保存一个本项目的 clone 。学会 push/pull 同步项目。


### 项目简介

项目名叫 sleep-write ，是一个写文章的平台。


### 具体 Github 操作

到首页，点 New Repository 按钮，创建一个新的仓库。


### 本地创建项目

```
mkdir sleep-write
cd sleep-write
atom . # 添加一个 README.md
git init
git add -A
git commit -m"first commit"
```


### 添加目标仓库位置

```
git remote add origin git@github.com:happypeter/sleep-write.git
git push -u origin master
```

这样 REAME.md 就被推送到 github.com 之上了。


### 添加项目文件夹

```
mkdir client
mkdir server
```

项目采用前后端分离的架构，前台 react 代码都放到 client 文件夹，后台 express 代码都放到
server 文件夹。
