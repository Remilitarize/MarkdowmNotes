[toc]

![因特网单子邮件系统](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/ElectronicMail.png)

It has three major components: 有 3 个主要组成部分：

- **User agents 用户代理**
	- Sometimes called **mail readers**. 有时叫做 **邮件阅读器**。
- **Mail servers 邮件服务器**
	- Mail servers form the core of the e-mail infrastructure. 邮件服务器组成了电子邮件体系结构的核心。
	- Each recipient has a **mailbox** located in one of the mail servers. 每个接收方在其中的某个服务器上有一个 **邮箱**。
- **Simple Mail Transfer Protocol(SMTP) 简单邮件传输协议**
	- SMTP is the principal **application-layer protocol** for Internet electronic mail.
	  SMTP 是因特网电子邮件中主要的 **应用层协议**。
	- It uses the reliable data transfer service of TCP. 它使用 TCP 可靠数据传输服务。

## SMTP

**SMTP is at the heart of Internet electronic mail. SMTP 是因特网电子邮件应用的核心。**

Suppose Alice wants to send Bob a simple ASCII message: 假设 Alice 想给 Bob 发送一封简单的 ASCII 报文：

![发送邮件](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/SendAMessage.png)

1. Alice invokes her **user agent** for e-mail, provides Bob's e-mail address, composes a message, and instructs the user agent to send the message.
  Alice 调用她的 **邮件代理程序** 并提供 Bob 的邮件地址，撰写邮件，然后通过用户代理发送该邮件。
2. Alice's user agent sends the message to her **mail server**, where it is placed in a **message queue**.
  Alice 的用户代理把报文发给 Alice 的 **邮件服务器**，在服务器中该报文被放在 **报文发送队列** 中。
3. The client side of **SMTP**, running on Alice's mail server, sees the message in the message queue.It opens a TCP connection to an SMTP server, running on Bob's mail server.
  运行在 Alice 邮件服务器上的 SMTP 客户机端发现了报文发送队列中的这个报文，它就创建一个到运行在 Bob 的邮件服务器上的 SMTP 服务器的 TCP 连接。
4. After some initial SMTP **handshaking**, the SMTP client sends Alice's message into the TCP connection.
  在经过一些初始 SMTP 握手之后，SMTP 客户机通过该 TCP 连接发送 Alice 的报文。
5. At Bob's mail server, the server side of SMTP receives the message. Bob's mail server then places the message in Bob's **mailbox**.
  在 Bob 的邮件服务器上，SMTP 的服务器端接收该报文，Bob 的邮件服务器然后将该报文放入 Bob 的 **邮箱** 中。
6. Bob invokes his user agent to read the message at his convenience.
  在 Bob 方便的时候，他调用用户代理阅读该报文。

In particular, if Bob's mail server is down, the message remains in Alice's mail server and waits for a new attempt —— the message does **not get placed in some intermediate mail server**.
特别是，如果 Bob 的邮件服务器没有开机，该报文会保留在 Alice 的邮件服务器上并在稍后进行新的尝试，这意味着邮件并 **不在中间的某个邮件服务器上存留**。

> The client SMTP (running on the sending mail server host) has TCP establish a connection to **port 25** at the server SMTP (running on the receiving mail server host).
  SMTP 客户机（运行在发送邮件服务器上）在 **25 号端口** 建立一个到 SMTP 服务器（运行在接收邮件服务器上）的 TCP 连接。

Take a look at an example transcript of messages exchanged between an SMTP client(C) and an SMTP server(s).
分析 SMTP 客户机（C）和 SMPT 服务器（S）之间交换报文脚本的例子。

- The hostname of client is `crepes.fr`. 客户机的主机名为 `crepes.fr`。
- The hostname of server is `hamburger.edu`. 服务器的主机名为 `hamburger.edu`。

```http
S: 220 hamburger.edu
C: HELO crepes.fr
S: 250 Hello crepes.fr, pleased to meet you
C: MAIL FROM: <alice@crepes.fr>
S: 250 alice@crepes.fr ... Sender ok
C: RCPT TO: <bob@hamburger.edu>
S: 250 bob@hamburger.edu ... Recipient ok
C: DATA
S: 354 Enter mail, end with "." on a line by itself
C: Do you like ketchup?
C: How about pickles?
C: .
S: 250 Message accepted for delivery
C: QUIT
S: 221 hamburger.edu closing connection
```

- The client sends a message ("Do you like ketchup? How about pickles?") from mail server `crepes.fr` to mail server `hamburger.edu`.
  客户机程序从邮件服务器 `crepes.fr` 向邮件服务器 `hamburger.edu` 发送了一个报文。
- As part of the dialogue, the client issued five commands: `HELO`/`MAIL`/`FROM`/`RCPT`/`TO`/`DATA`/`QUIT`.
  作为对话的一部分，该客户机发送了 5 条命令：`HELO`/`MAIL`/`FROM`/`RCPT`/`TO`/`DATA`/`QUIT`。
- The client also sends a line consisting of a single period, which indicates the end of the message to the server.
  该客户机通过发送一个只包含一个句点的行，告诉服务器该报文结束了。
- The server issues replies to each command, with each reply having a **reply code** and some English-language explanation.
  服务器对每条命令做出回答，其中每个回答含有一个 **回答码** 和一些英文解释。
- Issues `QUIT` only after all messages have been sent. 仅当所有邮件发送完后才发送 `QUIT`。

## Comparison with HTTP  与 HTTP 的对比

The same points: 相同点：

- Both protocols are used to transfer files from one host to another. 两个协议都用于从一台主机向另一台主机传送文件。
- Both persistent HTTP and SMTP use persistent connections. HTTP 和 SMTP 都使用持久连接。

Teh differences: 不同点：

1. First 第一
 	- HTTP is mainly a **pull protocol** —— someone loads information on a Web server and users use HTTP to pull the information from the server at their convenience.
    HTTP 主要是一个 **拉协议**，即人们可以在方便的时候装载 Web 服务器上的信息。
	- In particular, the TCP connection is initiated by the machine that **wants to receive the file**.
	  特别地，TCP 连接是由 **想获取文件** 的机器发起的。
	- SMTP is primarily a **push protocol** —— the sending mail server pushes the file to the receiving mail server.
    SMTP 基本上是一个 **推协议**，即发送邮件服务器把文件推向接受邮件服务器。
	- In particular, the TCP connection is initiated by the machine that **wants to send the file**.
	  特别地，TCP 连接是由 **要发送文件** 的机器发起的。
2. Second 第二
	- SMTP requires each message, including the body of each message, to be in 7-bits ASCII format.
	  SMTP 要求每个报文（包括它们的主体）都使用 7 位的 ASCII 码格式。
	- HTTP data does not impose this restriction. HTTP 数据则没有这个限制。
3. Third 第三
	- HTTP encapsulates **each** object in its own HTTP response message.
	  HTTP 把 **每个** 对象封装到它自己的 HTTP 响应报文中。
	- Internet mail places **all** of the message's objects into **one** message.
	  因特网电子邮件则把 **所有** 报文对象放在 **一个** 报文中。
4. Last 最后
	- HTTP uses in-band control. HTTP 使用带内控制。
	- FTP uses out-of-band control. FTP 使用带外控制。

## Mail Message Formats and MIME 邮件报文格式和 MIME

When an e-mail message is sent from one person to another, a header containing peripheral information precedes the body of the message itself.
当从一个人给另一个人发送电子邮件时，在报文主体前面附有环境信息。
This peripheral information is contained in a series of header lines.
这些环境信息包括在一系列首部行中。

```http
From: alice@crepes.fr
To: bob@hamburger.edu
Subject: Serching for the meaning of life

(....)
```

- The headerlines and the body of the message are separated by **a blank line**.
  首部行和报文主体用 **空行** 进行分隔。
- Each header line consists of a **keyword** followed by a colon followed by a value.
  每个首部行由 **关键词** 后跟冒号再后跟值组成的。
- Every header must have a `From: ` header line and a `To: ` header line.
  每个首部都必须含有一个 `From: ` 首部行和一个 `To: ` 首部行。

### The MIME Extension for Non-ASCII Data 非 ASCII 码数据的 MIME 扩展

To send content other than ASCII text, the sending user agent must include additional headers in the message.
为发送非 ASCII 文本的内容，发送方的用户代理必须在报文中使用附加的首部行。

The two key MIME headers for supporting multimedia are the `Content-Type: ` header and the `Content-Transfer-Encoding: ` header.
支持多媒体的两个关键字 MIME 首部是 `Content-Type: ` 和 `Content-Transfer-Encoding: `。

- The `Content-Type: ` header allows the receiving user agent to take an appropriate action on the message.
  `Content-Type: ` 首部允许接收用户代理对报文采取适当的动作。
- When a user agent receives a message with these two headers, it first uses the value of the value of the `Content-Transfer-Encoding: ` header to convert the message body back to its original non-ASCII form, and then uses the `Content-Type: ` header to determine what actions it should take on the message body.
  当用户代理接收到包含这两个首部行的报文时，就会根据 `Content-Transfer-Encoding: ` 的值将报文主体还原成非 ASCII 的格式，然根据 `Content-Type: ` 首部行决定它应当采取何种动作来处理报文主体。

```http
From: alice@crepes.fr
To: bob@hamburger.edu
Subject: Picture of yummy crepe.
MIME-Version: 1.0
Content-Transfer-Encoding: base64
Content-Type: image/jpeg

(base64 encoded data ...
........................
... base64 encoded data)
```

### The Received Message 接收的报文

The receiving server, upon receiving a message with RFC 822 and MIME header lines, appends a `Received: ` header line to the top of the message.
接收服务器一旦接收到具有 RFC 822 和 MIME 首部行的报文，就在该报文的顶部添加一个 `Received: ` 首部行。

This reader line specifies the name of the SMTP server that sent the message (from), the name of the SMTP server that received the message (by), and the time at which the receiving server received the message.
该首部行定义了发送该报文的 SMTP 服务器的名称（from），接收该报文的 SMTP 服务器的名称（by），以及接收服务器接收到的时间。

```http
Received: from crepes.fr by hamburger.edu; 12 Oct 98 15:27:39: GMT
From: alice@crepes.fr
To: bob@hamburger.edu
Subject: Picture of yummy crepe.
MIME-Version: 1.0
Content-Transfer-Encoding: base64
Content-Type: image/jpeg

(base64 encoded data ...
........................
... base64 encoded data)
```

## Mail Access Protocols 邮件访问协议

- **Post Office Protocol —— Version 3 (POP3) 第三版的邮局协议**
- **Internet Mail Access Protocol (IMAP) 因特网邮件访问协议**
- **HTTP 超文本传输协议**

![MailAccessProtocol](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/MailAccessProtocols.png)

### POP3

> Port number: 110  端口号：110

- **Authorization 特许**
	- The user agent sends a username and a password to authenticate the user. 用户代理发送用户名和口令以鉴别用户。
- **Transaction 事务处理**
	- The user agent retrieves message, mark messages for deletion, remove deletion marks, and obtain mail statistics.
	  用户代理取回报文，对报文做删除标记，取消报文删除标记，以及获取邮件的统计信息。
- **Update 更新**
	- Occurs after the client has issued the `quit` command, ending the POP3 session.
	  在客户机发出了 `quit` 命令之后发生，结束该 POP3 会话。
	- The mail server deletes the message that were marked for deletion.
	  邮件服务器删除被标记为删除的报文。

```http
C: list
S: 1 498
S: 2 912
S: .
C: retr 1
S: (message 1's body)
S: .
C: dele 1
C: retr 2
S: (message 2's body)
S: .
C: dele 2
C: quit
S: +OK POP3 server signing off
```

- Can't see the person whom the message was sent by. 看不到谁发送的报文。
- Stateless 无状态

### IMAP

- All of the messages place on the IMAP server. 所有报文存放在 IMAP 服务器上。
- An IMAP server will associate each message with a **folder**. IMAP 服务器把每个报文与一个 **文件夹** 联系起来。
- An IMAP server maintains user state information across IMAP sessions. IMAP 服务器维护了 IMAP 会话的用户状态信息。

### Web-Based E-mail 基于 Web 的电子邮件

- With this service, the user agent is an ordinary **Web browser**, and the user communicates with its remote mailbox wia **HTTP**.
  使用这种服务，用户代理就是普通的 **浏览器**，用户和其远程邮箱之间的通信通过 **HTTP** 进行。
- When a sender wants to send an e-mail message, the e-mail message is sent from the browser to the mail server over **HTTP** rather than over SMTP.
  当发件人要发送一封电子邮件报文时，该电子邮件报文从浏览器发送到邮件服务器，使用的是 **HTTP** 而不是 SMTP。
- However, still send message to, and receive message from, other mail servers using SMTP.
  然而，发送和接收邮件时仍使用 SMTP。
