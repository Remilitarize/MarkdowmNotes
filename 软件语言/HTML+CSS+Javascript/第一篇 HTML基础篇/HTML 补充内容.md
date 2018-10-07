[toc]

## 标题的定义

- 使用 `<h1></h1>` 等标签定义标题。
- 基本格式
```xml
<h1> 一级标题 </h1>
<h2> 二级标题 </h2>
<h3> 三级标题 </h3>
<h4> 四级标题 </h4>
<h5> 五级标题 </h5>
<h6> 六级标题 </h6>
```

- 可选属性（不赞成使用）
	- `align` 对齐方式

> 建议仅当做文章的标题是使用标题标记。

## 删除线

- 使用 `<del></del>` 标记为文字添加删除线。

> 不赞成使用 `<s></s>` 和 `<strike></strike>` 添加删除线。

## 引文、引用标记

### abbr 标记

- 使用 `<abbr></abbr>` 标记为缩写补充全称。
- 基本语法
	- `<abbr title = "Operator System"> OS </abbr>`

### address 标记

- 使用 `<address></address>` 标记添加作者联系方式。
- 通常以**斜体**显示。

### q 标记

- 使用 `<q></q>` 标记表示引用短的文字。
- 通常会将引用的文字用**双引号**括起来。

### blockquote 标记

- 使用 `<blockquote></blockquote>` 标记表示引用一段文字。
- 通常会将整段文字**缩进**。

## 计算机代码标记

- 使用 `<kbd></kbd>` 标记表示从键盘输入的内容。
- 使用 `<samp></samp>` 标记表示输出的内容。
- 使用 `<code></code>` 标记表示代码示例。
	- 不保留多余的空格和折行。
- 使用 `<pre></pre>` 标记表示代码示例。
	- 保留多余的空格和折行.
- 使用 `<var></var>` 标记表示一个数学变量。

## 条件注释

```xml
<!--[if IE 8]>
    .... some HTML here ....
<![endif]-->
```

- 解释
	- 当使用的是 IE 8 浏览器时，执行下面的 HTML。

## 列表

### 无序列表

- 使用 `<ul></ul>` 定义一个无序列表。
- 列表每一项用 `<li></li>` 进行表示。
- 基本语法
```xml
<ul>
	<li> item 1 </li>
	<il> item 2 </il>
	...
</ul>
```

### 有序列表

- 使用 `<ol></ol>` 定义一个有序列表。
- 列表每一项用 `<li></li>` 进行表示。
- 基本语法
```xml
<ol>
	<li> item 1 </li>
	<li> item 2 </li>
	...
</ol>
```

### 自定义列表

- 使用 `<dl></dl>` 定义一个自定义列表。
- 列表的每一个项用 `<dt></dt>` 进行表示，每一项的定义用 `<dd></dd>` 进行定义。
- 基本语法
```xml
<dl>
	<dt> item 1 </dt>
		<dd> content 1 </dd>
	<dt> item 2 </dt>
		<dd> content 2 </dd>
	...
</dl>
```

## div 和 span 标记

- 块元素
	- 块元素在浏览器中显示通常会以**新的一行**作为开始。
	- 例如：`<p></p>` `<table></table>`
- 内联元素
	- 内联元素在浏览器中显示通常**不会以新行**作为开始。
	- 例如：`<b></b>` `<a></a>` `<img></img>`
- div 标记
	- 使用 `<div></div>` 定义一个块级元素的容器。
	- 通常用于文档布局。
- span 标记
	- 使用 `<span></span>` 定义一个内敛元素的容器。

## 颜色

请查看资料：[W3School HTML 颜色](http://www.w3school.com.cn/html/html_colors.asp)

[W3School HTML 颜色名](http://www.w3school.com.cn/html/html_colornames.asp)
