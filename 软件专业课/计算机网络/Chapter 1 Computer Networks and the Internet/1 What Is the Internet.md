[toc]

## A Nuts-and-Bolts Description 具体构成描述

![Some pieces of the Internet](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/Internet.png)

The **computers and other devices** connected to **the Internet** are often referred to as **end systems**.
与 **因特网** 相连的 **计算机等设备** 通常称为 **端系统**

> End systems = **Hosts** 端系统等于 **主机**

End systems are connected together by a network of **communication links** and **packet switches**.
端系统通过 **通信链路** 和 **分组交换机** 连接到一起。

- There are many types of communication links, which are made up of different types of physical media.
  有许多不同类型的物理媒介组成许多类型的通信链路。
	- Coaxial cable 同轴电缆
	- Copper wire 铜线
	- Fiber optics 光纤
	- Radio spectrum 无线电频谱
- The **transmission rate** of a link measured in **bits/second**. 链路的 **传输速率** 是以 **bps** 度量的。

When one end system has data to send to another end system, the sending end system **segments** the data and **adds header bytes** to each segment.
当一台端系统有数据要向另一台端系统发送时，发送端系统将数据 **分段**，并为每段 **加上首部字节**。

- The resulting packages of information are called **packets**. 由此形成的信息包称为 **分组**。

A packet switch takes a packet arriving on one of its incoming communication links and forwards that packet on one of its outgoing communication links.
分组交换机从它的一条入通信链路接收到达的分组，并从它的一条出通信链路转发该分组。

- **Router 路由器**
- **Link-layer switch 链路层交换机**

From the sending end system to the receiving end system, the sequence of communication links and packet switches traversed by a packet is known as a **route** or **path**.
从发送端系统到接收端系统，一个分组所经历的一系列通信链路和分组交换机称为通过该网络的 **路径**。

End systems access the Internet through **Internet Service Providers(ISPs).**
端系统通过 **因特网服务提供商** 接入因特网。

End systems, packet switches, and other pieces of the Internet run **protocols** that control the sending and receiving of information within the Internet.
端系统、分组交换机和其他因特网部件，都要运行控制因特网中信息接收和发送的一系列 **协议**。

- **Transmission Control Protocol(TCP)** and the **Internet Protocol(IP)** are two of the most important protocols in the Internet.
  **TCP（传输控制协议）** 和  **IP（网际协议）** 是因特网中两个最为重要的协议。
- The Internet's principal protocols are collectively known as **TCP/IP**. 因特网主要的协议统称为 **TCP/IP**。

There are also many private networks, whose hosts cannot exchange messages with hosts outside of the private network.
有许多专用网络，其主机不能与专用网络外部的主机交换信息。
These private networks are often referred to as **intranets**.
这些专用网络常被称为 **内联网**。

## A Services Description 服务描述

The applications are said to be **distributed applications** since they involve multiple end systems that exchange data with each other.
涉及多台相互交换数据的端系统中的应用程序称为 **分布式应用程序**。

**Application Programming Interface(API)** specifies how a software piece running on one end system asks running on another end system.
**API（应用程序编程接口）** 规定了运行在一个端系统上的软件请求因特网技术设施向运行在另一个端系统上的特定目的地软件交互数据的方式。

## What Is a Protocol? 什么是协议？

![A human protocol and a computer network protocol](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/Protocol.png)

In our human protocol, there are specific messages we send, and specific actions we take in response to the received reply messages or other events.
在人类协议中，有我们发送的特定报文，有我们根据接收到的应答报文或其他事件。

A **protocol** defines the **format** and the **order** of messages exchanged between two or more communication entities, as well as the **actions** taken on the transmission and/or receipt of a message or other event.
一个 **协议** 定义了在两个或多个通信实体之间交换的报文 **格式** 和 **次序**，以及在报文传输和/或接收或其他事件方面所采取的 **动作**。
