---
title: 提交数据到服务器
---

### 任务一：后台接口

用 curl 请求一下，能够保存成功即可。

### 任务二：创建新建页面

新建页面的路由是 `/new`

localhost:3000/new 这样页面上应该可以看到一个 form 。

代码：[new post page](https://github.com/happypeter/sleep-write/commit/8f1ca889e24018b52e8db8ad5ed38307a4ef9c80)

### 任务三：得到 form 的填写数据

React 的 refs

```
<form onSubmit={this.handleSubmit.bind(this)}
  <input type='text' name="title" ref='title' />
  <input type='text' name="content" ref='content' />
  <input type="submit" />
</form>
```

我们虽然有 form 但是我们不用 form 提交数据，而是使用 axios 提交数据。

所以定义 handleSubmit

```
handleSubmit(){
  let content = this.refs.content.value;
  let title = this.refs.title.value;
  const data = {
    title: title,
    content: content
  }
  axios.post('/posts', data)
}
```

代码：[read value from form](https://github.com/happypeter/sleep-write/commit/34e40c895e19a862a7494534e8b1b0cf55a2a633)

### 任务四：提交数据到服务器

代码：[axios send data](https://github.com/happypeter/sleep-write/commit/0778e5a35b42e19b1caabb89800ec3963f432871)


### 任务五：文章发表后，跳转到首页

代码： [router push](https://github.com/happypeter/sleep-write/commit/1c313237e6ab608b86849bfe21b8223b7d67a03f)


### 任务六：编辑文章

代码： [update](https://github.com/happypeter/sleep-write/commit/3c5cdaebdec8a174115c8f6cb8998c50dc95c01f)


### 任务七：删除文章

代码：

后台 API 代码：[delete server api done](https://github.com/happypeter/sleep-write/commit/e0fd15cc1c74dc231805cc492d448eb4dfa368ba)

测试后台 API 的 curl 命令：

```
curl -X DELETE localhost:4000/posts/23243243243243
```

现在开始写前台：


```
<span className="delete-btn" onClick={this.handleClick.bind(this, post._id)}>删除</span>
```


- [filter posts](https://github.com/happypeter/sleep-write/commit/0b99ad259cce0a05fe9b6ee50feed1ea4950f362)

- [send request](https://github.com/happypeter/sleep-write/commit/022d8831e6115d4787fc15f461352afc5d325b2f)



### 进一步学习

- http://haoqicat.com/react-express-api
- http://haoqicat.com/hand-in-hand-react
