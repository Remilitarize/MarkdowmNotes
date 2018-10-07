[toc]

## 什么是 JSP

- JSP 是 Java Server Page 的缩写。
- 学习 JSP 技术需要的基础：
	- Java 语言
	- HTML 语言

## 安装与配置 JSP 运行环境

> [安装与配置方法](http://www.cnblogs.com/leftshine/p/5238001.html)

- 先安装 JDK，后安装 Tomcat
- Tomcat 默认端口号：**8080**
- 启动 Tomcat 服务器后，在浏览器地址栏中输入 <http://127.0.0.1:8080> 显示 Tomcat 测试页面表示成功。
- 安装后修改 Tomcat 端口号
	- 找到 Tomcat 安装目录下的 **conf** 文件夹中的 **server.xml** 文件。
	- 打开，找到
		`<Connector port="8080" redirectPort="8443" connectionTimeout="20000" protocol="HTTP/1.1"/>`
		修改将`port`后的数字即可，比如 9080。
	- 在浏览器地址栏中输入 <http://127.0.0.1:9080> ，显示 Tomcat 测试页面表示成功。

## JSP 页面

### JSP 页面介绍

- 一个 JSP 页面可以有 **普通的 HTML 标记** 和 **JSP 规定的 JSP 标记**，以及 `<% %>`加入的 **Java 程序片**。
- 一个 JPS 页面按文本文件保存时，扩展名是 **`.jsp`**。
- 保存 JSP 页面的文件名要求
	- 必须符合 **标识符** 规定，即字母、下划线、美元符号、数字。
	- 第一个字母不能使数字。
	- 名字区分大小写。

#### 简单的 JSP 页面

```xml
<%@ page contentType = "text/html; charset = GB2312" %>
<HTML>
<BODY BGCOLOR = cyan>
<h3>这是一个简单的页面</h3>
<% int i,sum = 0;
	for(i = 0; i <= 100; i++){
		sum = sum + i;
	}
%>
<h5>1 到 100 的连续和是：<%= sum %>
</h5></BODY></HTML>
```

### 设置 WEB 服务目录

- Tomcat 的 Web 服务目录的**根目录**是
	- 安装目录\\**webapps**\\**Root**
- 将 JSP 页面文件保存在目录中，在浏览器地址栏中输入 `127.0.0.1:8080/文件名.jsp` 运行

- 安装目录\\**webapps** 下**任意一个子目录**均可作为一个 Web 服务目录
	- 运行子目录中的 JSP 页面文件： `安装目录\webapps\子目录\文件名.jsp`

- 将计算机中的某个目录设置为一个 Web 服务目录
	1. `安装目录\conf\server.xml`
	2. 找到 **`</HOST>`** - 在 `server.xml` 末尾
	3. 在 `</HOST>` 前插入(例如将 `d:\sun` 文件夹作为服务目录)
			<Context path = "\hello" docBase = "d:\sun" debug = "0" reloadable = "true" />
		- 这里 `\hello` 为虚拟目录
	4. 将虚拟目录作为子目录进行访问。

## JSP 运行原理

- 服务器上的一个 JSP 页面被 **第一次请求执行** 时
	1. 服务器上的 JSP 引擎首先将 **JSP 页面文件** 转译成 **Java 文件**。
	2. 编译这个 Java 文件生成 **字节码文件**。
	3. 执行字节码文件响应用户请求。
- 当这个 JSP 页面 **再次** 被请求执行时
	- **JSP 引擎直接执行字节码文件** 响应用户请求。
- 字节码文件主要功能
	- 把 HTML 标记符号（静态部分）交给用户浏览器负责显示。
	- 处理 JSP 标记，并将有关处理结果发送给客户的浏览器。
	- 执行 `<% %>` 之间的 Java 程序片（动态部分），并把执行结果交给客户的浏览器显示。
	- **当多个用户请求一个 JSP 文件时， Tomcat 服务器为每个用户启动一个线程**。
