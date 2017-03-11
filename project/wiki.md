---
title: 项目
---

http://happypeter.coding.me/
 - https://github.com/happypeter/big-demo

very interesting


https://github.com/happypeter/digicity 这里的内容总结一下看能不能出个课程
然后最好删除掉。



### 补充技巧：如何拿到非默认分支的代码

问题是：现在我们想要拿到　021-react-router 这个文件夹，但是这个文件夹是在　old-stuff 分支上，本仓库的默认分支是　gh-pages 。具体操作步骤如下:

第一步，拿到　clone 链接，到仓库页面，http://github.com/happypeter/digicity ，找到
`clone or download` 按钮，点一下，有两种链接可以使用，一种　ssh 协议的（ git@github.com:happypeter/digicity.git ），这种形式的链接有时候只允许项目所有者使用。
如果出现这样的情况，可以使用　HTTPS 协议的链接。

```
git clone https://github.com/happypeter/digicity.git
```

第二步，切换到需要的分支。克隆得到　digicity/ 文件夹，

```
cd digicity
git branch
```

这是只能看到默认分支，gh-pages ，看不到我们需要的　old-stuff 分支，但是依然可以执行：

```
git checkout old-stuff
```

来切换到　old-stuff 分支。可以通过　`git branch -a` 来查看一共有多少分支。
