# htmx从0开始学习
文档链接：<https://htmx.org/docs/#introduction>

___
#### 是什么？
一种超文本标记语言, 继承和概括了html的核心思想
- 任何节点可以发http请求
- 事件不仅是点击或者提交，可以出发请求
- 请求不仅是get和post
- 可以作为http请求返回的展示内容节点

是一种典型服务端html语言，是一种原生的web语法模型，不需要学习新概念
```javascript
<button hx-post="/clicked"
    hx-trigger="click"
    hx-target="#parent-div"
    hx-swap="outerHTML"
>
    Click Me!
</button>
```
****
