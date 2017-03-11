---
title: 创建 express 的 Hello World
---

到 server 文件夹内，来创建一个基本的 express 的骨架。


### 用 curl 进行 API 测试


```
curl localhost:3000/
```

打印 Hello World 就算成功了。

### 用 nodemon 来自动加载后台代码

```
npm i -g nodemon
```

`-g` 是 `--global` 的缩写，意思是全局安装。全局安装有两个好处：

- 第一是，所有项目都可以公用
- 第二是，全局安装的包，之中的命令会被自动导出

也就是，上面的包装好之后，系统任意位置都可以执行

```
nodemon
```

命令。如果是局部安装，执行这个命令，就会报错 `Command Not Found` 。

### 代码

- [express hello](https://github.com/happypeter/sleep-write/commit/4db512c9ca754f88e03219cb17b0ddbf723862db)
