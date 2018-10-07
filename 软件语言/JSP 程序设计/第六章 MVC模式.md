[toc]

## MVC 模式介绍

**模型-视图-控制器**（Model-View-Controller），简称为 MVC。

- 模型是应用程序中用于 **处理应用程序数据逻辑** 的部分，通常模型对象负责在数据库中 **存取数据**。
- 视图是应用程序中 **处理数据显示** 的部分，通常视图是 **依据模型数据创建的**。
- 控制器是应用程序中 **处理用户交互** 的部分，通常控制器负责 **从视图读取数据，控制用户输入，并向模型发送数据**。

## JSP 中的 MVC 模式

- 模型：Javabean
- 视图：JSP
- 控制器：servlet

## 模型的生命周期与视图更新

JSP + Javabean 模式

```xml
<jsp:useBean id = "名字" class = "创建 bean 的类" scope = "生命周期" />
<jsp:getProperty name = "名字" property = "bean 的属性" />
```

下面讨论在 MVC 模式下 Javabean 的使用。

### request 周期的 Javabean

Javabean 的创建：

```java
BeanClass bean = new BeanClass();
request.setAttribute("keyword", bean);
```

视图更新：

```
request.getRequestDispatcher("指定的 JSP 页面.jsp").forward(request, response);
<jsp:useBean id = "keyword" type = "user.yourBean.BeanClass" scope = "request" />
<jsp:getProperty name = "keyword" property = "bean 的变量" />
```

> 注意 `<jsp:useBean>` 标记与上面 JSP + Javabean 的区别。

### session 周期的 Javabean

Javabean 的创建

```java
BeanClass bean = new BeanClass();
request.session(true).setAttribute("keyword", bean);
```

视图更新：

```xml
<jsp:useBean id = "keyword" type = "user.yourBean.BeanClass" scope = "session" />
<jsp:getProperty name = "keyword" property = "bean 的变量" />
```

### application 周期的 Javabean

Javabean 的创建

```java
BeanClass bean = new BeanClass();
getServletContext().setAttribute("keyword", bean);
```

视图更新：

```xml
<jsp:useBean id = "keyword" type = "user.yourBean.BeanClass" scope = "application" />
<jsp:getProperty name = "keyword" property = "bean 的变量" />
```
