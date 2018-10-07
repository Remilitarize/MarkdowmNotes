[toc]

## MAC Addresses  MAC 地址

A link-layer address is variously called: LAN 地址有各种不同的称呼：

- LAN address  LAN 地址
- Physical address 物理地址
- MAC address  MAC 地址

The MAC address is **6 bytes** long, giving 2<sup>48</sup> possible MAC addresses.
MAC 地址长度为 **6 字节**，共有 2<sup>48</sup> 个可能的 LAN 地址。

No two adapters have the same address. 没有两个适配器具有相同的地址。
The IEEE manages the MAC address space. IEEE 在管理着该 MAC 地址空间。

An adapter's MAC address has a **flat** structure. 适配器的 MAC 地址具有 **扁平** 结构。

- When an adapter wants to send a frame to some destination adapter, the sending adapter inserts the destination adapter's MAC address into the frame and then sends the frame into the LAN.
  当某适配器要向某些目的适配器发送一个帧时，发送适配器将目的适配器的 MAC 地址插入到该帧中，并将该帧发送到 LAN 上。
- Each adapter that receives the frame will check to see whether the destination MAC address in the frame matches its own MAC address.
  接收到该帧的每个适配器将检查，看在该帧中的目的 MAC 地址是否与它自己的 MAC 地址匹配。
- If there is a match, the adapter extracts the enclosed datagram and passes the datagram up the protocol statck to its parent node.
  如果匹配，该适配器提取出封装的数据报，并将该数据报沿协议栈向上传递给它的父节点。
- IF there isn't match, the adapter discards the frame. 如果不匹配，该适配器丢弃该帧。

Sometimes a sending adapter does want all the other adapters on the LAN to receive and process the frame it is about to send.
有时某发送适配器的确要让 LAN 上所有的其他适配器来接收并处理它打算发送的帧。
In this case, the sending adapter inserts a special MAC **broadcast address** into the destination address field of the frame.
在这种情况下，发送适配器在该帧的目的地址字段中插入一个特殊的 MAC **广播地址**。
The broadcast address is a string of 48 consecutive 1s (that is, **FF-FF-FF-FF-FF-FF** in hexadecimal notation).
广播地址是 48 个连续的 1 组成的字符串，即以十六进制表示法表示的 **FF-FF-FF-FF-FF-FF**。

## Address Resolution Protocol(ARP) 地址解析协议

ARP resolves an **IP address** to a **MAC address**.
ARP 将一个 **IP 地址** 解析为一个 **MAC 地址**。
DNS resolves a **host name** to an **IP address**.
DNS 将一个 **主机名** 解析为一个 **IP 地址**。

DNS resolves host names for hosts **anywhere in the Internet**.
DNS 为 **在因特网中任何地方** 的主机解析主机名。
ARP resolves IP addresses only for nodes **on the same subnet**.
ARP 只为在 **同一个子网** 上的节点解析 IP 地址。

**ARP table** contains mappings of IP addresses to MAC addresses.
**ARP 表** 包含 IP 地址到 MAC 地址的映射关系。

|IP Address|MAC Address|TTL|
|-|-|-|
|222.222.222.221|88-B2-2F-54-1A-0F|13:45:00|
|222.222.222.223|5C-66-AB-90-75-B1|13:52:00|

The ARP table contains a time-to-live(TTL) value, which indicates when each mapping will be deleted from the table.
ARP 表包含一个生存期值，指示了从表中删除每个映射的时间。
A typical expiration time for an entry is **20 minutes** from when an entry is placed in an ARP table.
从一个表项放置到 ARP 表中开始，一个表项通常的过期时间是 **20 分钟**。

Suppose that the table above is a possible ARP table in node 222.222.222.220.
假设上面的表格是 222.222.222.220 节点中的可能的 ARP 表。
The node 222.222.222.220 wants to send a datagram that is IP-addressed to another node on the subnet.
节点 222.222.222.220 要发送一个数据报，该数据报要 IP 寻址到子网上另一个节点。

- This task is easy if the sending node's ARP table has an entry for the destination node.
  如果发送节点的 ARP 表具有该目的节点的表项，这个任务很容易完成。
- If the ARP table doesn't currently have an entry for the destination node.
  如果 ARP 表中现在没有该目的节点的表项。
	- Node 222.222.222.220 passes an ARP query packet to the adapter along with an indication that adapter should send the packet to the MAC broadcast address.
	  节点 222.222.222.220 向它的适配器传递一个 ARP 查询分组，并且指示要求适配器应该用 MAC 广播地址。
	- The adapter encapsulates the ARP packet in a link-layer frame, uses the broadcast address for the frame's destination address, and transmits the frame into the subnet.
	  适配器在链路层帧中封装这个 ARP 分组，用广播地址作为帧的目的地址，并将该帧传输进子网中。
	- The frame containing the ARP query is received by all the other adapters on the subnet, and each adapter passes the ARP packet within the frame up to an ARP module in that node.
	  包含该 ARP 查询的帧能被子网上的所有其他适配器接收到，并且每个适配器都把该帧里的 ARP 分组向上传递给节点中的 ARP 模块。
	- Each node checks to see if its IP address matches the destination IP address in the ARP packet.
	  每个节点检查它的 IP 地址是否与 ARP 分组中的目的 IP 地址相匹配。
	- The (at most) one node with a match sends back to the querying node a response ARP packet with the desired mapping.
	  （至多）一个匹配的节点给查询节点发送回一个带有所希望映射的响应 ARP 分组。
