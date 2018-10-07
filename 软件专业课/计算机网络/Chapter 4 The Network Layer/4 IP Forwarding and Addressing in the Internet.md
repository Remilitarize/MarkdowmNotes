[toc]

Three major components: 三个主要组件：

- The IP protocol IP 协议
- The routing component 选路组件
	- Routing protocol 选路协议
- A facility to report errors in datagrams and respond to requests for certain network-layer information
  报告数据报中的差错和对某些网络层信息请求进行响应的设施
	- The Internet Control Message Protocol(ICMP) 互联网控制报文协议

## Datagram Format 数据报格式

![IPv4 Datagram Format](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/IPv4DatagramFormat.png)

- Version Number 版本号
	- These 4 bits specify the IP protocol version of the datagram. 这 4 比特规定了数据报的 IP 协议版本。
	- The datagram format for the current version of IP is IPv4. 目前使用的 IP 版本为 IPv4。
- Header Length 首部长度
	- These 4 bits are needed to determine where in the IP datagram the data actually begins.
	  需要用这 4 比特来确定 IP 数据报中的数据部分实际从哪里开始。
- Type of service 服务类型
	- The type of service(TOS) bits were included in the IPv4 header to allow defferent types of IP datagram to be distinguished from each other.
	  服务类型比特用来使不同类型的 IP 数据报能相互区别开来。
- Datagram Length 数据报长度
	- This is the total length of the IP datagram, measured in bytes. 这是 IP 数据报的总长度，以字节计。
- Identifier, flags, fragmentation offset 标识、标志、片偏移
	- These three fields have to do with so-called IP fragmentation. 该三个字段与所谓 IP 分片有关。
- Time-to-live 寿命
	- Time-to-live(TTL) field is included to ensure that datagram do not circulate forever in the network.
	  寿命字段用来确保数据报不会永远在网络中循环。
	- This field is decremented by one each time the datagram is processed by a router.
	  每当数据报经过一台路由器时，该字段的值减 1。
	- If the TTL field reaches 0, the datagram must be dropped.
	  如果 TTL 字段减为 0，则该数据报必须丢弃。
- Protocol 协议
	- This field is used only when an IP datagram reaches its final destination.
	  该字段仅在一个 IP 数据报到达其最终目的地时才会用到。
- Header checksum 首部检验和
	- The header checksum aids a router in detecting bit errors in a received IP datagram.
	  首部检验和用于帮助路由器检测收到的 IP 数据报中的比特错误。
- Source and destination IP address 源和目的 IP 地址
	- When a source creates a datagram, it inserts its IP address into the source IP address field and inserts the address of the ultimate destination into the destination IP address field.
	  当源主机产生一个数据报时，它在源 IP 字段中插入它的 IP 地址，在目的 IP 地址字段中插入其最终目的地的地址。
- Options 选项
	- The options fields allow an IP header to he extended. 选项字段允许 IP 首部被扩展。
- Data（payload） 数据（有效载荷）
	- In most circumstances, the data field of the IP datagram contains the transport-layer segment.
	  在大多数情况下，IP 数据报中的数据字段含有要交付给目的地的运输层报文段。
	- However, the data field can carry other types of data, such as ICMP messages.
	  然后，数据字段也可承载其他类型的数据，如 ICMP 报文段。

## IP Datagram Fragmentation IP 数据报分片

The maximum amount of data that a link-layer frame can carry is called the **maximum transmission unit(MTU)**.
一个链路层帧能承载的最大数据量叫做 **最大传输单元**。

- Fragment the data in the IP datagram into two or more smaller IP datagrams.
  将 IP 数据报中的数据分片成两个或更多个较小的数据报。
- Encapsulate each of these smaller IP datagrams in a separate link-layer frame.
  用单独的链路层帧封装这些较小的 IP 数据报。
- Send these frames over the outgoing link. 向输出链路上发送这些帧。
- Each of these smaller datagrams is referred to as a **fragment**. 这些较小的数据报叫做 **片**。

> The designers of IPv4 decided to put the job of datagram reassembly in the end systems rather than in network routers.
  IPv4 的设计者决定将数据报的重新组装工作放到端系统中。

- The designers of IPv4 put identification, flag, and fragmentation offset fields in the IP datagram heaser.
  IPv4 的设计者将标识、标志和片偏移字段放在 IP 数据报中。
- When a datagram is created, the sending host stamps the datagram with an identification number as well as source and destination addresses.
  当创建一个数据报时，发送主机在为该数据报设计源和目的地址的同时加上标识号。
- The sending host increments the identification number for each datagram it sends.
  发送主机将它发送的每个数据报中的标识号加 1。
- When the destination receives a series of datagrams from the same sending host, it can examine the identification numbers of the datagrams to determine which of the datagrams are actually fragments of the sage large datagram.
  当目的地从同一发送主机收到一系列数据报时，它可以检查数据报的标识号以确定那些数据报真正是统一较大数据报的片。
- Because IP is an unreliable service, in order for the destination host to be absolutely sure it has received the last fragment of the original datagram, the last fragment has a flag bit set to 0, whereas all the other fragments have this flag bit set to 1.
  由于 IP 是不可靠服务，为了让目的主机绝对地相信它已经收到了初始数据报的最后一个片，最后一个片的标志比特被设为 0，而所有其他片的标志比特被设为 1.
- In order for the destination host to determine whether a fragment is missing, the offset field is used to specify where the fragment fits within the original IP datagram.
  为了让目的主机确定一个片是否丢失，用偏移字段指定片应放在初始 IP 数据报的哪个位置。

![IP Fragmentation](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/IPfragmentation.png)

A datagram of 4000 bytes (20 bytes of IP header plus 3980 bytes of IP payload) arrives at a router and must be forwarded to a link with an MTU of 1500 bytes.
一个 4000 字节的数据报（20 字节 IP 首部加上 3980 字节 IP 有效载荷）到达一台路由器，且必须被转发到一条 MTU 为 1500 字节的链路上。
This implies that the 3980 data bytes in the original datagram must be allocated to three separate fragments (each of which is also an IP datagram).
这就意味着初始数据报中的 3980 字节数据必须被分成 3 个独立的片（每个片也是一个 IP 数据报）。
Suppose that the original datagram is stamped with an identification number of 777.
假定初始数据报附加上的标识号为 777。
The amount of original payload data in all but the last fragment be a multiple of **8 bytes**.
除了最后一片所有初始有效载荷数据的数量应当是 **8 字节** 的倍数。

The number of the fragment is (4000 - 20) / (MTU - 20) = 2.68 = 3.
片的数量是 3。
The offset of the fragment is (MTU - 20) / 8 = 185.32
片的偏移量是 185。

|Length|ID|MF|offset|
|-|-|-|
|1500B|777|1|0|
|1500B|777|1|185|
|1040B|777|0|370|

## IPv4 Addressing IPv4 编址

The boundary between the host and physical link is called an **interface**.
主机与物理链路之间的边界叫做 **接口**。

Each IP address is 32 bits long, and there are thus a total of 2<sup>32</sup> possible IP addresses.
每个 IP 地址长度为 32 比特，因此共有 2<sup>32</sup> 个可能的 IP 地址。
These addresses are typically written in so-called **dotted-decimal notation**, in which each byte of the address is written in its decimal form and is separated by a period (dot) from other bytes in the address.
这些地址一般按所谓的 **点分十进制记法** 的方式书写，即地址中的每个字节用十进制形式书写，各字节间以句点（点）隔开。

> 193.32.216.9 &rarr; 11000001 00100000 11011000 00001001

In IP terms, this network interconnecting host interfaces and one router interface forms a **subnet**.
用 IP 的术语来说。互连主机的接口与路由器的一个接口的网络形成一个 **子网**。
IP addressing assigns an address to this subnet, for example 223.1.1.0/24, where the /24 notation, sometimes known as a **subnet mask**, indicates that the leftmost 24 bits of the 32-bit quantity define the **subnet address**.
IP 编址为这个子网分配一个地址，比如 223.1.1.0/24，其中的 /24 记法有时称为 **子网掩码**，它表明 32 比特中的最左侧 24 比特定义了 **子网地址**。

> IP: 223.1.1.0/24
  subnet mask: 255.255.255.0
	subnet address: 223.1.1.0
  broadcast address: 223.1.1.255
	the range of address: 223.1.1.1 - 223.1.1.254
	how many hosts: 254

The Internet's address assignment strategy is known as **Classless Interdomain Routing(CIDR)**.
因特网的地址分配策略被称为 **无类别域间选路**。
The x most significant bits of an address of the form a.b.c.d/x constitute the network portion of the IP address, and are often referred to as the **prefix**(or **network prefix**) of the address.
形式为 a.b.c.d/x 的地址的 x 最高比特构成了 IP 地址的网络部分，并且经常被称为该地址的 **前缀**（或 **网络前缀**）。
The remaining 32-x bits of an address can be through of as distinguishing among the devices **within the organization**, all of which have the same network prefix.
一个地址的剩余 32-x 比特可认为是用于区分 **组织内部** 设备的，其中所有设备具有相同的网络前缀。

Before CIDR was adopted, the network portions of an IP address were constrained to be 24, 16, or 8 bits in length, an addressing scheme known as **classful addressing**, since subnets with 24-, 16-, and 8-bit subnet addresses were known as class A, B, and C networks, respectively.
在采用 CIDR 之前，IP 地址的网络部分被限制长度为 24、16 或 8 比特，因为具有 24、16 或 8 比特子网地址的网络分别被称为 A、B 和 C 类网络，所以这种编址方案称为 **分类编址**。
The requirement that the subnet portion of an IP address be exactly 1, 2, or 3 bytes long.
要求一个 IP 地址的网络部分正好为 1、2 或 3 字节。

|Class|Subnet portion|The range of IP address|Default subnet mask|
|-|-|-|-|
|A|0|1.0.0.0 - 126.255.255.255|/24|
|B|10|128.0.0.0 - 191.255.255.255|/16|
|C|110|192.0.0.0 - 223.255.255.255|/8|
|D|1110|224.0.0.0 - 239.255.255.255|&nbsp;|
|E|11110|240.0.0.0 - 255.255.255.255|&nbsp;|

The IP broadcast address 255.255.255.255. IP 广播地址 255.255.255.255。

### Obtain a Host Address: the Dynamic Host Configuration Protocl 获取主机地址：动态主机配置协议

A network administrator can configure **DHCP(Dynamic Host Configuration Protocol)** so that a given host receives the same IP address each time it connects to the network, or a host may be assigned a **temporary IP address** that will be different each time the host connects to the network.
网络管理员可以配置 **DHCP（动态主机配置协议）**，以便某给定主机每次与该网络连接时能得到一个相同的的 IP 地址，或者被分配一个 **临时的 IP 地址**，主机每次与该网络连接时该地址都可能是不同的。

Because of DHCP'S ability to automate the network-related aspects of connecting a host into a network, it is often referred to as a **plug-and-play protocol**.
由于 DHCP 具有能将主机连接进一个网络的自动化网络相关方面的能力，故它又常被称为 **即插即用协议**。

## Internet Control Message Protocol(ICMP) 互联网控制报文协议

ICMP is used by hosts and routers to communicate network-layer information to each other.
ICMP 用于主机和路由器彼此交互网络层信息。

ICMP is often considered part of IP but achitecturally it lies just above IP, as ICMP messages are carried inside IP datagrams.
ICMP 通常被认为是 IP 的一部分，但从体系结构上讲它是位于 IP 之上，因为 ICMP 报文是承载在 IP 分组中的。

## IPv6

### IPv6 Datagram Format IPv6 数据报格式

![IPv6 Datagram Format](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/IPv6.png)

The most important changes introduced in IPv6 are evident in the datagram format:
IPv6 中引入的最重要的变化表现在其数据报格式中：

- Expanded addressing capabilities. 扩大的地址容量。
	- IPv6 increases the size of the IP address from 32 to **128 bits**.
	  IPv6 将 IP 地址长度从 32 比特增加到 **128 比特**。
- A streamlined 40-byte header. 简单高效的 40 字节首部。
- Flow labeling and priority. 流标签与优先级。

The following fields are defined in IPv6: 以下是 IPv6 中定义的字段：

- Version 版本号
	- IPv6 carries a value of 6 in this field. IPv6 将该字段值设为 6.
- Traffic class 流量类型
	- This 8-bit field is similar in spirit to the TOS field. 这 8 比特字段与 TOS 字段的含义相似。
- Flow label 流标签
	- This 20-bit field is used to identify a flow of datagrams. 该 20 比特字段用于标识一个数据报的流。
- Payload length 有效载荷长度
	- This 16-bit value is treated as an unsigned integer giving the number of bytes in the IPv6 datagram following the fixed-length, 40-byte datagram header.
	  该 16 比特值作为一个无符号整数，给出了 IPv6 数据报中跟在定长的 40 字节数据报首部后面的字节数量。
- Next header 下一个首部
	- This field identifies the protocol to which the contents (data field) of this datagram will be delivered.
	  该字段标识该数据报中的内容（数据字段）需要交付给哪个协议。
- Hop limit 跳限制
	- The contents of this field are decremented by one by each router that forwards the datagram.
	  转发数据包的每台路由器将对该字段内容减 1。
- Source and destination addresses 源和目的地址
- Data 数据
	- This is the payload portion of the IPv6 datagram. 这是 IPv6 数据报的有效载荷部分。

Several fields appearing in the IPv4 datagram are no longer present in the IPv6 datagram:
IPv4 数据报中出现的几个字段在 IPv6 数据报中已不存在：

- Fragmentation/Reassembly 分片/重新组装
	- IPv6 does not allow for fragmentation and reassembly at intermediate routers.
	  IPv6 不允许在中间路由器上进行分片与重新组装。
- Header checksum 首部检验和
- Options 选项
	- An option field is no longer a part of the standard IP header.
	  选项字段不再是标准 IP 首部的一部分了。
