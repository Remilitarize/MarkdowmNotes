[toc]

A transport-layer protocol provides for **logical communication** between application processes running on different hosts.
运输层协议为运行在不同主机上的应用进程之间提供了 **逻辑通信** 功能。

Transport-layer protocols are implemented in the **end systems** but not in network routers.
运输层协议是在 **端系统** 中而不是在网络路由器中实现的。

On the sending side, the transport layer converts the messages it receives from a sending application process into transport-layer packets, known as **transport-layer segments** in Internet terminology.
在发送方，运输层将接收到的来自发送应用进程的报文转换成运输层分组，用因特网属于称其为 **运输层报文段**。

- This is done by breaking the application messages into **smaller chunks** and adding a **transport-layer header** to each chunk to create the transport-layer segment.
  将应用宝问划分为 **较小的块**，并为每块加上一个 **运输层首部** 来创建运输层报文段。
- The transport layer then passes the segment to the network layer at the sending end system, where the segment is **encapsulated** within a network-layer packet (a datagram) and sent to the destination.
  然后，在发送方端系统中，运输层将这些报文段传给网络层，网络层将其 **封装** 成网络层分组（一个数据报）并向目的地发送。
- On the receiving side, the network layer **extracts** the transport-layer segment from the datagram and passes the segment up to the transport layer.
  在接收方，网络层从数据报中 **提取** 运输层报文段，并将该报文段向上交给运输层。
- The transport layer then processes the received segment, making the data in the segment available to the receiving application.
  运输层则处理接收到的报文段，使得接收方应用进程可应用该报文段中的数据。

## Relationship Between Transport and Network Lyaers 运输层和网络层的关系

Whereas a transport-layer protocol provides logical communication between **processes** running on different hosts, a network-layer protocol provides logical communication between **hosts**.
运输层为运行在不同主机上的 **进程** 之间提供了逻辑通信，而网络层则提供了 **主机** 之间的逻辑通信。

## Overview of the Transport Layer in the Internet 因特网运输层概述

- **UDP(User Datagram Protocol) 用户数据报协议**
- **TCP(Transmission Control Portocol) 传输控制协议**

The Internet's network-layer protocol has a name —— **IP**, for the **Internet Protocol**.
因特网网络层协议有一个名字叫 **IP**，全程是 **网际协议**。

- The IP service model is a **best-effort delivery service**. IP 的服务模型是 **尽力而为交付服务**。
- IP is said to be an **unreliable service**. IP 被称为 **不可靠服务**。
- **Each host has an IP address. 每台主机有一个 IP 地址。**

The most fundamental responsibility of UDP and TCP is **to extend IP's delivery service between two end systems to a delivery service between two processes running on the end systems**.
UDP 和 TCP 最基本的任务是，**将两个端系统间 IP 的交付服务扩展为运行在两个端系统上的进程之间的交付服务**。
Extending host-to-host delivery to process-to-process delivery is called **transport-layer multiplexing** and **demultiplexing**.
将主机间交付扩展到进程间交付，称为 **运输层的多路复用** 与 **多路分解**。

- TCP provids **reliable data transfer**. TCP 提供 **可靠数据传输**。
- TCP also provides **congestion control**. TCP 还提供 **拥塞控制**。
- UDP traffic is **unregulated**. UDP 流量是 **不可调节的**。
