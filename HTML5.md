# HTML5

## 语义化标签

语义化标签作用：

- 能够便于开发者阅读和写出更优雅的代码。
- 同时让浏览器或是网络爬虫可以很好地解析，从而更好分析其中的内容。
- 更好地搜索引擎优化。

#### HTML5新增语义标签

- `<section>` 表示区块
- `<article>` 表示文章。如文章、评论、帖子、博客
- `<header>` 表示页眉
- `<footer>` 表示页脚
- `<nav>` 表示导航
- `<aside>` 表示侧边栏。如文章的侧栏
- `<figure>` 表示媒介内容分组。
- `<mark>` 表示标记 (用得少)
- `<progress>` 表示进度 (用得少)
- `<time>` 表示日期

**新增语义标签的兼容性处理**

IE8 及以下版本的浏览器不支持 H5 和 CSS3。解决办法：引入`html5shiv.js`文件。

引入时，需要做if判断，具体代码如下：

```html
    <!--  条件注释 只有ie能够识别-->
    <!--[if lte ie 8]>
        <script src="html5shiv.min.js"></script>
    <![endif]-->
```

#### HTML5新增表单标签

```html
<input type="number">
```

- `email` 只能输入email格式。自动带有验证功能。
- `tel` 手机号码。
- `<datalist>` 数据列表。input的内容与option自动提示。
- `url` 只能输入url格式。
- `number` 只能输入数字。
- `search` 搜索框
- `range` 滑动条
- `color` 拾色器
- `time` 时间
- `date` 日期
- `datetime` 时间日期
- `month` 月份
- `week` 星期

**表单属性**

- `placeholder` 占位符（提示文字）
- `autofocus` 自动获取焦点
- `multiple` 文件上传多选或多个邮箱地址
- `autocomplete` 自动完成（填充的）。on 开启（默认），off 取消。用于表单元素，也可用于表单自身(on/off)
- `form` 指定表单项属于哪个form，处理复杂表单时会需要
- `novalidate` 关闭默认的验证功能（只能加给form）
- `required` 表示必填项
- `pattern` 自定义正则，验证表单。

**表单事件**

- `oninput()`：用户输入内容时触发，可用于输入字数统计。
- `oninvalid()`：验证不通过时触发。比如，如果验证不通过时，想弹出一段提示文字，就可以用到它。

#### 多媒体标签

音频和视频

```html
<audio src="music/yinyue.mp3" autoplay controls> </audio>
<video src="video/movie.mp4" controls autoplay></video>
```

#### 其他标签

**拖拽**

`<dev draggable="true"></dev>`然后通过监听事件来完成动作

**历史**

`window.history`对象可以让我们管理历史记录，可用于单页面应用，Single Page Application，可以无刷新改变网页内容。

**地理位置**

- ip地址
- GPS
- WiFi
- 手机信号
- 用户自定义数据

**全屏**

`requestFullscreen()`

`cancleFullscreen()`

## DOM 操作

#### 获取元素和类名操作

- document.querySelector("selector") 通过CSS选择器获取符合条件的第一个元素。
- document.querySelectorAll("selector") 通过CSS选择器获取符合条件的所有元素，以类数组形式存在。

- Node.classList.add("class") 添加class
- Node.classList.remove("class") 移除class
- Node.classList.toggle("class") 切换class，有则移除，无则添加
- Node.classList.contains("class") 检测是否存在class

## Web存储

#### H5 中有两种存储的方式

1、**`window.sessionStorage` 会话存储：**

- 保存在内存中。
- **生命周期**为关闭浏览器窗口。也就是说，当窗口关闭时数据销毁。
- 在同一个窗口下数据可以共享。

2、**`window.localStorage` 本地存储**：

- 有可能保存在浏览器内存里，有可能在硬盘里。
- 永久生效，除非手动删除（比如清理垃圾的时候）。
- 可以多窗口共享。

```javascript
localStorage.setItem(key,value) //可新增，可更新
localStorage.getItem(key,value)
~.removeItem(key)
~.clear() //清空所存储内容
~.key(n) //根据索引值来获取内容
```

**Web 存储的特性**

（1）设置、读取方便。

（2）容量较大，sessionStorage 约5M、localStorage 约20M。

（3）只能存储字符串，可以将对象 JSON.stringify() 编码后存储。

## 网络状态

```html
<script>
    window.addEventListener('online', function () {
        alert('网络连接建立！');
    });

    window.addEventListener('offline', function () {
        alert('网络连接断开！');
    })
</script>
```

## 应用缓存

HTML5中可以构建一个离线（无网络状态）应用，只需要创建一个 `cache manifest` 缓存清单文件。

- 可配置需要缓存的资源，在网络无连接应用仍可用

- 本地读取缓存资源，提升访问速度，增强用户体验

- 减少请求，缓解服务器负担。

  

**缓存文件写法**

- 使用 `.appcache`作为后缀名，另外还要添加MIME类型
- 顶行写CACHE MANIFEST。

- CACHE: 换行 指定我们需要缓存的静态资源，如.css、image、js等。

- NETWORK: 换行 指定需要在线访问的资源，可使用通配符（也就是：不需要缓存的、必须在网络下面才能访问的资源）。

- FALLBACK: 换行 当被缓存的文件找不到时的备用资源（当访问不到某个资源时，自动由另外一个资源替换）。

```javascript
CACHE MANIFEST

#要缓存的文件
CACHE:
    images/img1.jpg
    images/img2.jpg


#指定必须联网才能访问的文件
NETWORK:
     images/img3.jpg
     images/img4.jpg


#当前页面无法访问是回退的页面
FALLBACK:
    404.html
```

以上文件如果叫`demo.appcache`，使用时在html根属性中添加`<html manifest="demo.appacche"></html>`

## HTML基础回顾和常见面试题

[HTML基础回顾和常见面试题](https://web.qianguyihao.com/01-HTML/12-HTML基础回顾.html)