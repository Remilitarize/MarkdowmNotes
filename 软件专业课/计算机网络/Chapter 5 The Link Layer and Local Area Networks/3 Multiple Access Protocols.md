[toc]

Two types of network links: 两种类型的网络链路：

- **Point-to-point link 点对点链路**
- **Broadcast link 广播链路**

Three categories of multiple access protocols: 三种类型的多路访问协议：

- **Channel partitioning protocols 信道划分协议**
- **Random access protocols 随机接入协议**
- **Taking-turns protocols 轮流协议**

## Channel Partitioning Protocols 信道划分协议

Time-division multiplexing(TDM) and frequency-division multiplexing(FDM) are two techniques that can be used to partition a broadcast channel's bandwidth among all nodes sharing that channel.
时分多路复用和频分多路复用是两种能够在所有共享信道节点之间用于划分广播信道带宽的技术。

- TDM 时分多路复用
	- TDM divides time into **time frames** and further divides each time frame into N **time slots**.
    TDM 将时间划分为 **时间帧**，并进一步划分每个时间帧为 N 个 **时隙**。
		- Each slot time is then assigned to one of the N nodes. 然后把每个时隙分配给 N 个节点中的一个。
- FDM 频分多路复用
	- FDM divides the R bps channel into **different frequencies** and assigns each frequency to one of the N nodes.
	  FDM 将 R bps 信道划分为 **不同的频段**，并把每个频率分配给 N 个节点中的一个。
- Advantages 优点
	- It avoids collisions and divides the bandwidth fairly among the N nodes.
	  它避免了碰撞，在 N 个节点之间公平地划分了带宽。
- Disadvantages 缺点
	- A node is limited to a bandwidth of R/N. 限制一个节点只能使用 R/N 的带宽。

A third channel partitioning protocol is **code division multiple access(CDMA)**.
第三种信道划分协议是 **码分多址**。

- CDMA assigns a different **code** to each node. CDMA 对每个节点分配一种不同的 **编码**。
- If the codes are chosen carefully, different nodes can transmit **simultaneously** and yet have their respective receivers correctly receive a sender's encoded data bits in spite of interfering transmissions by other nodes.
  如果精心选择这些编码，不同的节点能够 **同时** 传输，并且它们各自相应的接收方仍能正确接受发送方编码后的数据比特，而不在乎其他节点的干扰传输。

## Random Access Protocol 随机接入协议

In a random access protocol, a transmitting node always transmits at the full rate of the channel, namely, R bps.
在随机接入协议中，一个传输节点总是以信道的全部速率（即 R bps）进行发送。
When there is a collision, each node involved in the collision **repeatedly retransmits** its frame (that is, packet) until the frame gets through without a collision.
当有碰撞时，涉及碰撞的每个节点 **反复地重发** 它的帧（也就是分组），直到该帧无碰撞第通过为止。

But when a node experiences a collision, it doesn't necessarily retransmit the frame right away.
但是当一个节点经受一次碰撞时，它不必立即重发该帧。
Instead it waits a random delay before retransmitting the frame.
相反，它在重发该帧之前等待一个随机时延。

- ALOHA Protocol ALOHA 协议
- CSMA Protocol CSMA 协议

### Slotted ALOHA 时隙 ALOHA

Assume the following: 做下列假设：

- All frames consist of exactly L bits. 所有帧由恰好 L 比特组成。
- Time is divided into slots of size L/R seconds. 时间被划分为长度为 L/R s 的时隙。
- Nodes start to transmit frames only **at the beginnings of slots**. 节点只 **在时隙起点开始** 传输帧。
- The nodes are synchronized so that each node knows when the slots begin.
  节点是同步的，每个节点都知道时隙何时开始。
- If two or more frames collide in a slot, then all the nodes detect the collision event before the slot ends.
  如果在一个时隙中有两个或者更多个帧碰撞，则所有节点在该时隙结束之前检测到该碰撞事件。

Let p be a probability, that is, a number between 0 and 1. 令 p 是一个概率，即一个在 0 和 1 之间的数。

- When the node has a fresh frame to send, it waits until the beginning of the next slot and transmits the entire frame in the slot.
  当该节点有一个新帧要发送时，它等到下一个时隙开始并在该时隙传输整个帧。
- If there isn't a collision, the node has successfully transmitted its frame and thus need not consider retransmitting the frame.
  如果没有碰撞，该节点成功地传输它的帧，从而不需要考虑重传该帧。
- If there is a collision, the node detects the collision before the end of the slot.
  如果有碰撞，该节点在该时隙结束之前检测到这次碰撞。
- The node retransmits its frame in each subsequent slot with **probability p** until the frame is transmitted without a collision.
  该节点以 **概率 p** 在后续的每个时隙中重传它的帧，直到该帧被无碰撞地传输出去。

![Slotted ALOHA](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/SlottedALOHA.png)

- The probability that an arbitrary node has a success is Np(1-p)<sup>N-1</sup>.
  任意一个节点成功传送的概率是 Np(1-p)<sup>N-1</sup>。
- The maximum efficiency of the protocol is given by 1/e = 0.37.
  这个协议的最大效率为 1/e = 0.37。

### ALOHA

In pure ALOHA, when a frame first arrives, the node **immediately** transmits the frame in its entirely into the broadcast channel.
在纯 ALOHA 中，当一帧首次到达，节点 **立刻** 将该帧完整地传输进广播信道。

- If a transmitted frame experiences a collision with one or more other transmissions, the node will then **immediately** retransmit the frame with probability p.
  如果传输的一个帧与一个或多个传输经受了碰撞，这个节点将 **立即** 以概率 p 重传该帧。
- Otherwise, the node waits for a frame transmission time.
  否则，该节点等待一个帧传输时间。
- After this wait, it then transmits the frame with probability p, or **wait for another frame time with probability 1-p**.
  在此等待之后，它则以概率 p 传输该帧，或者 **以概率 1-p 等待另一个帧时间**。

![ALOHA](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/ALOHA.png)

- The probability that a given node has a successful transmission is p(1-p)<sup>2(N-1)</sup>.
  一个给定的节点成功传输一个的概率是 p(1-p)<sup>2(N-1)</sup>。
- The maximum efficiency of the pure ALOHA protocol is only 1/(2e).
  纯 ALOHA 协议的最大效率仅为 1/(2e)。

### Carrier Sense Multiple Access(CSNA) 载波侦听多路访问

- Listen before speaking. 说话之前先听。
	- If someone else is speaking, wait until they are finished. 如果其他人正在说话。等到他们说完话为止。
	- In the networking world, this is called **carrier sensing** —— a node listens to the channel before transmitting.
	  在网络领域中，这被称为 **载波侦听**，即一个节点在传输前先听信道。
	- If a frame from another node is currently being transmitted into the channel， a node then waits a **random** amount of time and then again senses the channel.
	  如果来自另一个节点的帧正向信道上发送，节点则等待一段 **随机** 时间，然后再侦听信道。
	- If the channel is sensed to be idle, the node then begins frame transmission.
	  如果侦听到该信道是空闲的，该节点则开始帧传输。
	- Otherwise, the node waits another random amount of time and repeats this process.
	  否则，该节点等待另一段随机时间，继续重复这个过程。
- If someone else begins talking at the same time, stop talking. 如果与他人同时开始说话，停止说话。
	- In the networking world, this is called **collision detection** —— a transmitting node listens to the channel while it is transmitting.
	  在网络领域中，这被称为 **碰撞检测**，即一个传输节点在传输时一直在侦听信道。
	- If it detects that another node is transmitting an interfering frame, it stops transmitting and uses some protocol to determine when it should next attempt to transmit.
	  如果它检测到另一个节点正在传输干扰帧，它就停止传输，用某个协议来确定它应该在什么时候再尝试下一次传输。

These two rules are embodied in the family of **carrier sense multiple access(CSMA) and CSMA with collision detection(CSMA/CD)** protocols.
这两个规则包含在 **载波侦听多路访问** 和 **具有碰撞检测的 CSMA** 协议族中。

![CSMA and CSMA/CD](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/CSMAandCSMACD.png)

## Taking-Turns Protocols 轮流协议

- Polling protocol 轮询协议
- Token-passing protocol 令牌传递协议

## Local Area Networks(LANs) 局域网

A LAN is a computer network concentrated in a geographical area. LAN 是一种集中在一个地理区域的计算机网络。

- The Ethernet LANs 以太网 LAN
	- Based on random-access。 基于随机接入。
- Token-passing technologies 令牌传递技术
