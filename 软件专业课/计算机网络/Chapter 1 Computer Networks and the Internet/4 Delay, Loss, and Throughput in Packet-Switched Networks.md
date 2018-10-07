[toc]

## Overview of Delay in Packet-Switched Networks 分组交换网中的时延概述

- **Nodal processing delay 节点处理时延**
- **Queuing delay 排队时延**
- **Transmission delay 传播时延**
- **Propagation delay 传播时延**

Together, these delays accumulate to give a **total nodal delay**.
这些时延总体累加起来是 **节点总时延**。

- Processing delay 处理时延
	- The time required to **examine the packet's header** and **determine where to direct the packet** is part of the **processing delay**.
	  **检查分组首部** 和 **决定将该分组导向何处** 所需要的时间是 **处理时延** 的一部分。

- Queuing delay 排队时延
	- At the queue, the packet experiences a **queuing delay** as it **waits to be transmitted onto the link**.
	  在队列中，当分组 **在链路上等待传输** 时，它经受 **排队时延**。

- Transmissiion delay 传输时延
	- Denote **the length of the packet** by L bits, and denote **the transmission rate** of the link from router A to router B by R bits/sec.
	  用 L 比特表示 **分组的长度**，用 R bps 表示从路由器 A 到路由器 B 的 **链路传输速率**。
	- The **transmission delay** is **L/R**, the amount of time required to push all of the packet's bits into the link.
	  **传输时延** 是 **L/R**，将所有分组的比特率推（传输）向链路所需要的时间。

- Propagation delay 传播时延
	- The time required to propagate from the beginning of the link to router B is the **propagation delay**.
	  从该链路的起点到路由器 B 传播所需要的时间是 **传播时延**。
	- Denote d is the **distance** between router A and router B and s is the **propagation speed** of the link.
	  用 d 表示路由器 A	和路由器 B 之间的 **距离**，用 s 表示该链路的 **传播速率**。
	- The propagation delay is **d/s**. 传播时延是 **d/s**。

If we let d<sub>proc</sub>, d<sub>queue</sub>, d<sub>trans</sub> and d<sub>prop</sub> denote the processing, queuing, transmission, and propagation delays:
如果令 d<sub>proc</sub>，d<sub>queue</sub>，d<sub>trans</sub> 和 d<sub>prop</sub> 分别表示处理时延、排队时延、传输时延和传播时延：

d<sub>nodal</sub> = d<sub>proc</sub> + d<sub>queue</sub> + d<sub>trans</sub> + d<sub>prop</sub>

## Queuing Delay and Packet Loss 排队时延和丢包

- Let a denote the **average rate** at which packets arrive at the queue.
  令 a 表示分组到达队列的 **平均速率**。
- Recall that R is the **transmission rate**. 前面定义了 R 是 **传输速率**。
- Also suppose that all packets consist of L bits. 也假定所有分组都是由 L 比特组成的。

The ratio **La/R** called the **traffic intensity**.
比率 **La/R** 被称为 **流量强度**。

- Design your system so that the traffic intensity is **no greater than 1**.
  设计系统时流量强度 **不能大于 1**。
- When the traffic intensity is **close to 1**, there will be intervals of time when the arrival rate exceeds the transmission capacity, and a queue will form during these periods of time.
  当流量强度 **接近于 1** 时，将存在到达率超过传输能力的时间间隔，从而将形成队列。
- If the traffic intensity is **close to zero**, then packet arrivals are few and far between and it is unlikely that an arriving packet will find another packet in the queue.
  如果流量强度 **接近于 0**，则几乎没有分组到达并且到达间隔很大，那么到达的分组将不可能在队列中发现别的分组。

Because the queue capacity is finite, packet delays do not really approach infinity as the traffic intensity approaches 1.
因为排队容量是有限的，所以流量强度接近于 1 时排队时延也不会趋向无穷大。
A packet can arrive to find a full queue.
到达的分组将发现一个满的队列。
With no place to store such a packet, a router will **drop** that packet, that is, the packet will be **lost**.
由于没有地方存储这个分组，路由器将 **丢弃** 该分组，即该分组将会 **丢失**。

## Throughput in Computer Networks 计算机网络中的吞吐量

The **instantaneous throughput** at any instant of time is the rate(in bits/sec) at which Host B is receiving the file.
任何瞬间的 **瞬时吞吐量** 是主机 B 接收到该文件的速率（以 bps 计）。

If the file consists of F bits and the transfer takes T seconds for Host B to receive all F bits, then the **average throughput** of the file transfer is **F/T bits/sec**.
如果该文件由 F 比特组成，而主机 B 接收到所有 F 比特用了 T 秒，则文件传送的 **平均吞吐量** 是 **F/T bps**.
