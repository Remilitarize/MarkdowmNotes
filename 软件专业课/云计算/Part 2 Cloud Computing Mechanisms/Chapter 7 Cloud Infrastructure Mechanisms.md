[toc]

## LOGICAL NETWORK PERIMETER 逻辑网路边界

Defined as the isolation of a network environment from the rest of a communications network, the **logical network perimeter** establishes a *virtual network boundary* that can encompass and isolate a group of related cloud-based IT resources that may be **physically distributed**.
**逻辑网络边界** 被定义为将一个网络环境与通信网络的其他部分隔离开来，形成了一个 *虚拟网络边界*，它包含并隔离了一组相关的基于云的 IT 资源，这些资源 **在物理上可能是分布式的**。

![逻辑网络边界](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/luojiwangluobianjie.PNG)

> 逻辑网络边界用一个虚线框表示。

This mechanism can be implemented to:
该机制可被用于：

- isolate IT resources in a cloud from non-authorized users
  将云中的 IT 资源与非授权用户隔离
- isolate IT resources in a cloud from non-users
  将云中的 IT 资源与非用户隔离
- isolate IT resources in a cloud from cloud consumers
  将云中的 IT 资源与云用户隔离
- control the bandwidth that is available to isolate IT resources
  控制被隔离 IT 资源的可用带宽

Logical network perimeters are typically established via **network devices** that supply and control the connectivity of a data center and are commonly deployed ad virtualized IT environments that include:
逻辑网络边界通常由提供和控制数据中心连接的 **网络设备** 来建立，一般是作为虚拟化的 IT 环境进行部署的。其中包括：

- **Virtual Firewall 虚拟防火墙**
    - An IT resource that actively filters network traffic to and from the isolated network while controlling its interactions with the Internet.
      一种 IT 资源，可以主动过滤被隔离网络的网络流量，并控制其与 Intermet 的交互。
- **Virtual Network 虚拟网络**
    - Usually acquired through VLANs, this IT resource isolates the network environment within the data center infrastructure.
      一般通过 VLAN 形成，这种 IT 资源用来隔离数据中心基础设施内的网络环境。
    
![虚拟防火墙](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/xunifanghuoqiang.PNG)

![虚拟网络](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/xunishebei.PNG)

> 虚拟防火墙用竖直长条表示，虚拟网络用斜长条表示。

A **logical network layout** is established through a set of logical network perimeters using various firewalls and virtual networks.
利用各种防火墙和虚拟网络，通过一组逻辑网络边界建立的 **逻辑网路布局**。

![逻辑网络布局](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/luojiwangluobuju.PNG)

## VIRTUAL SERVER 虚拟服务器

A **virtual server** is a form of virtualization software that emulates a physical server.
**虚拟服务器** 是一种模拟物理服务器的虚拟化软件。
Virtual servers are used by cloud providers to share the same physical server with multiple cloud consumers by providing cloud consumers with *individual virtual server instances*.
通过向云用户提供 *独立的虚拟服务器实例*，云提供者使多个云用户共享同一个物理服务器。

![虚拟服务器](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/xunifuwuqi.PNG)

As a commodity mechanism, the virtual server represents **the most foundational** building block of cloud environments.
作为一个有价值的机制，虚拟服务器是 **最基本的** 云环境构建块。
The instantiation of virtual servers from **image files** is a **resource allocation process** that can be completed *rapidly and on-demand*.
从 **映像文件** 进行虚拟服务器的实例化是一个可以 *快速且按需* 完成的 **资源分配过程**。
Cloud consumers that install or lease virtual servers can **customize** their environments *independently* from other cloud consumers that may be using virtual servers hosted by the same underlying physical server.
通过安装或释放虚拟服务器，云用户可以 **定制** 自己的环境，这个环境 *独立* 于其他正在使用由同一底层物理服务器控制的虚拟服务器的云用户。

![创建虚拟服务器](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/chuangjianxunifuwuqi.PNG)

![虚拟服务器的创建与管理](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/xunifuwuqidechaungjianyuguanli.PNG)

1. The cloud consumer uses the self-service portal to select a template virtual server for creation.
   云用户使用自助服务入口，为创建选择一个样板虚拟服务器。
2. A copy of the corresponding VM image is created in a cloud consumer-controlled cloud storage device.
   在云用户控制的云存储设备中生成相应 VM 映像的副本。
3. The cloud consumer initiates the virtual server using the usage and administration portal.
   云用户通过使用与管理入口启动虚拟服务器。
4. The portal interacts with the VIM to create the virtual server instance via the underlying hardware.
   该入口与 VIM 交互，通过底层硬件生成虚拟服务器实例。
5. The cloud consumer is able to use and customize the virtual server via other features on the usage and administration protal.
   通过使用与管理入口的其他功能，云用户可以使用并定制虚拟服务器。

## CLOUD STORAGE DEVICE 云存储设备

The **cloud storage device** mechanism represents storage devices that are designed specifically for cloud-based provisioning.
**云存储设备** 机制是指专门为基于云配置所设计的存储设备。

Instances of these devices can be **virtualized**, similar to how phyisical servers can spawn virtual server images.
如同物理服务器如何大量产生虚拟服务器映像一样，这些设备的实例可以被 **虚拟化**。
Cloud storage devices are commonly able to provide **fixed-increment capacity allocation** in support of the **pay-per-use** mechanism.
在支持 **按使用计费** 的机制时，云存储设备通常可以提供 **固定增幅的容量分配**。
Cloud storage devices can be exposed for **remote access** via cloud storage services.
通过云存储服务，还可以 **远程访问** 云存储设备。

A primary concern related to cloud storage is the **security, integrity, and confidentiality**.
一个与云存储相关的主要问题是 **数据的安全性、完整性和保密性**。
There can also be **legal and regulatory implications** that result from relocating data across geographical or national boundaries.
数据出现跨地域或国界的迁移时，也会导致 **法律和监管问题**。
Another issue applies specifically to the **performance of large databases**. LANs provide locally stored data with network reliability and latency levels that are superior to those of WANs.
还有一个问题是关于 **大型数据库性能方面** 的，即 LAN 提供的本地数据存储在网络可靠性和延迟水平上均优于 WAN。

### Cloud Storage Levels 云存储等级

Cloud storage device mechanisms provide common logical units of data storage, such as:
云存储设备机制提供常见的数据存储逻辑单元，例如：

- **Files 文件**
    - Collections of data are grouped into files that are located in **folders**.
      数据集合分组存放于 **文件夹** 中的文件里。
- **Blocks 块**
    - **The lowest level of storage and the closest to the hardware**, a block is the **smallest unit of data** that is still individually accessible.
      **存储的最低等级，最接近硬件**，数据块是可被独立访问的 **最小数据单位**。
- **Datasets 数据集**
    - Sets of data are organized into a **table-based, delimited, or record format**.
      **基于表格的、以分隔符分割的或以记录形式** 组织的数据集合。
- **Objects 对象**
    - Data and its associated **metadata** are organized as Web-based resources.
      将数据及其相关的 **元数据** 组织为基于 Web 的资源。

Each of these data storage levels is commonly associated with a certain type of technical interface which corresponds to a particular type of cloud storage device and cloud storage service used to expose its API.
每个数据存储等级通常都与某种类型的技术接口相关联，这个技术接口不仅与特定类型的云存储设备对应，还与显示其 API 的云存储服务对应。

### Network Storage Interfaces 网络存储接口

Legacy network storage most commonly falls under the category of network storage interfaces.
传统的网络存储大多受到网络存储接口类别的影响。
It includes storage devices in compliance with industry standard protocols.
它包括了符合工业标准协议的存储设备。

- **SCSI** for **storage blocks and the server message block(SMB)**
  用于 **存储块和服务消息块的 SCSI**
- *Common Internet file system(CIFS)*, and *network file system(NFS)* for *file and network storage*
  用于 *文件与网络存储* 的 *通用 Internet 文件系统* 和 *网络文件系统*

**Block storage** requires data to be in a fixed format (known as a **data block**), which is the smallest unit that can be stored and accessed and the storage format closest to hardware.
**块存储** 要求数据具有固定格式（称为 **数据块**），这种格式最接近硬件，并且是存储和访问的最小单元。
Using either the **logical unit number(LUN)** or **virtual volume block-level storage** will typically have better performance than file-level storage.
不论是使用 **逻辑单元号（LUN）** 还是 **虚拟卷**，与文件级存储相比，块级存储通常都具有更好的性能。

### Object Storage Interfaces 对象存储接口

Various types of data can be referenced and stored as **Web resources**.
各种类型的数据都可以作为 **Web 资源** 被引用和存储。
This is referred to as **object storage**, which is based on technologies that can support a range of data and media types.
这就是 **对象存储**，它以可以支持多种数据和媒体类型的技术为基础。

Cloud Storage Device mechanisms that implement this interface can typically be accessed via **REST** or **Web service-based cloud services** using **HTTP** as the prime protocol.
实现这种接口的云存储设备机制通常可以通关过以 **HTTP** 为主要协议的 **REST** 或者 **基于 Web 服务的云服务** 来访问。
The *Storage Networking Industry Association's Cloud Data Menagement Interface(SNIA's CDMI)* supports the use of object storage interfaces.
*网络存储行业协会（SNIA）的云数据管理接口（CDMI）* 规范支持使用对象存储接口。

### Database Storage Interfaces 数据库存储接口

Cloud storage device mechanisms based on database storage interfaces typically support a **query language** in addition to basic storage operations. Storage management is carried out using a **standard API** or an **administrative user-interface**.
基于数据库存储接口的运输局设备机制除了支持基本存储操作外，通常还支持 **查询语言**，并通过 **标准 API** 或 **管理用户接口** 来实现存储管理。

#### Relational Data Storage 关系数据存储

**Relational databases** (or relational storage devices) rely on **tables** to organize similar data into rows and columns.
**关系数据库**（或关系存储设备）依靠 **表格**，将相似的数据组织为行列形式。
Working with relational storage commonly involves the use of the industry standard **Structured Query Language(SQL)**.
使用关系存储，通常也要用到工业标准 **结构化查询语言（SQL）**。

Challenges with cloud-based relational databases commonly pertain to **scaling and performance**.
基于云的关系数据库的挑战主要来自于 **扩展和性能**。

#### Non-Relational Data Storage 非关系数据存储

**Non-relational storage** (also commonly referred to as **NoSQL storage**) moves away from the traditional relational database model in that it establishes a **looser** structure for stored data with less emphasis on defining relationships and relizing data normalization.
**非关系存储**（通常被称为 **NoSQL 存储**）与传统关系数据库模型相比有较大差异，它采用 **更加松散的** 结构来存储数据，不强调定义关系和实现数据规范化。

The primary motivation for using non-relational storage is to **avoid the potential complexity and processing overhead that can be imposed by relational databases**.
使用非关系存储的主要动力是 **避免关系数据库带来的可能的复杂性和处理成本**。
Also, non-relational storage can be **more horizontally scalable** than relational storage.
同时，与关系存储相比，非关系存储可以进行 **更多的水平扩展**。

The trade-off with non-relational storage is that the data **loses much of the native form and validation** due to limited or primitive schemas or data models.
由于有限的或原始的模式或者数据模型，非关系存储需要权衡的是数据 **失去多少原始形式和验证**。
Furthermore, non-relational repositories don't tend to support relational database functions, such as *transactions or joins*.
此外，非关系存储还倾向于不支持关系数据库的功能，如 *事务或连接*。

Cloud providers often offer non-relational storage that provides *scalability and availability* of stored data over multiple server environments.
在多服务器环境中，云提供者提供的非关系存储可以带来存储数据的 *可扩展性和可用性*。
However, many non-relational storage mechanisms are proprietary and therefore can severely limit data portability.
然而，许多非关系存储机制是专有的，因此严重限制了数据的可移植性。

![基于对象存储接口的云存储设备](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/jiyuduixiangcunchujiekoudeyuncunchushebei.PNG)

1. The cloud consumer interacts with the usage and administration portal to create a cloud storage device and define access control policies.
  云用户和使用与管理入口进行交互，创建一个云存储设备，并定义访问控制规则。
2. The usage and administration portal interact with the cloud storage software to create the cloud storage device instance and apply the required access policy to its data objects.
  使用与管理入口和云存储软件交互，创建云存储设备实例，并对其数据对象实行请求访问策略。
3. Each data object is assigned to a cloud storage device and all of the data objects are stored in the same virtual storage volume. The cloud consumer uses the proprietary cloud storage device UI to interact directly with the data objects.
  每个数据对象都分配到云存储设备，所有的数据对象都存入同一个虚拟存储卷。云用户通过专有云存储设备界面直接与数据对象交互。

![由虚拟化平台管理的基于块的云存储设备](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/youxunihuapingtaiguanlidejiyukuaideyuncunchushebei.PNG)

1. The cloud consumer uses the usage and administration portal to create and assign a cloud storage device to an existing virtual server.
  云用户通过使用与管理入口，为一个已有虚拟服务器创建并配置一个云存储设备。
2. (a) The usage and administration portal interacts with the VIM software, (b) which creates and configures the appropriate LUN. **Each cloud storage device uses a separate LUN controlled by the virtualization platform.**
  (a)使用与管理入口和 VIM 交互，(b)创建并配置适当的 LUN。**每个云存储设备使用的是虚拟化平台控制下的独立 LUN。**
3. (a) The cloud consumer remotely logs into the virtual server directly (b) to access the cloud storage device.
  (a)云用户直接远程登录到虚拟服务器，(b)以便访问云存储设备。

## CLOUD USAGE MONITOR 云使用监控

The **cloud usage monitor** mechanism is a *lightweight* and *autonomous* software program responsible for collecting and processing IT resources *usage data*.
**云使用监控** 机制是一种 *轻量级* 的 *自治* 软件程序，用于收集和处理 IT 资源的 *使用数据*。

Depending on the type of usage metrics they are designed to collect and the manner in which usage data needs to be collected, cloud usage monitors can exist in different formats.
根据需要收集的使用指标类型和使用数据收集方式，云使用监控器可以以不同的形式存在。
Each can be designed to forward collected usage data to a **log database** for *post-processing* and *reporting* purposes.
每种形式都将收集到的使用数据发送到 **日志数据库**，以便进行 *后续处理* 和 *报告*。

### Monitoring Agent 监控代理

A **monitoring agent** is an intermediary, **event-driven** program that exists as a service agent and resides along existing communication paths to transparently monitor and analyze dataflows.
**监控代理** 是一个中间的 **事件驱动** 程序，它作为服务代理驻留在已有的通信路径上，对数据流进行透明的监控和分析。
This type of cloud usage monitor is commonly used to measure *network traffic and message metrics*.
这种类型的云使用监控通常被用来计量 *网络流量和消息指标*。

![监控代理](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/jiankongdaili.PNG)

1. A cloud service consumer sends a request message to a cloud service.
  云服务用户向云服务发送请求消息。
2. The monitoring agent intercepts the message to collect relevant usage data,
  监控代理拦截此消息，收集相关使用数据。
3. (a) before allowing it to continue to the cloud service. (b) The monitoring agent stores the collected usage data in a log database.
  (a) 然后将其继续发往云服务。(b) 监控代理将收集到的使用数据存入日志数据库。
4. The cloud service replies with a response message
  云服务产生应答消息
5. That is sent back to the cloud service consumer without being intercepted by the monitoring agent.
  并将其发送回云服务用户，此时监控代理不会进行拦截。

### Resource Agent 资源代理

A **resource agent** is a *processing module* that collects usage data by having *event-driven* interactions with specialized resource software.
**资源代理** 是一种 *处理模块*，通过与专门的资源软件进行 *事件驱动* 的交互来收集使用数据。
This module is used to monitor usage metrics based on pre-defined, observable events at the **resource software level**.
它在 **资源软件级** 上，监控预定义的且可观测时间的使用指标。

![资源代理](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/ziyuandaili.PNG)

1. The resource agent is actively monitoring a virtual server and detects an increase in usage.
  资源代理主动监控虚拟服务器，并检测到使用的增加。
2. The resource agent receives a notification from the underlying resource management program that the virtual server is being scaled up and stores the collected usage data in a log database, as per its monitoring metrics.
  资源代理从底层资源管理程序收到通知，虚拟服务器正在进行扩展，按照其监控指标，资源代理将收集的使用数据存入日志数据库。

### Polling Agent 轮询代理

A **polling agent** is a **processing module** that collects cloud service usage data by polling IT resources.
**轮询代理** 是一种 **处理模块**，通过轮询 IT 资源来收集云服务使用数据。
This type of cloud service monitor is commonly used to **periodically** monitor IT resource status.
它通常被用于 **周期性地** 监控 IT 资源状态。

![轮询代理](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/lunxundaili.PNG)

1. A polling agent monitors the status of a cloud service hosted by a virtual server by sending periodic polling request message and receiving polling response messages that report usage status "A" after a number of polling cycles, until it receives a usage status of "B",
  轮询代理监控虚拟服务器上的云服务状态，它周期性地发送轮询消息，并在数个轮询周期后接收到使用状态为 "A" 的轮询相应消息。当代理接收到的使用状态为 "B" 时，
2. upon which the polling agent records the new usage status in the log database.
  轮询代理就将新的使用状态记录到日志数据库中。

### Case Study Example 案例研究示例

![案例研究示例](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/anliyanjiushili.PNG)

1. The cloud consumer(CS_ID = CS1) requests the creation of a virtual server(VM_ID = VM1) of configuration size type 1(VM_TYPE = type1).
  云用户（CS_ID = CS1）请求创建虚拟服务器（VM_ID = VM1），配置大小为 type1（VM_TYPE = type1）。
2. (a)The VIM creates the virtual server. (b)The VIM's event-driven API generates a resource usage event with timestamp = t1, which the cloud usage monitor software agent captures and records in the resource usage event log database.
  VIM 事件驱动 API 生成时间戳为 t1 的资源使用事件，云使用监控软件将其捕捉并记录在资源使用事件日志数据库中。
3. Virtual server usage increases and reaches the auto-scaling threshold.
  虚拟服务器使用增加并达到自动扩展的阈值。
4. (a)The VIM scales up Virtual Server VM1 (b)from configuration type1 to type2(VM_TYPE = type2). The VIM's event-driven API generates a resource usage event with timestamp = t2, which is captured and recorded at the resource usage event log database by the cloud usage monitor software agent.
  VIM 将虚拟服务器 VM1 的配置从 type1 扩展到 type2（VM_TYPE = type2）。VIM 事件驱动 API 生成时间戳为 t2 的资源使用事件，云使用监控软件代理将其捕捉并记录在资源使用事件日志数据库中。
5. The cloud consumer shuts down the virtual server.
  云用户关闭虚拟服务器。
6. (a)The VIM stops Virtual Server VM1 (b)and its event-driven API generates a resource usage event with timestamp = t3, which the cloud usage monitor software agent captures and records at the log database.
  (a)VIM 停止虚拟服务器 VM1，(b)其事件驱动 API 生成时间戳为 t3 的资源使用事件，云使用监控软件代理将其捕捉并记录在资源使用事件日志数据库中。
7. The usage and administration portal accesses the log database and calculates the total usage (Utotal) for Virtual Server Utotal VM1.
  使用与管理入口访问日志数据库，计算虚拟服务器的使用总量 Utotal VM1。

## RESOURCE REPLICATION 资源复制

Defined as the creation of multiple instances of the same IT resource, replication is typically performed when amn IT resource's availability and performance need to be enhanced.
复制被定义为同一个 IT 资源创建多个实例，通常在需要加强 IT 资源的可用性和性能时执行。
**Virtualization** technology is used to implement the **resource replication** mechanism to replicate cloud-based IT resources.
使用 **虚拟化** 技术来实现 **资源复制** 机制可以复制基于云的 IT 资源。

![资源复制](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/ziyuanfuzhi.PNG)

> VIMs from different data centers **coordinate** to overcome the unavailability by reallocating the virtual server to a different physical server running in another data center.
  不同数据中心的 VIM 通过 **协作**，将这个虚拟服务器重定位到另一个数据中心的物理服务器上，从而解决了其不可用的问题。

## READY-MADE ENVIRONMENT 已就绪环境

The **ready-made environment** mechanism is a **defining component** of the PaaS cloud delivery model that represents a pre-defined, cloud-based platform comprised of a set of already installed IT resources, ready to be used and customized by a cloud consumer.
**已就绪环境** 机制是 PaaS 云交付模型的 **定义组件**，它代表的是预定义的基于云的平台，该平台由一组已安装的 IT 资源组成，可以被云用户使用和定制。
These environments are utilized by cloud consumers to **remotely develop** and **deploy** their own services and applications within a cloud.
云用户使用这些环境在云内 **远程开发** 和 **配置** 自身的服务与应用程序。

![已就绪环境](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/yijiuxuhuanjing.PNG)

A ready-made environment is generally equipped with a complete **software development kit(SDK)**.
已就绪环境通常配备一套完整的 **软件开发工具包（SDK）**。
Middleware is available for multitenant platform to support the development and deployment of Web applications.
中间件用于多租户平台，支持开发和部署 Web 应用程序。
