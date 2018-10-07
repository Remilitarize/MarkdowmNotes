[toc]

With UDP there is no handshaking between sending and receiving transport-layer entities before sending a segment.
使用 UDP 时，在发送报文段之前，发送方和接收方的运输层实体之间没有进行握手。
For this reason, UDP is said to be **connectionless**. 正因如此，UDP 被称为 **无连接的**。

Many applications are better suited for UDP for the following reasons:
有许多应用更适合用 UDP，主要有以下原因：

- Finer application-level control over what data is sent, and when. 应用层更好地控制要发送的数据和发送时间。
- **No connection establishment**, thus UDP does not introduce any delay to establish a connection.
  **无需建立连接**，因此 UPD 不会引入建立连接的时延。
- **No connection state. 无连接状态。**
- **Small packet header overhead. 分组首部开销小。**

## UDP Segment Structure UDP 报文段结构

<table border = "1">
	<tr>
		<td>Source port#<br />源端口号</td><td>Dest. port#<br />目的端口号</td>
	</tr>
	<tr>
		<td>Length<br />长度</td><td>Checksum<br />检验和</td>
	</tr>
	<tr>
		<td  colspan = "2">Application data(message)<br />应用数据（报文）</td>
	</tr>
</table>

- The UDP header has only four fields, each consisting of **two bytes**.
  UDP 首部只有 4 个字段，每个字段由 **两个字节** 组成。
- The length field specifies the length of the UDP segment, including the header, in bytes.
  长度字段指明了包括首部在内的 UDP 报文段长度（以字节为单位）。

## UDP Checksum UDP 检验和

The UDP checksum provides for error detection. UDP 检验和提供了差错检测功能。

UDP at the sender side performs the **1s complement** of the sum of all the **16-bit words** in the segment, with any overflow encountered during the sum being **wrapped around**,
发送方的 UDP 对报文段中的所有 **16 比特字** 的和进行 **反码运算**，求和时遇到的任何溢出都被 **回卷**。

Example：例

0110011001100000
0101010101010101
1000111100001100

The sum of first two of these 16-bits words is: 前两个16 比特字之和是：

0110011001100000
0101010101010101
————————————————
1011101110110101

Adding the third word to the above sum gives: 再将上面的和与第三个字相加：

1011101110110101
1000111100001100
————————————————
0100101011000010

Note that this last addition had overflow, which was wrapped around:
注意到最后一次加法有溢出，这要被回卷。

0100101011000010
0000000000000001
————————————————
0100101011000011

The 1s complement is obtained by converting all the 0s to 1s and converting all the 1s to 0s:
反码运算是将所有的 0 换成 1，所有的 1 换成 0。

0100101011000011
————————————————
1011010100111100
