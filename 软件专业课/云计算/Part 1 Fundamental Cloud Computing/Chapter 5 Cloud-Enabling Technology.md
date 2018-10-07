[toc]

## BROADBAND NETWORKS AND INTERNET ARCHITECTURE 宽带网络和 Internet 架构

All clouds must be connected to a network. 所有的云都必须连接到网络。
Cloud consumers have the option of accessing the cloud using only **private and dedicated** network links in LANs, although most clouds are Internet-enabled.
虽然大多数云都允许 Internet 访问，但是云用户也可以选择只通过 LAN 中 **私有的和专用的** 网络链接来接入云。

### Internet Service Providers(ISPs) Internet 服务提供者

Established and deployed by **ISPs**, the Internet's largest backbone networks are strategically interconnected by core routers that connect the world's multinational networks.
Internet 最大的主干网由 **ISP** 建立并部署，它们依靠核心路由器进行战略互联，这些路由器又与世界上的跨国网络相连接。

![互联网络配置](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/hulianwangluopeizhi.PNG)

Worldwide connectivity is enabled through a hierarchical topology composed of **Tiers 1, 2, and 3**.
全球互联是通过一个 **三层** 的拓扑结构形成的。

- The core Tier 1 is made of **large-scale, international** cloud providers that oversee massive interconnected global networks, which are connected to Tier 2's **large regional** providers.
  第一层为核心层，由 **大型国际** 云提供者构成，负责监督大规模的全球互联网络，这些网络连接第二层的 **大区域** 提供者。
- The interconnected ISPs of Tier 2 connect with Tier 1 providers, as well as the **local** ISPs of Tier 3.
  第二层的 ISP 一方面与第一层的提供者互联，一方面与第三层的 **本地** ISP 互联。

![三层拓扑结构](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/sancengtuopujiegou.PNG)

Two fundamental components used to construct the internetworking architecture are:
互联架构的两个基本组成部分是：

- **connectioinless packet switching(datagram networks) 无连接分组交换（数据报网络）**
- **router-based interconnectivity 基于路由器的互联**

### Connectionless Packet Switching(Datagram Networks) 无连接分组交换（数据报网络）

**End-to-end(sender-receiver pair)** data flows are divided into **packets** of a limited size that are received and processed through network switches and routers, then **queued and forwarded** from one intermediary node to the next.
**端到端（发送方-接收方对）** 数据流被分割为固定大小的 **包**，由网络交换机和路由器进行接受和处理，通过 **排队转发** 从一个中间节点传递到下一个节点。

Each packet carries the necessary location information to be processed and routed at every *source, intermediary, and destination node*.
每个包包含了必需的地址信息，这些信息在 *源节点、中间节点和目标节点* 进行相应的处理和路由。

### Router-Based Interconnectivity 基于路由器的互联

A **router** is a device that is connected to multiple networks through which it forwards packets.
**路由器** 是连接多个网络的设备，通过它实现数据包的转发。
Even when successive packets are part of the same data flow, routers process and forward each packet individually while maintaining the network topology information that locates the next node on the communication path between the source and destination nodes.
即使是同一个数据流的连续数据包，路由器也是根据网络拓扑信息，在源节点与目的节点构成的通信路径上定位下一个节点，将这些数据包分别转发出去。
Routers manage network traffic and gauge the most efficient hop for packet delivery, since they are privy to both the packet source and packet destination.
由于路由器知道数据包的源信息和目的信息，因此它能管理网络流量，并为数据包传输估算最有效的转发。

The Internet's mesh structure connects Internet hosts (endpoint systems) using multiple alternative network routes that are determined at **runtime**.
Internet 的网状结构通过各种可选择的网络路由将 Internet 主机（终端系统）连接起来，实际 **运行时** 再决定选择哪个路由。
Communication can therefore be sustained even during **simultaneous network failures**, although using multiple network paths can cause **routing fluctuations and latency**.
因此，即使 **同时出现多个网络故障**，仍然可以保持正常通信。但是，使用多个网络路径会引起 **路由波动和延迟**。

#### Physical Network 物理网络

Physical networks comprise a **data link layer** that controls data transfer between neighboring nodes, and a **physical layer** that transmits data bits through both wired and wireless media.
物理网络包括 **数据链路层** 和 **物理层**，数据链路层控制数据在相邻节点间的传输，物理层通过有线和无线介质传输数据位。

#### Transport Layer Protocol 传输层协议

Transport layer protocols, such as the **Transmission Control Protocol(TCP)** and **User Datagram Protocol(UDP)**, use the IP to provide standardized, end-to-end communication support that facilitates the navigation of data packets across the Internet.
传输层协议（比如 **传输控制协议 TCP** 和 **用户数据包协议 UDP**）利用 IP 来提供标准化的、端到端的通信支持，以便对 Internet 上的数据包进行导航。

#### Application Layer Protocol 应用层协议

Protocols such as HTTP, SMTP for e-mail, BitTorrent for P2P, and SIP for IP telephony use **transport layer protocols** to standardize and enable specific data packet transferring methods over the Internet.
HTTP、电子邮件协议 SMPT、P2P 协议 BitTorrent、IP 电话协议 SIP 等都使用了 **传输层协议**，在 Internet 上实现特定的数据包传输方式，并对其进行标准化。

![协议栈](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/xieyizhan.PNG)

### Technical and Business Considerations 技术和商业考量

#### Connectivity Issues 连接性问题

TCP/IP facilitates both **Internet access** and **on-premise data exchange** over LANs.
TCP/IP 协议实现了 **Internet 接入** 以及 LAN 上的 **企业内部的数据交换**。

![私有云架构](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/siyouyunjiagou.PNG)

Organizations using this deployment model can **directly access** the network traffic to and from the Internet and usually have complete control over and can safeguard their corporate networks using **firewalls** and **monitoring software**.
采用这个部署模型的组织可以 **直接访问** Internet，通常还可以通过 **防火墙** 和 **监控软件** 来控制和保护其企业网络。
These organizations also assume the responsibility of deploying, operating, and maintaining their IT resources and Internet connectivity.
同样，组织也要承担部署、操作和维护其 IT 资源与 Internet 连接的责任。

![基于云部署模型的架构](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/jiyuyunbushumoxingdejiagou.PNG)

Cloud providers can easily configure cloud-based IT resources to be accessible for both external and internal users through an Internet connection.
云提供者可以将云 IT 资源轻松配置为允许内部和外部用户通过 Internet 连接进行访问。
The Internet is the *connecting agent* between *non-proximate cloud consumers, roaming end-users, and the cloud provider's own network*.
Internet 是 *不直接相连的云用户、漫游终端用户和云提供者* 之间的 *网络连接代理*。

A comparison of on-premise and cloud-based internetworking
企业内部和基于云的网络互联的比较

|On-Premise IT Resources|Cloud-Based IT Resources|
|-|-|
|internal end-user devices access corporate IT services through the corporate network<br />内部终端用户通过企业网络访问企业 IT 服务|internal end-user devices access corporate IT services through an Internet connection<br />内部终端用户通过 Internet 连接访问企业 IT 服务|
|internal users access corporate IT services through the corporate Internet connection while roaming in external networks<br />内部用户在外网漫游时，通过企业 Internet 连接访问企业 IT 服务|internal users access corporate IT services while roaming in external networks through the cloud provider's Internal connection<br />内部用户在外网漫游时，通过云提供者的 Internet 连接访问企业 IT 服务|
|external users access corporate IT services through the corporate Internet connection<br />外部用户通过企业 Internet 连接访问企业 IT 服务|external users access corporate IT services through the cloud provider's Internet connection<br />外部用户通过云提供者的 Internet 连接访问企业 IT 服务|

#### Network Bandwidth and Latency Issues 网络带宽和延迟问题

In addition to being affected by the **bandwidth of the data link** that connects networks to ISPs, end-to-end bandwidth is determined by the **transmission capacity of the shared data link** that connect intermediary nodes.
除了受到将网络连接到 ISP 的 **数据链路带宽** 的影响外，端到端带宽还由连接中间节点的 **共享数据链路的传输容量** 来决定。
ISPs need to use **broadband network technology** to implement the core network required to guarantee end-to-end connectivity.
为了保证端到端连接，ISP 需要利用 **宽带技术** 来实现核心网络。

Also referred to as **time delay**, **latency** is the amount of time it takes a packet to travel from one data node to another.
**延迟** 又称为 **时间延迟**，是一个数据包从一个数据节点传递到另一个节点所需要的时间。
Latency increases with every intermediary node on the data packet's path.
在传递路径上，每经过一个中间节点，延迟就会增加。
**Transmission queues** in the network infrastructure can result in **heavy load conditions** that also increase network latency.
网络基础设施中的 **传输队列** 可能会导致 **负载过重**，从而引起网络延迟增加。
Networks are dependent on **traffic conditions** in shared nodes, making Internet latency **highly variable** and often **unpredictable**.
网络依赖于节点之间的 **传输条件**，这使得网络延迟具有 **高度可变性**，而且常常是 **不可预测的**。

**Bandwidth** is critical for applications that require **substantial amounts of data to be transferred** to and from the cloud, while **latency** is critical for applications with a business requirement of **swift response times**.
对于与云之间有 **大量数据传输** 需求的应用而言，**带宽** 非常重要，而对于需要 **快速响应时间** 的应用而言，**延迟** 非常重要。

#### Cloud Carrier and Cloud Provider Selection 云运营商和云提供者选择

The service levels of Internet connections between cloud consumers and cloud providers are determined by their **ISPs**.
云用户和云提供者间 Internet 连接的服务水平是由它们的 **ISP** 决定的。
QoS(quality-of-service) management across multiple ISPs is difficult to achieve in practice, requiring collaboration of the cloud carriers on both sides to ensure that their end-to-end service levels are sufficient for business requirements.
在实际应用中，多个 ISP 之间的 QoS 管理是有难度的，这需要双方的云运营商协调，以保证其端到端服务水平能够满足业务需求。

Cloud consumers and cloud providers may need to use multiple cloud carries in order to achieve the necessary level of connectivity and reliability for their cloud applications, resulting in **additional costs**.
为了获得必要的互联水平以及云应用的可靠性，云用户和云提供者可能需要多个云运营商，这会导致 **成本增加**。
Cloud adoption can therefore be easier for applications with more relaxed latency and bandwidth requirements.
因此，对具有更加宽松的延迟和宽带需求的应用而言，采用云也更容易。

## DATA CENTER TECHNOLOGY 数据中心技术

Grouping IT resources in **close proximity with one another**, rather than having them geographically dispersed, allows for *power sharing, higher efficiency in shared IT resource usage, and improved accessibility for IT personnel*.
与地理上分散的 IT 资源相比，**彼此邻近** 的 IT 资源有利于 *能源共享、提高共享 IT 资源使用率以及提高 IT 人员的效率*。

**Modern data centers** exist as specialized IT infrastructure used to **house centralized** IT resources, such as servers, databases, networking and telecommunication devices, and software systems.
**现代数据中心** 是指一种特殊的 IT 基础设施，用于 **集中放置** IT 资源，包括服务器、数据库、网络与通信设备以及软件系统。

### Virtualization 虚拟化

Data centers consist of both **physical** and **virtualized** IT resouces.
数据中心包含了 **物理** 和 **虚拟** 的 IT 资源。

The **physical IT resource** layer refers to the **facility infrastructure** that houses computing/networking systems and equipement, together with **hardware systems and their operating systems**.
**物理 IT 资源** 是指放置计算/网络系统和设备，以及 **硬件系统及其操作系统** 的 **基础设备**。
The resource abstraction and control of the **virtualization layer** is comprised of **operational and menagement tools** that are othen based on **virtualization platforms** that **abstract** the physical computing and networking IT resources as virtualized components that are easier to allocate, operate, release, monitor, and control.
**虚拟层** 对资源进行抽象和控制，通常是由 **虚拟化平台** 上的 **运行和管理工具** 构成。虚拟化平台将物理计算和网络 IT 资源 **抽象** 为 虚拟化部件，这样更易于进行资源分配、操作、释放、监视和控制。

### Standardization and Modularity 标准化与模块化

Data centers are built upon **standardized commodity hardware** and designed with **modular architectures**, aggregating multiple identical building blocks of facility infrastructure and equipment to support scalability, growth, and speedy hardware replacements.
数据中心以 **标准化商用硬件** 位基础，用 **模块化架构** 进行设计，整合了多个相同的基础设施模块和设备，具备可扩展性、可增长性和快速更换硬件的特点。
Modularity and standardization are key requirements for **reducing** investment and operational costs as they enable *economies of scale* for the procurement, acquisition, deployment, operation, and maintenance processes.
模块化和标准化是 **减少** 投资和运营成本的关键条件，因为它们能实现采购、收购、部署、运营和维护的 *规模经济*。

**Consolidated IT resouces** can serve different systems and be shared among different cloud consumers.
**整合的 IT 资源** 可服务于不同的系统，也可以被不同的云用户共享。

### Automation 自动化

Data centers have specialized platforms that automate tasks like provisioning, configuration, patching, and monitoring **without supervision**.
数据中心具备特殊的平台将供给、配置、打补丁和监控等任务进行自动化，而 **不需要监管**。
Advances in data center management platforms and tools leverage **autonomic computing technologies** to enable self-configuration and self-recovery.
数据中心管理平台和工具的改进利用了 **自主计算技术** 来实现自配置和自恢复。

### Remote Operation and Management 远程操作和管理

Most of the operational and administrative tasks of IT resources in data centers are commanded through the **network's remote consoles** and **management systems**.
在数据中心，IT 资源的大多数操作和管理任务都是由 **网络远程控制台** 和 **管理系统** 来指挥的。
Technical personnel are **not required** to visit the dedicated rooms that house serves, except to perform highly specific tasks, such as equipment handling and cabling or hardware-level installation and maintenance.
技术人员 **无需** 进入放置服务器的专用房间，除非是执行特殊任务，比如设备处理、布线或者硬件级的安装与维护。

### High Availability 高可用性

Since any form of data center outage significantly impacts business continuity for the organizations that use their services, data centers are designed to operate with incresingly higher levels of **redundancy** to sustain abailability.
对于数据中心的用户来说，数据中心任何形式的停机都会对其任务的连续性造成重大影响，因此为了维持高可用性，数据中心采用了 **冗余度** 越来越高的设计。
Data centers usually have *redundant, uninterruptable power supplies*, *cabling*, and *environmental control subsystems* in anticipation of system failure, along with *communication links* and *clustered hardware* for *load balancing*.
数据中心通常具有 *冗余的不间断电源*、*综合布线*、*环境控制子系统*。为了 *负载均衡*，则有冗余的 *通信链路* 和 *集群硬件*。

### Security-Aware Design, Operation, and Management 安全感知技术、操作和管理

Requirements for security, such as physical and logical access controls and data recovery strategies, need to be *thorough and comprehensive* for data enters, since they are centralized structures that store and process business data.
由于数据中心采用集中式结构来存储和处理业务数据，因此它对安全的要求是 *彻底和全面的*，比如物理和逻辑的访问控制以及数据恢复策略。
**Outsourcing data center-based IT resources** has been a common industry practices for decades.
**基于数据中心的 IT 资源外包** 成为了行业惯例。
However, the outsourcing models often required *long-term consumer commitment* and usually could *not provide elasticity*, issues that a typical cloud can address via inherent features, such as ubiquitous access, on-demand provisioning, rapid elasticity, and pay-per-use.
然而，外包模式需要长期的 *用户承诺*，并且常常 *缺乏灵活性*，而这些都是典型的云通过自身特性（如随处访问、按需配置、快速弹性和按使用付费）等可以解决的问题。

### Facilities 配套设备

Data center facilities are *custom-designed* locations that are outfitted with specialized computing, storage, and network equipment.
数据中心的配套设施放置在 *专门设计* 的位置，配备了专门的计算设备、存储设备和网络设备。
The site and layout of a given data center facility are typically demarcated into *segregated spaces*.
一个给定的数据中心的位置和布局通常被划分为 *隔离的空间*。

### Computing Hardware 计算硬件

Much of the heavy processing in data centers is often executed by **standardized commodity servers** that have substantial computing power and storage capacity.
数据中心内许多工作量较重的处理是由 **标准化商用服务器** 来执行的，这些模块化服务器具备强大的计算能力和存储容量。

Several computing hardware technologies are intergrated into these modular servers, such as:
包括了一些计算硬件技术，例如：

- rackmount form factor server design composed of **standardized racks** with interconnects for power, network, and internal cooling
  机架式服务器设计由含有电源、网络和内部冷却线路的 **标准机架** 构成
- support for different **hardware processing architectures**, such as x86-32bits, x86-64, and RISC
  支持不同的 **硬件处理架构**，例如 x86-32位、x86-64位和 RISC
- a **power-efficient multi-core CPU architecture** that houses hundreds of processing cores in a spece as small as a single unit of standardized racks
  在大小如标准机架一个单元的空间上，可以容纳一个具有几百个处理器内核的 **高效能多核 CPU**
- redundant and **hot-swappable** components, such as hard disks, power supplies, network interfaces, and storage controller cards
  冗余且 **可热插拔** 的组件，如硬盘、电源、网络接口和存储控制器卡

**Computing architecture such as blade server technologies** use rack-embedded physical interconnections(blade enclousures), fabrics(switches), and shared power supply units and cooling fans.
**计算架构（如刀片服务器技术）** 使用了嵌入式机架物理互联（刀片机箱）、光纤（交换机）、共享电源和散热风扇。

### Storage Hardware 存储硬件

- **Hard Disk Arrays（硬盘阵列）**
  - Increase *performance and redundancy* by including spare disks.
    利用备份磁盘提升 *性能和冗余度*。
  - This technology is often implemented using redundant arrays of **independent disks(RAID)** schemes, which are typically realized through hardware disk array controllers.
    这项技术一般利用 **独立磁盘冗余阵列（RAID）** 方案，通常使用硬件磁盘阵列控制器来实现。
- **I/O Caching（I/O 高速缓存）**
  - This is generally performed through hard disk array controllers, which enhance disk access times and performance by data caching.
    通常由硬盘阵列控制器完成，通过数据缓存来降低磁盘访问时间，提高性能。
- **Hot-swappable hard disk（热插拔硬盘）**
  - These can be safely removed from arrays without requiring prior powering down.
    无需关闭电源，即可安全地从磁盘阵列移除硬盘。
- **Storage Virtualization（存储虚拟化）**
  - This is realized through the use of virtualized hard disks and storage sharing.
    通过虚拟化硬盘和存储共享来实现。
- **Fast Data Replication Mechanisms（快速数据复制机制）**
  - These include **snapshotting**, which is saving a virtual machine's memory into a hyperviser-readable file for future reloading, and **volume cloning**, which is copying virtual or physical hard disk volumes and partitions.
    包括 **快照** 和 **卷克隆**。快照是指将虚拟机内存保存到一个管理程序可读的文件中，以备将来重新装载。卷克隆是指复制虚拟或物理硬盘的卷和分区。

Storage systems encompass **tertiary redundancies**, which are used as backup and recovery systems that typically rely on removable media.
存储系统包含 **三级冗余**，通常依赖移动介质用于备份和恢复系统。
This type of system can exist as a *networked IT resource* or *direct-attached storage(DAS)*, in which a torage system is directly connected to the computing IT resource using a *host bus adapter(HBA)*.
这种类型的系统可能是通过 *网络连接的 IT 资源*，也可能是 *直接附加存储（DAS）*，在 DAS 中存储系统通过 *主机总线适配器（HBA）* 直接连接到计算 IT 资源。

Network storage devices usually fall into one of the following categories:
网络存储设备通常分为如下两类：

- **Storage Area Network(SAN)** —— Physical data storage media are connected through a dedicated network and provide block-level data storage access using industry standard protocols, such as the Small Computer System Interface(SCSI).
  **存储区域网络** —— 物理数据存储介质通过专门网络互联，使用工业标准协议（如小型计算机系统接口（SCSI））提供数据块级的数据存储访问。
- **Network-Attached Storage(NAS)** —— Hard drive arrays are contained and managed by this dedicated device, which connects through a network and facilitates access to data using file-centric data access protocols like the Network File System(NFS) or Server Message Block(SMB).
  **网络附加存储** —— 硬盘阵列包含在这个专用设备中，并由其管理。该设备通过网络链接，使用如网络文件系统（NFS）或服务器消息块（SMB）等以文件为中心的数据访问协议来访问数据。

### Network Hardware 网络硬件

#### Carrier and External Networks Interconnection 运营商和外网互联

A subsystem related to the internetworking infrastructure, this interconnection is usually comprised of 
**backbone routers** that provide *routing between external WAN connections and the data center's LAN*, as well as **perimeter network security devices** such as *firewalls and VPN gateways*.
这是与网络互联基础设施相关的子系统。这种互联通常由 **主干路由器** 和 **外围网络安全设备** 组成。其中，主干路由器提供 *外部 WAN 连接与数据中心 LAN 之间的路由*，外围网络安全设备包括 *防火墙和 VPN 网关*。

#### Web-Tier Load Balacing and Acceleration Web 层负载均衡和加速

This subsystem comprises Web acceleration devices, such as XML pre-processors, encryption/decryption appliances, and layer 7 switching devices that perform content-aware routing.
这个子系统包括 Web 加速设备，如 XML 预处理器、加密/解密设备以及进行内容感知路由的第 7 层交换设备。

#### LAN Fabric LAN 光网络

The LAN fabric constitutes the internal LAN and provides high-performance and redundant connectivity for all the data center's network-enabled IT resources.
内部 LAN 是光网络，为数据中心所有联网的 IT 资源提供高性能的冗余连接。

#### SAN Fabric SAN 光网络

Related to the implementation of storage area networks(SANs) that provide connectivity between servers and storage systems, the SAN fabric is usually implemented with Fibre Channel(FC), Fibre Channel over Ethernet(FCoE), and InfiniBand network switches.
SAN 光网络与提供服务器和存储系统互联的存储区域网络（SAN）相关，它通常由光纤通道（FC）、以太网光纤通道（FCoE）和 InfiniBand 网络交换机来实现。

#### NAS Gateways NAS 网关

This subsystems supplies attachment points for NAS-based storage devices and impliments protocol conversion hardware that facilitates data transmission between SAN and NAS devices.
这个子系统为基于 NAS 的存储设备提供连接点，提供实现协议转换的硬件，以便实现 SAN 和 NAS 设备之间的数据传输。

### Other Considerations 其他考量

IT hardware is subject to rapid technological obsolescence, with lifecycles that typically last between five to seven years.
IT 硬件受快速技术折旧的影响，其生命周期一般是 5~7 年。

Security is another major issue when considering the role of the data center and the vast quantities of data contained within its doors.
考虑到数据中心的作用以及其中存放的庞大数据，安全性也是一个关键问题。

## VIRTUALIZATION TECHNOLOGY 虚拟化技术

**Virtualization** is the process of converting a physical IT resource into a virtual IT resource.
**虚拟化** 是将物理 IT 资源转换为虚拟 IT 资源的过程。
Most types of IT resources can be virtualized, including *servers, storage, network and power*.
大多数 IT 资源都能被虚拟化，包括 *服务器、存储设备、网络和电源*。

> The terms **virtual server** and **virtual machine(VM)** are used synonymously throughout this book.
  本书中，术语 **虚拟服务器** 和 **虚拟机（VM）** 为同义词。

The first step in creating a new virtual server through **virtualization software** is **the allocation of physical IT resources**, followed by **the installation of an operating system**.
用 **虚拟化软件** 创建新的虚拟服务器时，首先是 **分配物理 IT 资源**，然后是 **安装操作系统**。
Virtual servers use their own **guest operating systems**, which are independent of the operating system in which they were created.
虚拟服务器使用自己的 **客户操作系统**，它独立于创建虚拟服务器的操作系统。

Both the guest operating system and the application software running on the virtual server are **unaware** of the virtualization process, meaning these virtualized IT resources are installed and executed as if they were running on a separate physical server.
在虚拟服务器上运行的客户操作系统和应用软件都 **不会感知到** 虚拟化的过程，也就是说，这些虚拟化 IT 资源就好像是在独立的物理服务器上安装执行一样。
This **uniformity** of execution that allows programs to run on physical systems as they would on virtual systems is a vital characteristic of virtualization.
这样程序在物理系统撒谎给你执行和在虚拟系统上执行就是一样的，这种执行上的 **一致性** 是虚拟化的关键特性。

Virtualization software runs on a physical server called a **host** or **physical host**, whose underlying hardware is made accessible by the virtualizaiton software.
运行虚拟化软件的物理服务器称为 **主机** 或 **物理主机**，其底层硬件可以被虚拟化软件访问。

The virtualization software functionality encompasses system services that are specifically related to virtual machine management and not normally found on standard operating systems.
虚拟化软件功能包括系统服务，具体来说是与虚拟机管理相关的服务，这些服务通常不会出现在标准操作系统中。
This is why this software is sometimes referred to as a **virtual machine manager** or a **virtual machine monitor(VMM)**, but most commonly known a **hypervisor**.
因此，这种软件有时也称为 **虚拟机管理器** 或 **虚拟机监视器**，而最常见的称呼为 **虚拟机监控器**。

### Hardware Independence 硬件无关性

The installation of an operating system's configuration and application software in a unique IT hardware platform in many software-hardware dependencies.
在一个 IT 硬件平台上配置操作系统和安装应用软件会导致许多软硬件依赖关系。

Virtualization is a *conversion process* that translates unique IT hardware into emulated and standardized software-based copies.
虚拟化则是一个 *转换的过程*，它对某种 IT 硬件进行仿真，将其标准化为基于软件的版本。
Through hardware independence, virtual servers can easily be moved to another virtualization host, automatically **resolving multiple hardware-software incompatibility issues**.
依靠硬件无关性，虚拟服务器能够自动 **解决软硬件不兼容的问题**，很容易地迁移到另一个虚拟主机上。

### Server Consolidation 服务器整合

The **coordination function** that is provided by the virtualization software allows *multiple virtual servers to be simultaneously created in the same virtualization host*.
虚拟化软件提供的 **协调功能** 可以 *在一个虚拟主机上同时创建多个虚拟服务器*。
Virtualization technology enables different virtual servers to share one physical server.
虚拟化技术允许不同的虚拟服务器共享同一个物理服务器。
This process is called **server consolidation** and is commonly used to increase hardware utilization, load balancing, and optimization of available IT resources.
这就是 **服务器整合**，通常用于提高硬件利用率、负载均衡以及可用 IT 资源的优化。

### Resource Replication 资源复制

Virtual servers are created as virtual disk images that contain **binary file copies** of hard disk content.
创建虚拟服务器就是生成虚拟磁盘映像，它是硬盘内容的 **二进制文件副本**。
The virtual disk images are accessible to the host's operating system, meaning simple file operations, such as copy, move, and paste, can be used to replicate, migrate, and back up the virtual server.
主机操作系统可以访问这些虚拟磁盘映像，因此，简单的文件操作（如复制、移动和粘贴）可以用于实现虚拟服务器的复制、迁移和备份。
This **ease of manippulation and replication** is one of the most salient features of virtualization technology.
这种 **操作和复制的方便性** 是虚拟化技术最突出的特点之一。

### Operating System-Based Virtualization 基于操作系统的虚拟化

**Operating system-based virtualization** is the installation of virtualization software in a pre-existing operating system, which is called the **host operating system**.
**基于操作系统的虚拟化** 是指，在一个已存在的操作系统上安装虚拟化软件，这个已存在的操作系统被称为 **宿主操作系统**。

![基于操作系统虚拟化](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/jiyucaozuoxitongxunihua.PNG)

Since the host operating system can provide hardware devices with the necessary support, operating system virtualization can **rectify hardware compatibility issues** even if the hardware driver is not available to the virtualization software.
由于操作系统可以提供对硬件设备的必要支持，所以，即使虚拟化软件不能使用硬件驱动程序，操作系统虚拟化也可以 **解决硬件兼容问题**。

Virtualization software translates hardware IT resources that require unique software for operation into virtualized IT resources that are compatible with a range of operating systems.
虚拟化软件将需要特殊操作软件的硬件 IT 资源转换为兼容多个操作系统的虚拟 IT 资源。
Since the host operating system is a complete operating system in itself, many operating system-based services that are available as **administration tools** can be used to manage the physical host.
由于宿主操作系统自身就是一个完整的操作系统，因此，许多用来作为 **管理工具** 的基于操作系统的服务可以被用来管理物理主机。

Operating system-based virtualization can introduce demands and issues related to **performance overhead** such as:
基于操作系统的虚拟化会产生与 **性能开销** 相关的如下需求和问题：

- The host operating system consumes CPU, memory, and other hardware IT resources.
  宿主操作系统消耗 CPU、内存和其他硬件 IT 资源。
- **Hardware-related calls** from guest operating systems need to traverse several layers to and from the hardware, which decreases overall performance.
  来自客户操作系统的 **硬件相关调用** 需要穿越多个层次，降低整体性能。
- **Licenses** are usually required for host operating systems, in addition to individual licenses for each of their guest operating systems.
  宿主操作系统通常需要 **许可证**，而其每个客户操作系统也需要一个独立的许可证。

### Hardware-Based Virtualization 基于硬件的虚拟化

This option represents **the installation of virtualization software directly on the physical host hardware** so as to bypass the host operating system, which is persumably engaged with operating system-based virtualization.
基于硬件的虚拟化是指 **将虚拟化软件直接安装在物理主机硬件上**，从而绕过宿主操作系统，这也适用于基于操作系统的虚拟化。

![基于硬件虚拟化](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/jiyuyingjianxunihua.PNG)

Allowing the virtual servers to interact with hardware without requiring intermediary action from the host operating system generally makes hardware-based virtualization **more efficient**.
由于虚拟服务器与硬件的交互不再需要来自宿主操作系统的中间环节，因此，基于硬件的虚拟化通常 **更高效**。

Virtualization software is typically referred to as a **hypervisor** for this type of processing.
在这种情况下，虚拟化软件一般是指 **虚拟机管理程序**。

**Device drivers and system services are optimized for provisioning of virtual servers**, althorgh many standard operating system functions are not implemented.
虽然没有实现许多标准操作系统的功能，但是为了供给虚拟服务器，**优化了设备驱动程序和系统服务**。

One of the main issues of hardware-based virtualization concerns **compatibility** with hardware devices.
基于硬件虚拟化的一个主要问题是与硬件设备的 **兼容性**。

Host management and administration features may further not include the range of advanced functions that are common to operating systems.
操作系统的高级功能在虚拟机管理程序中就不一定有了。

### Virtualization Management 虚拟化管理

Virtualized IT resource management is often supported by **virtualization infrastructure management(VIM)** tools that collectively manage virtual IT resources and rely on a centralized meanagement module, otherwise known as a controller, that runs on a dedicated computer.
虚拟化 IT 资源的管理通常是由 **虚拟化基础设施管理（VIM）** 工具予以实现。

### Other Considerations 其他考量

**Performance Overhead 性能开销**

A common strategy used to rectify the overhead issue is a technique called *para-virtualization*, which presents a software interface to the virtual machines that is not identical to that of the underlying hardware.
通常用来改进开销问题的策略是一种被称为 *半虚拟化* 的技术，它向虚拟机提供了一个不同于底层硬件的软件接口。

**Sepcial Hardware Compatibility 特殊硬件兼容性**

These types of incompatibility issues can be resolved using established commodity hardware platforms and mature virtualization software products.
解决这种兼容性问题的方法就是，使用现有的商品化硬件平台和成熟的虚拟化软件产品。

**Portability 可移植性**

Initiatives such as the Open Virtualization Format(OVF) for the standardization of virtual disk image formats are dedicated to alleviating this concern.
开放虚拟化格式（OVF）这样的项目就是为了标准化虚拟磁盘格式。

## WEB TECHNOLOGY Web 技术

### Basic Web Technology 基本 Web 技术

The **World Wide Web** is a system of interlinked IT resources that are accessed through the Internet.
**WWW** 是由通过 Internet 访问的互联 IT 资源构成的系统。
The two basic components of the Web are the **Web browser client** and the **Web server**.
它的两个基本组件是 **Web 浏览器客户端** 和 **Web 服务器**。
Other components, such as proxies, caching services, gateways, and load balancers, are used to improve Web application characteristics such as scalability and security.
还有其他一些组件，如代理、缓存服务、网关、负载均衡等，用于改进诸如可扩展性和安全性这样的 Web 应用特性。

Three fundamental elements comprise the technology architecture of the Web:
Web 技术架构由三个基本元素组成：

- **Uniform Resource Locator(URL) 统一资源定位符**
  - A standard syntax used for creating identifiers that point to Web-based resources, the URL is often structed using a logical network location.
    一个标准语法，用于创建指向 Web 资源的标识符。URL 通常由逻辑网络位置构成。
- **Hypertext Transfer Protocol(HTTP) 超文本传输协议**
  - This is the primary communications protocol used to exchange content and data throughout the World Wide Web.
    通过 WWW 交换内容和数据的基本通信协议。
- **Markup Languages(HTML, XML) 标记语言**
  - Markup languages provide a lightweight means of expressing Web-centric data and metadata.
    标记语言提供一个轻量级方法来表示以 Web 为中心的数据和元数据。

Web resources are represented as **hypermedia** as opposed to hypertext, meaning media such as graphics, audio, video, plain text, and URLs can be referenced collectively in a single document.
Web 资源也被称为 **超媒体**，以区别于超文本。这也意味着，媒体，如图形、音频、视频、纯文本和 URL 等，全部可以在单个文件中引用。
Some types of hypermedia resources cannot be rendered without **additional software** or **Web browser plug-ins**.
有些类型的超媒体需要 **额外的软件** 或 **Web 浏览器插件** 才可以提供。

### Web Applications Web 应用

A distributed application that uses Web-based technologies is typically considered a **Web application**.
使用基于 Web 技术的分布式应用通常被认为是 **Web 应用**。

![三层基本架构](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/sancengjibenjiagou.PNG)

The first tier is called the **presentation layer**, which represents the user-interface.
第一层为 **表示层**，用于表现用户界面。
The middle tier is the **application layer** that implimemnts application locic, while the third tier is the **data layer** that is comprised of persistent data stores.
第二层为 **应用层**，用于实现应用逻辑。第三层为 **数据层**，由持久性数据存储构成。

## MULTITENANT TECHNOLOGY 多租户技术

The multitenant application design was created to enable **multiple user(tenants)** to access the same application logic simultaneously.
设计多租户应用的目的是使得 **多个用户（租户）** 在逻辑上同时访问同一个应用。

Multitenant applications ensure that tenants do not have access to data and configuration information that is not their own.
多租户应用确保每个租户都不会访问到不属于自己的数据和配置信息。
Tenants can *individually customize* features of the application.
每个租户都可以 *独立定制* 应用特性。

Multitenant application architecture is often significantly more complex than that of single-tenant applications。
多租户应用架构通常比但租户应用要复杂得多。
Multitenant applications need to support the sharing of various artifacts by multiple user, while maintaining security levels that segregate individual tenant operational environments.
多租户应用架构需要支持多用户对各种构件的共享，同时还需要保持安全等级来隔离不同租户的操作环境。

Common characteristics of multitenant applications include:
多租户应用的一般特点包括：

- *Usage Isolation 使用隔离*
- *Data Security 数据安全*
- *Recovery 可恢复性*
- *Application Upgrades 应用升级*
- *Scalability 可扩展性*
- *Metered Usage 使用计费*
- *Data Tier Isolation 数据层隔离*

## SERVICE TECHNOLOGY 服务技术

The field of **service technology** is a *keystone* foundation of cloud computing that formed the basis of the "as-a-service" cloud delivery models.
**服务技术** 是云计算的 *基石*，它形成了 "作为服务" 的云交付模型的基础。

### Web Services Web 服务

Also commonly prefixed with "SOAP-based", Web services represent an established and common medium for sophisticatedm, Web-based service logic.
Web 服务也常冠以 "基于 SOAP" 的前缀，对于复杂的、基于 Web 的服务逻辑来说，它是确定的和通用的媒介。

Along with **XML**, the core technologies behind Web services are represented by the following industry standards:
与 **XML** 一起，Web 服务的核心技术表现为如下工业标准：

- **Web Service Description Language(WSDL) Web 服务描述语言**
- **XML Schema Definition Language(XML Schema) XML 模式描述语言**
- **SOAP**
- **Universal Description, Discovery, and Integration(UDDI) 统一描述、发现和集成**

### REST Services REST 服务

**REST services** are designed according to a set of **constraints** that shape the service architecture to emulate the properties of the World Wide Web, rusulting in service implementations that rely on the use of core Web technologies.
**REST 服务** 是按照一组 **约束条件** 设计的，这组约束条件使得服务架构模拟 WWW 的属性，从而导致服务的实现要依赖于使用核心 Web 技术。

Unlike Web services, REST services do not have individual technical interfaces but instead share a common technical interface that is known as the **uniforn contract**, which is typically established via the use of HTTP methods.
与 Web 服务不同，REST 服务没有独立的技术接口，取而代之的是共享一个通用技术接口，该接口称为 **统一合约**，一般通过使用 HTTP 方法来建立。

The six REST design constraints are:
REST 有 6 个设计约束，分别是：

- Client-Server 客户端-服务器
- Stateless 无状态
- Cache 缓存
- Interface/Uniform Contract 接口/统一合约
- Layered System 层次化系统
- Code-On-Demand 按需编码

### Service Agents 服务代理

Service agents are **event-driven programs** designed to intercept messages at runtime.
服务代理是 **事件驱动程序**，它在运行时拦截消息。
There are **active** and **passice service agents** perform an action upon intercepting and reading the contents of a message.
服务代理分为 **主动服务代理** 和 **被动服务代理**，两者在基于云的环境中都比较常见。

Active service agents **perform an action** upon intercepting and reading the contents of a message.The action typically requires making changes to the message contents or changes to the message path itself.
主动服务代理在拦截并读取消息内容后，会 **采取一定措施**，通常是修改消息内容，或者修改消息路径。

Passive service agents, on the other hand, **do not change** message contents.Instead, they read the message and may then capture certain parts of its contents, usually for monitoring, logging, or reporting purposes.
反之，被动服务代理 **不会修改** 消息内容，而是在读取消息后，捕捉特定内容以便进行监控、记录或者报告。

### Service Middleware 服务中间件

Falling under the umbrella of service technology is the large market of middleware platforms that evolves from messaging-oriented middleware(MOM) platform used primarily to facilitate integration, to sophisticated service middleware platforms designed to accommodate complex service compositions.
服务技术的大框架下是市场巨大的中间件平台，它从主要促进集成的面向消息的中间件（MOM）平台演变为适应复杂服务组合的高级服务中间件平台。

The two most common types of middleware platforms relevant to services computing are **the enterprise service bus(ESB)** and **the orchestration platform**.
与服务计算相关的中间件平台有两种最常见的类型，一个是 **企业服务总线（ESB）**，另一个是 **业务流程平台**。

The ESB encompasses a range of intermediary processing features, including service brokerage, routing, and message queuing.
ESB 包含了一系列中间处理功能，如服务中介、路由和消息队列。
Orchestration environments are designed to host and execute workflow logic that drives the runtime composition of services.
业务流程环境用于存储和执行工作流逻辑，以驱动运行时的服务组合。
