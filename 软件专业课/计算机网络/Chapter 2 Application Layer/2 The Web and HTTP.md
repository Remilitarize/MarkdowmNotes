[toc]

**WWW (World Wide Web) 万维网**

## Overview of HTTP  HTTP 概况

The **HyperText Transfer Protocol(HTTP)**, the Web's application-layer protocol, is at the heart of the Web.
Web 的应用层协议是 **超文本传输协议（HTTP）**， 它是 Web 的核心。

- A **Web page** (also called a document) consists of objects. **Web 页面**（也叫文档）是由对象组成的。
- An **object** is simply a file —— such as an HTML file, a JPEG image, a Java applet, or a vidow clip —— that is addressable by a single **URL**.
  **对象** 简单来说就是文件，如 HTML 文件、JPEG 图形文件、Java 小程序或视频片段文件，这些文件可通过一个 **URL** 地址寻址。
- Most Web pages consist of a **base HTML file** and several **referenced objects**.
  多数 Web 页面含有一个 **基本 HTML 文件** 以及几个 **引用对象**。
	- The number of objects = The number of referenced objects + 1 对象的数量 = 引用对象的数量 + 1
- Each URL has two components: 每个 URL 地址由两部分组成:
	- **The hostname of the server that houses the obejct 存放对象的服务器主机名**
	- **The object's path name 对象的路径名**

> `http://www.someSchool.edu/someDepartment/picture.gif`
  `www.someSchool.edu` for a hostname. 主机名就是 `www.someSchool.edu`。
	`/someDepartment/picture.gif` for a path name. 路径名就是 `/someDepartment/picture.gif`。

- **Web browsers** implement the client side of HTTP. **Web 浏览器** 实现了 HTTP 的客户机端。
- **Web servers** implement the server side of HTTP. **Web 服务器** 实现了 HTTP 的服务器端。

When a user requests a Web page, the browser sends **HTTP request messages** for the objects in the page to the server.
当用户请求一个 Web 页面时，浏览器向服务器发出对该页面中所包含对象的 **HTTP 请求报文**。
The server receives the requests and responds with **HTTP response messages** that contain the obejcts.
服务器接收请求并用包含这些对象的 **HTTP 响应报文** 进行相应。

![HTTP 的请求-响应行为](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/HTTPRequest-responseBehavior.png)

HTTP uses **TCP** as its underlying transport protocol(rather than rumming on top of UDP).
HTTP 使用 **TCP**（而不是UDP）作为它的支撑运输层协议。
Because an HTTP server maintains on information about the clients, HTTP is said to be a **stateless protocol**.
因为一个 HTTP 服务器并不保存关于客户机的任何信息，所以我们说 HTTP 是一个 **无状态协议**。

## Non-persistent and Persistent Connections 非持久连接和持久连接

When this client-server interaction is taking place over TCP, the application developer needs to make an important decision:
当这种客户机/服务器的交互运行于 TCP 协议之上时，应用程序的研制者需要确定：

- Each request/response pair be sent over a **separate** TCP connection.
  每个请求/响应对是经一个 **单独** 的 TCP 连接发送。
	- **Non-persistent connection 非持久连接**
- All of the requests and their corresponding responses be sent over the **same** TCP connection.
  所有的请求以及相应的响应经 **相同** 的 TCP 连接发送。
	- **Persistent connection 持久连接**

> HTTP uses persistent connections in its default mode. 默认方式下 HTTP 使用持久连接。

### HTTP/1.0

Non-persistent connection 非持久连接

![HTTP 1.0](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/HTTP1.png)

- Step 1 and Step 2 步骤1和步骤2
	- The HTTP cilent process initiates a TCP connection to the server `www.someSchool.edu` on **port number 80**.
	  HTTP 客户机进程在 **端口号 80** 发起一个到服务器 `www.someSchool.edu` 的 TCP 连接。
	- Port number 80 is the default port number for HTTP. 端口号 80 是 HTTP 的默认端口。
	- Associated with the TCP connection, there will be a **socket** at the client and a socket at the server.
	  客户机和服务器上分别有一个 **套接字** 与该连接相关联。
- Step 3 步骤3
	- The HTTP client sends an **HTTP request message** to the server via its socket.
	  HTTP 客户机经它的套接字向服务器发送一个 **HTTP 请求报文**。
	- The request message includes the path name `/someDepartment/home.index`.
	  请求报文中包含了路径名 `/someDepartment/home.index`。
- Step 4 步骤4
	- The HTTP server process receives the request message via its socket.
	  HTTP 服务器进行经它的接受该请求报文。
	- Retrieves the object `/someDepartment/home.index` from its storage, encapsulates the obejct in an **HTTP response message**.
	  从存储器中检索出对象 `/someDepartment/home.index`，在一个 **HTTP 响应报文** 中封装对象。
	- Sends the response message to the client via its socket. 通过其套接字向客户机发送响应报文。
	- The HTTP server process tells TCP to close the TCP connection. HTTP 服务器进程通知 TCP 断开该 TCP 连接。
	- The HTTP client receives the response message. The TCP connection terminates.
	  HTTP 客户机接收响应报文，TCP 连接关闭。
- The steps are then repeated for each of the referenced objects. 对每个引用对象对象重复步骤。

Conclusion 结论：**"Three-way handshake" 三次握手**

Define the **round-trip time(RTT)**, which is the time it takes for a small packet to travel from client to server and then back to the client.
定义 **往返时间** 为一个小分组从客户机到服务器再回到客户机所花费的时间。

The total response time T = RTT(TCP) + RTT(HTTP) + Transmission time
总响应时间 T = 往返时间（TCP） + 往返时间（HTTP） + 传输时间

### HTTP/1.1

Persistent connection 持久连接

#### Without pipelining 非流水型

![HTTP 1.1 非流水型](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/HTTP1.1WithoutPipelining.png)

The total response time T = RTT + (RTT + Transmission time) \* The number of objects
总响应时间 T = 往返时间 + （往返时间 + 传输时间）\++++* 对象数

#### With Pipelining 流水型

![HTTP 1.1 流水型](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/HTTP1.1WithPipelining.png)

The total response time T = RTT \* 3 + Transmission time \* The number of objects
总响应时间 T = 往返时间 \* 3 + 传输时间 \* 对象数

> The default mode of HTTP uses persistent connections with pipelining. HTTP 的默认模式使用流水型的持久链接。

## HTTP Message Format HTTP 报文格式

### HTTP Request Message HTTP 请求报文

```http
GET /somedir/page.html HTTP/1.1
Host: www.someschool.edu
Connection: close
User-agent: Mozilla/4.0
Accept-language: fr

```

- The message is written in ordinary **ASCII text**. 报文是用普通的 **ASCII 文本** 书写的。
- The message consists of five lines, each followed by a carriage return and a line feed.
  报文含有 5 行，每行用一个回车换行符结束。
- The last line is followed by an **additional carriage return and line feed**.
  最后一行后跟有 **附加的回车换行符**。
- The first line of an HTTP request message is called the **request line**; the subsequent lines are called the **header lines**.
  HTTP 请求报文的第一行叫做 **请求行**，其后继的行叫做 **首部行**。
- The request line has three fields: **the method field**, **the URL field**, and **the HTTP version field**.
  请求行有 3 个字段：**方法字段**、**URL 字段** 和 **HTTP 协议版本字段**。
	- The method field can take on several different values, including `GET`/`POST`/`HEAD`/`PUT`/`DELETE`.
	  方法字段可以取值 `GET`/`POST`/`HEAD`/`PUT`/`DELETE`。
		- HTTP/1.0：`GET`（获取请求）/`POST`（发送表单）/`HEAD`（调试时使用）
		- HTTP/1.1：`GET`/`POST`/`HEAD`/`PUT`（上传）/`DELETE`（删除）
	- The `GET` method is used when the browser requests an object, with the requested object identified in the URL field.
	  当浏览器请求一个对象时，使用 `GET` 方法，在 URL 字段填写该对象的 URL 地址。
- The header line `Host: www.someschool.edu` specifies the host on which the object resides.
  首部行 `Host: www.someschool.edu` 定义了目标所在的主机。
- By including the `Connection: close` header line, the browser is telling the server that it doesn't want to bother with persistent connections; it wants the server to close the connection after sending the requested object.
  通过包含 `Connection: close` 首部行，浏览器告诉服务器不希望麻烦地使用持久连接，它要求服务器在发送完被请求的对象后就关闭连接。
- `User-agent: ` header line specifies the user agent, that is, the browser type that is making the request to the server.
  `User-agent: ` 首部行用来定义用户代理，即向服务器发送请求的浏览器的类型。
- `Accept-language: fr` header indicates that the user prefers to receive a French version of the object, if such an object exists on the server; otherwise, the server should send its default version.
  `Accept-language: fr` 首部行表示用户想得到该对象的法语版本（如果服务器中有这样的对象），否则，使用服务器的默认版本。

![HTTP 请求报文的通用格式](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/GeneralFormatOfAnHTTPRequestMessage.png)

- Notice that after the header lines (and the additional carriage return and line feed) there is an **"entity body"**.
  注意到在首部行（和附加的回车换行符）后有一个 **"实体主体"**。
- The entity body is empty with the `GET` method, but is used with the `POST` method.
  使用 `GET` 方法时实体主体为空，而是用 `POST` 方法时才使用。

### HTTP Response Message HTTP 响应报文

```html
HTTP/1.1 200 OK
Connection: close
Date: Thu, 07 Jul 2007 12:00:15 GMT
Server: Apache/1.3.0 (Unix)
Last-Modified: Sun, 6 May 2007 09:23:24 GMT
Content-Length: 6821
Content-Type: text/html

(data data data ...)
```

- It has three sections: an **initial status line**, six **header lines**. and then the **entity body**.
  有三部分：一个 **初始状态行**，6 个 **首部行**，然后是 **实体主体**。
- The entity body is the meat of the message —— it contains the requested object itself.
  实体主体部分是报文的追她，即它包含了所请求的对象本身。
- The status line has three fields: the **protocol version field**, a **status code**, and a **corresponding status message**.
  状态行有 3 个字段：**协议版本**、**状态码** 和 **相应状态信息**。
- The server uses the `Connection: close` header line to tell the client that it is going to close the TCP connection after sending the message.
  服务器用 `Connection: close` 首部行告诉客户机在报文发送完后关闭了该 TCP 连接。
- `Date: ` header line indicates the time and date when the HTTP response was created and sent by the server.
  `Date: ` 首部行指示服务器产生并发送该响应报文的日期和时间。
- `Server: Apache/1.3.0 (Unix)` header line indicates that the message was generated by an Apache Web server.
  `Server: Apache/1.3.0 (Unix)` 首部行表明该报文是由一个 Apache Web 服务器产生的。
- `Last-Modified: ` header line indicates the time and date when the object was created or last modified.
  `Last-Modified: ` 首部行指示了对象创建或者最后修改的日期和时间。
- `Content-Length: ` header line indicates the number of bytes in the object being sent.
  `Content-Length: ` 首部行表明了被发送对象的字节数。
- `Content-Type: text/html` header line indicates that the object in hte entity body is HTML text.
  `Content-Type: text/html` 首部行指示了实体主体中的对象是 HTML 文本。

|Status codes<br />状态码|Associated phrases<br />相关短语|Descriptions<br />描述|
|-|-|-|
|200|OK|Request succeeded.<br />请求成功。|
|301|Moved Pemanently|Requested object has been permanently moved.<br />请求的对象已经被永久转移了。|
|400|Bad Request|A generic error code.<br />通用差错代码。|
|404|Not Found|The requested decument does not exist on this server.<br />被请求的文档不在服务器上。|
|505|HTTP Version Not Supported|The request HTTP protocol wersion is not supported by the server.<br />服务器不支持请求报文使用的 HTTP 协议版本。|

## User-Server Interaction: Cookies 用户与服务器的交互：cookie

- An HTTP server is stateless. HTTP 服务器是无状态的。
- It is often desirable for a Web site to identify users. 然而一个 Web 站点通常希望能够识别用户。
- HTTP uses **cookies**, which allow sites to keep track of users. HTTP 使用 **cookie**，其允许站点跟踪用户。

![用 cookie 保持用户状态](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/KeepingUserStateWithCookies.png)

Cookie technology has four components: cookie 技术有 4 个组成部分：

- A cookie header line in the HTTP response message. 在 HTTP 响应报文中有一个 cookie 首部行。
- A cookie header line in the HTTP request message. 在 HTTP 请求报文中有一个 cookie 首部行。
- A cookie file kept on the user's end system and managed by the user's browser. 在用户端系统中保留有一个 cookie 文件，由用户的浏览器管理。
- A back-end database at the Web site. 在 Web 站点有一个后端数据库。

The cookie header line in the HTTP response message may be:
在 HTTP 响应报文中的c ookie 首部行可能是：

```http
Set-cookie: 1678
```

Then the cookie header line in the HTTP request message must be:
接下来在 HTTP 请求报文中的 cookie 首部行一定是：

```http
Cookie: 1678
```

One week later, browser will continue to put the header line `Cookie: 1678` in the request message.
一个星期后，浏览器会在其请求报文中继续使用首部行 `Cookie: 1678`。

## Web Caching Web 缓存

A **Web cache** —— also called a **proxy server** —— is a network entity that saticfies HTTP requests on the behalf of an origin Web server.
**Web 缓存器**，也叫 **代理服务器**，它是能够代表初始 Web 服务器来满足 HTTP 请求的网络实体。

![Web 缓存器](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/WebCache.png)

- The browser establishes a TCP connection to the Web cache and sends an HTTP request for the object to the Web cache.
  浏览器建立一个到 Web 缓存器的 TCP 连接，并向 Web 缓存器中的对象发送一个 HTTP 请求。
- The Web cache checks to see if it has a copy of the object stored locally.
  Web 缓存器检查本地是否存储了该对象拷贝。
	- If does, the Web cache returns the object within an HTTP response message to the client browser.
	  如果有，Web 缓存器就用 HTTP 响应报文向客户机浏览器返回该对象。
	- If not, the Web cache opens a TCP connection to the origin server. The Web cache then sends an HTTP request for the object into the cache-to-server TCP connection.After receiving this request, the origin server sends the object within an HTTP response to the Web cache.
	  如果没有，它就与该对象的初始服务器打开一个 TCP 连接。Web 缓存器则在 TCP 连接上发送获取该对象的 HTTP 请求。在收到请求后，初始服务器向 Web 缓存器发送具有该对象的 HTTP 响应。
	- When the Web cache receives the object, it stores a copy in its local storage and sends a copy, within an HTTP response message, to the client browser.
	  当 Web 缓存器接收该对象时，它在本地存储空间存储了一份拷贝，并用 HTTP 响应报文向用户机的浏览器发送该拷贝。

> A cache is both a server and a client at the same time. Web 缓存器既是服务器又是客户机。

Web caching has seen deployment in the Internet for two reasons.
在因特网上部署 Web 缓存器有两个原因。

- A Web cache can substantially reduce the response time for a client request, particularly if the bottleneck bandwidth between the client and the origin server is much less than the bottleneck bandwidth between the client and the cache.
  Web 缓存器可以大大地减少对客户机请求的响应时间，特别是当客户机与初始服务器之间的瓶颈带宽远低于客户机与 Web 缓存器之间的瓶颈开髋时更是如此。
- Web caches can substantially reduce Web traffic in the Internet as a whole, thereby improving performance for all applications.
  Web 缓存器能从整体上大大降低因特网上的 Web 流量，从而改善了所有应用的性能。

### Traffic intensity 流量强度

![机构网络与因特网之间的瓶颈](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/GeneralFormatOfAnHTTPRequestMessage.png)

Suppose: 假设：
The average object size is 1 Mbits. 对象平均长度为 1 Mb。
The average request rate is 15 requests per second. 平均请求速率是 15 个请求每秒。

- The traffic intensity on the LAN is (15 requests/sec) * (1 Mbits/request) / (100 Mbps) = 0.15.
  局域网上的流量强度为（15 个请求/s） * （1 Mb/请求）/（100 Mbps）= 0.15。
- The traffic intensity on the access link is (15 requests/sec) * (1 Mbits/request) / (15 Mbps) = 1.
  接入链路上的流量强度为（15 个请求/s） * （1 Mb/请求）/（15 Mbps）= 1。

Solution： 解决方法

- To increase the access rate. 增加接入链路的速率。
	- Expensive 贵
- To install a Web cache in the institutional network. 安装一个 Web 缓存器。
	- The fraction of requests that are saticfied by a cache is the **hit rate**. 缓存器满足的请求的比率称为 **命中率**。

## The Conditional GET 条件 GET 方法

HTTP has a mechanism that allows a cache to verify that its objects are up to date. This mechanism is called the **conditional GET**.
HTTP 协议有一种机制，允许缓存器证实它的对象是最新的。这种机制就是 **条件 GET**。

An HTTP request message is a so-called conditional GET message if
如果满足下面两个条件，那么 HTTP 请求报文就是一个条件 GET 请求报文。

- The request message uses the GET method. 请求报文使用 GET 方法。
- The request message includes an `If-Modified-Since: ` header line. 请求报文中包含一个 `If-Modified-Since: ` 首部行。
