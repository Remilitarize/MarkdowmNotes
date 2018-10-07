[toc]

## ROLES AND BOUNDARIES 角色与边界

### Cloud Provider 云提供者

The organization that provides cloud-based IT resources is the **cloud provider**.
提供基于云的 IT 资源的组织机构就是 **云提供者**。

- Cloud providers normally **own** the IT resources that are made available for lease by cluod consumers.
  云提供者通常 **拥有** IT 资源，这些 IT 资源可供云用户租用。
- Some cloud providers also "**resell**" IT resources leased from other cloud recouses.
  有些云提供者也会 "**转售**" 从其他云提供者那里租来的 IT 资源。

### Cloud Consumer 云用户

A **cloud consumer** is an organization (or a human) that has a **formal contract** or **arrangement** with a cloud provider to use IT resources made available by the cloud provider.
**云用户** 是组织机构（或者人）与云提供者 **签订正式合同或者约定** 来使用云提供者提供的可用的 IT 资源。

The cloud consumer uses a **cloud service** consumer to access a cloud service.
云用户使用 **云服务用户** 来访问云服务。

![云用户访问云服务](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/yunyonghufangwenyunfuwu.PNG)

### Cloud Service Owner 云服务拥有者

The person or organization that legally owns a cloud service is called a **cloud service owner**.
在法律上拥有云服务的个人或者组织称为 **云服务拥有者**。

The **cloud consumer** of Cloud X or the **cloud provider** of Cloud X could own Cloud Service A.
云 X 的 **云用户** 或是云 X 的 **云提供者** 可以拥有云服务 A。

### Cloud Resource Administrator 云资源管理者

A **cloud resource administrator** is the person or organization responsible for administering a cloud-based IT resource (including cloud services).
**云资源管理者** 是负责管理基于云的 IT 资源（包括云服务）的人或者组织。

The cloud resource administrator can be (or belong to):
云资源管理者可以是（或者说属于）：

- The **cloud consumer** 云用户
- The **cloud provider** 云提供者
- The **third party organization** contracted to administer the cloud-based IT resource 签订了合约来管理基于云的 IT 资源的 **第三方组织**

### Additional Roles 其他角色

A third-party (often accredited) that conducts **independent** assessments of cloud environments assumes the role of the **cloud auditor**.
对云环境进行 **独立** 评估的第三方（通常是通过认证的），承担的是 **云审计者** 的角色。

**Cloud broker** is assumed by a party that assumes the responsibility of **managing and negotiating** the usage of cloud services between cloud consumers and cloud providers.
**云代理** 要承担 **管理和协商** 云用户和云提供者之间的云服务使用的责任。
Mediation services provided by cloud brokers include service *intermediation*, *aggregation*, and *arbitrage*.
云代理提供的仲裁服务包括服务 *调解*、*聚合* 和 *仲裁*。

**Cloud carrier** is the party responsible for the **wire-level connectivity** between cloud consumers and cloud providers.
**云运营商** 是负责提供云用户和云提供者之间的 **线路级连接** 的一方。

### Organizational Boundary 组织边界

An **organizational boundary** represents the **physical perimeter** that surrounds a set of IT resources that are owned and governed by an organization.
**组织边界** 是一个 **物理范围**，包括由一家组织拥有和管理的 IT 资源的集合。

![组织边界](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/zuzhibianjie.PNG)

> An organizational boundary is represented by a **broken line notation**.
  组织边界用 **虚线** 表示。

### Trust Boundary 信任边界

A **trust boundary** is a **logical perimeter** that typically spans beyond physical boundaries to represent the entent to which IT resouces are trusted.
**信任边界** 是一个 **逻辑范围**，通常会跨越物理边界，表明 IT 资源受信任的程度。
When analyzaing cloud environments, the trust boundary is most frequently associated with the trust issued by the organization acting as the cloud consumer.
在分析云环境的时候，信任边界最常与作为云用户的组织发出的信任关联到一起。

![信任边界](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/xinrenbianjie.PNG)

## CLOUD CHARACTERISTICS 云特征

- **On-demand usage 按需使用**
- **Ubiquitous access 随处访问**
- **Multitenancy (and resource pooling) 多租户（和资源池）**
- **Elasticity 弹性**
- **Measured usage 可测量的使用**
- **Resiliency 可恢复性**

A cloud consumer can **unilaterally** access cloud-based IT resources giving the cloud consumer the freedom to **self-provision** these IT resouces.
云用户可以 **单边** 访问基于云的 IT 资源，给予云用户 **自助提供** IT 资源的自由。

**Ubiquitous access** represents the ability for a cloud service to be widely accessible.
**泛在接入** 是一个云服务可以被广泛访问的能力。

The characteristic of a software program that enables an instance of the program to serve different **consumers(ternants)** whereby each is isolated from the other, is referred to as **Multitenancy**.
一个软件程序的实例能够服务不同的 **用户（租户）**，租户之间是互相隔离的，使得软件程序具有这种能力的特性称为 **多租户**。
A cloud provider pools its IT resources to serve multiple cloud service consumers by using **multitenancy models** that frequently rely on the use of **virtualization technologies**.
云提供者把它的 IT 资源放在一个池子里，使用 **多租户模型** 来服务多个云服务用户，这些模型通常依赖于 **虚拟化技术** 的使用。
Multitenancy allows several cloud consumers to use the same IT resource or its instance while each remains **unaware** that it may be used by others.
多用户允许多个云用户使用同一 IT 资源或其实例，每个用户都 **不会意识** 到该资源还在被其他用户使用。

**Elasticity** is the **automated** ability of a cloud to **transparently** scale IT resources, as required in response to **runtime conditions or as pre-determined** by the cloud consumer or cloud provider.
**弹性** 是一种能力，云根据 **运行时条件** 或云用户或云提供者 **事先确定** 的要求，**自动透明** 地扩展 IT 资源。

The **measured usage** characteristic represents the ability of a cloud platform to **keep track of** the usage of its IT resources, primarily by cloud consumers.
**可测量的使用** 特征表示的是云平台 **记录** 对 IT 资源使用情况的能力，这些 IT 资源主要是被云用户使用的。

**Resilienct computing** is a form of **failover** that distributes redundant implementations of IT resouces across physical locations.
**可恢复计算** 是一种 **故障转移** 的形式，它在多个物理位置分放 IT 资源的冗余实现。
Within cloud computing, the characteristic of **resiliency** can refer to redundant IT resouces within the same cloud (but in different physical locations) or across multiple clouds.
在云计算里，**可恢复性** 特性可以是指在同一云中（但不同物理位置上）的冗余 IT 资源，也可以是跨越多个云的冗余 IT 资源。

## CLOUD DELIEVERY MODELS 云交付模型

A **cloud delivery model** represents a specific, pre-packaged combination of IT resources offered by a cloud provider.
**云交付模型** 是云提供者提供的具体的、事先打包好的 IT 资源组合。

- **Infrastructure-as-a-Service(IaaS) 基础设置作为服务**
- **Platform-as-a-Service(PaaS) 平台作为服务**
- **Software-as-a-Service(SaaS) 软件作为服务**

### Infrastructure-as-a-Service(IaaS) 基础设施作为服务

The Iaas delivery model represents a **self-contained** IT environment comprised of infrastructure-centric IT resources that can be accessed and managed via cloud service-based interfaces and tools.
IaaS 交付模型是一种 **自我包含** 的 IT 环境，由以基础设施为中心的 IT 资源组成，可以通过基于云服务的接口和工具访问和管理这些资源。
This environment can include **hardwork**, **network**, **connectivity**, **operating systems**, and other "**raw**" IT resources.
这个环境可以包括 **硬件**、**网络**、**连通性**、**操作系统** 以及其他一些 "**原始的**" IT 资源。

The IT resources provided by IaaS are generally not pre-configured, placing the administrative responsibility directly upon **the cloud consumer**.
IaaS 提供的 IT 资源通常是未配置好的，管理的责任直接落在 **云用户** 身上。
This model is therefore used by cloud consumers that require a **high level of control** over the cloud-based environment they intend to create.
因此，对创建的基于云的环境需要有 **更高控制权** 的用户会使用这种模型。

IT resources available through IaaS environments are generally offered as freshly initialized **virtual instances**.
通过 IaaS 环境可得的 IT 资源通常是新初始化生成的 **虚拟实例**。
A central and primary IT resource within a typical IaaS environment is the **virtual server**.
一个典型的 IaaS 环境中的核心和主要的 IT 资源就是 **虚拟服务器**。
Virtual servers are leased by *specifying server hardware requirements*, such as processor capacity, memory, and local storage space.
虚拟服务器的租用是通过 *指定服务器硬件需求* 来完成的。例如，处理器能力、内存和本地存储空间。

### Platform-as-a-Service(PaaS) 平台作为服务

The PaaS delivery model represents a pre-defined "**ready-to-use**" environment typically comprised of already deployed and configured IT resources.
PaaS 交付模型是预先定义好的 "**就绪可用**" 的环境，一般由已经部署好和配置好的 IT 资源组成。

Common reasons a cloud consumer would use and invest in a PaaS environment include:
云用户会使用和投资 PaaS 环境的常见原因包括：

- The cloud consumer wants to **entend** on-premise environments into the cloud for scalability and economic purposes.
  为了可扩展性和经济原因，云用户想要把企业内的环境 **扩展** 到云中。
- The cloud consumer uses the ready-made environment to entirely **substitute** an on-premise environment.
  云用户使用已就绪环境来完全 **替代** 企业内的环境。
- The cloud consumer wants to become a cloud provider and deploys its own cloud services to be made available to **other external cloud consumers**.
  云用户想要成为云提供者并部署自己的云服务，使之对 **其他外部云用户** 可用。

### Software-as-a-Service(SaaS) 软件作为服务

A **software program** positioned as a shared cloud service and made available as a "product" or generic utility represents the typical profile of a SaaS offering.
SaaS 通常是把 **软件程序** 定位成共享的云服务，作为 "产品" 或通用的工具进行提供。
The SaaS delivery model is typically used to make a resuable cloud service widely available (often commercially) to *a range of cloud consumers*.
SaaS 交付模型一般是使一个可重用云对 *大多数用户* 可用（通常是商用）。
An **entire marketplace** exists around SaaS products that can be leased and used for different purposed and via different terms.
SaaS 产品具有 **完善的市场**，可以出于不同的目的和通过不同的条款来作用和使用这些产品。

A cloud consumer is generally granted **very limited administrative control** over a SaaS implementation.
通常，云用户对 SaaS 实现的 **管理权限非常有限**。

### Comparing Cloud Delivery Models 云交付模型比较

A comparison of typical cloud delivery model control levels
典型云交付模型的控制等级比较

|Cloud Delivery Model<br />云交付模型|Typical Level of Control Granted to Cloud Consumer<br />赋予云用户的典型控制等级|Typical Functionality Made Available to Cloud Consumer<br />云用户可用的典型功能|
|-|-|-|
|SaaS|usage and usage-related configuration<br />使用和与使用相关的配置|access to front-end user-interface<br />前端用户接口访问|
|PaaS|limited administrative<br />有限的管理|moderate level of administrative control over IT resources relevant to cloud consumer's usage of platform<br />对与云用户使用平台相关的 IT 资源的中等级别的管理控制|
|IaaS|full administrative<br />完全的管理|full access to virtualized infrastructure-related IT resources and, possibly, to underlying physical IT resources<br />对虚拟化的基础设施相关的 IT 资源以及可能的底层物理 IT 资源的完全访问|

Typical activities carried out by cloud consumers and cloud providers in relation to the cloud delivery models
云用户和云提供者与云交付模型有关的典型行为

|Cloud Delivery Model<br />云交付模型|Common Cloud Consumer Activities<br />常见的云用户行为|Common Cloud Provider Activities<br />常见的云提供者行为|
|-|-|-|
|SaaS|uses and configures cloud service<br />使用和配置云服务|implements, manages, and maintains cloud service<br />实现、管理和维护云服务<br />monitor usage by cloud consumers<br />监控云用户的使用|
|PaaS|develops, texts, deploys, and manages cloud services and cloud-based solutions<br />开发、测试、部署和管理云服务以及基于云的解决方案|pre-configures platform and provisions underlying infrastructrue, middleware, and other needed IT resources, as necessary<br />实现配置好的平台和在需要时提供底层的基础设施、中间件和其他所需的 IT 资源<br />monitors usage by cloud consumers<br />监控云用户的使用|
|IaaS|sets up and configures bare infrastructure, and installs, manages, and monitors any needed software<br />建立和配置原始的基础设施，安装、管理和监控所需的软件|provisions and manages the physical processing, storage, networking, and hosting required<br />提供和管理需要的物理处理器、存储、网络和托管<br />monitors usage by cloud consumers<br />监控云用户的使用|

### Combineing Cloud Delivery Models 云交付模型组合

- IaaS + PaaS
  - A PaaS environment will be built upon an underlying infrastructure comparable to the physical and virtual servers and other IT resources provided in an IaaS environment.
    PaaS 环境构建在底层基础设施之上，这个底层基础设施类似于 IaaS 环境中提供的物理和虚拟服务器以及其他 IT 资源。
  - The motivation for such an arrangement may be influenced by *economics* or maybe because the first cloud provider is close to *exceeding its existing capacity* by serving other cloud consumers.
    之所以会这样做，可能是 *经济因素*，也可能是因为原来的云提供者还服务者其他云用户而它 *现有的容量快要不够用了*。
  - Or, perhaps a particular cloud consumer imposes a *legal requirement* for data to be physically stored in a specific region.
    或者，可能某个云用户有 *法律上的要求*，必须物理地存放在某个特定的区域内。
- IaaS + PaaS + SaaS
  - All three cloud delivery models can be combined to establish layers of IT resources that build upon each other.
    可以将所有三种云交付模型组合起来，一层建立在另一层之上，形成 IT 资源的层次结构。

## CLOUD DEPLOYMENT MODELS 云部署模型

A **cloud deployment** model represents a specific type of cloud environment, primarily distinguished by **ownership, size, and access**.
**云部署模型** 表示的是某种特定的云环境类型，主要是以 **所有权、大小和访问方式** 来区别的。

Four common cloud deployment models:
四种常见的云部署模型：

- **Public cloud 公有云**
- **Community cloud 社区云**
- **Private cloud 私有云**
- **Hybrid cloud 混合云**

### Public cloud 公有云

A **public cloud** is **publicly accessible** cloud environment owned by a third-party cloud provider.
**公有云** 是由第三方云提供者拥有的 **可公共访问** 的云环境。
The IT resources on public clouds are usually provisioned via the previously described cloud delivery models and are generally offered to cloud consumers at a **cost** or are **commercialized** via other avenues (such as advertisement).
公有云里的 IT 资源通常是按照事先描述好的晕交付模型提供的，而且一般是需要 **付费** 才能提供给云用户的，或者是通过其他途径 **商业化** 的（例如广告）。

The cloud provider is responsible for the **creation** and **on-going maintenance** of the public cloud and its IT resources.
云提供者负责 **创建** 和 **持续维护** 公有云及其 IT 资源。

### Community Clouds 社区云

A community cloud is similar to a public cloud except that its access is **limited to a specific community of cloud consumers**.
社区云类似于公有云，只是它的访问 **被限制为特定的云用户社区**。
The member cloud consumers of the community typically share the responsibility for *defining* and *evolving* the community cloud.
社区的云用户成员通常会共同承担 *定义* 和 *发展* 社区云的责任。

Membership in the community **does not necessarily** guarantee access to or control of all the cloud's IT resouces.
社区中的成员 **不一定要** 能够访问或控制云中的所有 IT 资源。
Parties outside the community are generally not granted access unless allowed by the community.
除非社区允许，否则社区外的组织通常不能访问社区云。

### Private Clouds 私有云

A **private cloud** is owned by a **single** organization.
**私有云** 是由一家组织 **单独** 拥有的。
Private clouds enable an organization to use cloud computing technology as a means of **centralizing access** to IT resources by different parts, locations, or departments of the organization.
私有云使得组织把云计算技术当作一种手段，可以 **集中访问** 不同部分、位置或部门的 IT 资源。

- A **separate** organizational department typically assumes the responsibility for provisioning the cloud.
  通常组织中会有一个 **单独** 的部门承担提供云的责任。
- Departments requiring access to the private cloud assume the cloud consumer role.
  需要访问私有云的部门承担的就是云用户的角色。

### Hybrid Clouds 混合云

A **hybrid cloud** is a cloud environment comprised of two or more different cloud deployment models.
**混合云** 是由两个或者更多不同云部署模型组成的云环境。

A cloud consumer may choose to deploy cloud services processing sensitive data to a private cloud and other, less sensitive cloud services to a public cloud.
云用户可能会选择把处理敏感的云服务部署到私有云上，而将其他不那么敏感的云服务部署到公有云上。

Hybrid deployment architectures can be **complex and challenging** to create and maintain due to the potential disparity in cloud environments and the fact that management responsibilities are typically split between the private cloud provider organization and the public cloud provider.
由于云环境中潜在的差异以及私有云提供组织和公有云提供者之间在管理责任上是分离的，因此混合部署架构的创建和维护可能会很 **复杂** 和具有 **挑战性**。

### Other Cloud Deployment Models 其他云部署模型

**Virtual Private Cloud 虚拟私有云**
Also known as a "**dedicated cloud**" or "**hosted cloud"**, this model results in a self-contained cloud environment hosted and managed by a public cloud provider, and made available to a cloud consumer.
也称为 "**专有云**" 或 "**托管云**"，这种模型是一个公有云提供者托管和管理的、自我包含的云环境，仅对一个云用户可用。

**Inter-Cloud 互联云**
This model is based on an architecture comprised of two or more inter-connected clouds.
这个模型是基于由两个或更多互相连接起来的云组成的架构。
