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
#### 如何发AJAX请求？
- 直接通过节点元素属性去设置请求的相关参数，例如请求类型、触发请求的条件、请求返回的展示内容元素的id
- 触发条件类型：
  1. 元素的原生事件，input、select、textarea的change事件，form表单的submit事件
   ```javascript
    <div hx-post="/mouse_entered" hx-trigger="mouseenter">
     [Here Mouse, Mouse!]
    </div>
   ```
   2. 给触发事件增加限定条件修饰语，changed、delay:\<time interval>、throttle:\<time interval>、from:\<CSS Selector>
   ```javascript
        // 当按键起来事件、值变化、延迟500毫秒，才会发请求。
        // 请求返回值会插入到id为search-results的div
        <input type="text" name="q"
            hx-get="/trigger_delay"
            hx-trigger="keyup changed delay:500ms"
            hx-target="#search-results"
            placeholder="Search..."
        >
        <div id="search-results"></div>
   ```
- 触发器过滤，在事件名称后面用方括号包裹js表达式，当表达式为true时才会触发
    ```javascript
    // 当点击了control键的时候触发
    <div hx-get="/clicked" hx-trigger="click[ctrlKey]">
        Control Click Me
    </div>
    ```
- 特殊事件
  1. load,当节点第一次加载的时候只执行一次
  2. revealed，当节点第一次滚动到视野里只执行一次
  3. intersect，当节点首次与视口交叉时只执行一次
- 轮询请求
  ```javascript
  // 每两秒会发请求，当请求返回码是286就会停止轮询
  <div hx-get="/news" hx-trigger="every 2s"></div>
  ```
