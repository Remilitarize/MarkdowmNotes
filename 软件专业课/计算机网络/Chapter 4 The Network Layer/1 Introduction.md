[toc]

## Forwarding and Routing 转发和选路

- **Forwarding 转发**
	- When a packet arrives at a router's input link, the router must move the packet to the appropriate output link.
	  当一个分组达到某路由器的一条输入链路时，该路由器必须将该分组移动到适当的输出链路。
- **Routing 选路**
	- The network layer must determine the route or path taken by packets as they flow from a sender to a receiver.
	  当分组从发送方流向接收方时，网络层必须决定这些分组所采用的路由或路径。
	- The algorithms that calculate these paths are referred to as **routing algorithms**.
	  计算这些路径的算法被称为 **选路算法**。

A router forwards a packet by examining the value of a field in the arriving packet's header, and then using this value to index into the router's **forwarding table**.
路由器通过检查到达分组首部中的一个字段的值，然后使用该值在该路由器的 **转发表** 中索引查询来转发一个分组。

Some packet switches, called **link-layer switches**, base their forwarding decision on the value in the link-layer field.
某些分组交换机称为 **链路层交换机**，它们基于链路层字段中的值作转发决定。
Other packet switches, called **routers**, base their forwarding decision on the value in the network-layer field.
其他分组交换机称为 **路由器**，它们基于网络层字段中的值作转发决定。

In the network layer, it is referred to as **connection setup** that in order to set up state before network-layer data packets within a given source-to-destination connection.
在网络层，给定的源目的地连接之间建立起状态称为 **连接建立**。

## Network Service Models 网络服务模型

The Internet's network layer provides a single service, known as **best-effort service**,
因特网的网络层提供了单一的服务，称为 **尽力而为服务**。
