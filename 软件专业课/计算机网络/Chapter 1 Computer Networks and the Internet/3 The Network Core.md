[toc]

## Circuit Switching and Packet Switching 电路交换和分组交换

- **Circuit switching 电路交换**
- **Packet switching 分组交换**

### Circuit Switching 电路交换

When two hosts want to communicate, the network establishes a **dedicated end-to-end connection** between the two hosts.
当两台主机要通信时，该网络在两台主机之间创建一条 **专用的端到端通信**。

A circuit in a link is implemented with either **frequency-division multiplexing(FDM)** or **time-division multiplexing(TDM)**.
链路中的电路要么通过 **频分多路复用** 实现，要么通过 **时分多路复用** 实现。

> The width of the band is called **bandwidth**. 频段的宽度被称为 **带宽**。

- TDM 时分多路复用
  - Time is divided into **frames** or fixed duration. 时间被分成固定区间的 **帧**。
  - Each frame is divided into a fixed number of **time slots**. 每帧又被划分为固定数量的 **时隙**。
  - When the network establishes a connection across a link, the network dedicates one **time slot** in every frame to this connection.
    当网络跨越一条链路创建一条连接时，该网络在每个帧中为该连接指定一个 **时隙**。

- FDM 频分多路复用
  - The frequency spectrum of a link is divided up among the connections established across the link.
    链路的频谱由跨越链路创建的所有连接所共享。
  - The link dedicates a **frequency band** to each connection for the duration of the connection.
    链路在连接期间为每条连接专用一个 **频段**。

Circuit switching is wasteful because the dedicated circuits are idle during **silent periods**.
电路交换效率较低，因为在 **静默期** 专用电路空闲。

### Packet Switching 分组交换

Distributed applications exchange **message** in accomplishing their task.
各种应用程序在完成其任务时要交换 **报文**。

In modern computer networks, the source breaks long messages into smaller chunks of data known as **packets**.
在现代计算机网络中，源主机将长报文划分为较小的数据块，并称为 **分组**。

Between source and destination, each of these packets travels through communication links and **packet switches**.
在源和目的地之间，这些分组中的每个都通过通信链路和 **分组交换机** 传送。

> Packets are transmitted over each communication link at a rate equal to the **full** transmission rate of the link.
  分组以该链路的 **最大** 传输速率在通信链路上传输。

Most packet switches use **store-and-forward transmission** at the inputs to the links.
多数分组交换机在链路的输入端使用 **存储转发传输** 机制。
Store-and-forward transmission means that the switch must receive the entire packet before it can begin to transmit the first bit of the packet onto the outbound link.
存储转发传输机制是指在交换机能够开始向输出链路传输该分组的第一个比特之前，必须接收到整个分组。

## How Do Packets Make Their Way Through Packet-Switched Networks? 分组是怎样通过分组交换网形成其通路的

略

## ISPs and Internet Backbones ISP 和因特网主干

![ISP 的互联](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/InterconnectionOfISPs.png)

At the very top of the hierarchy is a relatively small number of so-called **tier-1 ISPs**.
层次结构的最顶层是数量相对较少的 **第一层 ISP**。

Tier-1 ISPs are also characterized by being: 第一层 ISP 的特性可以表示为：

- Directly connected to each of the other tier-1 ISPs. 直接与其他每个第一层 ISP 相连。
- Connected to a large number of tier-2 ISPs and other customer networks. 与大量的第二层 ISP 和其他客户网络相连。
- International in coverage. 覆盖国际区域。

Tier-1 ISPs are also known as **Internet backbone** networks. 第一层 ISP 也被称为 **因特网主干** 网络。

- A tier-2 ISP is said to be a **customer** of the tier-1 SIP to which it is connected.
  第二层 ISP 被称为是它所连接的第一层 ISP 的 **客户**。
- The tier-1 ISP is said to be a **provider** to its customer. 第一层 ISP 相对该客户而言是 **提供商**。

> Access ISPs are at the bottom of this hierarchy. 接入 ISP 位于该层次结构的底部。

When two ISPs are directly connected to each other, they are said to **peer** with each other.
当两个 ISP 彼此直接相连时，它们被称为彼此是 **对等** 的。
