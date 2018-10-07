[toc]

The computer and other devices are referred to as end systems because they sit at the **edge** of the Internet.
因为计算机等设备位于因特网的 **边缘**，故而被称为端系统。

Hosts are sometimes further divides into two categories:
主机有时又被进一步划分为两类：

- **Clients 客户端**
- **Servers 服务端**

## Client and Server Programs 客户机和服务器程序

A **client program** is a program running on one end system that requests and receives a service form a **server program** running on another end system.
**客户机程序** 是运行在一个端系统上的程序，它发出请求，并从运行在另一个端系统上的 **服务器程序** 接收服务。

- **Client-server model** is undoubtedly the most prevalent structure of Internet applications.
  **客户机-服务器模式** 无疑是因特网应用程序的最为流行的结构。

> Client-server Internet applications are, by definition, distributed applications.
  根据定义，客户机-服务器因特网应用程序是分布时应用程序。

Many applications are **peer-to-peer(P2P)** applications, in which end systes interact and run programs that perform **both client and server** functions.
越来越多的应用程序是 **对等（P2P)** 应用程序，其中的端系统相互作用并运行执行 **客户机和服务器** 功能的程序。

## Access Networks 接入网

**Access networks** —— the physical link(s) that connect an end system to its **edge router**.
**接入网** —— 将端系统连接到其 **边缘路由器** 的物理链路。

- Residential access 住宅接入
- Company access 公司接入
- Wireless access 无线接入

### Residential Access 住宅接入

One form of residential access is the **dial-up modem** over an ordinary analog telephone line into a residential ISP.
一种住宅接入形式是通过普通模拟电话线和 **拨号调制解调器** 与住宅 ISP 相连。

- The home modem converts the digital output of the PC into analog format for transmission over the analog phone line.
  家用调制解调器将 PC 输出的数字信号转换为模拟形式，以便在模拟电话线上传输。
- This analog phone line is made of twisted-pair copper wire. 模拟电话线由双绞铜线构成。

Weakness 缺点

- Due to the poor quality of the twisted-pair line between many homes and ISPs, many users get an effective rate significantly **less than** 56 kpbs.
  由于在许多家庭和 ISP 之间的双绞线质量较低，所以许多用户获得的有效速率大大 **低于** 56 kbps。

- Dial-up modem access **ties up** a user's ordinary phone line —— while a residential user uses a dial-up modem to surf the Web, the user cannot receive and make ordinary phone calls over the phone line.
  拨号调制解调器接入 **占用** 了用户的普通电话线，当住宅用户使用拨号调制解调器在 Web 上冲浪时，该用户就不能用该电话线接收和拨打普通电话。

New **boradband access** technologies are providing residential user higher bit rates.
新型 **宽带接入** 技术为住宅用户提供了更高的比特速率。

- **Digital subscriber line(DSL) 数字用户线**
- **Hybrid fiber-coaxial cable(HFC) 混合光纤同轴电缆**

One of the attractive features of DSL, HFC, and satellite access is that the services are **always on**.
DSL、HFC 和卫星接入的一个吸引人之处是服务 **总是在线**。

### Company Access 公司接入

On corporate and university campuses, a **local area network(LAN)** is typically used to connect an end system to the edge routers.
在公司和大学校园，**局域网（LAN）** 通常被用于连接端用户与边缘路由器。

### Wireless Access 无线接入

In a **wireless LAN**, wireless users transmit/receive packets to/from a base station(also known as a wireless access point).
在 **无线局域网（wLAN）** 中，无线用户与位于几十米半径内的基站（也成为无线接入点）之间传输/接收分组。

In **wide-area wireless access networks**, packets are transmitted over the same wireless infrastructure used for cellular telephony, with the base station thus being managed by a telecommunications provider.
在 **广域无线接入网** 中，分组经用于蜂窝电话的相同无线基础设施进行发送，基站由电信提供商管理。

## Physical Media 物理媒体

- Guided media 导引型媒体
  - With guided media, the waves are guided along a **solid medium**.
    对于导引型媒体，电波沿着 **固体媒体** 被导引。
- Unguided media 非导引型媒体
  - With unguided media, the waves propagate in the **atmosphere** and in **outer space**.
    对于非导引型媒体，电波在 **空气** 或 **外层空间** 中传播。

1. Twisted-Pair Copper Wire 双绞铜线
  - The least expensive and most commonly used guided transmission medium. 最便宜并且使用最为普遍的导引型传输媒体。
2. Coaxial Cable 同轴电缆
3. Fiber Optics 光缆
4. Terrestrial Radio Channels 陆地无限电信道
5. Satellite Radio Channels 卫星无限电信道
