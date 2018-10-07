[toc]

## Ethernet Frame Structure 以太网帧结构

![Ethernet Frame](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/EthernetFrame.png)

- Data Field 数据字段
	- This field carries the IP datagram. 这个字段承载了 IP 数据报。
- Destination address 目的地址
	- This field contains the MAC address of the destination adapter. 这个字段包含目的适配器的 MAC 地址。
- Source address 源地址
	- This field contains the MAC address of the adapter that transmits the frame onto the LAN.
	  这个字段包含了传输该帧到 LAN 上的适配器的 MAC 地址。
- Type field 类型字段
	- The type field permits Ethernet to multiplex network-layer protocols.
	  该类型字段允许以太网复用多种网络层协议。
- Cyclic redundancy check(CRC)
- Preamble 前同步码
	- The Ethernet frame begins with an 8-byte preamble field.
	  以太网帧以一个 8 字节的前同步码字段开始。
	- The first 7 bytes of the preamble has a value of 10101010.
	  前同步码的前 7 个字节的值都是 10101010。
	- The last byte is 10101011. 最后一个字节是 10101011。

All of the Ethernet technologies provide **connectionless service** to the network layer.
所有的以太网技术都向网络层提供 **无连接服务**。

All of the Ethernet technologies provide **unreliable service** to the network layer.
所有的以太网技术都向网络层提供 **不可靠服务**。

## CSMA/CD: Ethernet's Multiple Access Protocol CSMA/CD: 以太网的多路访问协议

CSMA/CD does the following: CSMA/CD 使用了以下机制：

1. An adapter may begin to transmit at any time; that is, there is no notion of time slots.
  适配器可以在任何时刻开始传输；这就是说没有时隙的概念。
2. An adapter never transmits a frame when it senses that some other adapter is transmitting; that is, it uses carrier sensing.
  当一个适配器侦听到有某些其他的适配器正在传输，它决不会传输帧；这就是说它使用了载波侦听。
3. A transmitting adapter aborts its transmission as soon as it detects that another adapter is also transmitting; that is, it uses collision detection.
  一旦传输中的适配器检测到另一个适配器正在传输，就终止它的传输；这就是说它使用了碰撞检测。
4. Before attempting a retransmission, an adapter waits a random time that is typically small compared with the time to transmit a frame.
  在尝试重传之前，适配器等待一个随机时间，这个时间通常比传输一帧的时间要短。

CSMA/CD protocol works as follows: CSMA/CD 协议按下列方式工作：

1. The adapter obtains a datagram from the network layer, prepares an Ethernet frame, and puts the frame in an adapter buffer.
  适配器从网络层得到一个数据报，准备一个以太网帧，并把该帧放到适配器缓存区中。
2. If the adapter senses that the channel is idle, it starts to transmit the frame. If the adapter senses that the channel is busy, it waits until it senses no signal energy and then starts to transmit the frame.
  如果适配器侦听到信道空闲，它开始传输该帧。如果适配器侦听到信道忙，它等待到侦听不到信号能量，然后开始传输该帧。
3. While transmitting, the adapter monitors for the presence of signal energy coming from other adapters. If the adapter transmits the entire frame without detecting signal energy from other adapters, the adapter is finished with the frame.
  在传输过程中，适配器监听来自其他适配器的信号能量的出现。如果该适配器传输了整个帧，而没有检测到来自其他适配器的信号能量，它就完成了该帧的传输。
4. If the adapter detects signal energy from other adapters while transmitting, it stops transmitting its frame and instead transmits a 48-bit jam signal.
  如果适配器在传输中检测到来自其他适配器的信号能量，它就停止传输它的帧，而代之以传输一个 48 比特的阻塞信号。
5. After aborting, the adapter enters an **exponential backoff** phase.
  在中止以后，适配器进入一个 **指数后退** 阶段。

Specially, when transmitting a given frame, after experiencing the nth collisiion in a row for this frame, the adapter chooses a value for K at random from {0, 1, 2, ..., 2<sup>m</sup>-1} where m = min(n, 10).
特别地，当传输一个给定帧时，在该帧经受了一连串的第 n 次碰撞后，适配器随机地从 {0, 1, 2, ..., 2<sup>m</sup>-1} 为 K 选一个值，其中 m = min{n, 10}。
The adapter then waits K&sdot;512 bit times and then returns to 2.
适配器等待 K&sdot;512 比特时间，并返回到第二步。
