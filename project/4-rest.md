---
title: 实现 RESTful API
---

RESTful API 就是约定俗成的一套东西。

### 第一个 API ：拿到所有文章标题

要求做到的是：

前台发 curl 请求，请求格式为

```
curl -X GET localhost:3000/posts
```

发出的请求为：

```
GET /posts
```

后台 API 响应，返回所有文章给前台。

代码：[show all posts](https://github.com/happypeter/sleep-write/commit/018df2901327a47f2674e6f33b8aa28567e4b0ed)

### 完成全部 API

得到所有博客：

```
app.get('/posts'...)
```

得到一篇博客

```
app.get('/posts/:id'...)
```


删除一篇博客

```
app.delete('/posts/:id'...)
```

创建一篇博客

```
app.post('/posts'...)
```

更新一篇博客

```
app.put('/posts/:id'...)
```

这样，我们就实现了一套 RESTful API 。具体每个 API 的回调函数中执行什么语句，这个不是
RESTful 涉及到的范围。

代码： [full RESTful API](https://github.com/happypeter/sleep-write/commit/81826dec2b547f39abcb2049800ca613ccc0b3d5) 。

### RESTful 就是一套规范

规定，我们要执行特定操作，请求格式是什么：

- 得到所有博客 `GET /posts`
- 得到一篇博客 `GET /posts/:id`
- 删除一篇博客 `DELETE /posts/:id`
- 创建一篇博客 `POST /posts`
- 更新一篇博客 `PUT /posts/:id`

我们好的习惯是遵守 RESTful 规范
