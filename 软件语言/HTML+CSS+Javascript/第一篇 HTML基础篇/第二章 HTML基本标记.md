[toc]

## HTML 页面主体标记

- `<body></body>` 标签包含的标记有：网页的背景颜色、文字属性设置和链接设置等。
- 属性总是在**开始标签**中定义。
- **在 HTML 4.01 中，所有 body 元素的 “呈现属性” 均不被赞成使用。
  在 XHTML 1.0 Strict DTD 中，所有 body 元素的 “呈现属性” 均不被支持。**

### 定义网页背景色

- 使用 `bgcolor` 属性定义整个 HTML 文档的背景颜色。
- 基本语法
  `<body bgcolor = "背景颜色">`

- 背景颜色有三种表示方法
	- 使用颜色名指定，例如 red、 green、 blue 等。
	- 使用十六进制格式数据值 #RRGGBB 来表示。
	- 使用 `rgb(x, x, x)` 指定。

### 设置背景图片

- 使用 `background` 属性定义 HTML 文档的背景图片。
- 基本语法
  `<body background = "URL">`

### 设置文字颜色

- 使用 `text` 属性定义 `<body></body>` 之间所有文本的颜色。
- 基本语法
  `<body text = "文字的颜色">`

### 设置链接文字的颜色

- 使用 `link` 属性定义超链接文字**点击前**的颜色。
- 使用 `alink` 属性定义超链接文字**被点击时**的颜色。
- 使用 `vlink` 属性定义超链接文字**点击后**的颜色。
- 基本语法
  `<body link = "点击前的颜色" alink = "被点击时的颜色" vlink = "点击后的颜色">`

### 设置页面边距

- HTML 默认设置的 topmargin、leftmargin 值都是 **12**。
- 使用 `topmargin` 属性设置**到顶端的距离**。
- 使用 `leftmargin` 属性设置**到左边的距离**。
- 使用 `rightmargin` 属性设置**到右边的距离**。
- 使用 `bottommargin` 属性设置**到底边的距离**。
- 基本语法
  `<body topmargin = "顶端" leftmargin = "左边" rightmargin = "右边" bottommargin = "底边">`

## head 部分标记

- `<head></head>` 标记中包含的内容基本上描述了所属页面的基本属性，包括标题、字符集、站点信息、网站作者信息、站点描述、站点关键字、刷新及跳转、样式表链接以及其他一些有用的附加功能。

### 标题标记

- 使用 `<title></title>` 标记定义 HTML 文档的标题。
- 基本语法
```xml
<head>
	<title>标题内容</title>
</head>
```

> 标题只有一个，且只能定义在 `<head></head>` 之间。

### meta 标记

参考资料：[W3School meta 标签](http://www.w3school.com.cn/tags/tag_meta.asp)

- `<meta>` 标记用于提供有关页面的描述信息。
- 包含属性
	- `name` 属性
		- 通过一些特定的值对页面进行描述。
	- `http-equiv` 属性
		- 服务器在发送实际的文档之前先在要传送给浏览器的 MIME 文档头部包含名称/值对。
	- `content` 属性
		- 提供了另一属性需要的值。
	- `scheme` 属性
		- 指定要用来翻译属性值的方案。
- **在 HTML 中，<meta> 标签没有结束标签。
  在 XHTML 中，<meta> 标签必须被正确地关闭。**

#### 定义页面关键字

- 当用关键字搜索网站时，如果网页中包含该关键字，就可以在搜索结果中列出来。
- 基本语法
  `<meta name = "keywords" content = "关键字" />`

#### 定义页面描述

- 为搜索引擎提供了关于这个网页的总括性描述。
- 基本语法
  `<meta name = "description" content = "设置页面描述" />`

#### 定义编辑工具

- 编辑工具只在页面的代码中可以看到，并不会显示在浏览器中。
- 基本语法
  `<meta name = "generator" content = "编辑工具名称" />`

#### 定义作者信息

- 作者信息只在页面的代码中可以看到，并不会显示在浏览器中。
- 基本语法
  `<meta name = "author" content = "作者信息" />`

#### 定义网页文字及语言

- 设置语言的编码方式。
- 基本语法
  `<meta http-equiv = "content-type" content = "text/html; charset = 字符集类型" />`

#### 定义网页的定时跳转

- 完成页面自身的刷新，也可以实现页面间的跳转过程。
- 基本语法
  `<meta http-equiv = "refresh" content = "跳转时间" />`
  `<meta http-equiv = "refresh" content = "跳转时间; URL = 跳转地址" />`

- 跳转时间的单位为**秒**。

> [更多内容点击这里](http://www.haorooms.com/post/html_meta_ds)

---

本章实例代码：

Test.html
```xml
<!DOCTYPE html>
<html>
	<head>
		<title>第二章 HTML基本标记</title>
		<meta name = "keywords" content = "HTML,基本标记" />
		<meta name = "description" content = "HTML基本标记" />
		<meta name = "generator" content = "HBuilder" />
		<meta name = "author" content = "Remilitarize" />
		<meta http-equiv = "content-type" content = "text/html; charset = UTF-8" />
		<meta http-equiv = "refresh" content = "60" />
	</head>
	<body text = "black" bgcolor = "aqua" link = "red" alink = "yellow" vlink = "white">
		<p>现在是 aqua 颜色的背景。</p>
		<p>字体的颜色是 black</p>
		<p>这个页面 60 秒就会刷新一次。</p>
		<a href = "#">这个超链接用来查看文字颜色变化</a>
	</body>
</html>
```
