[toc]

## The Services Provided by the Link Layer 链路层提供的服务

The **link-layer protocol** defines the format of the packets exchanged between the nodes at the ends of the link, as well as the actions taken by these nodes when the packets are sent and received.
**链路层协议** 定义了在链路两侧的节点之间交互的分组格式，以及当发送和接受分组时这些节点采取的动作。

The units of data exchanged by a link-layer protocol are called **frames**.
链路层协议交换的数据单元称为 **帧**。

- An important characteristic of the link layer is that a datagram may be carried by **different link-layer protocols** on the different links in the path.
  链路层的一个重要特点是数据报在路径的不同链路上可能由 **不同链路层协议** 所承载。
- The services provided by the link-layer protocols may be **different**.
  链路层协议提供的服务可能是 **不同的**。

Possible services that can be offered by a link-layer protocol include:
链路层协议能够提供的可能服务包括：

- **Framing 成帧**
- **Link access 链路接入**
- **Reliable delivery 可靠交付**
- **Flow control 流量控制**
- **Error detection 差错检测**
- **Error correciton 差错纠正**
- **Half-duplex and full-duplex 半双工和全双工**

## Where Is The Link Layer Implemented? 链路层在何处实现？

For the most part, the link layer is implemented in a **network adapter**, also sometimes known as a **network interface card(NIC)**.
链路层的主体部分是在 **网络适配器** 中实现的，网络适配器也称为 **网络接口卡**。

At the heart of the network adapter is the **link-layer controller**, usually a single, special-purpose chip that implements many of the link-layer services identified in the previous section.
网络适配器的内核是 **链路层控制器**，该控制器通常是实现了许多链路层服务的单个特定目的的芯片。
