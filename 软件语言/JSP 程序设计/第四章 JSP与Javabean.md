[toc]

Javabean 是一个可重复使用的软件组件。

- 实际上，Javabean 是一种 Java **类**。
- 通过封装**属性**和**方法**成为具有某种功能或者处理某个业务的对象。

具有以下特点：

- 可以实现代码的重复利用。
- 易编写、易维护、易使用。
- 不需要重新编译。

## 编写 Javabean 和使用 Javabean

### 编写 Javabean

规则如下：

1. 如果类的成员变量的名字是 xxx，那么为了获取或更改成员变量的值，类中必须提供两个方法：
	- `getXxx()` 用来**获取**属性 xxx
	- `setXxx()` 用来**修改**属性 xxx
	- 方法的名字用 **get** 或 **set** 为前缀，后缀是将成员变量名字的**首字母大写**的字符序列。
2. 对于 `boolean` 类型的成员变量，允许使用 **is** 代替上面的 get 和 set。
3. 类中声明的方法的访问属性都必须是 **`public`** 的。
4. 类中声明的构造方法必须是 **`public`**、**无参数**的。

> 如果使用版本 Tomcat 5.x 之后的服务器，创建 bean 的类必须带有**包名**。

例：
```java
package tom;
public class Circle{
	double radius;
	public Circle(){
		radius = 1;
	}
	public double getRadius(){
		return radius;
	}
	public void setRadius(double newRadius){
		radius = newRadius;
	}
	public double circleArea(){
		return Math.PI * radius * radius;
	}
	public double circleLength(){
		return 2.0 * Math.PI * radius;
	}
}
```

### 保存 bean 的字节码

为了让 Tomcat 服务器能够找到字节码，字节码文件必须保存在特定的目录中。

1. 在当前 Web 服务目录下创建子目录结构：**\WEB-INF\classes**。
2. 根据类的包名，在 classes 下再建立相应的子目录。
3. 为了让 Tomcat 服务器起用上述 \WEB-INF\classes 目录，必须重新启动 Tomcat 服务器。
4. 将创建的 bean 的字节码文件复制到 \WEB-INF\classes\%包名%\ 中。

### 创建与使用 bean

- 使用 Javabean
	- 语法：`<jsp:useBean id = "bean 的名字" class = "创建 bean 的类" scope = "bean 有效页面" ></jsp:useBean>`
- bean 的加载原理
	- 当 JSP 页面使用 JSP 动作标记 useBean 加载一个 bean 时，JSP 引擎将首先根据 JSP 动作标记 useBean 给出的 bean 的 id 名字以及 scope 给出的使用范围（bean 生命周期）。
	- 在一个同步块中查找 JSP 引擎内置 **pageContent** 对象中是否含有这样的 bean。
	- 如果这样的 bean 存在，JSP 引擎就分配这样的 bean 给用户。
	- 如果在 pageContent 中没有查找到 JSP 动作标记要求的 bean，就根据 class 指定的字节码创建一个 JSP 动作标记 useBean 要求的 bean，并将所创建的 bean 添加到 pageContent 内置对象中。
- bean 的有效范围（生命周期）
	- `scope` 的取值范围给出了 bean 的存活时间（生存周期）。
	- 取值 **`page`**
		- bean 的有效范围是 page 期间，即 **当前页面**。
		- JSP 引擎分配给每个 JSP 页面的 page 期间的 bean 是 **互不相同的**。
		- **不同用户的 bean 也是互不相同的**。
	- 取值 **`session`**
		- bean 的有效范围是用户的 **session 期间**。
		- 同一个用户在所有页面的到的 bean 是 **同一个**。
		- **不同的用户的 bean 是互不相同的**。
		- 保证用户端支持 Cookie。
	- 取值 **`request`**
		- bean 的有效范围时 request 期间，即只在 **当前页面有效，直到响应结束**。
		- 存活时间略长于 page。
		- **不同用户的 bean 也是互不相同的**。
	- 取值 `application`
		- bean 的有效范围是 **application 期间**。
		- Web 服务目录下所有 JSP 页面 **分配一个共享的 bean**。
		- **不同用户的 bean 也都是相同的一个**。

## 获取和修改 bean 的属性

### getProperty 动作标记

使用 `getProperty` 动作标记可以获得 bean 的属性值，并将这个值用字符串的形式发送给用户的浏览器。

> 使用 `getProperty` 动作标记之前，必须使用 useBean 动作标记获得相应的 bean。

- 语法：
	- `<jsp:getProperty name = "bean 的 id 的名字" property = "bean 的属性"></jsp:getProperty>`
- 相当于 Java 表达式 `<%= bean.getXxx() %>`

### setProperty 动作标记

使用 `setProperty` 动作标记可以设置 bean 的属性值。

> 使用 `setProperty` 动作标记之前，必须使用 useBean 动作标记获得相应的 bean。

#### 将 bean 属性的值设置为一个表达式的值或字符串

- 语法：
	- 将 bean 属性的值设置为一个表达式的值的语法格式
		- `<jsp:setProperty name = "bean 的 id 的名字" property = "bean 的属性" value = "<%= 表达式 %>" />`
	- 将 bean 属性的值设置为一个字符串语法格式
		- `<jsp:setProperty name = "bean 的 id 的名字" property = "bean 的属性" value = "字符串" />`

> Java 语言讲字符串转化为其他数值类型的方法：

>  - 转化到 `int`：`Integer.parseInt(String s)`
  - 转化到 `long`：`Long.parseLong(String s)`
  - 转化到 `float`：`Float.parseFloat(String s)`
  - 转化到 `double`：`Double.parseDouble(String s)`

> 这些方法都可能发生 `NumberFormatException` 异常。

#### 通过 HTTP 表单的参数的值来设置 bean 的相应属性的值

- 语法：
	- 用 HTTP 表单的所有参数的值设置 bean 相对应的属性值
		- `<jsp:setProperty name = "bean 的 id 的名字" property = "*" />`
		- **要求 bean 属性的名字必须在表单中有名称相同的参数名字相对应**。
	- 用 HTTP 表单的某个参数的值设置 bean 的某个属性值
		- `<jsp:setProperty name = "bean 的名字" property = "属性名" param = "参数名" />`

## bean 的辅助类

有时在写一个 bean 的时候，除了需要用 import 语句引入 JDK 平台提供的类，可能还需要自己编写一些其他的类。
只要将这些类和创建 bean 的类写在一个 Java 源文件中即可，但必须将源文件编译后 **产生的全部字节码文件复制到相应的目录** 中。

## JSP 与 bean 结合的简单例子

例：计算三角形面积

triangle.Java

```Java
package re;

public class triangle{
	private double sizeA, sizeB, sizeC;
	private boolean triangle;

	public triangle() {
		sizeA = sizeB = sizeC = 0.0;
	}

	public void setSizeA(double sizeA) {
		this.sizeA = sizeA;
	}

	public void setSizeB(double sizeB) {
		this.sizeB = sizeB;
	}

	public void setSizeC(double sizeC) {
		this.sizeC = sizeC;
	}

	public double getSizeA() {
		return sizeA;
	}

	public double getSizeB() {
		return sizeB;
	}

	public double getSizeC() {
		return sizeC;
	}

	public double getArea() {
		double p = (sizeA + sizeB + sizeC) / 2.0;
		isTriangle();
		if(triangle) {
			return Math.sqrt(p * (p - sizeA) * (p - sizeB) * (p - sizeC));
		}
		else {
			return 0.0;
		}
	}

	public boolean isTriangle() {
		if(sizeA < (sizeB + sizeC) && sizeB < (sizeA + sizeC) && sizeC < (sizeA + sizeB)) {
			triangle = true;
		}
		else {
			triangle = false;
		}
		return triangle;
	}
}
```

test.jsp

```xml
<%@ page contentType = "text/html; charset = UTF-8" pageEncoding = "UTF-8" language = "java" %>
<!DOCTYPE html>
<jsp:useBean id = "tri" class = "re.triangle" scope = "request" />
<html>
<head>
	<title>计算三角形面积</title>
	<meta name = "author" content = "Remilitarize" />
	<meta name = "generator" content = "Eclipse EE" />
</head>
<body>
	<p>输入三角形的三边：</p>
	<form action = "" method = "get">
		边 a：<input type = "text" name = "sizeA" size = "5" maxlength = "5" />
		边 b：<input type = "text" name = "sizeB" size = "5" maxlength = "5" />
		边 c：<input type = "text" name = "sizeC" size = "5" maxlength = "5" />
		<input type = "submit" value = "提交" />
	</form>
	<jsp:setProperty name = "tri" property = "*" />
	<%
		if(tri.getSizeA() != 0.0 || tri.getSizeB() != 0.0 || tri.getSizeC() != 0.0){
			%>
			<p>三角形的三边是：</p>
			<jsp:getProperty name = "tri" property = "sizeA" />
			<jsp:getProperty name = "tri" property = "sizeB" />
			<jsp:getProperty name = "tri" property = "sizeC" /><br />
		<%	boolean triangle = tri.isTriangle();
			out.print("这三个边能构成一个三角形吗？" + triangle + "<br />");
			if(triangle){
				out.print("面积是：" + tri.getArea());
			}
		}
	%>
</body>
</html>
```
