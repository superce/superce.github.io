---
title: 实现首页文章列表
---

今天把前后台都启动起来，联调一下，显示出文章列表。

### 启动流程

先启动前台：

第一步编译 bundle.js ，运行

```
npm run build
```

编译完成，启动前台服务器

```
npm start
```

再来启动后台：

先启动数据库：

```
mongod --dbpath=./data/db
```

然后启动后台服务：

```
npm start
```

步骤开始变多，实际项目中，是通过**bash 脚本**来一键执行。

写 Bash 脚本的推荐资料：http://billie66.github.io/TLCL/ 。


### 任务一： 首页变成链接

代码：[link to post/id](https://github.com/happypeter/sleep-write/commit/214e3ecf38d9d7793115bd4add4529bdb2041648)

### 任务二：创建空白的 posts/xxx 页面

要完成的任务就是首页的链接可以打开，打开后不要求有具体内容，显示 Hello 就行。
主要考察 React-router 传参数这个知识点。


react-router 传参数，就是从前台的一个页面，传递给下一个页面，跟后台没有发生关系。

如何发起传参：

```
<Link to={/posts/23456}> My Dog</Link>
```

我们写下这条语句，我们期待用户点击这个 Link ，我们的目的有两个：

- 跳转到 /posts/23456 这个页面
- 要能够在 /posts/23456 这一个页面中，使用 '23456' 这个字符串

接受路由的语句怎么写

```
<Route path={/posts/:id} component={ Post }
```

下一步，就是如何在新”页面“中得到 `23456` 这个字符串，那么在 Post.js
中，语句如下：

```
this.props.params.id
```

这样得到的就是 `23456` 这个 id 值了，方便进一步的使用。

代码：[router pass params](https://github.com/happypeter/sleep-write/commit/0647c18f7eb1465a43674af95c97daf0361dfbd6)

### 任务三：Post.js 页面中显示  title/content

后台 api 也要调整一下，不然没有数据。

开发小技巧，先写后台 API ，完成后，用 curl 测试一下，打印

```
$ curl localhost:4000/posts/58574ecd7bedd716df5669ea
{"post":{"_id":"58574ecd7bedd716df5669ea","title":"hello1","content":"hello1 content"}}%
```

这样表示后台肯定没问题了，然后再动手写前端代码。


> 小贴士：异步函数
Post.findById({_id: req.params.id}, function(err, post) {
   res.json({ post: post })
})
上面的 findById 就是一个异步函数，异步函数的特点是，所要的结果，不能通过
返回值的形式直接得到，而要通过回调函数来获得


### 展示一篇博客详情

代码： [show post](https://github.com/happypeter/sleep-write/commit/4c0384e73780c57aaa3dbdbba0655c24d697220e)


### bundle.js 请求报错

访问： http://localhost:3000/posts/58574ecd7bedd716df5669ea

报错如下：

```
bundle.js:1 Uncaught SyntaxError: Unexpected token <
```

原因就是请求 bundle.js 的时候，结果请求得到的是 index.js 。

解决方法：index.js 中写 `/bundle.js` 不能省略 `/` 。

原理：

server.js 中是这样写的

```
app.use(express.static('public'));

app.get('*', function(req, res){
  res.sendFile('index.html', {root: 'public'});
});
```

`express.static` 这一行的作用是把 public/ 文件夹中的所有静态文件的路径都导出了，
也就是，如果服务器访问的是 localhost:3000/bundle.js 那么，直接就可以返回正确的 bundle.js 。
而不会执行到 `app.get('*')` 这一句。

但是，如果请求的是 localhost:3000/posts/ 注意 posts 后面的 `/` 同时，index.html 的 bundle.js
前面又没有加 `/` 那么，浏览器请求 bundle.js 的时候，发起的请求就是 localhost:3000/posts/bundle.js
这样，自然服务器就会返回 index.html 的内容，所以就有了一开始的报错了。
