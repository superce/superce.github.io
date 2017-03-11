---
title: 保存数据到 MongoDB
---

发出 curl 请求

```
curl -H 'Content-Type: application/json' -X POST -d '{"title":"Hello", "content": "hello content"}' localhost:3000/posts
```

我们可以把上面的额 json 数据，保存到 mongodb 数据库之中。


### 任务一： mongoose 打印连接 mongdb 成功的字符串

主要包括下面的几个任务：

- 安装 MongoDB
- 代码中安装 mongoose 这个包
- connect 数据库，如果连接成功打印 success 字符串。


### 安装 mongodb

参考以前的文档安装就可以了。

安装好之后，运行

```
mongod --dbpath=./data/db
mongo
```

命令，就可以使用 mongoshell 了。

### 安装 mongoose

```
npm i --save mongoose
```

### 添加 mongoose 的代码

到以前的文档中去粘贴过来就可以。


### 任务二： 创建 API

创建如下的 API

```
app.post('/posts', function(req, res){
  console.log(req.body);
})
```

此时用 curl 请求

```
curl -H "Content-Type: application/json" -X POST -d '{"title":"Hello", "content": "hello content"}' localhost:3000/posts
```

console.log 中可以有正确的输出。


### 保存数据到 db

代码

- [save curl data to db](https://github.com/happypeter/sleep-write/commit/8218afa9a0168fcea05cb86eda2b8c4ad9e157ee)
