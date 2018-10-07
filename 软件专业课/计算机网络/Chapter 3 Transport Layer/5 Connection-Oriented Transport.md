[toc]

## The TCP Connection TCP 连接

TCP is said to be **connection-oriented**. TCP 是 **面向连接的**。

- A TCP connection provides a **full-duplex service**. TCP 连接提供的是 **全双工服务**。
	- If there is a TCP connection between Process A on one host and Process B on another host, then application-layer data can flow from Process A to Process B at the same time as application-layer data flows from Process B to Process A.
	 如果一台主机上的进程 A 与另一台主机上的进程 B 存在一条 TCP 连接，那么应用层数据就可在从进程 B 流向进程 A 的同时，也从进程 A 流向进程 B。
- A TCP connection is also always **point-to-point**. TCP 连接也总是 **点对点的**。
	- Between a single sender and a single receiver. 在单个发送方与单个接收方之间的连接。

1. The client first sends a special TCP segment. 客户机首先发送一个特殊的 TCP 报文段。
2. The server responds with a second special TCP segment. 服务器用另一个特殊的 TCP 报文段来响应。
3. The client responds again with a third special segment. 客户机再用第三个特殊报文段作为响应。

The first two segments carry no payload, that is, no application-layer data; the third of these segments may carry a payload.
前两个报文段不承载 "有效载荷"，也就是不包含应用层数据，而第三个报文段可以承载有效载荷。

Because three segments are sent between the two hosts, this connection-establishment procedure is often referred to aa a **three-way handshake**.
由于在这两台主机之间发送了 3 个报文，所以这种连接建立过程常被称为 **三次握手**。

## TCP Segment Structure TCP 报文段结构

![TCP Segment Structure](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/TCPSegmentStructure.png)

- The header includes **source and destination port numbers**, which are used for multiplexing/demultiplexing data from/to upper-layer applications.
  首部包括 **源端口号和目的端口号**，它用于多路复用/多路分解来自或送至上层应用的数据。
- The header includes a **checksum field**. TCP 首部也包括 **检验和字段**。
- The 32-bit **sequence number field** and the 32-bit **acknowledgment number field** are used by the TCP sender and receiver in implementing a reliable data transfer service.
  32 比特的 **序号字段** 和 32 比特的 **确认号字段**。这些字段被 TCP 发送方和接收方用来实现可靠数据传输服务。
- The 16-bit **receive window** field is used for flow control. 16 比特的 **接收窗口** 字段，用于流量控制。
- The 4-bit **header length field** specifies the length of the TCP header in 32-bits words.
  4 比特的 **首部长度字段**，指示了以 32 比特的字为单位的 TCP 首部长度。
	- The TCP header can be of variable length due to the TCP options field.
	  由于 TCP 选项字段的原因，TCP 首部长度是可变的。
- The optional and variable-length **options field** is used when a sender and receiver negotiate the maximum segment size(MSS) or as a window scaling factor for use in high-speed networks.
  可选与变长的 **选项字段**，该字段用于当发送方与接收方协商最大报文段长度（MSS），或在高速网络环境下用作窗口调节因子时使用。
- The **flag field** contains 6 bits. 6 比特的 **标志字段**。
	- The **ACK bit** is used to indicate that the value carried in the acknowledgment field is valid.
	  **ACK 比特** 用于指示确认字段中的值是有效的。
	- The **RST/SYN/FIN** bits are used for connection setup and teardown.
	  **RST/SYN/FIN** 比特用于连接建立和拆除。
	- Setting the **PSH** bit indicates that the receiver should pass the data to the upper layer immediately.
	  当 **PSH** 比特被设置时，就指示接收方应立即将数据交给上层。
	- The **URG** bit is used to indicate that there is data in this segment that the sending-side upper-layer entity has marked as "urgent".
	  **URG** 比特用来指示报文段里存在着被发送方的上层实体置为 "紧急" 的数据。
- The location of the last byte of this urgent data is indicated by the 16-bit **urgent data pointer field**.
  紧急数据的最后一个字节由 16 比特的 **紧急数据指针字段** 指出。

### Sequence Numbers and acknowledgment Numbers 序号和确认号

The **sequence number for a segment** is the byte-stream number of the **first byte** in the segment.
一个 **报文段的序号** 是该报文段 **首字节** 的字节流编号。
The **acknowledgment number** that Host A puts in its segment is the sequence number of the **next byte** Host A is expecting from Host B.
主机 A 填充进报文段的 **确认号** 是主机 A 期望从主机 B 收到的 **下一字节** 的序号。

- Suppose that Host A has received one segment from Host B containing bytes 0 through 535 and another segment containing bytes 900 through 1000.
  假设主机 A 已收到一个来自主机 B 的包含字节 0-535 的报文段，以及另一个包含字节 900-1000 的报文段。
- For some reason Host A has not yet received bytes 536 through 899.
  由于某种原因，主机 A 还没有收到字节 536-899 的报文段。
- Host A is waiting for byte 536 and all the subsequent bytes in Host B's data stream.
  主机 A 为了重组主机 B 的数据流，仍在等待字节 536。
- So Host A puts 536 in the acknowledgment number field of the segment it sends to B.
  因此，A 到 B 的下一个报文段将在确认字段中包含 536。

> TCP is said to provide **cumulative acknowledgments**. TCP 被称为是提供 **累积确认**。

![Sequence and Acknowledgment](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/SequenceAndAcknowledgment.png)

> The second segment: The acknowledgment is said to be **piggyback** on the server-to-client-data segment.
  第二个报文段：确认被称为是 **捎带** 在服务器到客户机的数据报文段中。

## Round-Trip Time Estimation and Timeout 往返时延的估计与超时

Upon obtaining a new SampleRTT, TCP updates EstimatedRTT according to the following formula:
一旦获取一个新 SampleRTT，TCP 就会根据下列公式来更新 EstimatedRTT:

EstimatedRTT = (1 - &alpha;)&sdot;EstimatedRTT + &alpha;&sdot;SampleRTT

Define the RTT variation, DevRTT, as an estimate of how much SampleRTT typically deviates from EstimatedRTT.
定义了 RTT 偏差 DevRTT，用于估算 SampleRTT 一般会偏离 EstimatedRTT 的程度：

DevRTT = (1 - &beta;)&sdot;DevRTT + &beta;&sdot;|SampleRTT - EstimatedRTT|

The retransmission timeout interval: 重传超时间隔：

TimeoutInterval = EstimatedRTT + 4&sdot;DevRTT

## Reliable Data Transfer 可靠数据传输

- Retransmission due to a lost acknowledgment 由于确认报文丢失而重传

![Retransmission due to a lost acknowledgment](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/RetransmissionDueToALostAcknowledgment.png)

- Segment 100 not retransmitted 报文段 100 没有重传

![Segment 100 not retransmitted](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/Segment100NotRetransmitted.png)

- A cumulative acknowledgment avoids retransmission of the first segment 累积确认避免了第一个报文段的重传

![A cumulative acknowledgment avoids retransmission of the first segment](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/ACumulativeAcknowledgmentAvoidsRetransmission.png)

Whenever the timeout event occurs, TCP retransmits the not-yet-acknowledged segment with smallest swquence number.
每当超时时间发送时，TCP 重传具有最小序号的还未被确认的报文段。
Each time TCP retransmits, it sets the next timeout interval to **twice** the previous value.
每次 TCP 重传都会将下一次的超时间隔设为先前值的 **两倍**。

Three duplicate ACKs are received, the TCP sender performs a **fast retransmit**.
收到 3 个冗余 ACK，TCP 就执行 **快速重传**。

## Flow Control 流量控制

**Flow-control service**: To eliminate the possibility of the sender overflowing the receiver's buffer.
**流量控制服务**：消除发送方使接收方缓存溢出的可能性。
**Congestion control**: A TCP sender can also be throttled due to congestion within the IP network.
**拥塞控制**：TCP 发送方也可能因为 IP 网络的拥塞而被遏制。

## TCP Connection Management TCP 连接管理

Three-way handshake 三次握手

1. The client-side TCP first sends a special TCP segment to the server-side TCP.
  客户机端的 TCP 首先向服务器端的 TCP 发送一个特殊的 TCP 报文段。
	- This special segment contains no application-layer data.
	  该报文段中不包含应用层数据。
	- But one of the flag bits in the segment's header, **the SYN bit**, is set to 1.
	  但是报文段的首部中的一个标志位（即 **SYN 比特**）被置为 1。
	- This special segment is referred to as a **SYN segment**. 这个特殊报文段被称为 **SYN 报文段**。
	- The client randomoly choose an initial sequence number(client_isn) and puts this number in the sequence number field of the initial TCP SYN segment.
	  客户机会选择一个起始序号（client_isn），并将其放置到该起始的 TCP SYN 报文段的序号字段中。
2. Once the IP datagram containing the TCP SYN segment arrives at the server host, the server extracts the TCP SYN segment from the datagram, allocates the TCP buffers and variables to the connection, and sends a connection-granted segment to the client TCP.
  一旦包含 TCP SYN 报文段的 IP 数据报到达服务器主机，服务器会从该数据报中提取出 TCP SYN 报文段，为该 TCP 连接分配 TCP 缓存和变量，并向客户机 TCP 发送允许连接的报文段。
	- This connection-granted segment also contains no application0layer data.
	  这个允许连接的报文段也不包含应用层数据。
	- The SYN bit is set to 1. SYN 比特被置为 1。
	- The acknowledgment field of the TCP segment header is set to client_isn + 1.
	  该 TCP 报文段首部的确认号字段被置为 client_isn + 1。
	- The server chooses its own initial sequence number and puts this value in the sequence number field of the TCP segment header.
	  服务器选择自己的初始序号，并将其放置到 TCP 报文段首部的序号字段中。
	- The connection-granted segment is referred to as a **SYNACK segment**.
	  该允许连接的报文段被称为 **SYNACK 报文段**。
3. Upon receiving the SYNACK segment, the client also allocates buffers and variables to the conneciton.
  在收到 SYNACK 报文段后，客户机也要给该连接分配缓存和变量。
	- The client host then sends the server yet another segment. 客户机还会向服务器发送另一个报文段。
	- This last segment acknowledges the server's connection-granted segment.
	  这个报文段对服务器的允许连接的报文段进行了确认。
	- The SYN bit is set to zero, since the connection is established.
	  因为连接已经建立了，所以该 SYN 比特被置为 0。

![Three-way handshake](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/Three-wayHandshake.png)

Four-way handwave 四次挥手

- Either of the two processes participating in a TCP connection can end the connection.
  参与 TCP 连接建立的两个进程中的任何一个都能终止该连接。
- When a connection ends, the resources in the hosts are deallocated.
  当连接结束后，主机中使用的资源将被释放。
- The client application process issues a close command. 客户机应用进程发送一个关闭连接命令。
	- This causes the slient TCP to send a special TCP segment to the server process.
	  这会引起客户机 TCP 向服务器进程发送一个特殊的 TCP 报文段。
	- This special segment has a flag bit in the segment's header, **the FIN bit**, set to 1.
	  这个特殊的报文段首部中的一个标志比特，即 **FIN 比特** 将被设置为 1。
	- When the server receives this segment, it sends the client an acknowledgment segment in return.
	  当服务器接收到该报文段后，就向客户机回送一个确认报文段。
	- The server then sends its own shutdown segment, which has the FIN bit set to 1.
	  然后服务器发送其终止报文段，其 FIN 比特被置为 1。
	- Finally, the client acknowledges the server's shutdown segment.
	  最后，该客户机对这个服务器的终止报文段进行确认。

![Four-way handwave](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/Four-wayHandwave.png)

A Typical Sequence of TCP states visited by a client TCP
客户机 TCP 经历的典型的 TCP 状态序列

![A Typical Sequence of TCP states visited by a client TCP](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/TypicalSequenceOfTCPStatesVisitedByAClientTCP.png)

A typical Sequence of TCP states visited by a server-side TCP
服务器 TCP 经历的典型 TCP 状态序列

![A typical Sequence of TCP states visited by a server-side TCP](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/TypicalSequenceOfTCPStatesVisitedByAClientTCP.png)
