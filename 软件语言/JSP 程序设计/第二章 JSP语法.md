[toc]

## JSP 页面的基本结构

- 一个 JSP 页面由 **5** 个元素构成
	- 普通的 HTML 标记
	- JSP 标记
	- 变量和方法的声明
	- Java 程序片
	- Java 表达式

> 除 HTML 外，其余均需要**服务器**运行

## 变量和方法的声明

### 声明变量

- 在**`<%!  %>`**标记符之间声明变量和方法

```xml
<%!
int a, b, c;
String s;
%>
```

- 在`<%!  %>`中声明的变量在整个 JSP 页面上均有效，称为 **JSP 页面的成员变量**。
- JSP 页面的成员变量在 **JSP 引擎关闭**时才**释放**。
- JSP 页面的成员变量对**所有访问该 JSP 页面的用户共享**，所以任何用户操作了 JSP 页面的成员变量，均会影响到其他用户。

> 实际上 JSP 页面的成员变量等同于 Java 中的**全局变量**

### 声明方法

- JSP 页面在**只允许在`<%!  %>`之间**声明方法。
- 方法在整个 JSP 页面内均有效。
- 在方法内声明的变量以及方法的形式参数只在方法内有效。

```xml
<%!
int sum(int a, int b){
	return a + b;
}
%>
```

## Java 程序片

- 在**`<%  %>`**标记符之间插入 **Java 程序片**。
- 如果 JSP 页面中有多个`<%  %>`标记符，则按先后顺序执行。
	- Java 程序片实际上是将一个 Java 程序拆分成很多个程序片执行。
	- 利用这个性质，我们可以在**几个程序片之间插入 HTML 标记等其他的标记符**。
- 在程序片中定义的变量称为 **JSP 页面的局部变量**。
- JSP 页面的局部变量在**声明位置之后**的所有代码中均有效。
- 运行在不同线程内的 JSP 页面的局部变量**互不干扰**。
- 当一个 **JSP 页面运行完毕**后，JSP 页面的局部变量就会被释放。


### `synchronized` 关键字

- 被`synchronized`修饰方法时，该方法会仅被一个线程访问，其他线程访问时将会阻塞。

## Java 表达式

- 在**`<%=  %>`**标记符之间插入 **Java 表达式**。
- 表达式不可以是**语句**，且表达式**必须能够求值**。
- 表达式的值由**服务器**进行计算，并将结果以**字符串**的形式发送给客户端显示。

## 示例 JSP 页面

现在已经认识了 JSP 页面中的 5 个元素，下面是两个小程序。

1.
```xml
<%@ page language="java" contentType="text/html; charset= UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<title>简单的计数器</title>
</head>
<body bgcolor = cyan>
<%! int i = 0;
%>
<% i++;
%>
你是本页面第<%= i %>个访问的用户
</body>
</html>
```

> 若编译器提示`processing instruction not closed`

> - 可能代码中标签没有闭合。
- 直接忽视。

- 补充说明：
	- HTML 标签是由**一对尖括号`<>`**包围的**关键字**组成。
	- HTML 标签通常是**成对**出现的，其中第一个是**开始标签**，第二个带有`/`的是**结束标签**。
		- 开始标签和结束标签又被称为**开放标签**和**闭合标签**。
	- **`<html>`**标签之间是**所有对网页的描述**。
	- **`<head>`**标签之间是网页**头部**的描述。
		- **`<title>`**标签之间是网页的**标题**，是`<head>`标签中**必需**的元素。
	- **`<body>`**标签之间是网页要**显示**的所有内容。
		- **`bgcolor`**是`<body>`标签的一个**属性**，表示**背景颜色**，等号后是具体的值。
- 这段代码会显示在 Tomcat 服务器启动后访问 JSP 页面的人数，不断刷新会发现人数在增加。
- 当断开 Tomcat 并再次启动时，页面刷新后会发现人数变会 1 。
- 当打开多个页面时，人数会随着页面的打开增加。

2.
```xml
<%@ page language="java" contentType="text/html; charset= UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<title>输出大写字母</title>
</head>
<body bgcolor = cyan>
<%! char begin = 'A', end = 'Z', c;
int count = 0;
%>
<table border = "1">
<%
for(c = begin; c <= end; c++){
	if(count == 0){	%>
		<tr>
<%	}	%>
	<td><%= c %></td>
<%	count ++;
	if(count == 4 || c == end){	%>
		</tr>
<% 		count = 0;
	}
}
%>
</table>
</body>
</html>
```

- 补充说明：
	- **`<table>`**标签定义一个表格。
	- **`<tr>`**标签定义表格中的一行。
	- **`<td>`**标签定义每一行中的每一格。
- 这个页面应用了 Java 程序片允许拆分成多块代码运行。

---

## JSP 中的注释

- HTML 注释
	- **`<!-- 注释内容 -->`**
	- 这个注释可以通过一些浏览器自带的 “查看源代码” 功能查看。
- JSP 注释
	- `<%-- 注释内容 --%>`
	- JSP 引擎忽视 JSP 注释。

## JSP 指令标记

### page 指令标记

- page 指令用来定义整个 JSP 页面的一些属性和这些属性的值，属性值用**单引号**或**双引号**括起来。
- page 指令表示方法

```
<%@ page 属性 1 = "属性 1 的值" 属性 2 = "属性 2 的值" ... %>
```

```
<%@ page 属性 1 = "属性 1 的值" %>
<%@ page 属性 2 = "属性 2 的值" %>
...
<%@ page 属性 n = "属性 n 的值" %>
```

- page 指令的作用对**整个 JSP 页面有效**，与其书写位置无关。

#### contentType 属性

- 用于设置 JSP 页面的响应 **MIME 类型**和**字符编码**。
- 属性值一般形式
	- "MIME 类型"
	- "MIME 类型; charset = 编码"
- 常用属性值：
	- HTML 解析器 `<%@ page contentType = "text/html; charset = gb2312" %>`
	- MS - word 应用程序 `<%@ page contentType = "application/msword" %>`
	- 默认值 `<%@ page contentType = "text/html; charset = ISO-8859-1" %>`
- **一个 JSP 页面只允许为 `contentType` 指定一个值。**

#### language 属性

- 定义 JSP 页面的脚本语言。
- **目前属性值只能取 "java"**
- 格式：`<%@ page language = "java" %>`
- **默认值是 "java"**

#### import 属性

- 为 JSP 页面引入 java 运行环境提供的包中的类。
- 格式：

`<%@ page import = "java.io.*", "java.util.Date" %>`

```xml
<%@ page import = "java.io.*" %>
<%@ page import = "java.util.Date" %>
```

- 默认值有 "java.lang.\*", "javax.servlet.\*", "javax.servlet.jsp.\*", "javax.servlet.http.\*"

#### session 属性

- 设置是否需要使用内置的 session 对象。
- 属性值为 `true` 或 `false`
- **默认值为 `true`**

#### buffer 属性

- 指定 `out` 设置的缓冲区的大小或不使用缓冲区
- 格式：`<%@ page buffer = "24KB" %>`
- 默认值是 **8KB**
- 取值为 **"none"** 时，不使用缓冲区

#### autoFlush 属性

- 当 `out` 的缓冲区被填满时，缓冲区是否自动刷新。
- 取值为 `true` 或 `false`
- **默认值为 `true`**
- 当取值为 `false` 时，如果 `out` 的缓冲区填满，就会出现缓存溢出异常。
- **当 `buffer`的值是 `none`时，`autoFlush` 的值就不能设置成 `false`。**

#### isThreadSafe 属性

- 设置 JSP 页面是否可多线程访问、
- 取值为 `true` 或 `false`
- **默认值为 `true`**
- 当设置为 `true` 时， JSP 页面能同时相应多个用户的请求
- 当设置为 `false` 时， JSP 页面同一时刻只能相应一个用户的请求，其他用户须排队等待。

#### info 属性

- 为 JSP 页面准备一个常用但可能要经常修改的**字符串**
- 格式：`<%@ page info = "we are students" %>`
- 在 JSP 页面中的使用方法：`getServletInfo();`

### include 指令标记

- 格式：`<%@ include file = "文件的 URL" %>`
- 作用：在 JSP 页面出现该指令的位置处，**静态**插入一个文件。
	- 静态是指将插入的文件整体插入 JSP 页面后**一同编译**。

> 文件的 URL 必须是相对于当前 JSP 页面的路径

- 若被插入的文件是一个 JSP 页面，且使用 page 指令为 contentType 属性设置了属性值，则**被插入文件的 contentType 属性值与插入该文件的 contentType 属性值必须相同**。

## JSP 动作标记

### include 动作标记

- 格式：

`<jsp:include page = "文件的 URL" />`

```xml
<jsp:include page = "文件的 URL" >
	param 子标记
</jsp:include>
```

> 当**不使用 `param` 子标记**时，必须使用前一种形式。

- include 动作标记是动态加载
	- **当 JSP 页面运行时才将文件加入**
- 如果包含的是**普通的文本文件**，则将文件的内容发送到客户端。
- 如果包含的是 **JSP 页面**，JSP 引擎就执行这个文件，然后将执行的结果发送到用户端，并由用户端的浏览器负责显示这些结果。

### param 动作标记

- 以“名 —— 值”对的形式为其他标记提供附加信息。
- 格式：`<jsp:param name = "名字" value = "指定给 param 的值">`
- 当该标记语 `jsp:include` 动作标记一起使用时，可以将 **`param` 标记中的值**传递到 **`include` 动作标记要加载的文件**中去，被加载的 JSP 文件可以使用 Tomcat 服务器提供的 **`request` 内置对象获取 `include` 动作标记的 `param` 子标记**中 `name` 属性所提供的值。

### forward 动作标记

- 语法格式

`<jsp:forward page = "要转向的页面" />`

```xml
<jsp:forward page  ="要转向的页面">
	param 子标记
</jsp:forward>
```

- 作用
	- 从该指令处**停止当前页面的执行**，而转向执行 page 属性指定的 JSP 页面。
	- 当前页面使用 forward 动作标记转向后，尽管用户看到了转向后的页面的效果，但浏览器地址栏中显示的仍然是**转向前的 JSP 页面的 URL 地址**。
