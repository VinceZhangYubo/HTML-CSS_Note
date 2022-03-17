# CSS



##  引入方式

- **行内样式**：在某个特定的标签里采用 style **属性**。范围只针对此标签。
- **内嵌样式**（内联样式）：在页面的 head 标签里里采用`<style>`**标签**。范围针对此页面。
- **外链样式**：引入外部样式表 CSS **文件**。这种引入方式又分为两种：
  - 3.1 采用`<link>`标签。例如：`<link rel = "stylesheet" type = "text/css" href = "a.css"></link>`
  - 3.2 采用 import 导入，必须写在`<style>`标签中。然后用类似于`@import url(a.css) ;`这种方式导入。

##  选择器

#### 基本选择器

- 标签选择器：选择的是页面上所有这种类型的标签，所以经常描述“**共性**”，无法描述某一个元素的“个性”。所有的标签都可以是选择器，无论有多少层嵌套都能选中。

  ```css
  p{ font-size:14px; }
  ```

- id 选择器：`#`针对某一个特定的标签来使用，只能使用一次。HTML页面不能出现相同的id。

  ```css
  #mytitle{ border:3px dashed green; }
  ```

- class 选择器：`.`同一个标签可以使用多个类选择器，用**空格**隔开。

  注：JavaScript 要通过 id 属性得到标签，CSS层面尽量不用 id。**类上样式，id 上行为**。

- 通用选择器（通配符）：`*`针对所有的标签都适用（不建议使用），IE 有些版本不支持，增加网站客户端负担。效率不高，如果页面上的标签越多，效率越低，所以页面上不能出现这个选择器。

#### 高级选择器

- 后代选择器：空格隔开。对于`E F`这种格式，表示**所有属于 E 元素后代的 F 元素**，只要是后代就可，不必是儿子，后续还可嵌套class和id选择器。

  ```css
  h3 b .one{
  	color: red;
  }
  ```

- 交集选择器：标签和class或id的交集元素。`div.special`：元素既属于div标签，又属于special的class；`div#special`：元素既属于div标签，又属于special的id。中间无空格，没有后代选择器的嵌套关系，只有相交关系，同属于两类。

- 并集选择器：逗号隔开，三种基本选择器都可以放进来。

  ```css
  p,h1,.title1,#one {
      color: red;
  }
  ```

- 子代选择器：（IE7开始兼容，IE6不兼容），只能选择儿子。

  ```css
  div > p {
      color: red;
  }
  ```

- 相邻兄弟选择器：`div+p` 选中div后面相邻的第一个p
- div~p: 选中的div后面所有的p

#### 伪类选择器

伪类：同一个标签，不同状态有不同的样式。

（1）**静态伪类**：只能用于**超链接**的样式。如下：

- `:link` 超链接点击之前
- `:visited` 链接被访问过之后

PS：以上两种样式，只能用于超链接。

（2）**动态伪类**：针对**所有标签**都适用的样式。如下：

- `:hover` “悬停”：鼠标放到标签上的时候
- `:active` “激活”： 鼠标点击标签，但是不松手时。
- `:focus` 是某个标签获得焦点时的样式（比如某个输入框获得焦点）

**超链接的四种状态**

a标签有4种伪类（即对应四种状态）如下：

- `:link` “链接”：超链接点击之前
- `:visited` “访问过的”：链接被访问过之后
- `:hover` “悬停”：鼠标放到标签上的时候
- `:active` “激活”： 鼠标点击标签，但是不松手时。

在CSS里必须按照这个顺序写，love hate，a:link 、a:visited 、a:hover 、a:active。且一定要将a标签写在前面，将`:link、:visited、:hover、:active`这些伪类写在后面。

**`a{}`和`a:link{}`的区别：**

- `a{}`定义的样式针对所有的超链接(包括锚点)
- `a:link{}`定义的样式针对所有写了href属性的超链接(不包括锚点)

a:link 、a:visited一般一起绑定书写，也可省略在a标签里不用写。	

**思维拓展**：Vue的Element中el-table里面做的选中行的阴影可能底层就是用的hover

#### CSS3选择器

- 属性选择器

```text
^：开头  $：结尾  *：包含
```

格式：

`E[title]` 选中页面的E元素，并且E存在 title 属性即可。

`E[title="abc"]`选中页面的E元素，并且E需要带有title属性，且属性值**完全等于**abc。

`E[attr~=val]` 

`E[attr|=val]` 

`E[title^="abc"]` 选中页面的E元素，并且E需要带有 title 属性,属性值以 abc 开头。

`E[title$="abc"]` 选中页面的E元素，并且E需要带有 title 属性,属性值以 abc 结尾。

`E[title*="abc"]` 选中页面的E元素，并且E需要带有 title 属性,属性值任意位置包含abc。

- 结构伪类选择器

`E:first-child` 匹配父元素的第一个子元素E。

`E:last-child` 匹配父元素的最后一个子元素E。

`E:nth-child(n)` 匹配父元素的第n个子元素E。**注意**，盒子的编号是从`1`开始算起，不是从`0`开始算起。

`E:nth-child(odd)` 匹配奇数

`E:nth-child(even)` 匹配偶数

`E:nth-last-child(n)` 匹配父元素的倒数第n个子元素E。

注：**父元素指E元素的父元素为参考。且以上选择器中所选到的元素的类型，必须是指定的类型E，如果选不中，则无效。**

- 伪元素选择器

`E::before` 设置在 元素E 前面（依据对象树的逻辑结构）的内容，配合content属性一起使用。

`E::after` 设置在 元素E 后面（依据对象树的逻辑结构）的内容，配合content属性一起使用。

```css
span::after {
	content: "永不止步";
}
```

可以实现类似`span`的效果，添加的伪元素是行内元素，如果设置宽高需要先转化为block。

## CSS3继承性、层叠性和优先级

#### 继承性

- 关于文字样式的属性，都具有继承性。这些属性包括：color、 text-开头的、line-开头的、font-开头的。
- 关于盒子、定位、布局的属性，都不能继承。

#### 层叠性

当多个选择器，选择上了某个元素的时候，要按照如下顺序统计权重：

- id 选择器>类选择器、属性选择器、伪类选择器>标签选择器、伪元素选择器

- 行级样式 > 内嵌样式表 > 外部样式表（就近原则）

**例：**所有人当中一个为红其他为蓝。

为了达到这种效果，即为了防止权重不够，比较稳妥的做法是：把第二个样式表照着第一个样式表来写，在此基础上，给第二个样式表再加一个class权重。

**`!important`**

```css
font-size:60px !important;
```

- `!important`提升的是一个属性而不是一个选择器
- `!important`无法提升继承的属性，应该写在直接作用的标签里面
- `!important`不影响就近原则

## 盒模型

![标准盒子模型](.\picture\CSSBoxModel.jpg)

CSS盒模型和IE盒模型的区别：

- 在 **标准盒子模型**中，width 和 height 指的是内容区域的宽度和高度。增加内边距、边框和外边距不会影响内容区域的尺寸，但是会增加元素框的总尺寸。
- **IE盒子模型**中，width 和 height 指的是内容区域+border+padding的宽度和高度。



网页最大的盒子是`<document>`与`<body>`之间的margin是8px，所以`<body>`不是占据了页面全部。

- **小属性迭代大属性**，反之则无效

```css
padding: 20px;
padding-left: 30px;
```

上面左侧padding可以迭代覆盖成30px，先写padding-left则不行。

- 盒模型的每个属性都可以拆分成三个方向的小属性：

```css
border: 10px solid red;
border-width:10px;    //边框宽度
border-style:solid;   //线型
border-color:red;     //颜色。
```

#### 盒子大小box-sizing

外加方式（默认）

`box-sizing: content-box;`：盒子的宽高是内容区域的宽高，改变padding和border不会改变content大小，盒子总宽高改变。

内减模式

`box-sizing: border-box;`：包括padding和border，设置的宽高就是盒子的宽高，改变padding和border会改变content的宽高。

##  文档流

#### 标准流

- 空白折叠：无论多少个空格、换行、tab，都会折叠为一个空格
- 高矮不齐，底边对齐
- 一行写不完，自动换行

#### 行内元素和块级元素

##### 行内元素

- 与其他行内元素并排；
- 不能设置宽、高。默认的宽度，就是文字的宽度。

##### 块级元素

- 霸占一行，不能与其他任何元素并列；
- 能接受宽、高。如果不设置宽度，那么宽度将默认变为父亲的100%。

文本级标签：p、span、a、b、i、u、em

容器级标签：div、h系列、li、dt、dd

- 行内元素：除了p之外，所有的文本级标签，都是行内元素。p是个文本级，但是是个块级元素。
- 块级元素：所有的容器级标签都是块级元素，还有p标签。

##### 互相转化

```css
display: inline; //转为行内元素
display: block; //转为块级元素
```

盒子居中：

```css
margin 0 auto;
```

- 只有标准流的盒子，才能使用`margin:0 auto;`居中。当一个盒子浮动了、绝对定位了、固定定位了，都不能使用
- 使用`margin:0 auto;`的盒子，必须有有明确的width。（如果没有width，那么它的width就是霸占整行，没有意义）
- `margin:0 auto;`是让盒子居中，不是让盒子里的文本居中。文本的居中，要使用`text-align:center;`
- **要善于使用父亲的padding而不是儿子的margin**

#### 浮动

##### 浮动特性

```css
float: left;
float: right;
```

- 浮动的元素脱离标准流限制，不区分行内和块级，都可以设置宽高
- 浮动的元素互相贴靠
- 浮动元素有“字围”效果，所以初期布局就要想好：要浮动，所有同级元素都要浮动
- 收缩：不设置width自动收缩为内容的宽度
- parent div width < sons div width 之和，超出width的sons往下掉

##### 清除浮动

- 父元素设置高度：一个元素要浮动，它的祖先元素要有高度。**有高度的盒子才能关住浮动**。实际项目不能一直设置
- `clear:both`清除两侧浮动。缺点：所在的标签margin属性失效，一般所用方式。
- 隔墙法：中间加一个div设置为`clear:both`，并设置height以曲线救国达到margin效果
- `overflow:hidden`：本意清除盒子外的浮动。但一个父亲不能被自己浮动的儿子，撑出高度。但是，只要给父亲加上`overflow:hidden`; 那么，父亲就能被儿子撑出高了。这是一个偏方。

#### 定位

##### 默认static

还是相当于标准流

##### 相对定位 relative↘

相对于原来位置调整，用于盒子微调。

```css
position: relative;
left: 50px;/*横坐标：正值表示向右偏移，负值表示向左偏移*/
top: 50px;/*纵坐标：正值表示向下偏移，负值表示向上偏移;*/
/*
可以理解为盒子距离左边50px，距离上边50px，所以就相应向右下方移动了
*/
```

相对定位不脱离标准文档，不会挤走位置。相对定位用于：1. 微调元素；2.做绝对定位的参考，子绝父相。

##### 绝对定位absolute

定义横纵坐标。原点在父容器的左上角或左下角。横坐标用left表示，纵坐标用top或者bottom表示。绝对定位脱离标准文档。

**绝对定位的参考点⭐**

top：页面左上角，而不是浏览器左上角；

bottom：浏览器**首屏窗口尺寸**，对应页面的左下角

![绝对定位的bottom](.\picture\绝对定位的bottom.png)

- **如果绝对定位的父元素是定位元素，则绝对定位的子元素的参考点则参考父元素。**不仅是一级父元素，向上的祖元素只要有定位元素，就会被绝对定位的子元素拿来做参考点。

- “子绝父相”可以保证父亲没有脱标，儿子脱标在父亲的范围里面移动。
- 绝对定位的子元素，无视被参考元素的padding，不管padding有多厚，参考点定位到border。

**绝对定位的子元素在父元素中居中方法**

```css
div {
	width: 600px;
	height: 60px;
	position: absolute;  绝对定位的盒子
	left: 50%;           首先，让左边线居中
	top: 0;
	margin-left: -300px;  然后，向左移动宽度（600px）的一半
}
```

方法：left:50%; margin-left:负的宽度的一半

##### 固定定位fixed

相对浏览器窗口，怎么滚动都不动。（IE6不兼容）

用途：右下角的“返回到顶部”；顶端固定的导航条

##### 粘性定位sticky

相对定位和固定定位的结合，主要用于对scroll事件的监听。对移动端兼容不好。

在滑动过程中，某个元素距离其父元素的距离达到sticky粘性定位的要求时(比如`top：100px`) ，`position: sticky`这时的效果相当于fixed定位，固定到屏幕适当位置。

```css
.div {
	position: sticky;
	top: 100px;
}
```

- 父元素不能`overflow:hidden`或者`overflow:auto`属性。

- 必须指定top、bottom、left、right4个值之一，否则只会处于相对定位

- 父元素的高度不能低于sticky元素的高度

- sticky元素仅在其父元素内生效

##### z-index的层叠规则⭐️

- 只有定位了的元素才能使用，没有z-index，定位的元素压住没有定位的元素，而定位的元素中默认代码越靠下越显示在页面前面
- z-index从0开始没有单位，越大越显示在页面前面
- 层级从父：z-index of A > z-index of B, then even z-index of a < z-index of b, a在b前面

**CSS样式案列讲解和处理技巧细节：**[09-CSS案例讲解：博雅互动 | 千古前端图文教程 (qianguyihao.com)](https://web.qianguyihao.com/02-CSS基础/09-CSS案例讲解：博雅互动.html#内容区域的制作)

## CSS3

#### 边框圆角和边框阴影

边框圆角

```css
border-radius: 50% //圆
border-radius: 10% //圆角矩形
```

边框阴影

```css
box-shadow: 水平偏移 垂直偏移 模糊程度（不能为负） 阴影大小 阴影颜色 inset（内阴影，不写默认外）

box-shadow: 15px 21px 48px -2px #666;
```

#### 动画、过渡和渐变

动画：[12-CSS3属性详解：动画详解 | 千古前端图文教程 (qianguyihao.com)](https://web.qianguyihao.com/02-CSS基础/12-CSS3属性详解：动画详解.html#前言)

#### 字体

替换字体、伪元素插入图标等：[14-CSS3属性详解：Web字体 | 千古前端图文教程 (qianguyihao.com)](https://web.qianguyihao.com/02-CSS基础/14-CSS3属性详解：Web字体.html#前言)

## Flex布局

`display: flex;`

Flex布局优势：flex布局的子元素不会脱离文档流，不会像浮动一样涉及各种BFC、清除浮动等；

Flex布局劣势：不支持IE9及以下版本，所以面对海量用户的大型网站还不能尝试。

#### 弹性布局

- **弹性盒子**：指的是使用 `display:flex` 或 `display:inline-flex` 声明的**父容器**。

  **子元素/弹性元素**：指的是父容器里面的子元素们（父容器被声明为 flex 盒子的情况下）

- 默认**主轴**从左向右，**侧轴**从上向下。`flex-direction`设置子元素排列方向。

```css
flex-direction: row; //默认
flex-direction: column; //从上到下
flex-direction: row-reverse; //横向反向
flex-direction: column-reverse; //纵向反向
```

- `flex-wrap: wrap/nowrap`控制子元素溢出时换行处理

- `justify-content`控制子元素在主轴上的排列方式

  - `flex-start` 从主轴的起点对齐（默认值）
  - `flex-end` 从主轴的终点对齐
  - `center` 居中对齐
  - `space-around` 在父盒子里平分
  - `space-between` 两端对齐边界 平分

  <img src="C:\Users\yubo.zhang\Desktop\微信截图_20220317164453.png" alt="微信截图_20220317164453" style="zoom:60%;" />

- `align-items`侧轴对齐方式

![20190821_2101](C:\Users\yubo.zhang\Desktop\20190821_2101.png)



- ❗ BFC 和 IFC 机制
  - ⭐️ 响应式布局
    - 媒体查询
    - Flex 布局
    - Grid 布局
    - 瀑布流

## 浏览器的兼容性问题

> 可以用`IETester`这个软件测一下 CSS 在各个版本 IE 浏览器上的显示效果。

为了测试浏览器 CSS 3 的兼容性，可以在网上搜"css3 机器猫"关键字，然后在不同的浏览器中打开如下链接：

- http://www1.pconline.com.cn/pcedu/specialtopic/css3-doraemon/

坚持**渐进增强**的原则：**让低版本浏览器能正常访问页面，高版本的浏览器用户体验更好**。

#### 各种选择器(浏览器兼容性)

IE6层面兼容的选择器： 标签选择器、id选择器、类选择器、后代、交集选择器、并集选择器、通配符。如下：

```text
p
#box
.spec
div p
div.spec
div,p
*
```

IE7能够兼容的：儿子选择器、下一个兄弟选择器。如下：

```text
div>p
h3+p
```

IE8能够兼容的：

```text
ul li:first-child
ul li:last-child
```

#### CSS属性的IE6兼容

IE6留了一个**后门**：只要给CSS属性之前，加上**下划线**，这个属性就是IE6的专有属性。

于是乎，为了解决微型盒子（即height小于12px）的问题，正确写法：（注意不要忘记下划线）

```css
height: 10px;
_font-size:0;
```

#### 私有前缀

适配不同浏览器

```css
 -webkit-: 谷歌 苹果
 -moz-:火狐
 -ms-：IE
 -o-：欧朋

background: -webkit-linear-gradient(left, green, yellow);
background: -moz-linear-gradient(left, green, yellow);
background: -ms-linear-gradient(left, green, yellow);
background: -o-linear-gradient(left, green, yellow);
background: linear-gradient(left, green, yellow);
```

#### 渐进增强和优雅降级

**渐进增强（Progressive Enhancement）**（向上兼容）：一开始就针对低版本浏览器进行构建页面，完成基本的功能，然后再针对高级浏览器进行效果、交互、追加功能达到更好的体验。

**优雅降级（Graceful Degradation）**（向下兼容）：一开始就构建站点的完整功能，然后针对浏览器测试和修复

参考链接：

- [渐进增强 VS 优雅降级 | 简书](https://www.jianshu.com/p/d313f1108862)
- [渐进增强和优雅降级之间的不同（面试题目）](https://www.cnblogs.com/iceflorence/archive/2017/03/27/6625466.html)

选择哪种开发方式主要取决于客户端的用户主要是哪种类型，如果年轻人居多，客户端版本高占比高就选择优雅降级方式；反之，低版本客户端占比高，为了保证内容显示优先，选择渐进增强的方式。