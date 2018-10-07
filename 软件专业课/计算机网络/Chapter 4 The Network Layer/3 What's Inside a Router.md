[toc]

![Router Structure](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/RouterStructure.png)

- **Input ports 输入端口**
	- It performs the physical-layer functions of terminating an incoming physical link to a router.
	  它要执行将一条输入的物理链路端接到路由器的物理层功能。
	- It performs the data link-layer functions needed to interoperate with the data link-layer functions at the remote side of the incoming link.
	  它也要执行需哟啊与位于入链路远端的数据链路层功能交互的数据链路层功能。
	- It also performs a lookup and forwarding function so that a packet forwarded into the switching fabric of the router emerges at the appropriate output port.
	  它还要完成查找和转发功能，以便转发到路由器交换结构部分的分组能出现在适当的输出端口。
- **Switch fabric 交换结构**
	- The switching fabirc connects the router's input ports to its output ports.
	  交换结构将路由器的输入端口链接到它的输出端口。
- **Output ports 输出端口**
	- An output port stores the packets that have been forwarded to it through the switching fabric and then transmits the packets on the outgoing link.
	  输出端口存储经过转换结构转发给它的分组，并将这些分组传输到输出链路。
- **Routing processor 选路处理器**
	- The routing processor executes the routing protocols, maintains the routing information and forwarding tables, and performs network management function within the router.
	  选路处理器执行选路协议，维护选路信息与转发表，并执行路由器中的网络管理功能。

## Input ports 输入端口

![Input port processing](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/InputPort.png)

The input port's **line termination** function and **data link processing** implement the physical and data link layers associated with an individual input link to the router.
输入端口的 **线路端接** 功能与 **数据链路处理** 实现了与通向路由器的各个输入链路相关的物理层和数据链路层。

It is here that the router determines the output port to which an arriving packet will be forwarded via the switching fabric in the **lookup/forwarding module** in the input port.
在输入端口的 **查找/转发模块** 中确定一个到达的分组经交换结构转发给哪个输出端口。

Once the output port for a packet has been determined via the lookup, the packet can be forwarded into the switching fabric.
一旦通过查找确定了一个分组的输出端口，则该分组可转发进入交换结构。
However, a packet may be temporarily **blocked** from entering the switching fabric (due to the fact that packets from other input ports are currently using the fabric).
然后，一个分组可能会在进入交换结构时暂时 **阻塞**，这是由于来自其他输入端口的分组当前正在使用该交换结构。
A blocked packet must thus be **queued** at the input port and then scheduled to cross the switching fabric at a later point in time.
一个被阻塞的分组必须要在输入端口处 **排队**，并等待稍后被及时调度以通过交换结构。

## Switching Fabric 交换结构

![Switching fabric](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/SwitchingFabric.png)

- **Switching via memory 经内存交换**
- **Switching via a bus 经一根总线交换**
- **Switching via an interconnecion network 经一个互联网络交换**

## Output Ports 输出端口

![Output Port](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/OutputPort.png)

Output port processing takes the packets that have been stored in the output port's memory and transmits them over the outgoing link.
输出端口处理取出存放在输出端口内存中的分组并将其传送到输出链路上。

## Where Does Queuing Occur? 何时出现排队？

Since as the queues grow large, the router's buffer space will eventually be exhausted and **packet loss** will occur.
随着队列的增长，路由器的缓存空间将会耗尽，且出现 **丢包**。

![Queuing](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/Queuing.png)
