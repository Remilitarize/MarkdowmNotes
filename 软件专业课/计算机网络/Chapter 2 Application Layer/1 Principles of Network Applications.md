[toc]

## Network Application Architectures 网络应用程序体系结构

The **application architecture** is designed by the application developer and dictates how the applicatiion is structured over the various end systems.
**应用程序体系结构** 由应用程序研发者设计，规定了如何在各种端系统上组织该应用程序。

- **Client-server architecture 客户机/服务器体系结构**
- **Peer-to-peer architecture 对等体系结构**

In a client-server architecture, there is an **always-on** host, called the **server**, which services **requests** from many other hosts, called **clients**.
在客户机/服务器体系结构中，有一个 **总是打开** 的主机称为 **服务器**，它服务于来自许多其他称为 **客户机** 的主机 **请求**。

- Clients **do not** directly communicate with each other. 客户机 **相互之间不** 直接通信。
- The server has a **fixed, well-known** address, called an IP address. 服务器具有 **固定的、周知的** 地址，称为 IP 地址、
- A cluster of hosts —— sometimes referred to as a **server farm** —— is often used to create a powerful **virtual server** in client-server architectures.
  常用主机群集（有时称为 **服务器场**）创建强大的 **虚拟服务器**。

In a **P2P architecture**, there is minimal (or no) reliance on always-on infrastructure servers.
在 **P2P 体系结构** 中，对总是打开的基础设施服务器又最小的（或者没有）依赖。
Instead the application exploits **direct communication** between pairs of intermittently connected hosts, called **peers**.
相反，任意简短连接的主机对 —— 称为 **对等方**，直接 **相互通信**。

> One of the most compelling features of P2P architectures is their **self-scalability**.
  P2P 体系结构的最突出特性之一是它的 **自扩展性**。

## Processes Communcating 进程通信

In the jargon of operating system, it is not actually programs but **processes** that communicate.
在操作系统的术语中，进行通信的实际上是 **进程** 而不是程序。

In the context of a communicatino session between a pair of processes, the process that **initiates the communication** (that is, initially contacts the other process at the beginning of the session) is labeled as the **client**.The process that **waits to be contacted** to begin the session is the **server**.
在给定的一对进程之间的通信会话中，**发起通信**（即在该会话开始时与其他进程联系）的进程被标志为 **客户机**，在会话开始时 **等待联系** 的进程是 **服务器**。

A process sends messages into, and receives messages from, the network through a software interface called a **socket**.
进程通过一个称为 **套接字** 的软件接口在网络上发送和接受报文。

- A socket is the interface between the application layer and the transport layer within a host.
  套接字是同一台主机内应用层和运输层之间的接口。

## Transport Services Available to Applications 可供应用程序使用的运输服务

- Reliable Data Transfer 可靠数据传输
  - If a protocol provides such a guaranteed data delivery service, it is said to provide **reliable data transfer**.
    如果一个协议提供了这样的确保数据交付服务，就提供了 **可靠数据传输**。
  - When a transport-layer protocol doesn't provide reliable data transfer, data sent by the sending process may never arrive at the receiving process. This may be acceptable for **loss-tolerant applications**.
    当一个运输层协议不提供可靠数据传输时，由发送进程发送的数据可能不能到达接收进程。对于 **容忍丢失的应用** 来说这是可以接受的。
- Throughput 吞吐量
  - Applications that have throughput requierments are said to be **bandwidth-sensitive applications**.
    具有吞吐量要求的应用程序称为 **带宽敏感的应用**。
  - While bandwidth-sensitive applications have specific throughput requirements, **elastic applications** can make use of as much, or as little, throughput as happens to be available.
    带宽敏感的应用需要提供一定的吞吐量，而 **弹性应用** 能够根据需要充分利用可供使用的吞吐量。
- Timing 定时
- Security 安全性

## Transport Services Provided by the Internet 因特网提供的运输服务

|Application<br />应用|Data Loss<br />数据丢失|Bandwidth<br />带宽|Time-Sensitive<br />时间敏感|
|-|-|-|-|
|File transfer<br />文件传输|No loss<br />不能丢失|Elastic<br />弹性|No<br />不|
|E-mail<br />电子邮件|No loss<br />不能丢失|Elastic<br />弹性|No<br />不|
|Web document<br />Web 文档|No loss<br />不能丢弃|Elastic(few kbps)<br />弹性（几 kbps）|No<br />不|
|Internet telephony<br />因特网电话|Loss-tolerant<br />容忍丢失|Audio: few kbps-1Mbps<br />音频（几 kpbs-1Mbps）|Yes: 100s of msec<br />是，100ms|
|Video conferencing<br />视频会议|Loss-tolerant<br />容忍丢失|Video: 10kbps-5Mbps<br />视频（10 kbps-5Mbps）|Yes: 100s of msec<br />是，100ms|
|Stored audio/video<br />存储音频/视频|Loss-tolerant<br />容忍丢失|Same as above<br />同上|Yes: few seconds<br />是，几秒|
|Interactive games<br />交互式游戏|Loss-tolerant<br />容忍丢失|Few kbps-10 kbps<br />几 kbps-10 kbps|Yes: 100s of msec<br />是，100ms|
|Instant messaging<br />即时讯息|No loss<br />不能丢失|Elastic<br />弹性|Yes and no<br />是和不是|

- TCP Services TCP 服务
  - **Connection-oriented service 面向连接服务**
  - **Reliable data transfer 可靠数据传输**
  - **Congestion-control mechanism 拥塞控制机制**
  - **Flow Control 流量控制**
- UDP Services UDP 服务
  - **Connectionless 无连接**
  - **Unreliable data transfer 不可靠数据传输**
  - **No guarantee 无保证**

Services Not Provided by Internet Transport Protocols 因特网运输层协议所不提供的服务

- **Throughput 吞吐量**
- **Timing 定时**

|Application<br />应用|Application-Layer Protocol<br />应用层协议|Underlying Transprot Protocol<br />支撑的运输层协议|
|-|-|-|
|Electronic mail<br />电子邮件|**SMTP**|TCP|
|Remote terminal access<br />远程终端访问|Telnet|TCP|
|Web|**HTTP**|TCP|
|File transfer<br />文件传输|**FTP**|TCP|
|Streaming multimedia<br />流媒体|HTTP/RTP|TCP or UDP|
|Internet telephony<br />因特网电话|SIP/RIP or proprietary|Typically UDP<br />通常用 UDP|

- In the Internet, the host is identified by its **IP address**. 在因特网中，主机使用 **IP 地址** 进行标识的。
- A destination **port number** identify the receiving process running in the host. 目的 **主机号** 标识运行在主机上的接收进程。

## Application-Layer Protocols 应用层协议

An **application-layer protocol** defines how an application's processes, running on defferent end systems, pass messages to each other.
**应用层协议** 定义了运行在不同端系统上的应用程序进程如何相互传递报文。

## Network Applications Convered in This Book 本书涉及的网络应用

略
