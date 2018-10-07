[toc]

Computer networks that provide only a **connection** service at the network layer are called **virtual-circuit(VC) network**.
仅在网络层提供 **连接服务** 的计算机网络被称为 **虚电路**。

Computer networks that provide only a **connectionless** service at the network layer are called **datagram networks**.
仅在网络层提供 **无连接服务** 的计算机网络被称为 **数据报网络**。

## Virtual-Circuit Networks 虚电路网络

Many alternative network architectures —— including those of ATM and frame relay —— are virtual-circuit networks.
许多其他网络体系结构（包括 ATM、帧中继）都是虚电路网络。

> The Internet is a datagram network. 因特网是数据报网络。

A VC consists of: 一条虚电路（VC）的组成如下：

- **A path**(that is, a series of links and routers) 源和目的主机之间的 **路径**
- **VC numbers**, one number for each link along the path **VC 号**，沿着该路径的每段链路一个号码
- **Entries in the forwarding table** in each router along the path 沿着该路径的每台路由器中的 **转发表表项**

In a VC network, the network's routers must maintain **connection state information** for the ongoing connections.
在虚电路网络中，该网络的路由器必须为进行中的连接维持 **连接状态信息**。

There are three identifiable phases in a virtual circuit: 在虚电路中有 3 个明显不同的阶段：

- VC setup. 虚电路建立。
- Data transfer. 数据传送。
- VC teardown. 虚电路拆除。

Routers along the path between the two end systems are involved in VC setup, and each router is fully aware of all the VCs passing through it.
沿两个端系统之间路径上的路由器都要参与虚电路的建立，且每台路由器都完全知道经过它的所有虚电路。

The messages that the end systems send into the network to initiate or terminate a VC, and the message passed between the routers to set up the VC (that is, to modify connection state in router table) are known as **signaling messages**.
端系统向网络发送指示虚电路启动与终止的报文，以及路由器之间传递的用于建立虚电路（即修改路由器表中的连接状态）的报文被称为 **信令报文**。
The protocols used to exchange these messages are often referred to as **signaling protocols**.
用来交换这些报文的协议常称为 **信令协议**。

## Datagram Networks 数据报网络

In a **datagram network**, each time an end system wants to send a packet, it stamps the packet with the address of the destination end system and then pops the packet into the network.
在 **数据报网络** 中，每当一个端系统要发送分组时，它就为该分组加上目的地端系统的地址，然后将该分组推进网络中。

- Each router has a forwarding table that maps destination address to link interfaces.
  每台路由器有一个将目的地址映射到链路接口的转发表。
- When a packet arrives at the router, the router uses the packet's destination address to look up the appropiate output linke interface in the fouwarding table.
  当分组到达路由器时，该路由器使用该分组的目的地址在该转发表中查找适当的输出链路接口。
- The router then intentionally forwards the packet to that output link interface.
  然后，路由器有意识地将该分组向该输出链路接口转发。

|Destination Address Range<br />目的地址范围|Link Interface<br />链路接口|
|-|-|
|11001000 00010111 00010000 00000000<br />through<br />11001000 00010111 00010111 11111111|0|
|11001000 00010111 00011000 00000000<br />through<br />11001000 00010111 00011000 11111111|1|
|11001000 00010111 00011001 00000000<br />through<br />11001000 00010111 00011111 11111111|2|
|Otherwise|3|

The router matches a **prefix** of the packet's destination address with the entries in the table.
路由器用分组的目的地址的 **前缀** 与表中的表项进行匹配。

|Prefix Match<br />前缀匹配|Link Interface<br />链路接口|
|-|-|
|11001000 00010111 00010|0|
|11001000 00010111 00011000|2|
|11001000 00010111 00011|3|
|Otherwise|3|

When there are multiple matches, the router uses the **longest profix matching rule**.
当有多个匹配时，该路由器使用 **最长前缀匹配规则**。
