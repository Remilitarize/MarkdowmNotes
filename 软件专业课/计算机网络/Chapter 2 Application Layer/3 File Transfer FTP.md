[toc]

Same points between HTTP and FTP: HTTP 和 FTP 之间相同点：

- HTTP and FTP are both file transfer protocols. HTTP 和 FTP 都是文件传输协议。
- HTTP and FTP both run on top of TCP. HTTP 和 FTP 都运行在 TCP 上。

Differences between HTTP and FTP: HTTP 和 FTP 之间的不同点：

- FTP uses two parallel TCP connections to transfer a file, a **control connection** and a **data connection**.
  FTP 使用两个并行 TCP 连接来传输文件，一个是 **控制连接**，一个是 **数据连接**。
	- The control connection is used for sending control information between the two hosts and commands to "put" and "get" files.
	  控制丽娜姐用于在两个主机之间传输控制信息，以及 "put" 和 "get" 文件的命令。
	- The data connection is used to actually send a file. 数据连接用于实际传输一个文件。
- Because FTP uses a **separate** control connection, FTP is said to send its control information **out-of-band**.
  因为 FTP 协议使用一个 **分离** 的控制连接，所以我们也称 FTP 的控制信息是 **带外** 传送的。
- Because HTTP sends request and response header lines into the **same** TCP connection that carries the transferred file itself, HTTP is said to send its control information **in-band**.
  因为 HTTP 协议是在传输文件的 TCP 连接中发送请求和响应首部行，所以 HTTP 可以说是 **带内** 的。
- The FTP server must maintain **state** about the user. FTP 服务器必须保留用户的 **状态信息**。
	The HTTP is stateless. HTTP 是无状态的。

![FTP](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/FTP.png)

When a user starts an FTP session with a remote host, the client side of FTP first initiates a control TCP connection with the server side on server **port number 21**.
当用户主机与远程主机开始一个 FTP 会话前，FTP 的客户机首先在 **21 号端口** 上发起一起用于控制的与服务器的 TCP 连接。

### FTP Commands and Replies FTP 命令和回答

Some of the more common commands: 一些常见的命令：

- `USER username: ` Used to send the user identification to the server.
  `USER username: ` 用于向服务器传送用户标识。
- `PASS password: ` Used to send the user password to the server.
  `PASS password: ` 用于向服务器传送用户口令。
- `LIST: ` Used to ask the server to send back a list of all the files in the current remote directory.
  `LIST: ` 用于请求服务器返回远程主机当前目录的所有文件列表。
- `RETR filename: ` Used to retrieve (that is, get) a file from the current directory of the remote host.
  `RETR filename: ` 用于从远程主机的当前目录检索（即 get）文件。
- `STOR filename: ` Used to store (that is, put) a file into the current directory of the remote host.
  `STOR filename: ` 用于向远程主机的当前目录存放（即 put）文件。

The replies are three-digit numbers, with an optional message following the number.
回答是一个 3 位数字，后跟一个可选信息。

```http
311 Username OK, Password required
125 Data connection already open; transfer starting
425 Can't open data connections
452 Error writing file
```
