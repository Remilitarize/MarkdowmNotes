[toc]

- 五个内置对象
	- request
	- response
	- session
	- application
	- out
- 内置对象的名字不能更改

## request 对象

- 内容
	- 封装了用户提交的信息，即用户请求的全部内容
		- 输入的数据
		- URL地址
		- HTTP数据包
- form 表单标记
	- 使用 HTML 表单向服务器的某个JSP页面提交信息
	- action 属性：信息提交的**目的地页面**
	- method 属性：取值 **get** / **post**
		- 不填写则需要用组件处理
		- 区别
			- 使用 get 方法提交的信息会在提交的过程中**显示在浏览器的地址栏**中。
			- 使用 post 方法提交的信息**不会显示**在地址栏中。

### 获取用户提交的信息

- 方法：**`request.getParameter(String s)`**
	- 封装在请求对象中的参数的值
	- 返回参数的值类型是 **`String`**
- action 属性取值为**空**
	- 请求的页面为**当前页面**
	- 注意对空指针进行处理

> 例1： 计算三角形面积

```xml
<%-- Test.jsp --%>
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<title>计算三角形面积</title>
</head>
<body>
<form action = "triangle.jsp" method = post>
	<input type = "text" name = "sizeA" size = 6>
	<input type = "text" name = "sizeB" size = 6>
	<input type = "text" name = "sizeC" size = 6>
	<input type = "submit" value = "提交" name = "submit">
</form>
</body>
</html>

<%-- triangle.jsp --%>
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<title>计算结果</title>
</head>
<body>
<%!
boolean judge(double p, double sizeA, double sizeB, double sizeC){
	if(p <= sizeA || p <= sizeB || p <= sizeC){
		return false;
	}
	return true;
}
%>
<%
try{
	double sizeA = Double.parseDouble(request.getParameter("sizeA"));
	double sizeB = Double.parseDouble(request.getParameter("sizeB"));
	double sizeC = Double.parseDouble(request.getParameter("sizeC"));
	double p = (sizeA + sizeB + sizeC) / 2;
	double area = Math.sqrt((p - sizeA) * (p - sizeB) * (p - sizeC) * p);
	if(judge(p, sizeA, sizeB, sizeC)){
		out.print("<br />三角形的面积为" + area);
	}
	else{
		out.print("<br />输入的三边不能构成三角形");
	}
}
catch(NumberFormatException e){
	out.print("<br />请输入正确的数字");
}
%>
</body>
</html>
```

> 例2： 计算字符串中数字的和（acton 属性为空）

```xml
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<title>计算字符串中数字的和</title>
</head>
<body>
<form action = "" method = get>
	<input type = "text" name = "textContent">
	<input type = "submit" name = "确定">
</form>
<%
String textContent = request.getParameter("textContent");
try{
	String []numbers = textContent.split("#");
	int x, sum = 0;
	boolean flag = true;
	for(String number:numbers){
		x = Integer.parseInt(number);
		if(flag){
			out.print("<br />输入的数字有：");
			flag = false;
		}
		out.print(" " + x);
		sum += x;
	}
	out.print("<br />总和为：" + sum);
}
catch(NullPointerException e){
	out.print("<br />请输入以 # 分隔的字符串");
}
catch(NumberFormatException e){
	out.print("<br />请输入以 # 分隔的字符串");
}
%>
</body>
</html>
```

### 处理汉字信息

- 对信息重新编码
	- 在**出口**处重新解析

```
String str = request.getParameter("message");
byte b[] = str.getBytes("ISO-8859-1");
str = new String(b, "UTF-8");
```

- request 设置编码
	- 在**入口**处进行设置

```
request.setCharacterEncoding("UTF-8");
```

> 当表单 method 为 get 时使用第一个，为 post 时使用第二个。

### 常用方法举例

- getProtocol() 获取用户向服务器提交信息所使用的通信协议
- getServletPath() 获取用户请求的JSP页面文件的目录
- getContextPath() 获取用户请求的当前JSP页面文件的目录
- getContentLength() 获取用户提交的整个信息的长度
- getMethod() 获取用户提交信息的方式
- getHeader(String s) 获取HTTP头文件中由参数s制定的头名字的值
- getHeaderNames() 获取头名字的一个枚举
- getHeaders(String s) 获取头文件中制定头名字的全部值的一个枚举
- getRemoteAddr() 获取用户的IP地址
- getRemoteHost() 获取用户机的名称（若获取不到，就获取IP地址）
- getServerName() 获取服务器的名称
- getServerPort() 获取服务器的端口号
- getParameterNames() 获取用户提交的信息体部分中name参数值的一个枚举

## 处理 HTML 标记

### form 标记

- 一般格式

```
<form action = "提交信息的目的地页面' method = get | post name = "表单地名字">
	数据提交手段部分
</form>
```

- 一般获取值通过 `request.getParameter(String s)`
- 在 HTML 4.01 中，`<input>` 的 align 属性已废弃。请使用 CSS 代替。

### input 标记

- 格式
	- `<input type = "输入对象的GUI类型" name = "名字">`
	- name 属性：获取“输入对象的 GUI 类型“中提交的数据

#### 文本框 text

- 格式
	- `<input type = "text" name = "t" value = "hi" size = "12" maxlength = "30">`
- value 属性：text 的初始值
- size 属性：显示大小
- maxlength 属性：可输入最大长度

#### 单选按钮 radio

- 格式
	`<input type = "radio" name = "color" value = "red" checked = "checked">`
- name 属性：区分不同组的单选按钮
- value 属性：选中后获取到的值
- checked 属性：初始选项
	- 在 XHTML 中，禁止属性最小化，checked 属性必须定义为 **`<input checked="checked" />`**

#### 复选框 checkbox

- 格式
	`<input type = "checkbox" name = "fruit" value = "color" checked = "checked">`
- name 属性：区分不同组的复选框
- value 属性：选中后获取到的值
	- 由于存在多个选项，需要通过 `request.getParameterValues(String s)` 方法
- checked 属性：初始选项
	- 在 XHTML 中，禁止属性最小化，checked 属性必须定义为 **`<input checked="checked" />`**

#### 口令框 password

- 格式
	`<input type = "password" name = "pw" size = "12" maxlength = "20">`
- 口令框仅防止别人偷看，不进行加密

#### 隐藏值 hidden

- 格式
	`<input type = "hidden" name = "h" value = "123">`
- 隐藏值是不可见的，获取是会直接将 value 的值返回。

#### 提交按钮 submit

- 格式
	`<input type = "submit" name = "submit" value = "确定" size = "10">`
- name 属性：区别不同提交按钮
- value 属性：按钮上显示的文字
- size 属性：按钮大小

#### 重置按钮 reset

- 格式
	`<input type = "reset">`
- 将表单数据清空。

> 例：

```xml
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<title>测试 1</title>
</head>
<body>
<form action = "" method = get>
	<input type = "text" name = "txt" value = "1" size = 100 maxlength = 6 />
	<br /><input type = "radio" name = "color" value = "red" checked = "checked" />red
	<input type = "radio" name = "color" value = "blue" />blue
	<br /><input type = "checkbox" name = "fruit" value = "apple" checked = "checked" />apple
	<input type = "checkbox" name = "fruit" value = "banana" />banana
	<br />请输入密码：<input type = "password" name = "pw" size = 12 maxlength = 12 />
	<br />这里有个隐藏值<input type = "hidden" name = "h" value = "123" />
	<br /><input type = "submit" name = "submit" value = "确定" size = 12 />
	<input type = "reset" />
</form>
<%
String s = request.getParameter("txt");
out.print("<br />文本框中的内容是" + s);
s = request.getParameter("color");
out.print("<br />单选按钮选中的是" + s);
String ss[] = request.getParameterValues("fruit");
out.print("<br />多选按钮选中的是");
try{
	for(String x:ss){
		out.print(x + " ");
	}
}
catch(NullPointerException e){
	out.print("空");
}
s = request.getParameter("pw");
out.print("<br />输入的密码是" + s);
s = request.getParameter("h");
out.print("<br />隐藏值是" + s);
%>
</body>
</html>
```

### select/option 标记

- 下拉列表格式
```xml
<select name = "down">
	<option value = "item1"> item1 </option>
	<option value = "item2"> item2 </option>
	...
</select>
```
- 滚动列表格式
```xml
<select name = "role" size = "6">
	<option value = "item1"> item1 </option>
	<option value = "item2"> item2 </option>
	...
</select>
```

- name 属性：获取到下拉列表被选中的 option 的值
- size 属性：添加后由下拉列表变为滚动列表，表示滚动列表可见行的数目。

### textArea 标记

- 格式
```xml
<textArea name = "txt" rows = "5" cols = "5">
</textArea>
```
- name 属性：区别不同 textArea
- rows 属性：文本可见行数
- cols 属性：文本可见列数

### table 标记

- 格式
```xml
<table border = "1">
	<tr width = "5">
		<td width = "5"> 内容 </td>
		<th width = "5"> 内容 </th>
	</tr>
</table>
```

- border 属性：表格的边框宽度，默认**没有边框**。
- width 属性：每一行或每一格的宽度。
- `<tr></tr>` 标记：定义表格的一行。
- `<td></td>` 标记：定义表格一行中的一个格，**不着重显示**。
- `<th></th>` 标记：定义表格一行中的一个格，**着重显示**。

### image 标记

- 格式
```xml
<image src = "图片的 URL 地址"> 描述文字 </image>
```

- width/height 属性：指定显示图像的长和宽，不指定则默认图片原始大小。

### embed 标记

- 格式
```xml
<embed src = "音频或视频文件的 URL 地址" autostart = "false" loop = "-1" >
	描述文字
</embed>
```

- autostart 属性：打开 jsp 页面时是否自动播放，**默认值为 false**。
- loop 属性：指定音频或视频的播放次数，**取值为 -1 时无限循环**。
- width/height 属性：指定播放界面的长和宽，不指定则取默认值。

### 处理超链接

- 常用格式
```xml
<a href = "url ? 参数1 = 串值1 & 参数2 = 串值2 & ... ">
	文字说明
</a>
```

- href 属性：填写要跳转的页面 url 地址，同时允许传递参数。
	- 不需要传递参数时将 `?` 后的内容省略即可。

> 参数与值中不要使用汉字。

> 例：
```xml
<%@ page language = "java" contentType = "text/html; charset = UTF-8" pageEncoding = "UTF-8"%>
<! DOCTYPE html>
<html>
<head>
<title>测试 2：用表格输出文本内容</title>
</head>
<body>
<a href = "www.baidu.com">百度</a>
<br />
<a href = "www.sogou.com">搜狗</a>
<br />
<a href = "www.djtu.com">大连交通大学学校官网</a>
<p>请在文本框中输入一些内容：</p>
<form action = "" method = get>
	<textArea name = "txt" rows = "10" cols = "20"></textArea>
	<br />请输入每行表格格数
	<input type = "text" name = "num" size = "2" maxlength = "2" />
	<input type = "submit" name = "提交" value = "submit" />
</form>
<table>
<%
try{
	String s = request.getParameter("txt");
	s = new String(s.getBytes("ISO-8859-1"),"UTF-8");
	int len = s.length();
	int n = Integer.parseInt(request.getParameter("num"));
	if(n > 0 && s != null && len != 0){
		int count = 0;
		for(int i = 0; i < len; i++){
			if(count == 0){ %>
				<tr>
<%			} %>
			<td> <%= s.charAt(i) %> </td>
<%			count ++;
			if(count == n){ %>
				</tr>
<%				count = 0;
			}
		}
	}
	else if(n <= 0){
		out.print("请输入大于 0 的数字！");
	}
	else if(len == 0){
		out.print("请在文本框内输入字符！");
	}
}
catch(NullPointerException e){
	out.print("请输入数字");
}
catch(NumberFormatException e){
	out.print("请输入一个有效的数字!");
}
finally{ %>
	</table>
<%
}
%>
</body>
</html>
```

## response 对象

### 动态响应 contextType 属性

- 动态改变 contentType 的属性值来响应用户。
	- 使用 `response.setContentType(String s)`设置
- 当用 setContentType 方法动态改变了 contentType 的属性值时，JSP 引擎就会按照**新的 MIME 类型**将 JSP 页面的输出结果返回给用户。

### response 的 HTTP 文件头

- 动态添加
	- `response.addHeader(String head, String value)`
- 动态设置
	- `response.setHeader(String head, String value)`

### response 重定向

- 在某些情况下响应用户时，需要将用户 **重新引导至另一个页面**。
- `response.sendRedirect(URL url)`

### response 状态行

- 当服务器对用户请求进行响应时，它发送的首行称为 **状态行**。
- 分类：
	- 1xx：主要是实验性质的。
	- 2xx：用来表明请求成功。
	- 3xx：用来表明在请求满足之前应采取进一步的行动。
	- 4xx：当浏览器给出无法满足的请求时，返回该状态代码。
	- 5xx：用来表示服务器出现问题。
- 使用`response.setStatus(int n)`方法来改变响应的状态行的内容。

## session 对象

- 用于记录有关连接的信息。
- 由 Tomcat 服务器负责创建，针对特定的用户。
- 每一个 session 都有 **唯一** 的 id。
- session 的 id 同时存在于 **用户的 cookie 和服务器** 中用于标志。
- session 有效期
	- 到达了 **最大的生存时间**
		- 设置在 **服务器** 上
	- **服务器关闭**
	- 修改 Tomcat 服务器下的 **web.xml**，重新设置 session 对象的 **最长“发呆“时间**
	- 通过方法获取或设置与生存时间有关的信息

### session 对象的 id

- 同一个用户在 **不同的 Web 服务目录** 中的 session 是互不相同的。
- 获取 session 的 id
	- `session.getId()`
	- 返回值为 String

### session 对象与 URL 重写

- session 对象是否能和用户建立起一一对应关系依赖于用户端是否 **支持 Cookie**。
- 如果用户端不支持 Cookie，那么用户在不同网页之间的 session 对象可能是互不相同的
- 如果用户端不支持 Cookie，JSP 页面可以通过 URL 重写来实现 session 对象的唯一性。
	- 当用户从一个页面跳转到另一个页面时，通过向这个新的 URL 添加参数，把 session 对象的 id 传过去。
	- 方法：`response.encodeURL()`或`response.encodeRedirectURL()`

### session 对象存储数据

- 调用某些方法保存用户在访问某个 Web 服务目录期间的有关数据。
- 方法
	- `public void setAttribute(String key, Object obj)`
		- 将参数 Object 指定的对象 obj 添加到 session 对象中，并为添加到对象指定一个索引关键字。
		- 如果添加到两个对象的关键字相同，则先前添加的对象被清除。
	- `public Object getAttribute(String key)`
		- 获取 session 对象索引关键字是 key 的对象
		- 由于任何对象都可以添加到 session 对象中，因此取回时应 **强制转换** 为原来的类型。
	- `public Enumeration getAttributeNames()`
		- 产生一个枚举对象，该枚举对象使用 `nextElemets()` 遍历 session 中的各个对象所对应的关键字。
	- `public void removeAttribute(String name)`
		- 移除 key 关键字对应的对象。

### session 对象的生存期限

- “发呆”状态时间
	- 用户对某个 Web 服务目录发出 **两次请求的间隔时间**。
	- 默认为 **30 分钟**。
- 通过`web.xml`设置
	- %Tomcat 安装目录% / conf / web.xml
	- 将 `30` 修改为自己需要的时间长度。
	- 单位为 分钟、
```xml
<session-config>
	<session-timeout> 30 </session-timeout>
</session-config>
```

- 获取或设置生存时间的方法
	- **`public long getCreationTime()`**
		- **获取 session 的创建时间**
		- 单位是 毫秒。
	- `public long getLastAccessedTime()`
		- 获取 session 最后一次被操作的时间
		- 单位是 毫秒。
	- `public int getMaxInactiveTime()`
		- 获取 session 最长的“发呆”时间
		- 单位是 秒。
	- **`public void setMaxInactiveTime(int interval)`**
		- **设置 session 最长的“发呆”时间**
	- `public boolean isNew()`
		- 判断 session 是否是一个新建的对象
	- **`invalidate()`**
		- **使 session 无效**

> 例：

```xml
<!-- Main.jsp -->
<%@ page language = "java" contentType = "text/html; charset = UTF-8" pageEncoding = "UTF-8" %>
<!DOCTYPE html>
<html>
<head>
<title>猜数字小游戏</title>
</head>
<body>
<%
int ans = (int)(Math.random() * 100);
session.setAttribute("ans", new Integer(ans));
session.setAttribute("count", new Integer(0));
%>
<h1> 请输入数字（0 ~ 100）：</h1>
<form action = "handler.jsp" method = get>
	<input type = "text" name = "guess" size = "5" maxlength = "3" />
	<input type = "submit" name = "submit" value = "提交" />
</form>
</body>
</html>

<!-- big.jsp -->
<%@ page language = "java" contentType = "text/html; charset = UTF-8" pageEncoding = "UTF-8"%>
<!DOCTYPE html>
<html>
<head>
<title>猜大了！</title>
</head>
<body>
<h1><%= session.getAttribute("guess") %>猜大了！</h1>
<p>再试一次吧！</p>
<form action = "handler.jsp" method = get>
	<input type = "text" name = "guess" size = "5" maxlength = "3" />
	<input type = "submit" name = "submit" value = "提交" />
</form>
</body>
</html>

<!-- small.jsp -->
<%@ page language = "java" contentType = "text/html; charset = UTF-8" pageEncoding = "UTF-8"%>
<!DOCTYPE html>
<html>
<head>
<title>猜小了！</title>
</head>
<body>
<h1><%= session.getAttribute("guess") %>猜小了！</h1>
<p>再试一次吧！</p>
<form action = "handler.jsp" method = get>
	<input type = "text" name = "guess" size = "5" maxlength = "3" />
	<input type = "submit" name = "submit" value = "提交" />
</form>
</body>
</html>

<!-- correct.jsp -->
<%@ page language = "java" contentType = "text/html; charset = UTF-8" pageEncoding = "UTF-8" %>
<!DOCTYPE html>
<html>
<head>
<title>恭喜你猜对了！</title>
</head>
<body>
<h1>恭喜你猜对了！</h1>
<p>这个数就是<%= session.getAttribute("ans") %></p>
<p>你一共猜了<%= session.getAttribute("count") %>次</p>
</body>
</html>

<!-- handler.jsp -->
<%
String str = request.getParameter("guess");
if(str == null && str.length() == 0){
	response.sendRedirect("Main.jsp");
}
int guess = Integer.parseInt(str);
session.setAttribute("guess", new Integer(guess));
session.setAttribute("count", new Integer(((Integer)session.getAttribute("count")).intValue()+1));
int ans = ((Integer)session.getAttribute("ans")).intValue();
if(guess == ans){
	response.sendRedirect("correct.jsp");
}
else if(guess > ans){
	response.sendRedirect("big.jsp");
}
else if(guess < ans){
	response.sendRedirect("small.jsp");
}
%>
```

## application 对象

application 对象由服务器负责创建。
每个 Web 服务目录下的 application 对象 **被访问该服务目录的所有的用户所共享**。
不同 Web 服务目录下的 application **互不相同**。

### application 对象的常用方法

- `public void setAttribute(String key, Object obj)`
	- 将参数 Object 指定的对象 obj 添加到 application 对象中。
	- 并为添加的对象指定一个索引关键字 key。
- `public Object getAttribute(String key)`
	- 获取 application 对象中含有的关键字是 key 的对象。
- `public Enumeration getAttributeNames()`
	- 产生一个枚举对象。
	- 使用 `nextElements()` 方法遍历 application 中的各个对象所对应的关键字。
- `public void removeAttribute(String key)`
	- 从当前 application 对象中删除关键字是 key 的对象。
- `public String getServletInfo()`
	- 获取 Servlet 编译器的当前版本的信息。
	- 对应 `<%@ page info = "字符串" %>`

> 当有些服务器不直接使用 application 对象时
> 1. 使用 `ServletContext` 类声明这个对象。
  2. 使用 `getServletContext()` 方法对这个 application 对象进行初始化。

### 用 application 制作留言板

- 向量 `Vector`
```xml
<%@ page import = java.util.* %>
<%
Vector<String> v = new Vector<String>();  // 实例化一个 Vector 对象
v.add();      // 使用 add 方法向 v 结尾添加
%>
```

```xml
<%-- input.jsp --%>
<%@ page language = "java" contentType = "text/html; charset = utf-8" pageEncoding = "utf-8" %>
<!DOCTYPE html>
<html>
<head>
	<title>留言板</title>
	<meta name = "generator" content = "Eclipse" />
	<meta name = "author" content = "Remilitarize" />
</head>
<body>
	<form action = "handle.jsp" method = "get">
		<p>输入名字：<input type = "text" name = "name" size = "10" maxlength = "10" /></p>
		<p>留言标题：<input type = "text" name = "title" size = "10" maxlength = "10" /></p>
		<p>留言：</p>
		<textArea name = "message" rows = "10" cols = "36" ></textArea>
		<br />
		<input type = "submit" value = "提交" />
	</form>
	<hr />
	<form action = "show.jsp" method = "get">
		<input type = "submit" value = "查看留言板" />
	</form>
</body>
</html>

<%-- handle.jsp --%>
<%@ page language = "java" contentType = "text/html; charset = utf-8" pageEncoding = "utf-8" %>
<!DOCTYPE html>
<html>
<head>
	<meta name = "generator" content = "Eclipse" />
	<meta name = "author" content = "Remilitarize" />
	<title>提交成功！</title>
</head>
<body>
<%@ page import = "java.util.*" %>
<%!
	Vector<String> v = new Vector<String>();
	int count = 0;
	ServletContext application;
	synchronized void addMessage(String s){
		application = getServletContext();
		count ++;
		s = "No." + count + " " + s;
		v.add(s);
		application.setAttribute("message", v);
	}
%>
<%
	String name = request.getParameter("name");
	String title = request.getParameter("title");
	String message = request.getParameter("message");
	if(name == null || name == ""){
		name = "guest" + (int)(Math.random() * 10000);
	}
	if(title == null || title == ""){
		title = "无标题";
	}
	if(message == null || message == ""){
		message = "无内容";
	}
	addMessage(name + "#" + title + "#" + message);
	out.print("提交成功！<br />");
	out.print("你提交的内容是：<br />");
	out.print("留言人：" + name + "<br />");
	out.print("标题：" + title + "<br />");
	out.print("内容：<br />" + message + "<br />");
%>	<a href = "input.jsp" target = "_self">点击此处返回留言页面</a>
</body>
</html>

<%-- show.jsp --%>

<%@ page language = "java" contentType = "text/html; charset = utf-8" pageEncoding = "utf-8" %>
<html>
<head>
	<title>查看留言板</title>
	<meta name = "generator" content = "Eclipse" />
	<meta name = "author" content = "Remilitarize" />
</head>
<%@ page import = "java.util.*" %>
<body>
<%
	Vector<String> v = (Vector<String>)application.getAttribute("message");
	try{
		for(int i = 0; i < v.size(); i ++){
			String[] str = ((String)(v.elementAt(i))).split("#");
			out.print("留言人：" + str[0] + "<br />");
			out.print("标题：" + str[1] + "<br />");
			out.print("内容：<br />" + str[2]);
			out.print("<br />-------------------<br />");
		}
	}
	catch(NullPointerException e){
		out.print("留言板中没有任何消息！");
	}
	finally{
%>
		<a href = "input.jsp" target = "_self">返回留言页面</a>		
<%	}
%>
</body>
</html>
```

## out 对象

out 对象是一个输出流，用来向用户端输出数据。

- 常用方法
	- `out.print()` 输出但不换行
	- `out.println()` 输出并换行
	- `out.newLine()` 输出换行
	- `out.flush()` 输出缓冲区里的内容
	- `out.close()` 关闭流
