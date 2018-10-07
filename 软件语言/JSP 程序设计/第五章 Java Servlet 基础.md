[toc]

## servlet 的部署、创建与运行

Java servlet 的核心思想就是在服务器端创建能响应用户请求的对象。

- 需要 `javax.servlet.http` 包中的类。
- 运行环境不同于普通 java 文件。
 	- 需要 `servlet-api.jar` 文件。
	- 该文件会在 Tomcat 安装目录 lib 子目录中，并复制粘贴到 JDK 的扩展目录。

### 源文件及字节码文件

#### Servlet 类

写一个创建 servlet 的类就是编写一个特殊类的子类，这个特殊的类就是 **`javax.servlet.http`** 包中的 **`HttpServlet`** 类。
HttpServlet 类的子类被习惯地称作一个 Servlet 类，这样的类创建的对象习惯地被称作一个 servlet。

#### 字节码文件的保存

将写好的 servlet 类编译成 class 字节码文件后，放入 **`\% Web 服务目录 %\WEB-INF\classes\% 包名 %\`** 下。

### 编写部署文件 web.xml

Servlet 类的字节码文件保存到指定的目录后，必须为 Tomcat 服务器编写一个部署文件，只有这样，Tomcat 服务器才会按用户的请求使用 Servlet 字节码文件创建对象。
该部署文件是一个 XML 文件，名字是 **web.xml**，由 Tomcat 服务器负责管理。

> web.xml 文件部署在 **`\% Web 服务目录 %\WEB-INF\`** 下。

```xml
<?xml version = "1.0" encoding = "iso - 8859 - 1" ?>
<web-app>
	<servlet>
		<servlet-name>hello</servlet-name>
		<servlet-class>myservlet.servlet</servlet-class>
	</servlet>
	<servlet-mapping>
		<servlet-name>hello</servlet-name>
		<url-pattern>/lookHello</url-parttern>
	</servlet-mapping>
</web-app>
```

- 一个 XML 文件应当以 **XML 声明** 作为文件的 **第一行**，在其前面不能有空白、其他的处理指令或注释。
	- XML 声明以 **`<?xml`** 标识开始，以 **`?>`** 标识结束。注意标识内不能有空格。
	- 如果 XML 声明中没有显式地指定 encoding 属性的值，那么该属性的默认值为 UTF-8 编码。
- 根标记
	- xml 文件必须有一个根标记。
	- web.xml 文件的根标记是 **`<web-app>`**。
- `<servlet>` 标记及子标记
	- web.xml 文件中可以有若干个 `<servlet>` 标记。
	- `<servlet>` 标记需要有两个子标记：
		- **`<servlet-name>`** 标记的内容是 Tomcat 服务器 **创建的 servlet 的名字**。
		- **`<servlet-class>`** 标记的内容指定 Tomcat 服务器 **用哪个 Servlet 类来创建 servlet**。
	- 若 web.xml 文件中存在多个 `<servlet>` 标记，它们的 `<servlet-name>` 子标记的内容必须互不相同。
- `<servlet-mapping>` 标记及子标记
	- web.xml 文件中出现一个 `<servlet>` 标记就会对应地出现一个 `<servlet-mapping>` 标记。
	- `<servlet-mapping>` 标记需要有两个子标记：
		- **`<servlet-name>`** 标记的内容必须与 **`<servlet>` 标记的 `<servlet-name>` 子标记的内容相同**。
		- **`<url-pattern>`** 标记用来指定用户 **用怎样的 URL 格式来请求 servlet**。
- 每当 Web 服务目录增加新的 servlet 时，都需要为 web.xml 文件添加 `<servlert>` 标记和 `<servlet-mapping>` 标记。

### servlet 的创建与运行

servlet 由 Tomcat 服务器负责创建，Web 设计者只需为 Tomcat 服务器预备好 Servlet 类的字节码文件，编写好相应的配置文件 web.xml，用户就可以根据 web.xml 部署文件请求服务器创建并运行一个 servlet。

> Servlet 类可以使用 `getServletName()` 方法返回配置文件中 `<servlet-name>` 标记给出的 servlet 名字。

### 向 servlet 传递参数的值

```xml
servlet 名 ? 参数 1 = 值 1 & 参数 2 = 值 2 ... 参数 n = 值 n
```

那么被请求的 servlet 就可以使用 request 对象获取参数的值。

```xml
request.getParameter(参数 n)
```

## servlet 的工作原理

### servlet 对象的生命周期

servlet 是 javax.servlet 包中 HttpServlet 类的子类的一个实例，**由服务器负责创建并完成初始化工作**。
当多个用户请求一个 servlet 时，服务器为每个用户启动一个线程而不是启动一个进程。

- 首次：
	- 实例化（服务器引擎）
	- 初始化（服务器引擎）
		- 调用 **`init()`** 方法
- 非首次：
	- 调用 **`servlet()`** 方法响应用户的请求。
		- 根据对应的请求调用 **`doGet()` 或 `doPost()`** 方法。
	- 当服务器关闭时，调用 **`destroy()`** 方法销毁 servlet。
- `init()` 方法只被调用一次，即在 servlet 第一次被请求加载时调用该方法。
- 当后续的用户请求 servlet 服务时，Web 服务将启动一个新的线程，servlet 调用 `service()` 方法响应用户的请求。
	- 每个用户的每次请求都导致 `service()` 方法被调用执行，其执行过程分别运行在 **不同的线程** 中。

### init 方法

该方法是 HttpServlet 类中的方法，可以在子类中重写这个方法。

```java
public void init(ServletConfig config) throws ServletException {}
```

`ServletConfig` 对象负责向 servlet 传递服务设置信息。
如果传递失败就会发生 `ServletException`。

### service 方法

该方法是 HttpServlet 类中的方法，可以在子类中直接继承或重写这个方法。

```java
public void service(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {}
```

当 servlet 成功创建和初始化之后，调用 service 方法来处理用户的请求并返回响应。

- `HttpServletRequest` 类型的对象封装了用户的请求信息。
- `HttpServletResponse` 类型的对象用来响应用户的请求。

### doGet 和 doPost 方法

可以在 Servlet 类中重写 `doGet()` 和 `doPost()` 方法来响应用户的请求，可以增加响应的灵活性并降低服务器的负担。
如果根据请求的类型进行不同的处理，就要在两个方法中编写不同的处理过程。
如果服务器的处理过程完全一样，可以在任意一个方法中编写，并在另一个方法中调用即可。

例：

web.xml

```xml
<?xml version = "1.0" encoding = "UTF-8" ?>
<web-app>
	<servlet>
		<servlet-name>handler</servlet-name>
		<servlet-class>re.Handler</servlet-class>
	</servlet>
	<servlet-mapping>
		<servlet-name>handler</servlet-name>
		<url-pattern>/handler</url-pattern>
	</servlet-mapping>
</web-app>
```

text.jsp

```xml
<%@ page contentType = "text/html; charset = UTF-8" pageEncoding = "UTF-8" language = "java" %>
<!DOCTYPE html>
<html>
	<head>
		<title>测试 doGet 和 doPost 方法</title>
		<meta name = "author" content = "Remilitarize" />
		<meta name = "generator" content = "Eclipse EE" />
	</head>
	<body>
		<form action = "handler" method = "get">
			输入数字，用逗号分隔提交给 servlet（get 方法）：<br />
			<input type = "text" name = "get" size = "20" maxlength = "20" />
			<input type = "submit" name = "submit" value = "提交" />
		</form>
		<form action = "handler" method = "post">
			输入数字，用逗号分隔提交给 servlet（post 方法）：<br />
			<input type = "text" name = "post" size = "20" maxlength = "20" />
			<input type = "submit" name = "submit" value = "提交" />
		</form>
	</body>
</html>
```

Handler.java

```java
package re;

import java.io.*;
import javax.servlet.*;
import javax.servlet.http.*;

public class Handler extends HttpServlet{

	public void init(ServletConfig config) throws ServletException{
		super.init(config);
	}

	public void doGet(HttpServletRequest request, HttpServletResponse response)
			throws ServletException, IOException{
		response.setContentType("text/html; charset = UTF-8");
		PrintWriter out = response.getWriter();
		out.print("<html>" +
						"<head>" +
							"<title>" + request.getMethod() + "方法</title>" +
							"<meta name = \"author\" content = \"Remilitarize\" />" +
							"<meta name = \"generator\" content = \"Eclipse EE\" />" +
						"</head>" +
						"<body>");
		String s[] = request.getParameter("get").split("[,,]+");
		out.print("用户请求的方式是" + request.getMethod() + "<br />");
		double sum = 0;
		for(String num : s) {
			if(num.length() >= 1) {
				out.print(num + " ");
				sum += Double.parseDouble(num);
			}
		}
		out.print("<br />的和是：" + sum);
		out.print("</body>" +
			"</html>");
	}

	public void doPost(HttpServletRequest request, HttpServletResponse response)
			throws ServletException, IOException{
		response.setContentType("text/html; charset = UTF-8");
		PrintWriter out = response.getWriter();
		out.print("<html>" +
						"<head>" +
							"<title>" + request.getMethod() + "方法</title>" +
							"<meta name = \"author\" content = \"Remilitarize\" />" +
							"<meta name = \"generator\" content = \"Eclipse EE\" />" +
						"</head>" +
						"<body>");
		String s[] = request.getParameter("post").split("[,,]+");
		out.print("用户请求的方式是" + request.getMethod() + "<br />");
		double product = 1;
		for(String num : s) {
			if(num.length() >= 1) {
				out.print(num + " ");
				product *= Double.parseDouble(num);
			}
		}
		out.print("<br />的积是：" + product);
		out.print("</body>" +
			"</html>");
	}
}
```

### destroy 方法

该方法是 HttpServlet 类中的方法，可以在子类中直接继承这个方法，一般不需要重写。

```java
public destroy() {}
```

当服务器终止服务时，`destroy()` 方法会被执行，销毁 servlet。

## 通过 JSP 页面访问 servlet

**注意，如果 web.xml 文件中 `<web-mapping>` 标记的子标记 `<url-pattern>` 指定的请求 servlet 的格式是 "/lookHello"，那么 JSP 页面请求 servlet 时，必须要写成 "lookHello"，否则将变成请求 ROOT 服务目录下的某个 servlet。**

### 通过表单向 servlet 提交数据

```xml
<%-- 假设指定的请求 servlet 的格式是 "/lookHello" --%>
<form action = "lookHello" ...>
	...
</form>
```

或

```xml
<form action = "lookHello ? 参数 1 = 值 1 & 参数 2 = 值 2 ... 参数 n = 值 n" ...>
	...
</form>
```

> servlet 在处理用户提交的汉字信息时，可以让 request 执行 `request.setCharacterEncoding("gb2312");`。

### 通过超链接访问 servlet

```xml
<%-- 假设指定的请求 servlet 的格式是 "/lookHello" --%>
<a href = "lookHello">...</a>
```

### 通过重定向或转发访问 servlet

- `sendRedirect()` 方法
	- 当用户请求一个 servlet 时，该 servlet 在处理数据后，可以使用重定向方法将用户重新定向到另一个 JSP 页面或 servlet。
	- 重定向方法仅仅是将用户从当前页面或 servlet 定向到另一个 JSP 页面或 servlet，**不能将用户对当前页面或 servlet 的请求（HttpServlet 对象）转发给所定向的资源**。
- `RequestDispatcher` 对象
	- `ResqustDispatcher`对象可以把用户对当前JSP 页面或 servlet 的请求转发给另一个 JSP 页面或 servlet，而且将用户对当前 JSP 页面或 servlet 的请求和相应（`HttpServletRequest` 对象和 `HttpServletResponse` 对象）传递给转发到的 JSP 页面或 servlet。
  - 实现转发
    - 让 `HttpServletRequest` 对象 request 调用 `public RequestDispatcher getRequestDispatcher(String path)`，参数 path 是要转发到的 JSP 页面或 servlet。
    - 让获取的 `RequestDispatcher` 对象调用 `void forward(ServletRequest request, ServletResponse response) throws ServletException, ava.io.IOException`。
  - 用户在浏览器的地址栏中不能看到 `forward` 方法转发的页面的地址或 servlet 的地址，只能看到该页面或 servlet 的运行效果。

例：

web.xml

```xml
<?xml version = "1.0" encoding = "UTF-8" ?>
<web-app>
	<servlet>
		<servlet-name>servlet</servlet-name>
		<servlet-class>re.servlet</servlet-class>
	</servlet>
	<servlet-mapping>
		<servlet-name>servlet</servlet-name>
		<url-pattern>/servlet</url-pattern>
	</servlet-mapping>
</web-app>
```

servlet.java

```java
package re;

import java.io.*;
import javax.servlet.*;
import javax.servlet.http.*;

public class servlet extends HttpServlet{

	public void init(ServletConfig config) throws ServletException{
		super.init(config);
	}

	public void doPost(HttpServletRequest request, HttpServletResponse response)
		throws ServletException, IOException{
		String []choices = request.getParameterValues("bill");
		double sum = 0.0;
		for(int i = 0;i < choices.length; i++) {
			switch(choices[i]) {
			case "1": sum += 12.8; break;
			case "2": sum += 1.2; break;
			case "3": sum += 10; break;
			}
		}
		request.setAttribute("sum", new Double(sum));
		RequestDispatcher dispatcher = request.getRequestDispatcher("test.jsp");
		dispatcher.forward(request, response);
	}

	public void doGet(HttpServletRequest request, HttpServletResponse response)
			throws ServletException, IOException{
		doPost(request, response);
	}
}
```

test.jsp

```xml
<%@ page contentType = "text/html; charset = UTF-8" pageEncoding = "UTF-8" language = "java" %>
<!DOCTYPE html>
<html>
	<head>
		<title>123</title>
		<meta name = "author" content = "Remilitarize" />
		<meta name = "generator" content = "Eclipse EE" />
	</head>
	<body>
		<form action = "servlet" method = "post">
			<table border = "1">
				<tr>
					<th>商品名</th>
					<th>价格（元）</th>
					<th>购买</th>
				<tr>
				<tr>
					<td>洗衣粉</td>
					<td>12.8</td>
					<td><input type = "checkbox" name = "bill" value = "1" /></td>
				</tr>
				<tr>
					<td>泡菜</td>
					<td>1.2</td>
					<td><input type = "checkbox" name = "bill" value = "2"/></td>
				</tr>
				<tr>
					<td>可乐</td>
					<td>10</td>
					<td><input type = "checkbox" name = "bill" value = "3"/></td>
				</tr>
			</table>
			<input type = "submit" name = "submit" value = "提交" />
		</form>
		<%
			try{
				Double d = (Double)request.getAttribute("sum");
				if(d == null) {}
				else{
					out.print("价格总计" + d + "元");
				}
			}
			catch(NumberFormatException e){
			}

		%>
	</body>
</html>
```

## 共享变量

Servlet 类是 **HttpServlet** 的一个子类，在编写子类时就可以声明某些成员变量。
请求该 Servlet 类所创建的 servlet 的用户将共享该 servlet 的成员变量。

## 使用 session

用户在访问一个 Web 服务目录期间，服务器为该用户分配一个 session 对象，服务器可以在各个页面以及 servlet 中使用这个 session 记录当前用户的有关信息，而且服务器保证不同用户的 session 对象互不相同。

```java
HttpSession session = request.getSession(true);
```
