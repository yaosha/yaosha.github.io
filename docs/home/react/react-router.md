---
title: React路由
---

{% capture article %}

## 下载教程

```
git clone https://github.com/reactjs/react-router-tutorial
cd react-router-tutorial
cd lessons/01-setting-up
npm install
npm start
```

## Router

Router是一个组件，路由的核心。

### 属性

history：路由历史记录

### 示例


```js
render(<Router/>, document.getElementById('app'))
```

## Route
 
Route也是一个组件，表示一个路由。

### 属性

path：路径

component：路径对应的页面

### 示例

```js
// insert into index.js
import About from './modules/About'
import Repos from './modules/Repos'

render((
  <Router history={hashHistory}>
    <Route path="/" component={App}/>
    {/* add the routes here */}
    <Route path="/repos" component={Repos}/>
    <Route path="/about" component={About}/>
  </Router>
), document.getElementById('app'))
```


## history

### hashHistory

### browserHistory

## Link

Link是一个链接，设置路由导航。


### 属性

to：设置导航路由

activeStyle：设置激活样式

activeClassName：设置激活样式类名

### 示例

```js
// modules/App.js
<li><Link to="/about" activeStyle={{ color: 'red' }}>About</Link></li>
<li><Link to="/repos" activeStyle={{ color: 'red' }}>Repos</Link></li>
```

```js
// modules/App.js
<li><Link to="/about" activeClassName="active">About</Link></li>
<li><Link to="/repos" activeClassName="active">Repos</Link></li>
```

## 路由嵌套

路由嵌套实现页面嵌套，导航复用，页面模板。


```js
// index.js
// ...
render((
  <Router history={hashHistory}>
    <Route path="/" component={App}>
      {/* make them children of `App` */}
      <Route path="/repos" component={Repos}/>
      <Route path="/about" component={About}/>
    </Route>
  </Router>
), document.getElementById('app'))
```
在`App.js`中使用`this.props.children`实现页面嵌套。

```js
// modules/App.js
// ...
  render() {
    return (
      <div>
        <h1>React Router Tutorial</h1>
        <ul role="nav">
          <li><Link to="/about">About</Link></li>
          <li><Link to="/repos">Repos</Link></li>
        </ul>

        {/* add this */}
        {this.props.children}

      </div>
    )
  }
// ...
```

## 参数

Route的path中使用`:`开头的字符串实现参数传递。

```js
// ...
// import Repo
import Repo from './modules/Repo'

render((
  <Router history={hashHistory}>
    <Route path="/" component={App}>
      <Route path="/repos" component={Repos}/>
      {/* add the new route */}
      <Route path="/repos/:userName/:repoName" component={Repo}/>
      <Route path="/about" component={About}/>
    </Route>
  </Router>
), document.getElementById('app'))
```

使用`this.props.params[paramName]`获取参数。

```js
// modules/Repo.js
import React from 'react'

export default React.createClass({
  render() {
    return (
      <div>
        <h2>{this.props.params.repoName}</h2>
      </div>
    )
  }
})
```

{% endcapture %}

{% include templates/home.md %}
