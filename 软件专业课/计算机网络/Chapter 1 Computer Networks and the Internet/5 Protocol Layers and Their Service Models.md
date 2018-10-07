[toc]

## Layered Architecture 分层的体系结构

To provide structure to the design of network protocols, network designers organize protocols —— and the network hardware and software that implement the protocols —— in **layers**.
为了给网络协议的设计提供一个结构，网络设计者以 **分层** 的方式组织协议以及实现这些协议的网络硬件和软件。

The procotols of the various layers are called the **protocol stack**. 各层的所有协议被称为 **协议栈**。

- **The application layer 应用层**
	- Network applications and their application-layer protocols reside. 网络应用程序及其应用层协议停留的地方。
	- The packet of information at the application layer as a **message**. 位于应用层的信息分组称为 **报文**。
- **The transport layer 传输层**
	- Transports application-layer messages between application endpoints. 提供了在应用程序端点之间传送应用层报文的服务。
	- We'll refer to a transport-layer packet as a **segment**. 我们将运输层分组称为 **报文段**。
- **The network layer 网络层**
	- Responsible for moving network-layer packets known as datagrams from one host to another.
	  负责将称为 **数据报** 的网络层分组从一台主机移动到另一台主机。
- **The link layer 链路层**
	- At each node, the network layer passes the datagram down to the link layer, which delivers the datagram to the next node along the route.
	  在每个节点，网络层将数据报下传给链路层，链路层沿着路径将数据报传递给下一个节点。
	- We'll refer to the link-layer packets as **frames**. 我们将链路层分组称为 **帧**。
- **The physical layer 物理层**
	- The job of the physical layer is to move the individual **bits** within the frame from one node to the next.
	  物理层的任务是将该帧中的一个一个 **比特** 从一个节点移动到下一个节点。

## Message, Segments, Datagrams, and Frames 报文、报文段、数据报和帧

Similar to end systems, routers and link-layer switches organize their networking hardware and software into layers.
与端系统类似，路由器和链路层交换机以层的方式组织它们的网络硬件和软件。

But routers and link-layer switches **do not implement all** of the layers in the protocol stack.
但路由器和链路层交换机 **并不实现** 协议栈中 **所有** 层次。

- Link-layer switches implement layers **1 and 2**. 链路层交换机实现了 **第一层和第二层**。
- Routers implement layers **1 through 3**. 路由器实现了 **第一层到第三层**。

![Hosts, routers, and link-layer switches](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/HostRouterAndLink-layerSwitch.png)

> Encapsulation 封装

In the simplest case, the transport layer takes the message and appends **additional imformation**(so-called **transport-layer header information H<sub>t</sub>**) that will be used by the receiver-side transport layer.
在最简单的情况下，运输层收取报文并附上 **附加信息**（即 **运输层首部信息 H<sub>t</sub>**），该首部信息被接收端的运输层使用。
The application-layer message and the transport-layer header information together constitute the **transport-layer segment**.
应用层报文和运输层首部信息共同构成了 **运输层报文段**。

The transport layer then passes the segment to the network layer, which adds **network-layer header information(H<sub>n</sub>)** such as source and destination end system addreasses, creating a **network-layer datagram**.
运输层向网络层传递该报文段，网络层增加了如源和目的端系统地址等 **网络层首部信息（H<sub>n</sub>）**，形成了 **网络层数据报**。

The datagram is then passed to the link layer, which will add its own **link-layer header information** and create a **link-layer frame**.
数据报接下来被传递给链路层，链路层也增加它自己的 **链路层首部信息** 并创建了 **链路层帧**。

A packet has two types of fields: 分组具有两种类型的字段：

- **Header fields 首部字段**
- **A payload field 有效载荷字段**
