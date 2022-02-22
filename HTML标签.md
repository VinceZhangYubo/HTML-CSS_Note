# HTML标签



## 头标签内常见标签

```
<title>：指定整个网页的标题，在浏览器最上方显示。
<base>：为页面上的所有链接规定默认地址或默认目标。
<meta>：提供有关页面的基本信息
<body>：用于定义HTML文档所要显示的内容，也称为主体标签。我们所写的代码必须放在此标签內。
<link>：定义文档与外部资源的关系。
```

#### \<meta\> 标签：

meta表示“元”。“元”配置，就是表示基本的配置项目。

**name属性:**

```html
<meta name="参数" content="参数值">
```

meta的name属性的参数有：字符集 charset （网页编码方式），视口 viewport，关键词keywords，页面描述description，网页作者author：

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="Keywords" content="网易,邮箱,游戏,新闻,体育,娱乐,女性,亚运,论坛,短信" />
<meta name="Description" content="网易是中国领先的互联网技术公司，为用户提供免费邮箱、游戏、搜索引擎服务，开设新闻、娱乐、体育等30多个内容频道，及博客、视频、论坛等互动交流，网聚人的力量。" />
```
**http-equiv属性:**

相当于http的文件头作用，它可以向浏览器传回一些有用的信息，以帮助正确和精确地显示网页内容，与之对应的属性值为content，content中的内容其实就是各个参数的变量值。

- Expires(期限) ：可以用于设定网页的到期时间。一旦网页过期，必须到服务器上重新传输。

``` html
<meta http-equiv="expires" content="Fri,12Jan200118:18:18GMT"> 
```

注意：必须使用GMT的时间格式。 

- Pragma(cache模式) ：禁止或允许浏览器从本地计算机的缓存中访问页面内容。 

```html
<meta http-equiv="Pragma" content="no-cache"> 
```

这样设定，访问者将无法脱机浏览。 

- Refresh(刷新) ：自动刷新并指向新页面。 

```html
<meta http-equiv="Refresh" content="2; URL=http://www.baidu.com"> 
```

其中的2是指停留2秒钟后自动刷新到URL网址。 

- Set-Cookie(cookie设定) 

说明：如果网页过期，那么存盘的cookie将被删除。

```html
<meta http-equiv="Set-Cookie" content="cookievalue=xxx; expires=Friday,12-Jan-200118:18:18GMT；path=/"> 
```

其中的2是指停留2秒钟后自动刷新到URL网址。必须使用GMT的时间格式。 

- Window-target(显示窗口的设定) ：强制页面在当前窗口以独立页面显示。

```html
<meta http-equiv="Window-target" content="_top"> 
```

用来防止别人在框架里调用自己的页面。 

- Cache-Control指定请求和响应遵循的缓存机制。在请求消息或响应消息中设置Cache-Control并不会修改另一个消息处理过程中的缓存处理过程。

- ...

#### \<base\>标签：

```html
<base href="/">
```

base 标签用于指定基础的路径。指定之后，所有的 a 链接都是以这个路径为基准。

#### \<body\>标签：

<body>标签属性：

- `bgcolor`：设置整个网页的背景颜色。

- `background`：设置整个网页的背景图片。

- `text`：设置网页中的文本颜色。

- `leftmargin`：网页的左边距。IE浏览器默认是8个像素。

- `topmargin`：网页的上边距。

- ...

  

## 排版标签

#### 行内标签：

p、span、a、b、i、u、em。文本级标签里只能放**文字、图片、表单元素**。（a标签里不能放a和input）

#### 块级标签：

div、h系列、li、dt、dd。容器级标签里可以放置任何东西。

- `<h1>`~`<h5>`：标题
  - align属性：left center right
- `<p>`：段落
  - align属性：left center right
- `<hr />`：水平线
  - `<hr align="center" size="2" width="70%" color="#0000FF" noshade />`  2像素粗居中横向占屏70%无阴影的水平线
- `<br />`：换行
- `<div>`：块级元素标签
- `<span>`:小文本标签，不换行
- `<pre>`: 将保留标签内部所有的空白字符(空格、换行符)，原封不动地输出结果（告诉浏览器不要忽略空格和空行）



## 超链接标签

**外部链接**：

```html
<a href="02页面.html">点击进入另外一个文件</a>
```

**锚链接**：

```html
<body>
	<a name="a.html#name1">点击跳转到a.html的name1位置</a>
</body>
```

常用于点击跳转回顶部

**邮箱链接**：

```html
<a href="mailto:xxx@163.com">点击进入我的邮箱</a>
```

#### 超链接的属性

- `href`：目标URL

- `title`：悬停文本。

- `name`：主要用于设置一个锚点的名称。

- `target`：告诉浏览器用什么方式来打开目标页面。

  target属性有以下几个值：

  - `_self`：在同一个网页中显示（默认值）
  - `_blank`：**在新的窗口中打开**。
  - `_parent`：在父窗口中显示
  - `_top`：在顶级窗口中显示

  

## 图片标签

```html
<img src="图片的URL" />
```

HTML页面不是直接插入图片，而是插入图片的引用地址，所以要先把图片上传到服务器上。

#### 相对路径和绝对路径

**相对路径**

**.是当前文件夹下，代表包含当前文件的一级文件夹**

**..是上一级文件夹，代表包含当前文件的一级文件夹的上一层文件夹。**

#### 图片标签的属性

```html
<img src="images/1.jpg" width="300" height="`188"  align="center" title="猫猫" alt="猫猫加载错误">
```

- `alt`：当图片不可用（无法显示）的时候，代替图片显示的内容。
- `title`：鼠标悬停时出现的文本。
- 如果要想保证图片等比例缩放，请只设置width和height中其中一个。
- `align`属性：图片和周围文字的相对位置，实现基础的图文混合排版。



## 列表标签和表格标签

#### 普通列表

```html
<ul type="square">
	<li>默认1</li>
	<li>默认2</li>
	<li>默认3</li>
</ul>
<ol>
    <li>默认1</li>
	<li>默认2</li>
	<li>默认3</li>
</ol>
```

- li不能单独存在，必须包裹在ul里面；反过来说，ul的“儿子”不能是别的东西，只能有li。但li是一个容器级标签，li里面什么都能放。
- `<ul>`的`type="属性值"`。属性值可以选： `disc`(实心原点，默认)，`square`(实心方点)，`circle`(空心圆)。
- `<ol>`的`type="属性值"`。属性值可以是：1(阿拉伯数字，默认)、a、A、i、I。结合`start`属性表示`从几开始`。
- 常用于导航条

#### 定义列表

`<dl>`英文单词：definition list，没有属性。dl的子元素只能是dt和dd。

- `<dt>`：definition title 列表的标题，这个标签是必须的
- `<dd>`：definition description 列表的列表项，如果不需要它，可以不加

备注：dt、dd只能在dl里面；dl里面只能有dt、dd。

dt、dd都是容器级标签，想放什么都可以。dt与dd是一对多或一对一都可。

#### 表格标签

```html
<table>
    <th>
        <caption align="center">表格标题</caption>
        <td>1</td>
    	<td>2</td>
    	<td>3</td>
    </th>
	<tr>
		<td>4</td>
		<td>5</td>
        <td rowspan="2">6</td>
	</tr>
    <tr>
		<td>7</td>
		<td>8</td>
	</tr>
</table>
```

**`<table>`常用属性**

- `border`：边框。像素为单位。
- `style="border-collapse:collapse;"`：单元格的线和表格的边框线合并（表格的两边框合并为一条）
- `width`：宽度。像素为单位。
- `height`：高度。像素为单位。
- `bordercolor`：表格的边框颜色。
- `align`：**表格**的水平对齐方式。属性值可以填：left right center。 注意：这里不是设置表格里内容的对齐方式，如果想设置内容的对齐方式，要对单元格标签`<td>`进行设置）
- `cellpadding`：单元格内容到边的距离，像素为单位。默认情况下，文字是紧挨着左边那条线的，即默认情况下的值为0。 注意不是单元格内容到四条边的距离哈，而是到一条边的距离，默认是与左边那条线的距离。如果设置属性`dir="rtl"`，那就指的是内容到右边那条线的距离。
- `cellspacing`：单元格和单元格之间的距离（外边距），像素为单位。默认情况下的值为0

当表格非常大内容非常多的时候，如果用thead、tbody、tfoot标签的话，那么**数据可以边获取边显示**。如果不写，则必须等表格的内容全部从服务器获取完成才能显示出来。

- `colspan`：横向合并。例如`colspan="2"`表示当前单元格在水平方向上要占据两个单元格的位置。
- `rowspan`：纵向合并。例如`rowspan="2"`表示当前单元格在垂直方向上要占据两个单元格的位置。

## 内嵌框架标签

`<iframe>`是`<body>`的子标签。

```html
<iframe src="newHtml.html"></iframe>
```

属性：

- `src="subframe/the_second.html"`：内嵌的那个页面
- `width=800`：宽度
- `height=“150`：高度
- `scrolling="no"`：是否需要滚动条。默认值是true。
- `name="mainFrame"`：窗口名称。公有属性。

## 表单标签

```html
<form>
		名字：<input type="text" value="name"><br>
		密码：<input type="password" value="pwd" size="50"><br>
    性别：<input type="radio" name="gender" id="radio1" value="male" checked=""><label for="radio1">男</label>
			  <input type="radio" name="gender" id="radio2" value="female" >女<br>
		爱好：<input type="checkbox" name="love" value="eat">吃饭
			  <input type="checkbox" name="love" value="sleep">睡觉
			  <input type="checkbox" name="love" value="bat">打豆豆
</form>
```

表单标签`<form>`用于与服务器的交互，表单就是收集用户信息。

**`<form>`属性**：

- `name`：表单的名称，用于JS来操作或控制表单时使用；
- `id`：表单的名称，用于JS来操作或控制表单时使用；
- `action`：指定表单数据的处理程序，表单被提交到哪里。一般是PHP，如：action=“login.php”
- `method`：表单数据的提交方式，一般取值：get(默认)和post

**`<input>`属性**：

- - `text`（默认）
  - `password`：密码类型
  - `radio`：单选按钮，名字相同的按钮作为一组进行单选（单选按钮，天生是不能互斥的，如果想互斥，必须要有相同的name属性。name就是“名字”。 ）。非常像以前的收音机，按下去一个按钮，其他的就抬起来了。所以叫做radio。
  - `checkbox`：多选按钮，**name 属性值相同的按钮**作为一组进行选择。
  - `checked`：将单选按钮或多选按钮默认处于选中状态。当`<input>`标签设置为`type="radio"`或者`type=checkbox`时，可以用这个属性。属性值也是checked，可以省略。
  - `hidden`：隐藏框，在表单中包含不希望用户看见的信息
  - `button`：普通按钮，结合js代码进行使用。
  - `submit`：提交按钮，传送当前表单的数据给服务器或其他程序处理。这个按钮不需要写value自动就会有“提交”文字。这个按钮真的有提交功能。点击按钮后，这个表单就会被提交到form标签的action属性中指定的那个页面中去。
  - `reset`：重置按钮，清空当前表单的内容，并设置为最初的默认值
  - `image`：图片按钮，和提交按钮的功能完全一致，只不过图片按钮可以显示图片。
  - `file`：文件选择框。 提示：如果要限制上传文件的类型，需要配合JS来实现验证。对上传文件的安全检查：一是扩展名的检查，二是文件数据内容的检查。
- **`value="内容"`**：文本框里的默认内容（已经被填好了的）
- `size="50"`：表示文本框内可以显示**五十个字符**。一个英文或一个中文都算一个字符。 注意**size属性值的单位不是像素哦**。
- `readonly`：文本框只读，不能编辑。因为它的属性值也是readonly，所以属性值可以不写。 用了这个属性之后，在google浏览器中，光标点不进去；在IE浏览器中，光标可以点进去，但是文字不能编辑。
- `disabled`：文本框只读，不能编辑，光标点不进去。属性值可以不写。

`<label>`标签

让label标签的**for 属性值**，和 input 标签的 **id 属性值相同**，那么这个label和input就有绑定关系了。

**`<select>`下拉标签**

```html
<form>
    <fieldset>
        <legend>账号信息</legend>
        <select multiple="">
			<option>小学</option>
			<option>初中</option>
			<option selected="">高中</option>
			<option>大学</option>
			<option>研究生</option>
		</select>
    </fieldset>
	</form>
```

`<select>`属性：

- `multiple`：可以对下拉列表中的选项进行多选。属性值为 multiple，也可以没有属性值。也就是说，既可以写成 `multiple=""`，也可以写成`multiple="multiple"`。
- `size="3"`：如果属性值大于1，则列表为滚动视图。默认属性值为1，即下拉视图。

`<option>`属性：

- `selected`:已选中

  `<fieldset>`划分区域

**`<textarea>`属性**：

- `rows="4"`：指定文本区域的行数。
- `cols="20"`：指定文本区域的列数。
- `readonly`：只读。

## get提交和post提交的区别⭐

**GET方式**： 将表单数据，以"name=value"形式追加到action指定的处理程序的后面，两者间用"?"隔开，每一个表单的"name=value"间用"&"号隔开。 特点：只适合提交少量信息，并且不太安全(不要提交敏感数据)、提交的数据类型只限于ASCII字符。

**POST方式**： 将表单数据直接发送(隐藏)到action指定的处理程序。POST发送的数据不可见。Action指定的处理程序可以获取到表单数据。 特点：可以提交海量信息，相对来说安全一些，提交的数据格式是多样的(Word、Excel、rar、img)。

**Enctype：** 表单数据的编码方式(加密方式)，取值可以是：application/x-www-form-urlencoded、multipart/form-data。Enctype只能在POST方式下使用。

- Application/x-www-form-urlencoded：**默认**加密方式，除了上传文件之外的数据都可以
- Multipart/form-data：**上传附件时，必须使用这种编码方式**。