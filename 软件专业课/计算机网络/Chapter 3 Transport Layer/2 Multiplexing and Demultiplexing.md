[toc]

The transport layer in the receiving host does not actually deliver data directly to a process, but instead of an intermediary **socket**.
接收主机中的运输层实际上并没有直接将数据交付给进程，而是通过一个中间的 **套接字** 来传递。

This job of delivering the data in a transport-layer segment to the correct socket is called **demultiplexing**.
将运输层报文段中的数据交付到正确的套接字的工作称为 **多路分解**。
The job of gathering data chunks at the source host from different sockets, encapsulating each data chunk with header information to create segments, and passing the segments to the network layer is called **multiplexing**.
从源主机的不同套接字收集数据块，并为每个数据块封装上首部信息从而生成报文段，然后将报文段传送到网络层的工作称为 **多路复用**。

The transport-layer multiplexing requires: 运输层多路复用的要求：

- Sockets have unique identifiers. 套接字有唯一标识符。
- Each segment have special fields that indicate the socket to which the segment is to be delivered.
  每个报文段有特殊字段来指示该报文段所要交付的套接字。

These special fields are the **source port number field** and the **destination port number field**.
这些特殊字段是 **源端口号字段** 和 **目的端口号字段**。

- Each port number is a 16-bit number. 每个端口号是一个 16 比特的数字。
- The port numbers ranging from 0 to 1023 are called **well-known port numbers** and are restricted.
  0-1023 范围的端口号称为 **周知端口号**，是受严格限制的。

How the transport layer could implement the demultiplexing service:
运输层如何实现多路分解服务：

- Each socket in the host could be assigned a port number, and when a segment arrives to the host, the transport layer examines the destination port number in the segment and directs the segment to the corresponding socket.
  主机上的每个套接字被分配一个端口号，当报文段到达主机时，运输层检查报文段中的目的端口号，并将其定向到相应的套接字。
- The segment's data then passes through the socket into the attached process.
  然后报文段中的数据通过套接字进入其所连接的进程。

> This is basically how UDP does it, but the multiplexing/demultiplexing in TCP is more subtle.
  UDP 基本上是这样做的，但是 TCP 的多路复用与多路分解更为复杂。

- A UDP socket is fully identified by a two-tuple consisting of a destination IP address and a destination port number.
  UDP 套接字是由一个包含目的 IP 地址和目的端口号的二元组来全面标识的。
- A TCP socket is identified by a four-tuple:(source IP address, source port number, destination IP address, destination port number).
  TCP 套接字是由一个四元组（源 IP 地址，源端口号，目的 IP 地址，目的端口号）来标识的。
