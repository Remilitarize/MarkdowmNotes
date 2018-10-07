[toc]

## 插入其他标记

参考资料：[菜鸟联盟 字符实体](http://www.runoob.com/html/html-entities.html)

- HTML 中的预留字符必须被替换为字符实体。
	- 一些特殊的以及键盘上无法输入的字符同样可以通过字符实体表示出来。
	- **`<` `>`** 这两个字符在 HTML 中会被认为是标签，需要用字符实体代替。
	- 浏览器总是截短 HTML 中的空格，如果想要输出多个空格，需要用字符实体表示。
- 字符实体格式
	- `&entity_name;`
	- `&#entity_number;`
- 常用字符实体

|字符名称|字符样式|实体名称|实体数字|
|-|-|-|-|
|空格|&nbsp;|`&nbsp;`|`&#160;`|
|大于号|&gt;|`&gt;`|`&#62;`|
|小于号|&lt;|`&lt;`|`&#60;`|

> 更多字符实体参照：[W3School 字符实体](http://www.w3school.com.cn/tags/html_ref_symbols.html)

## 设置文字的格式

- 使用 `<font></font>` 标记控制字体、字号和颜色等属性。
- **在 HTML 4.01 中，font 元素不被赞成使用。
  在 XHTML 1.0 Strict DTD 中，font 元素不被支持。**

### 设置字体

- 使用 **`face`** 属性规定字体的样式。
- 设置的字体效果必须在浏览器中安装相应的字体后才能正确浏览。
- 基本语法
	- `<font face = "字体样式"> 内容 </font>`

### 设置字号

- 使用 **`size`** 属性规定文字的字号。
- 字体大小有相对和绝对两种方式
	- 1 到 7 个等级，1 级最大，7 级最小，默认的字体大小是 **3 号字**。
	- 用具体的数值表示字体大小。
- 基本语法
	- `<font size = "字号"> 内容 </font>`

### 设置文字颜色

- 使用 **`color`** 属性规定文字的颜色。
- 基本语法
	- `<font color = "颜色"> 内容 </font>`

### 设置粗体、斜体、下划线

- 使用 **`<b></b>`** 或 **`<strong></strong>`** 标签使字体加粗。
- 使用 *`<i></i>`* 或 *`<em></em>`* 或 *`<cite></cite>`* 标签使字体变为斜体。
- 使用 ***`<u></u>`*** 为文字加下划线。**（不赞成使用）**
- 区别
	- `<b></b>` 和 `<i></i>` 属于**样式标签**，即从样式上加粗加斜，建议不要使用或在 CSS 中设置。
	- `<strong></strong>` 和 `<em></em>` 属于**语义标签**，前者表示**重点**，后者表示**强调**。
	- `<cite></cite>` 通常用于**引用文献**。
- 基本语法
```xml
<b> 这是粗体 </b>
<strong> 这是重点 </strong>
<i> 这是斜体 </i>
<em> 这是强调 </em>
<cite> 这是引用 </cite>
<u> 这是下划线 </u>
```

### 设置上标与下标

- 使用 **`<sub></sub>`** 标签将文字下标。
- 使用 **`<sup></sup>`** 标签将文字上标。
- 基本语法
```xml
A<sub>1</sub>, A<sub>2</sub>, ..., A<sub>n</sub>
A<sup>2</sup> + B<sup>2</sup> = C<sup>2</sup>
```

## 设置段落的格式

- 直接在 HTML 文档中放置一段文字是可以显示出来的。
- 使用段落标记可以让文字按照格式显示出来。

### 段落标记

- 使用 **`<p></p>`** 标记表示段落。
- 段落标记会在文字的前后加上一块空白。
- 基本语法
	- `<p> 文字 </p>`

### 段落的对齐属性

- 使用 **`align`** 属性规定文字的对齐方式。
- **在 HTML 4.01 中，所有 p 元素的呈现属性均不被赞成使用。
  在 XHTML 1.0 Strict DTD 中，所有 p 元素的呈现属性均不被支持。**
- 基本语法
	- `<p align = "对齐方式"> 文字 </p>`

|属性值|含义|
|-|-|
|left|左对齐|
|right|右对齐|
|center|居中对齐|

### 不换行标记

- 使用 **`<nobr></nobr>`** 标记规定一段较长文字不被自动换行。
- 基本语法
	- `<nobr> 文字 `</nobr>`

> 改标签已经被废弃，建议使用 CSS 设置。

### 换行标记

- 使用 **`<br />`** 标记将标记后面的文字换行显示。
- 由于换行标记没有元素，需要在开始标签内结束。
- 基本语法
	- `这里换行了。<br />已换行。`

## 水平线标记

- 使用 **`<hr />`** 标记在 HTML 文档中添加一条水平线。
- 由于水平线标记没有元素，需要在开始标签内结束。
- 基本语法
	- `水平线上面<hr />水平线下面`
- **在 HTML 4.01 中，hr 元素的所有呈现属性均不被赞成使用。
  在 XHTML 1.0 Strict DTD 中，hr 元素的所有呈现属性均不被支持。**

### 设置水平线宽度与高度属性

- 使用 **`width`** 和 **`height`** 属性规定水平线的宽度与高度。
- 宽度属性允许用**与窗口大小的百分比**表示，或是具体的像素值。
- 高度只能用具体的像素值表示。
- 基本语法
	- `<hr width = "像素值或百分比" heignt = "像素值" />`

### 设置水平线的颜色

- 使用 **`color`** 属性规定水平线的颜色。
- 基本语法
	- `<hr color = "颜色" />`

### 设置水平线的对齐方式

- 使用 **`align`** 属性规定水平线的对齐方式。
- 默认对齐方式为 `center`.
- 基本语法
	- `<hr align = "对齐方式" />`

### 利用水平线去掉阴影

- 使用 **`noshade`** 属性去掉水平线的阴影。
- 默认水平线带有阴影。
- 基本语法
	- `<hr noshade = "noshade" />`

## 使用 marquee 设置滚动效果

- 使用 **`<marquee></marquee>`** 标记设置一段滚动字幕。
- **在 HTML 5 中已被废止，建议使用 CSS 实现**。
- 基本属性
	- behavior 设置滚动方式
		- alternative：来回滚动
		- scroll：重复滚动
		- silde：不重复滚动
	- bgcolor 设置字幕的背景颜色
	- direction 设置字母的滚动方向
		- up：向上
		- down：向下
		- left：向左
		- right：向右
	- width 设置滚动字幕的宽度
	- height 设置滚动字幕的高度
	- loop 设置滚动次数
		- 正整数 N：滚动 N 次
		- -1：无限滚动（默认）
	- scrollamount 设置滚动速度
	- scrolldelay 设置两次滚动之间的延时
	- hspace 设置字幕左右的空白大小
	- vspace 设置字幕上下的空白大小
- 基本事件
	- `mouseOver = "this.start()"` 当鼠标放上时开始
	- `mouseOut = "this.out()"` 当鼠标移开时停止

---

本节课代码
Test.html
```xml
<!DOCTYPE html>
<html>
<head>
       <meta name="content_type" content="text/html; charset = utf-8" />
       <meta name="generator" content="visual studio 2015" />
       <meta name="author" contnent="Remilitarize" />
       <title>第三章 用 HTML 设置文字、段落与列表</title>
</head>
<body>
    <h2>插入其他标记</h2>
    <p>
        每 两 个 字 中 间 加 了 一 个 空 格
        <br />
        每  两  个  字  中  间  加  了  两  个  空  格
        <br />
    </p>
    <p>
        3 < 5<br/>
        5 > 3<br />
    </p>
    <hr />
    <h2>设置文字的格式</h2>
    <h3>粗体、斜体、下划线</h3>
    <p>
        <b>我是粗体</b><br />
        <strong>我是重要</strong><br />
        <i>我是斜体</i><br />
        <em>我是强调</em><br />
        <cite>我是引用</cite><br />
        <u>我是下划线</u>
    </p>
    <h3>使用 font 标记</h3>
    <p>
        <font face="宋体">当前字体为宋体</font>
        <font fase="楷体">当前字体为楷体</font>
        <br />
        <font size="20">当前字体字号为 20</font>
        <br />
        <font color="yellow">当前字体颜色为 yellow</font>
        <br />
    </p>
    <h3>上下标</h3>
    <p>
        C<sub>2</sub>H<sub>5</sub> COOH 酒精的化学式<br />
        a<sup>2</sup> + b<sup>2</sup> = c<sup>2</sup> 勾股定理
    </p>
    <hr />
    <h2>设置段落格式</h2>
    <h3>p 标记</h3>
    <p align="center">居中对齐</p>
    <br />
    <p align="left">左对齐</p>
    <br />
    <p align="right">右对齐</p>
    <br />
    <h3>换行与不换行</h3>
    <p>
        <nobr>这一行不会被自动换行</nobr>
    </p>
    <br />
    <p>
        换行之前<br />换行之后
    </p>
    <hr />
    <h2>水平线</h2>
    <hr color="blue" /><p>蓝色水平线</p>
    <hr noshade="noshade" /><p>没有阴影水平线</p>
    <hr align="left" /><p>左侧对齐</p>
    <hr align="right" /><p>右侧对齐</p>
    <hr align="center" /><p>居中对齐</p>
</body>
</html>
```
