---
title: 添加 React Router
---


### 服务器软件

一个网站的本质：就是几个网页。就是几个静态文件。

网站要上线需要什么？第一个就是服务器硬件（简称 server ），硬件之上还要安装**服务器软件**（简称
 server ）。

 我们用 express 可以以写一个静态服务器软件，它的功能最少要包含什么呢？

- 用户访问 haoqicat.com ，服务器要能够提供静态文件给浏览器
- 所有的网页，到底要放到那个文件夹里
- 到底要监听那个端口号，是服务器软件指定的
- 如果我访问 haoqicat.com/ 的时候，没有指定网页，那么默认到底返回那个 .html 页面呢？
  这个也是由服务器规定的（大部分时候都规定 index.html/index.htm 当然也可以任意修改)
- 当然，服务器软件的功能还有非常多


在 https://happypeter.github.io/digicity/react/3-router-hello.html 中的 server.js
就是这个情况。


```
app.use(express.static('public'));
```

首先 public 是个文件夹，这个名子可以叫任意的名字。static 的意思是“静态”（静态文件就算是只
纯粹的 xxx.html xxx.css xxx.js 这些文件，他们是不会被在服务器上执行的）。

这个这句话的意思是：搭建一个静态服务器，所有的页面都要放在 public 文件夹下。而且 public 下
的文件，都不会被服务器进行进一步的处理了，也就是说这里面不能有浏览器不能直接运行的格式了（例如
React 格式的代码）。


```
app.get('/', function(req, res){
  res.sendFile('index.html');
});
```

这三句的意思：如果访问 `/` 就给用户返回 index.html 文件。


```
app.listen(3000, function(err) {
  console.log('Listening at http://localhost:3000');
});
```

最后这三行，就是让这个静态服务器，跑在3000端口。意思就是我们要想得到 public 文件夹
下的静态页面，输入网址的时候： xxx.com:3000 后面的 3000 必须加上。










代码：[react router hello](https://github.com/happypeter/sleep-write/commit/bc3243f5fea8abc06333948aea913d009e36194b)


但是，当前如果直接访问 localhost:3000/hello1 或者，跳转到 localhost:3000/hello1 之后
刷新页面，就会报错 `can not GET /hello1`

解决方法是修改 server.js 如下：

代码: [change server.js](https://github.com/happypeter/sleep-write/commit/d0aba4debeb9dcf46a351c27183ed57ca95e1211)

### 组件化拆分

代码: [router refactor](https://github.com/happypeter/sleep-write/commit/c5a8950602bb545c66430e93e5f8db8a54274717)

### Nested Router

代码 [router nest](https://github.com/happypeter/sleep-write/commit/dd9279dd5095f14c04d81339837846d1017924ee)
