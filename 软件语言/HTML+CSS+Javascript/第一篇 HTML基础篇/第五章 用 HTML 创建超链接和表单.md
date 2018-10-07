[toc]

## 超链接的基本概念

- 超链接是从一个网页或文件到另一个网页或文件的链接。
- 超链接由**源地址文件**和**目标地址文件**构成。
- 当访问者单机超链接时，浏览器会从相应的目标地址检索网页并显示在浏览器中。
- 如果目标地址不是网页而是其他类型的文件，浏览器会中自动调用本机上的相关程序打开访问的文件。

## 创建基本超链接

- 使用 `<a></a>` 标记添加一个超链接。
- 基本语法
	- `<a> 描述文字 </a>`
- 可选属性
	- `href`：指向跳转的目标文件地址或锚点。
	- `target`：规定链接的目标窗口。
		- \_blank：在新页面打开
		- \_self：在当前页面打开（默认）
		- \_top：在顶级窗口中打开
		- \_parent：在父级窗口中打开
	- `name`：设置锚点名称
		- HTML 5 不支持 name 属性
	- `id`：设置锚点名称
		- 推荐使用 id 属性

## 创建图像的超链接

- 将 `<img></img>` 放在 `<a></a>` 描述文字位置即可。
- 基本语法
	- `<a href = "目标地址"><img src = "图像的 URL" /></a>`

### 设置图像热区链接

参考资料：[W3School area 标签](http://www.w3school.com.cn/tags/tag_area.asp)

- 将图像的一部分或多个部分分别成为不同的链接。
- 基本语法
```xml
<img usemap = "#热区名称" />
<map name = "热区名称">
	<area alt = "当不正常显示时替代的文字" />
</map>
```

- map 标记的属性
	- `id`：map 的唯一标识
	- `name`：img 规定的名称
- area 标记的属性
	- 必需属性
		- `alt`：当图像不正常显示时替代的文字
	- 可选属性
		- `shape`：规定热区的形状
		- `coords`：规定热区的坐标
		- `href`：规定热区指向的目标地址或锚点
		- `nohref = "nohref"`：规定该部分热区没有相关的链接
		- `target`：规定链接的目标窗口。

|shape 属性值|shape 属性含义|coords 属性值|
|-|-|-|
|rect|矩形|x1, y1, x2, y2|
|circ|圆形|x, y, radius|
|poly|多边形|x1, y1, x2, y2, ...|
|default|默认|（整个图像）|

## 创建锚点链接

### 创建锚点

- 使用 `name` 或 `id` 属性创建锚点。
- 基本语法
	- `<a name = "锚点名称"> 文字 </a>`
	- `<a id = "锚点名称"> 文字 </a>`
- 说明
	- 只能包含**小写的 ASCII 码和数字**。
	- **不能以数字开头**。
	- 允许有无数个锚点，但不允许有相同名称的锚点。

> HTML 5 不支持 name 属性，建议使用 id 属性。

### 创建锚点链接

- 使用 `href` 属性建立锚点链接。
- 基本语法
	- `<a href = "#锚点名称"> 文字 </a>`

## 插入表单

- 使用 `<form></form>` 创建一个表单。
- 属性
	- `action`：指定表单数据提交到哪个地址进行处理。
	- `name`：表单名称。
		- 不能包含**特殊字符和空格**。
	- `method`：传送方法
		- get：表单数据被传送到 action 属性指定的 URL，然后这个新的 URL 被送到处理程序上。
		- post：表单数据被包含在表单主体中，然后被送到处理程序上。
	- `enctype`：编码方式
		- application/x-www-form-urlencoded：发送前编码所有字符（默认）。
		- multipart/form-data：不对字符编码。
			- 在使用包含**文件**上传控件时必须使用该值。
		- text/plain：空格转换为 “+” 符号，但不对特殊字符编码。
	- `target`：规定目标窗口打开方式。

## 补：input 标记

> 基本用法请参见[JSP 内置对象 input 标记](http://remilitarize.space/2017/09/18/%E7%AC%AC3%E7%AB%A0-jsp%E5%86%85%E7%BD%AE%E5%AF%B9%E8%B1%A1/)
> 更多资料请访问[W3School input 标签](http://www.w3school.com.cn/tags/tag_input.asp)

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
       <title>第五章 用 HTML 创建超链接和表单</title>
</head>
<body>
    <a href="http://www.baidu.com" target="_blank">百度（在新页面打开）</a>
    <a href="http://www.sogou.com" target="_self">搜狗（在当前页面打开）</a>
    <a href="http://www.baidu.com" target="_blank"><img src="https://ss0.bdstatic.com/5aV1bjqh_Q23odCf/static/superman/img/logo_top_ca79a146.png" alt="百度"/></a>
    <p><a id="maodian1">锚点1</a> <a id="maodian2">锚点2</a></p>
    <br /><br /><br />
    <br /><br /><br />
    <br /><br /><br />
    <a href="#maodian1">锚点1在这里！</a>
    <br /><br /><br />
    <br /><br /><br />
    <br /><br /><br />
    <a href="#maodian2">锚点2在这里！</a>
</body>
</html>
```
