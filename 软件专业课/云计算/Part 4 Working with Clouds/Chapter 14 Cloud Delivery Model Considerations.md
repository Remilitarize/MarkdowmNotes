[toc]

## CLOUD DELIVERY MODELS: THE CLOUD PROVIDER PERSPECTIVE 云交付模型：从云提供者的角度看

### Building IaaS Environments 构建 IaaS 环境

The **virtual server** and **cloud storage device mechanisms** represent the two most fundamental IT resources that are delivered as part of a standard rapid provisioning architecture within **IaaS environments**.
**虚拟服务器** 和 **云存储设备机制** 代表着两个最基本的 IT 资源，它们是作为 **IaaS 环境** 中标准快速供给架构的一部分交付的。

Properties used to define various standardized configurations:
由下述这些属性定义各种标准化的配置：
 
- operating system 操作系统
- primary memory capacity 主存容量
- processing capacity 处理能力 
- virtualized storage capacity  虚拟化的存储容量 

#### Data Centers 数据中心

- Multiple data centers can be linked together for **increased resiliency**.
  多数据中心可以连接来以 **增加弹性**。
- Each data center is placed in a different location to **lower the chances of a single failure**.
  每个数据中心放在不同的地理位置，**降低了单一故障** 导致所有的数据中心同时下线的 **可能性**。
- Connected through high-speed communications networks with low latency, data centers can perform load balancing, IT resource backup and replication and increase storage capacity when improving availability and reliability. 
  数据中心通过低延迟的高速通信网络连接起来，在提高可用性和可靠性的同时，还可以进行负载均衡、IT 资源备份和复制以及增加存储容量。

#### Scalability and Reliability 可扩展性和可靠性

- *the dynamic vertical scaling 动态垂直扩展*
- *resource replication 资源复制*
- horizontal scaling process 水平扩展过程
    - *load balancer mechanism 负载均衡机制*
- automatic scalability 自动扩展
    - *the automated scaling listener 自动扩展监听器*
- high-availability configuration 高可用性配置
- replicated IT resources 复制的 IT 资源
    - *failover system 故障转移系统*
- resource cluster 资源集群
    - *a high-availability/high-performance 高可用/高性能*
- the multipath resource access architecture(redundant access paths) 多路径资源访问架构（冗余访问路径）
    - *resource reliability 资源可靠性*
- provisioning of dedicated IT resources 专用 IT 资源的供给
    - *reservation architecture 资源保留架构*

#### Monitoring 监控

- Virtual Server Lifecycles 虚拟服务器生命周期
- Data Storage 数据存储
- Network Traffic 网络流量
- Failure Conditions 失效情况
- Event Triggers 事件触发器

#### Security 安全

略

### Equipping PaaS Environments 装备 PaaS 环境

PaaS environments typically need to be outfitted with a selection of application development and deployment platforms, a matching SDK and IDE, a resource management system mechanism.
PaaS 环境一般需要配置一组选择出来的应用开发和部署平台，以容纳不同的编程模型、语言和框架。

#### Scalability and Reliability 可扩展性与可靠性

- dynamic scalability and workload distribution architectures 动态可扩展性和工作负载分配架构
    - *automated scaling listeners and load balancers 自动扩展监听器和负载均衡器*
- the resource pooling architecture 资源池架构
- standard failover system mechanisms 标准故障转移系统机制
- non-disruptive service relocation architecture 不中断服务重置架构
- resource reservation architecture 资源保存机制
- span multiple data centers and geographical regions 跨多个数据中心和地理区域

![装备 PaaS 环境](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/zhuangbeipaashuanjing.PNG)

1. Load balancers are used to distribute ready-made environment instances that are part of a failover system, while automated scaling listeners are used to monitor the network and instance workloads.
  已就绪环境实例是故障转移系统的一部分，负载均衡器在它们之间分配工作负载，而自动扩展监听器则监控网络和实例工作负载。
2. The ready-made environments are scaled out in response to an increase in workload, 
  为了响应工作负载的增加，已就绪环境进行扩展，
3. and the failover system detects a failure condition and stops replicating a failed ready-made environment.
  而故障转移系统检测到一个故障情况，停止复制一个失效的已就绪环境。

#### Monitoring 监控

- Ready-Made Environment Instances 已就绪环境实例
- Data Persistence 数据持久化
- Network Usage 网络使用
- Failure Conditions 失效情况
- Event Triggers 事件触发器

#### Security 安全

略

### Optimizing SaaS Environments 优化 SaaS 环境

based on **multitenant** environments 基于 **多租户** 环境

SaaS implementations rely heavily on the *native dynamic scalability*, *workload distribution architectures* and *non-disruptive service relocation*.
SaaS 的实现严重依赖于 *本地动态可扩展* 和 *工作负载分布架构* 的特性，并依赖 *不中断服务重置*。

## CLOUD DELIVERY MODELS: THE CLOUD CONSUMER PERSPECTIVE 云交付模型：从云用户的角度看

### Working with IaaS Environments 使用 IaaS 环境

*Virtual servers* are accessed at the operating system level through the use of *remote terminal applications*.
通过使用 *远程终端应用*，可以在操作系统层面上访问 *虚拟服务器*。

- **Remote Desktop Client (or Remote Desktop Connection)  远程桌面（或者远程桌面连接）客户端**
- **SSH Client SSH 客户端**

A cloud storage device can be *attached directly to the virtual servers* or *an on-premise device over a WAN or VPN*.
云设备可以 *直接附加到虚拟服务器* 上，或者一个 *通过 WAN 或 VPN 连接的企业内部设备*。

- Networked File System 网络连接的文件系统
- Storage Area Network Devices 存储区域网设备
- Web-Based Resources 基于 Web 的资源

### Working with PaaS Environments 使用 PaaS 环境

A typical PaaS IDE can offer a wide range of tools and programming resources, such as software libraries, class libraries, frameworks, APIs, and various runtime capabilities that emulate the intended cloud-based deployment environment.
一个典型的 PaaS IDE 可以提供范围广泛的工具和编程资源，例如软件库、类库、框架、API 和各种运行时能力，能够模拟预期的基于云的部署环境。

PaaS also allows for applications to use cloud storage devices as independent data storing systems for holding development-specific data (for example in a repository that is available outside of the cloud environment). Both SQL and NoSQL database structures are generally supported.
PaaS 还允许应用把云存储设备作为独立的数据存储系统来使用，用来存放于开发有关的数据（例如，存放在一个从云环境外部也可以访问的库中）。一般来讲既支持 SQL 的数据库结构，也支持 NoSQL 的数据库结构。

The *usage and administration portal* that is used to access PaaS management features.
*使用与管理入口* 使用的是 PaaS 管理特性。

### Working with SaaS Environments 使用 SaaS 服务

SaaS-based cloud services are almost always accompanied by refined and generic APIs, they are usually designed to be incorporated as part of larger distributed solutions.
因为基于 SaaS 的云服务几乎总是有精炼的、通用的 API，所以这些服务通常被设计为更大的分布式解决方案的一部分。

Many SaaS offerings are provided *free of charge*.
许多 SaaS 服务是 *免费提供的*。

Cloud consumers using SaaS products supplied by cloud providers are relieved of the responsibilities of implementing and administering their underlying hosting environments.
使用云提供者提供的 SaaS 产品的云用户省去了实现和管理它们底层承载环境的麻烦。


