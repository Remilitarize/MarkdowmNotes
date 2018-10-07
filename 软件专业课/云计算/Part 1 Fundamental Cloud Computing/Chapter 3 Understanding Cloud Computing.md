[toc]

## ORIGINS AND INFLUENCES 起源与影响

### A Brief History 简要历史

The idea of computing in a **"cloud"** traces back to the origins of **utility computing**, a concept that computer scientist John McCarthy publicly proposed in 1961.
**云** 中计算的想法可以追溯到 **效用计算** 的起源，这个概念是计算机科学家 **John McCarthy** 在 1961 年公开提出的。

The general public has been leveraging forms of Internet-based **computer utilities** since the mid-1990s through various incarnations of search engines, e-mail services, open publising platforms, and other types of social media.
从 20 世纪 90 年代中期开始，普通大众已经开始以各种形式使用基于 Internet 的 **计算机应用**，比如：搜索引擎、电子邮件、开放的发布平台，以及其他类型的社交媒体。
Though consumer-centric, these services popularized and validated core concepts that form the basis of modern-day cloud computing.
虽然这些服务是以用户为中心的，但是他们普及并且验证了形成现代云计算基础的核心概念。

In the late 1990s, **Saleforce.com** pioneered the notion of bringing remotely provisioned services into the enterprise.
20 世纪 90 年代后期，**Salesforce.com** 率先在企业中引入远程提供服务的概念。

In 2002, Amazon.com launched the Amazon Web Services(AWS) platform, a suite of enterprise-oriented services that provide remotely provisioned storage, computing resources, and business functionality.
2002 年，Amazon.com 启用 Amazon Web 服务（Amazon Web Service, AWS）平台，该平台是一套面向企业的服务，提供远程配置存储、计算资源以及业务功能。

*A slightly different evocation* of the term "Network Cloud" or "Cloud" was introduced in the early 1990s throughout the networking industry.
20 世纪 90 年代早期，在整个网络行业出现了 "网络云" 或 "云" 这一术语，但其含义与现在的 *略有不同*。

It wasn't until **2006** that the term "cloud computing" emerged in the commercial arena.
直到 **2006** 年，"云计算" 这一术语才出现在商业领域。

### Definitions 定义

The definition that received industry-wide acceptance was composed by the **National Institute of Standards and Technology(NIST)**.
由 **美国国家标准与技术研究院（NIST）** 制订的定义被业界广泛接受。
*Cloud computing is a model for enabling ubiquitous, convenient, on-demand network access to a **shared pool** of configurable computing resources(e.g., networks, servers, storage, applications, and services) that can be rapidly **provisioned and released** with minimal management effort or service provider interaction.This cloud model is composed of **five essential characteristics, three service models, and four deployment models**.*
*云计算是一种模型，可以实现随时随地、便捷地、按需地从可配置计算资源 **共享池** 中获取所需的资源（例如，网络、服务器、存储、应用程序及服务），资源可以快速 **供给和释放**，使管理的工作量和服务提供者的介入降低到最少。这种云模型由 **五个基本特征、三种服务模型和四种部署模型** 构成。*

This book provides a more concise definition:
本书给出了云计算更为简洁的定义：
*Cloud computing is a specialized form of  **distributed computing** that introduces **utilization models** for remotely provisioning scalable and measured resources.*
*云计算是 **分布式计算** 的一种特殊形式，它引入了 **效用模型** 来远程供给可扩展和可测量的资源。*

### Business Drivers 商业驱动力

#### Capacity Planning 容量规划

**Capacity planning** is the process of determining and fulfilling future demands of an organization's IT resources, products, and services.
**容量规划** 是确定和满足一个组织未来对 IT 资源、产品和服务需求的过程。
Within this context, **capacity** represents the maximum amount of work that an IT resource is capable of delivering in a given period of time.
这里的 **容量** 是指一段给定时间内，一个 IT 资源能够提供的最大工作量。

- **Lead Strategy** —— adding capacity to an IT resource in anticipation of demand
  **领先策略** —— 根据预期增加 IT 资源的容量。
- **Lag Strategy** —— adding capacity when the IT resource reachs its full capacity
  **滞后策略** —— 当 IT 资源到其最大容量时增加资源容量。
- **Match Strategy** —— adding IT recource capacity in small increments, as demand increases
  **匹配策略** —— 当需求增加时，小幅增加 IT 资源容量。

#### Cost Reduction 降低成本

Two costs need to be accounted for:
需要考虑的成本分为两种：

- **the cost of acquiring new infrastructure** 获得新基础设施的成本
- **the cost of its ongoing ownership** 保有其所有权的成本

**Operational overhead** represents a considerable share of IT budgets, often exceeding up-front investment costs.
**运营开销** 在 IT 预算中占了相当大的一部分，往往超过了前期投资成本。

#### Organizational Agility 组织灵活性

Businesses need the ability to adapt and evolve to successfully face change caused by both internal an external factors.
企业需要有适应和进步的能力，以便成功应对由于各种因素而导致的变化。

- Scaling its IT resouces —— Inadequate budgets
  扩展 IT 资源规模 —— 预算不足
- Require IT resources to be more available and reliable —— A business' overall continuity is threatened
  要求 IT 资源具备更高的可用性和可靠性 —— 导致业务的持续性受到威胁

### Technology Innovations 技术创新

#### Clustering 集群化

A **cluster** is a group of independent IT resources that are interconnected and work as a single system.
**集群** 是一组互联的独立 IT 资源，以整体形式工作。

System failure rates are **reduced** while **availability and reliability are increased**, since **redundancy and failover features** are inherent to the cluster.
由于集群固有的 **冗余和容错特性**，当其 **可用性和可靠性提高** 时，系统故障率就会 **降低**。

#### Grid Computing 网格计算

A **computing grid**(or computational grid) provides a platform in which computing resources are organized into one or more logical pools. These pools are collectively cooridinated to provide a high performance distributed grid, sometimes referred to as a "super virtual computer".
**计算网格**（或计算的网格）为计算资源提供了一个平台，使其能组织成一个或多个逻辑池。这些逻辑池统一协调为一个高性能分布式网格，有时也称为 "超级虚拟计算机"。

Grid computing is based on a *middleware layer* that is deployed on computing resources.
网格计算以 **中间件层** 为基础，这个中间件层是在计算资源上部署的。

It is for this reason that **some classify cloud comoputing as a descendant of earlier grid computing initiatives**.
有些观点认为 **云计算是早期网格计算的衍生品**。

#### Virtualization 虚拟化

**Virtualization** represents a technology platform used for the creation of virtual instances of IT resources.
**虚拟化** 是一个技术平台，用于创建 IT 资源的虚拟实例。

Established virtualization technologies can be traced to several cloud characteristics and cloud computing mechanisms, having inspired many of their core features.
在一些云特性和云计算机制中能发现现有的虚拟化技术的影子，这些技术启发了云计算的某些核心特性。

#### Technology Innovations vs. Enabling Technologies 技术创新与使能技术

**Cloud-enabling technologies 云使能技术**

- Broadband Networks and Internet Architecture 宽带网络和 Internet 架构
- Data Center Technology 数据中心技术
- (Modern) Virtualization Technoogy （现代）虚拟化技术
- Web Technology Web 技术
- Multitenant Technology 多租户技术
- Service Technology 服务技术

Some were refined further, and on occasion even redefined, as a result of the subsequent evolution of cloud computing.
随着云计算的演进，有些技术更加精进了，而有些技术则被重新定义了。

## BASIC CONCEPTS AND TERMINOLOGY 基本概念与术语

### Cloud 云

A **cloud** refers to a distinct IT environment that is designed for the purpose of remotely provisioning scalable and measured IT resources.
**云** 是指一个独特的 IT 环境，其设计目的是为了远程供给可扩展和可测量的 IT 资源。

The cloud symbol 云符号

![Cloud symbol](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/cloudsymbol.PNG)

Internet Symbol  Internet 符号

![Internet symbol](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/internetsymbol.PNG)

### IT Resource IT 资源

An **IT resource** is a **physical or virtual** IT-related artifact that can be either **software-based**, such as a virtual server or a custom software program, or **hardware-based**, such as a physical server or a network device.
**IT 资源** 是指一个与 IT 相关的 **物理的或虚拟的** 事务，它既可以是某种 **基于软件的**，比如虚拟服务器或定制软件程序，也可以是 **基于硬件的**，比如物理服务器或网络设备。

![Common IT resources symbols](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/commonitresourcesymbols.PNG)

- Hardware 硬件
    - Physical server 物理服务器
    - Storage device 存储设备
    - Network device 网络设备
- Software 软件
    - Virtual server 虚拟服务器
    - Software program 软件程序
    - Service 服务

It is important to note the following points when studying and working with these diagrams:
在学习和使用这些图时，需要注意以下两点：

- The IT resources shown within the boundary of a given cloud symbol usually do not represent all of the available IT resources hosted by that cloud. Subsets of IT resources are generally highlighted to demonstrate a particular topic.
  一个给定云符号边界中画出的 IT 资源并不代表这个云中包含的所有可用 IT 资源。为了说明一个特定的话题，通常只突出显示一部分 IT 资源。
- Focusing on the relevant aspects of a topic requires many of these diagrams to intentionally provide abstracted views of the underlying technology architectures. This means that *only a portion of* the actual technical details are shown.
  当重点集中在一个问题的某些方面时，就需要特意用抽象图示来表示底层技术架构。这就意味着，在图示中只会显示实际技术的 *部分* 细节。

Physical servers are sometimes referred to as **physical hosts**(or just hosts) in reference to the fact that they are responsible for **hosting virtual server**.
物理服务器有时也被称为 **物理主机**（或简称主机），这是因为它们负责 **承载虚拟服务器**。

### On-Premise 企业内部的

An IT resource that is hosted in a conventional IT enterprise within an organizational boundary(that does not specifically represent a cloud) is considered to be located on the premises of the IT enterprise, or **on-premise** for short.
处于一个组织边界（并不特指云）中的传统 IT 企业内部承载的 IT 资源被认为是位于 IT 企业内部的，简称为 **内部的**。
In other words, the term "on-premise" is another way of stating "on the premises of a controlled IT enbironment that is **not cloud-based**".
换句话说，术语 "内部的" 是指 "在一个 **不基于云** 的可控的 IT 环境内部的"。

*An IT resource that is on-premise cannot be cloud-based, and vice-versa.*
*一个内部的 IT 资源不可能是基于云的，反之亦然。*

- An on-premise IT resource can **access** and **interact** with a cloud-based IT resource.
  一个内部的 IT 资源可以 **访问** 一个基于云的 IT 资源，并与之 **交互**。
- An on-premise IT resource can be **moved** to a cloud, thereby changing it to a cloud-based IT resource.
  一个内部的 IT 资源可以被 **迁移** 到云中，从而成为一个基于云的 IT 资源。
- **Redundant deployments** of an IT resource can exist in both on-premise and cloud-based environments.
  IT 资源既可以 **冗余部署** 在内部的环境中，也可以在云环境中。

### Cloud Consumers and Cloud Providers 云用户与云提供者

The party that provides cloud-based IT resources is the **cloud provider**.
提供基于云的 IT 资源的一方称为 **云提供者**。
The party that uses cloud-based IT resources is the **cloud consumer**.
使用基于云的 IT 资源的一方称为 **云用户**。

### Scaling 可扩展性

**Scaling**, from an IT resource perspective, represents the ability of the IT resource to handle increased or decreased usage demands.
从 IT 资源的角度来看，**可扩展** 是指 IT 资源可以处理增加或减少的使用需求的能力。

- **Horizontal Scaling 水平扩展**
    - The **allocation or releasing** of IT resources that are of the same type is referred to as **horizontal scaling**.
      **分配和释放** IT 资源都属于 **水平扩展**。
    - The horizontal **allocation** of resources is referred to as **scaling out**.
      水平 **分配** 资源称为 **向外扩展**。
    - The horizontal **releasing** of resources is referred to as **scaling in**.
      水平 **释放** 资源称为 **向内扩展**。
- **Vertical Scaling 垂直扩展**
    - When an existing IT resource is replaced by another with **higher or lower capacity**, **vertical scaling** is considered to have occurred.
      当一个现有 IT 资源被具有 **更大或更小容量** 的资源所代替，则为 **垂直扩展**。
    - The replacing of an IT resource with another that has a **higher capacity** is referred to as **scaling up**.
      被具有 **更大容量** 的 IT 资源代替，称为 **向上扩展**。
    - The replacing of an IT resource with another that has a **lower capacity** is considered **scaling down**.
      被具有 **更小容量** 的 IT 资源代替，称为 **向下扩展**。

A comparison of horizontal and vertical scaling
水平扩展与垂直扩展对比

|Horizontal Scaling<br />水平扩展|Vertical Scaling<br />垂直扩展|
|-|-|
|Less expensive(through commodity hardware components)<br />更便宜（使用商品化的硬件组件）|More expensive(specialized servers)<br />更昂贵（专用服务器）|
|IT resources instantly available<br />IT 资源立即可用|IT resources normally instantly available<br />IT 资源通常为立即可用|
|Resource replication and automated scaling<br />资源复制和自动扩展|Additional setup is normally needed<br >通常需要额外设置|
|Additional IT resources needed<br />需要额外 IT 资源|No additional IT resources needed<br />不需要额外 IT 资源|
|Not limited by hardware capacity<br />不受硬件容量限制|Limited by maximum hardware capacity<br />受限于硬件最大容量|

### Cloud Service 云服务

A **cloud service** is any IT resource that is made remotely accessible via a cloud.
**云服务** 是指任何可以通过云远程访问的 IT 资源。

The driving motivation behind cloud computing is to provide IT resources as services that **encapsulate** other IT resources, while offering functions for clients to use and leverage remotely.
云计算背后的推动力是以服务的形式提供 IT 资源，这些服务 **封装** 了其他 IT 资源，并向客户端提供远程使用功能。

- Remotely 远程的
- As-a-service 作为服务的
- SLA 服务水平协议

### Cloud Service Consumer 云服务用户

The **cloud service consumer** is a **temporary** runtime role assumed by a **software proguam** when it accesses a cloud service.
**云服务用户** 是一个 **临时的** 运行时角色，由访问云服务的 **软件程序** 担任。

Types of cloud service consumers 云服务用户类型：

- Software programs and services capable of remotely accessing cloud services with published service contracts
  能够通过已发布的服务合同远程访问云服务的软件程序和服务
- Workstations, laptops and mobile devices running software
  运行某些软件的工作站、便携电脑和移动设备

## GOALS AND BENIFITS 目标与收益

### Reduced Investments and Proportional Costs 降低的投资与成比例的开销

Common measurable benefits to cloud consumers include:
云用户能获得的常见可测收益包括：

- On-demand access to *pay-as-you-go* computing resources on a short-term basis, and the ability to release these computing resources when they are no longer needed.
  可以短期按需访问 *按使用付费* 的计算资源，并在不需要的时候释放这些资源。
- The perception of having *unlimited computing resources* that are available on demand, thereby reducing the need to prepare for provisioning.
  感觉上在需要时可以获得 *无限的计算资源*，因此减少了资源供给的需求。
- The ability to add or remove IT resources at a *fine-grained* level.
  可以 *细粒度* 地增加或删除 IT 资源。
- Abstraction of the infrastructure so applications are not locked into devices or locations and can be easyily moved if needed.
  基础设施抽象画，这样应用不会与设备或位置绑定，可以在需要时方便地迁移。

### Increased Scalability 提高的可扩展性

By providing pools of IT resources, along with tools and tecknologies designed to leverage them collectively, clouds can instantly and dynamically allocate IT resources to cloud consumers, on-demand or via the cloud consumer's direct configuration.
通过提供 IT 资源池，以及设计同来使用这些资源池的工具和技术，云可以即时地、动态地向云用户按需或按用户的直接配置来分配 IT 资源。

This empowers cloud consumers to scale their cloud-based IT resources to acommodat e processing fluctrations and peaks **automatically or manually**.
这使得云用户可以根据处理需求的波动和峰值来 **自动或手动** 地扩展其云 IT 资源。

### Increased Availability and Reliability 提高的可用性和可靠性

An IT resource with increased availability is accessible for longer periods of time. Cloud providers generally offer "**resilient**" IT resources for which they are able to guarantee high levels of availability.
可用性更高的 IT 资源具有更长的可访问时间。云提供者通常提供 "**可恢复的**" IT 资源，以便能够保证高水平的可用性。

An IT resource with increased reliability is able to better avoid and recover from exception conditions. The **modular** architecture of cloud environments provides extensive failover support that increases reliability.
具有更强可靠性的 IT 资源能更好地避免意外情况，或是从中更快回复。云环境的 **模块** 架构为故障转移提供了广泛的支持，从而增强了可靠性。

> Capacity planning strategies – lag and match strategies more applicable. 从容量计划策略来看，滞后和匹配策略更合适。

## RISKS AND CHALLENGES 风险与挑战

### Increased Securituy Vulnerabilities 增加的安全漏洞

![重叠的信任边界](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/chongdiedexinrenbianjie.PNG)

Two organizations accessing the same cloud service are required to extend their respective trust bondaries to the cloud, resulting in **overlapping trust bondaries**.
两个组织需要访问同一个云服务，这要求它们将各自的新人边界都扩展到这个云，从而出现了 **信任边界重叠**。

### Reduced Operational Governance Control 降低的运营管理控制

![影响通信质量](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/yingxiangtongxinzhiliang.PNG)

An unreliable cloud provider may **not maintain the guarantees it makes in the SLAs that were published for its cloud services**. This can jeopardize the quality of the cloud consumer solutions that rely on these cloud services.
一个不可靠的云提供者可能 **不会遵守对它的云服务发布的 SLA 保证**。对于使用这些云服务的用户来说，这将威胁到它们的解决方案的质量。

Longer geographic distances between the cloud consumer and cloud provider can require additional network hops that introduce **fluctuating latency and potential bandwidth constraints**.
云用户和云提供者之间较长的地理距离可能需要更多的网络跳数，这导致了 **延迟波动和可能的带宽受限**。

### Limited Portability Between Cloud Providers 云提供者之间有限的可移植性

![可移植性不高](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/keyizhixingbugao.PNG)

Due to a lack of established industry standards within the cloud computing industry, public clouds are commonly proprietary to various extents.
由于云计算行业内没有建立工业标准，因此，公有云存在不同程度的私有化。

**Portability** is a measure used to determine the impact of moving cloud consumer IT resources and data between clouds.
**可移植性** 用来衡量在云之间迁移云用户资源和数据产生的影响。

### Mulit-Reginal Compliance and Legal Issues 多地区法规遵循和法律问题

Third-party cloud providers will frequently establish data centers in affordable or convenient geographical locations.
第三方云提供者常常在可负担的或是方便的地理位置建立数据中心。
For some organizations, this can pose serious legal concerns pertaining to industry or government regulations that specify data privacy and storage policies.
对某些组织来说，这可能会造成严重的法律问题，因为这关系到规定了数据隐私和存储政策的行业或政府法规。
