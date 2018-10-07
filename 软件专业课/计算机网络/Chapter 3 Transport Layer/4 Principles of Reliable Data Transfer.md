[toc]

**rdt(reliable data transfer protocol) 可靠数据传输协议**

> Consider only the case of **unidirectional data transfer**. 仅考虑 **单向数据传输**。

## Building a Reliable Data Transfer Protocol 构造可靠数据传输协议

### Reliable Data Transfer over a Perfectly Reliable Channel: rdt1.0 完全可靠信道上的可靠数据传输：rdt1.0

> The underlying channel is completely reliable now. 现在底层信道完全可靠。

![rdt 1.0](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/rdt1.0.png)

![rdt 1.0 有限状态机](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/rdt1.0FSM.png)

All packet flow is from the sender to receiver, with a perfectly reliable channel there is **no need** for the receiver side to **provide any feedback** to the sender since nothing can go wrong.
有了完全可靠的信道，接收方就 **不需要提供任何反馈信息** 给发送方，因为不会发生任何差错。

### Reliable Data Transfer over a Channel with Bit Errors: rdt2.0 具有比特差错信道上的可靠数据传输：rdt2.0

Assume for the moment that all transmitted packets are received in the order in which they were sent.
假定所有传输的分组将按其发送的顺序被接受。

![rdt 2.0](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/rdt2.0.png)

![rdt 2.0 有限状态机](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/rdt2.0FSM.png)

- **ACK(positive acknowledgment) 肯定确认**
- **NAK(negative acknowledgment) 否定确认**
- Reliable data transfer protocols based on such retransmission are known as ARQ(Automatic Repeat reQuest) protocols.
  基于这种重传机制的可靠数据传输协议称为 **自动重传请求**。
	- **Error detection 差错检测**
	- **Receiver feedback 接收方反馈**
	- **Retransmission 重传**

1. The sender will create a packet containing the data to be sent, along with a packet checksum, and then send the packet via the operation.
  发送方将产生一个包含待发送数据的分组，计算出分组检验和，然后经由操作发送该分组。
2. The sender protocol is waiting for an ACK or a NAK packet from the receiver.
  发送方协议等待接收方的 ACK 或 NAK 分组。
	- If an ACK packet is received, the sender knows that the most recently transmitted packet has been received correctly and thus the protocol returns to the state of waiting for data from the upper layer.
	  如果收到一个 ACK 分组，则发送方知道最近传输的分组已被正确接受，因此协议返回到等待来自上层数据的状态。
	- If a NAK is received, the protocol retransmits the last packet and waits for an ACK or NAK to be returned by the receiver in response to the retransmitted data packet.
	  如果收到一个 NAK 分组，该协议重传最后一个分组并等待接收方返回的响应重传分组的 ACK 或 NAK。

The sender will not send a new piece of data until it is sure that the receiver has correctly received the current packet.
发送方将不会发送一块新数据，知道发送方确信接收方已正确接收当前分组为止。

> Protocols such as rdt2.0 are known as **stop-and-wait protocols** 类似于 rdt2.0 的协议被称为 **停等协议**。

If an ACK or NAK is corrupted, the sender has no way of knowing whether or not the receiver has correctly received the last piece of transmitted data.
如果一个 ACK 或 NAK 分组受损，发送方无法知道接收方是否正确接受了上一块发送的数据。

![rdt 2.1](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/RDT2.1.png)

![rdt 2.1 发送方](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/rdt2.1Sender.png)

![rdt 2.1 接收方](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/rdt2.1Receiver.png)

Add a new field to the data packet and have the sender number its data packets by putting a **sequence number** into this field.
在数据分组中添加一新字段，让发送方对其数据分组编号，即将发送的数据分组的 **序号** 放在该字段。
The receiver then need only check this sequence number to determine whether or not the received packet is a retransmission.
接收方只需要检查序号即可确定收到的分组是否是一次重传。

- When an **out-of-order** packet is received, the receiver sends a **positive acknowledgment** for the packet it has received.
  当接收到 **失序** 的分组时，接收方对所接收的分组发送一个 **肯定确认**。
- When a corrupted packet is received, the receiver sends a negetive acknowledgment.
  当接收到 **受损** 的分组，接收方将发送一个否定确认。

A sender that receives two ACKs for the same packet (that is, received **duplicate ACKs**) knows that the receiver did not correctly receive the packet following the packet that is being ACKed twice.
发送方接收到对同一个分组的两个 ACK（即接受 **冗余 ACK**）后，就知道接收方没有正确接收到跟在被确认两次的分组后面的分组。

![rdt 2.2](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/RDT2.2.png)

![rdt 2.2 发送方](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/rdt2.2Sender.png)

![rdt 2.2 接收方](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/rdt2.2Receiver.png)

Our **NAK-free** reliable data transfer protocol for a channel with bit errors is rdt2.2.
rdt2.2 是在具有比特差错信道上实现的一个 **无 NAK** 的可靠数据传输协议。

### Reliable Data Transfer over a Lossy Channel with Bit Errors: rdt3.0 具有比特差错的丢包信道上的可靠数据传输：rdt3.0

![rdt 3.0](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/rdt3.0.png)

![rdt 3.0 发送方](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/rdt3.0Sender.png)

The sender does not simply know whether a data packet was lost, an ACK was lost, or if the packet or ACK was simply overly delayed.
发送方不知道是一个数据分组丢失、一个 ACK 丢失，还是该分组或 ACK 只是过度时延。
In all cases, the action is the same: retransmit.
在所有情况下，采取的动作是同样的：重传。

- Implementing a time-based retransmission mechanism requires a **countdown timer** that can interrupt the sender after a given amount of time has expired.
  为了实现基于时间的重传机制，需要一个 **倒计数定时器**，在一个给定的时间过期后，可中断发送方。

Because packet sequence numbers alternate between 0 and 1, protocol rdt3.0 is sometimes known as the **alternating-bit protocol**.
因为分组序号在 0 和 1 之间交替，因此 rdt3.0 有时被称为 **比特交替协议**。

## Pipelined Reliable Data Transfer Protocols 流水线可靠数据传输协议

Since the many in-transit sender-to-receiver packets can be visualized as filling a pipeline, this technique is known as **pipelining**.
因为从发送方向接收方传输的众多分组可以被看成是填充到一条流水线中，故这种技术被称为 **流水线**。

![Pipelined sending](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/Pipelining.png)

- The range of sequence numbers must be increased. 必须增加序号范围。
- The sender and receiver sides of the protocols may have to **buffer** more than one packet.
  协议的发送方和接收方也许必须 **缓存** 多个分组。
- The range of sequence numbers needed and the buffering requirement will depend on the manner in which a data transfer protocol responds to lost, correupted, and overly delayed packets.
  所需序号范围和对缓冲的要求取决于数据传输协议处理丢失、损坏及过度延时分组的方式。
	- **Go-Back-N 回退 N 步**
	- **Selective repeat 选择重传**

## Go-Back-N(GBN) 回退 N 步

In a **Go-Back-N(GBN)** protocol, the sender is allowed to transmit multiple packets (when available) without waiting for an acknowledgment, but is constrained to have no more than some maximum allowable number, N.
在 **回退 N 步** 协议中，允许发送方发送多个分组（当有多个分组可用时）而不需要等待确认，但它也受限于在流水线中未确认的分组数不能超过某个最大允许数 N。

- Define **base** to be the sequence number of the oldest unacknowledged packet.
  定义 **基序号** 为最早的未确认分组的序号。
- Define **nextseqnum** to be the smallest unused sequence number.
  定义 **下一个序号** 为最小的未使用序号。
- N is often referred to as the **window size**.
  N 常被称为 **窗口长度**。

![Go-Back-N](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/GoBackN.png)

- Sequence numbers in the interval [0, base-1] correspond to packets that have already been transmitted and acknowledged.
  [0, 基序号-1] 内的序号对应于已发送并确认过的分组。
- The interval [base, nextseqnum-1] corresponds to packets that have been sent but not yet acknowledged.
  [基序号, 下一个序号-1] 内的序号对应已经发送但未被确认的分组。
- Sequence numbers in the interval [nextseqnum-1, base+N-1] can be used for packets that can be sent immediately, should data arrive from the upper layer.
  [下一个序号, 基序号+N-1] 内的序号可用于那些要被立即发送的分组，其数据来自上层。
- Sequence numbers greater than or equal to base+N cannot be used until an unacknowledged packet currently in the pipeline has been acknowledged.
  大于或等于 基序号+N 的序号是不能使用的，直到当前流水线中未被确认的分组已得到确认为止。

> The GBN protocol itself as a **sliding-window protocol**. GBN 协议常被称为 **滑动窗口协议**。

If k is the number of bits in the packet sequence number field, the range of sequence numbers is thus [0, 2<sup>k</sup>-1].
如果分组序号字段的比特数是 k，则该序号范围是 [0, 2<sup>k</sup>-1]。

The GBN sender must respond to three types of events: GBN 发送方必须响应以下三种类型的时间：

- Invocation from above 上层的调用
- Receipt of an ACK 收到 ACK
	- In GBN protocol, an acknowledgment for a packet with suquence number n will be taken to be a **cumulative acknowledgment**, indicating taht all packets with a sequence number up to and including n have been correctly received at the receiver.
	  在 GBN 协议中，对序号为 n 的分组的确认采取 **累积确认** 的方式，表明接收方已正确接收到序号 n 以前（包括 n 在内）的所有分组。
- A timeout event 超时事件
	- If a timeout occurs, the sender resends **all packets that have been perviously sent but that have not yet been acknowledged**.
	  如果出现超时，发送方将重传 **所有已发送但还未被确认的分组**。

The receiver's actions in GBN are also simple. 接收方的动作也很简单。

- If a packet with swquence number n is received correctly and is in order, the receiver sends an ACK for packet n and delivers the data portion of the packet to the upper layer.
  如果一个序号为 n 的分组被正确接收到，并且按序，则接收方为分组 n 发送一个 ACK，并将该分组中的数据交付到上层。
- In all other cases, the receiver **discards** the packet and **resends an ACK for the most recently received in-order packet**.
  在所有其他情况下，接收方都 **丢弃** 该分组，并 **为最近按序接受的分组重传 ACK**。

![运行中的 GBN](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/GBN.png)

## Selective Repeat(SR) 选择重传

**Selective-repeat** protocols avoid unnecessary retransmissions by having the sender retransmit only those packets that it suspects were received in error (that is, were lost or corrupted) at the receiver.
**选择重传** 协议通过让发送方仅重传那些它怀疑在接收方出错（即丢失或受损）的分组而避免了不必要的重传。

![SR](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/SR.png)

**The window size must be less than or equal to half the size of the sequence number space for SR protocols.**
**窗口长度必须小于或等于序号空间大小的一半。**
