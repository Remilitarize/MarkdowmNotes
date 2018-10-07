[toc]

## 创建并设置表格属性

### 表格的基本标记

- 表格由三部分组成
	- 表格标记 table
	- 行标记 tr
	- 单元格标记 td
- 基本语法
```xml
<table>
	<tr>
		<td>第一行第一格</td>
		<td>第一行第二格</td>
	</tr>
	<tr>
		<td>第二行第一格</td>
		<td>第二行第二格</td>
	</tr>
</table>
```

- table 标记可选属性
	- `width`：宽度。
	- `height`：高度。
	- `align`：对齐方式。**（不赞成使用）**
	- `border`：添加边框并设置边框宽度。
		- 仅影响表格四周的边框宽度。
	- `bordercolor`：设置边框颜色。
	- `cellspacing`：设置单元格间距。（默认为2）
	- `cellpadding`：设置单元格内文字与边框的距离。
	- `bgcolor`：设置表格背景颜色。**（不赞成使用）**
	- `background`：设置背景图片。**（不赞成使用）**
- tr 标记可选属性
	- `align`：对齐方式。
	- `valign`：垂直对齐方式。
	- `bgcolor`：背景颜色。**（不赞成使用）**
- td 标记可选属性
	- `align`：对齐方式。
	- `bgcolor`：背景颜色。**（不赞成使用）**
	- `colspan`：单元格可横跨的列数。
	- `valign`：垂直对齐方式。

### 表格的标题

- 使用 `<caption></caption>` 标记为表格定义一个简明的标题。
- 基本语法
	- `<caption> 标题 </caption>`
- 包含属性
	- `align`：对齐方式（默认居中对齐）

> 在 HTML 4.01 中，caption 元素的 align 属性是不被赞成使用的。
  在 XHTML 1.0 Strict DTD 中，caption 元素的 align 属性是不被支持的。

### 表格的表头

- 使用 `<th></th>` 标记定义表格的表头。
- 语法等同于单元格，样式上比普通单元格多了**居中对齐和加粗**。

## 表格的结构标记

- 用于更加清楚地区分表格结构。
- 当使用结构标记是，必须使用全部的元素。
- **只允许在 table 内部使用**。
- 各个浏览器对结构标记的支持并不好。
- 表头 `<thead></thead>`
	- `<thead>` 内部必须拥有 `<tr>` 标签。
- 表体 `<tbody></tbody>`
- 表尾 `<tfoot></tfoot>`
- 共有可选属性
	- `align`：对齐方式。
	- `valign`：垂直对齐方式
	- `bgcolor`：背景颜色（不赞成使用）

---

本节课代码：
Test.html

```xml
<!DOCTYPE html>
<html>
<head>
       <meta name="content_type" content="text/html; charset = utf-8" />
       <meta name="generator" content="visual studio 2015" />
       <meta name="author" contnent="Remilitarize" />
       <title>第六章 用 HTML 创建表格</title>
</head>
<body>
    <h2>不使用结构标记创建的表格</h2>
    <table>
        <caption>表格 1</caption>
        <tr>
            <th>表头 1</th><th>表头 2</th>
        </tr>
        <tr>
            <td>第一行第一列</td><td>第一行第二列</td>
        </tr>
        <tr>
            <td>第二行第一列</td><td>第二行第二列</td>
        </tr>
    </table>
    <hr />
    <h2>使用结构标记创建的表格</h2>
    <table>
        <caption>表格 2</caption>
        <thead bgcolor="blue">
            <tr>
                <td>表头 1</td><td>表头 2</td>
            </tr>
        </thead>
        <tbody bgcolor="green">
            <tr>
                <td>第一行第一列</td><td>第一行第二列</td>
            </tr>
            <tr>
                <td>第二行第一列</td><td>第二行第二列</td>
            </tr>
        </tbody>
        <tfoot bgcolor="red" align="right">
            <tr>
                <td colspan="2">这里是表尾~</td>
            </tr>
        </tfoot>
    </table>
</body>
</html>
```
