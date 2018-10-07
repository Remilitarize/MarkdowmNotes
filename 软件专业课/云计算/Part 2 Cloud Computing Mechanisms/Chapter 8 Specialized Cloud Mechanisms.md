[toc]

## AUTOMATED SCALING LISTENER 自动伸缩监听器

The **automated scaling listener** mechanism is a *server agent* that **monitors and tracks** communications between cloud service consumers and cloud services for dynamic scaling purposes.
**自动伸缩监听器** 机制是一个 *服务代理*，它 **监控和追踪** 云服务用户和云服务之间的通信，用以动态自动伸缩。
Automated scaling listeners are deployed within the cloud, typically **near the firewall**.
自动伸缩监听器部署在云中，通常 **靠近防火墙**。
**Workloads** can be determined by the volume of cloud consumer-generated requests or via back-end processing demands triggered by certain types of requests.
**负载量** 可以由云用户产生的请求量或某种类型的请求引发的后端处理需求量来决定。

- Automatically scaling IT resources out or in based on parameters previously defined by the cloud consumer (commonly referred to as **auto-scaling**).
  根据云用户事先定义的参数，自动伸缩 IT 资源（通常称为 **自动伸缩**）。
- **Automatic notification** of the cloud consumer when workloads exceed current thresholds or fall below allocated resources.
  当负载超过当前阈值或低于已分配资源时，**自动通知** 云用户。

Different cloud provider vendors have different names for service agents that act as automated scaling listeners.
不同的云提供者对作为自动伸缩监听器的服务代理有不同的名字。
Automated scaling listener agents run on the *hypervisor*.
自动伸缩监听器代理运行在 *虚拟机监控器* 上。

![自动伸缩监听器 1](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/zidongshensuojiantingqi1.PNG)

1.A cloud consumer creates and starts a virtual server with 8 virtual processor cores and 16GB of virtual RAM.
  云用户创建并启动了一个带有 8 个虚拟处理器核心和 16GB 虚拟 RAM 的虚拟服务器。
2.The VIM creates the virtual server at the cloud service consumer's request and allocates it to Physical Server 1 to join 3 other active virtual servers.
  VIM 根据云服务用户的请求创建了该虚拟机，并把它分配到了物理服务器 1 上，该物理服务器上已经有了三个活动着的虚拟服务器。
3.Cloud consumer demand causes the virtual server usage to increase by over 80% of the CPU capacity for 60 consecutive seconds.
  云用户的需求导致虚拟服务器的使用上升到持续 60 秒超出 CPU 能力的 80%。
4.The automated scaling listener running at the hypervisor detects the need to scale up and commands the VIM accordingly.
  运行在虚拟机监控器上的自动伸缩监听器察觉到了需求，相应地发送增大命令给 VIM。

![自动伸缩监听器 2](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/zidongshensuojiantingqi2.PNG)

5.The VIM determines that scaling up the virtual server on Physical Server 1 is not possible and proceeds to live migrate it to Physical Server 2.
  VIM 确定在物理服务器 1 上增大虚拟服务器是不可能的，就进而把它在线迁移到物理服务器 2 上。

![自动伸缩监听器 3](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/zidongshensuojiantingqi3.PNG)

6.The virtual server's CPU/RAM usage remains below 15% capacity for 60 consecutive seconds.
  虚拟服务器的 CPU/RAM 使用持续 60 秒低于容量的 15%。
7.The automated scaling listener detects the need to scale down and commands the VIM,
  自动伸缩监听器发现了这一需求，发送缩小命令给 VIM。
8.VIM scales down the virtual server while it remains active on Physical Server 2.
  VIM 会缩小虚拟服务器的容量，虚拟服务器在物理服务器 2 上仍然保持活跃。

## LOAD BALANCER 负载均衡器

A common approach to horizontal scaling is to balance a workload across *two or more IT resources* to increase performance and capacity beyond what a single IT resource can provide.
水平扩展的常见方法是把负载在 *两个或更多的 IT 资源* 上做负载均衡。
The **load balancer** mechanism is a **runtime agent** with logic fundamentally based on this premise.
**负载均衡器** 机制是一个 **运行时机制**，其逻辑基本上就是基于这个思想的。

Beyond simple *division of labor algorithms*, load balancers can perform a range of specialized runtime *workload distribution* functions that include:
除了简单的 *劳动分工算法*，负载均衡器可以执行一组特殊的运行时 *负载分配* 功能，包括：

- **Asymmetric Distribution** —— larger workloads are issued to IT resources with higher processing capacities.
  **非对称分配** —— 较大的工作负载被送到具有较强处理能力的 IT 资源。
- **Workload Prioritization** —— workloads are scheduled, queued, discarded, and distributed workloads according to their priority levels.
  **负载优先级** —— 负载根据其优先等级进行调度、排队、丢弃和分配。
- **Content-Aware Distribution** —— requests are distributed to different IT resources as dictated by the request content.
  **上下文感知的分配** —— 根据请求内容的指示把请求分配到不同的 IT 资源。

![负载均衡器](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/fuzaijunhengqi.PNG)

A load balancer is programmed or configured with a set of performance and QoS rules and parameters with the general objectives of *optimizing IT resource usage*, *avoiding overloads*, and *maximizing throughput*.
负载均衡器被程序编码或者被配置成含有一组性能和 QoS 规则与参数，一般目标是 *优化 IT 资源的使用*，*避免过载* 并 *最大化吞吐量*。

The load balancer is typically located on the **communication path** between the IT resources **generating** the workload and the IT resources **performing** the workload processing.
负载均衡器通常位于 **产生** 负载的 IT 资源和 **执行** 负载处理的 IT 资源之间的 **通信路径**上。
This mechanism can be designed as a **transparent agent** that remain hidden from the cloud service consumers, or as a **proxy component** that abstracts the IT resources performing their workload.
这个机制可以被设计成一个 **透明的代理**，保持对云服务用户不可见，或者设计成一个 **代理组件**，对执行工作负载的 IT 资源进行抽象。

## SLA MONITOR SLA 监控器

The **SLA monitor** mechanism is used to specifically **observe the runtime performance of cloud services** to ensure that they are fulfilling the contractual QoS requirements that are published in SLAs.
**SLA 监控器** 机制被用来专门 **观察云服务的运行时性能**，确保它们履行了 SLA 中公布的约定 QoS 需求。
The data collected by the SLA monitor is processed by an **SLA management system** to be aggregated into SLA reporting metrics.
SLA 监控器收集的数据由 **SLA 管理系统** 处理并集成到 SLA 报告的标准中。
The system can **proactively repair or failover** cloud services when exception conditions occur.
当异常条件发生时，系统可以 **主动地修复或故障转移** 云服务。

![SLA 监视器 1](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/slajianshiqi1.PNG)

![SLA 监视器 2](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/slajianshiqi2.PNG)

> 2a 的 M<sub>REQN+M</sub> 的箭头画反。

1. The SLA monitor polls the cloud service by sending over polling request messages (M<sub>REQ1</sub> to M<sub>REQN</sub>).(a) The monitor receives polling response messages (M<sub>REP1</sub> to M<sub>REPN</sub>) that report that the service was "up" at each polling cycle.(b) The SLA monitor stores the **"up"** time —— time period of all polling cycles **1 to N —— in the log database**.
  SLA 监控器通过发送轮询请求信息（M<sub>REQ1</sub> 到 M<sub>REQN</sub>）来轮询云服务。(a) 监控器接收轮询相应信息（M<sub>REP1</sub> 到 M<sub>REPN</sub>），报告在每个轮询周期服务都是 "在线" 的。(b) SLA 监控器在日志数据库中存储 **"在线"** 的时间 —— 所有的轮询周期 **1 到 N 的时间长度**。
2. (a) The SLA monitor polls the cloud service that sends polling request messages(M<sub>REQN+1</sub> to M<sub>REQN+M</sub>). (b) The response messages continue to time out, so the SLA monitor stores the **"down"** time —— time period of all polling cycles **N+1 to N+M —— in the log database**.
  (a) SLA 监控器通过发送轮询请求信息（M<sub>REQN+1</sub> 到 M<sub>REQN+M</sub>）来轮询云服务，没有收到轮询相应消息。(b) 响应消息一直超时，所以 SLA 监控器在日志数据库中存储 **"下线"** 时间 —— 所有的轮询周期 **N+1 到 N+M 的时间长度**。
3. (a) The SLA monitor sends a polling request message (M<sub>REQN+M+1</sub>) and receives the polling response message (M<sub>REPN+M+1). (b) The SLA monitor stores the **"up"** time in the log database.
  (a) SLA 监控器发送轮询消息（M<sub>REQN+M+1</sub>）并接收轮询响应消息（M<sub>REPN+M+1</sub>）。(b) SLA 监控器在日志数据库中存储 **"在线"** 时间。

![SLA 监视器 3](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/slajianshiqi3.PNG)

1.At **timestamp = t1**, the physical host server has failed and becomes **unavailable**.
  在 **时间戳为 t1** 时，物理主机服务器失效，变得 **不可用**。
2.(a) The SLA monitoring agent captures a **VM_unreachable** event that is generated for each virtual server in the failed host server. (b) The SLA monitor polling agent stops receiving responses from the host server and issues **PS_timeout** events.
  (a) SLA 监控代理捕获了 **VM_unreachable** 事件，这是对失效主机服务器上的每个虚拟服务器都会产生的。(b) SLA 监控轮询代理停止接收来自主机服务器的响应，并发送 **PS_timeout** 事件。
3.(a)At **timestamp = t2**, the SLA monitoring agent captures a **VM_failure** event that is generated for each of the failed host server's three virtual server. (b) The SLA monitor polling agent starts to issue **PS_unavailable** events after three successive **PS_timeout** events at **timestamp = t3**.
  (a) 在 **时间戳为 t2** 时，SLA 监控代理捕获了 **VM_failure** 事件，这是对失效主机服务器的三个虚拟服务器中的每一个都会产生的。(b) 在 **时间戳为 t3** 时，在收到三个连续的 **PS_timeout** 事件后，SLA 监控轮询代理开始发送 **PS_unavailable** 事件。

![SLA 监视器 4](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/slajianshiqi4.PNG)

4.The host server becomes operational at **timestamp = t4**.
  在 **时间戳为 t4** 时，主机服务器变得可运行。
5.(a) The SLA monitor polling agent receives responses from the physical server and issues **PS_reachable** events at **timestamp = t5**. (b) At **timestamp = t6**, the SLA monitoring agent captures a **VM_reachable** event that is generated for each virtual server.
  (a) 在 **时间戳为 t5** 时，SLA 监控轮询代理收到来自物理服务器的响应，发送 **PS_reachable** 事件。(b) 在 **时间戳为 t6** 时，SLA 监控代理收到为每个虚拟服务器产生的 **VM_reachable** 时间。
6.The SLA management system calculates the unavailability period that affected all of the virtual server as **t6-t2**.
  SLA 管理系统把影响所有虚拟服务器的不可用时间计算为 **t6-t2**。

## PAY-PER-USE MONITOR 按使用付费监控器

The **pay-per-use monitor** mechanism measures cloud-based IT resource usage in accordance with predefined pricing parameters and generates usage logs for fee calculations and billing purposes.
**按使用付费监控器** 机制按照预先定义好的定价参数测量基于云的 IT 资源使用，并生成使用日志用于计算费用。

Some typical monitoring variables are:
一些典型的监控变量包括：

- request/response message quantity 请求/响应消息数量
- transimtted data volume 传送的数据量
- bandwidth consumption 带宽消耗

![按使用付费监控器](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/anshiyongfufeijiankongqi.PNG)

1. The cloud consumer (CS_ID=CS1) creates and starts a virtual server (VM_ID=VM1) of configuration size type1 (VM_TYPE=type1).
  云用户（CS_ID=CS1）创建并启动了一个虚拟服务器（VM_ID=VM1），配置大小为类型 type1（VM_TYPE=type1）。
2. (a) The VIM creates the virtual server instance as requested. (b) The VIM's event-driven API generates a resource usage event with **timestamp=t1**, which is captured and forwarded to the pay-per-use monitor by the cloud usage monitor.
  (a) VIM 按照请求创建了虚拟服务器实例。(b) VIM 的时间驱动 API 产生了一个 **时间戳为 t1** 的资源使用事件，该事件被云使用监控器捕获并转发给按使用付费监控器。
3. The pay-per-use monitor interacts with the pricing scheme database to identify the chargeback and usage metrics that apply to the resource usage. A **"started usage"** billable event is generated and stored in the billable event log database.
  按使用付费监控器与定价机制数据库进行交互，确定适用于此次资源使用的扣费和使用指标。生成 **"开始使用"** 可计费事件，并存储到可计费事件日志数据库中。
4. The virtual server's usage increases and *reaches the auto-scaling threshold*.
  虚拟服务器的使用增加，*达到了自动扩展的阈值*。
5. (a) The VIM scales up Virtual Server VM1 (b) from configuration type1 to type2 (VM_TYPE=type2). The VIM's event-driven API generates a resource usage event with **timestamp = t2**, which is captured and forwarded to the pay-per-use monitor by the cloud usage monitor.
  (a) VIM 扩展虚拟服务器 VM1，(b) 配置从类型 1 变到类型 2（VM_TYPE=type2）。VIM 的事件驱动 API 产生一个 **时间戳为 t2** 的资源使用事件，该事件被云使用监控器捕获并转发给按使用付费监控器。
6. The pay-per-use monitor interacts with the pricing scheme database to identify the chargeback and usage metrics that apply to the updated IT resource usage. A **"changed usage"** billable event is generated and stored in the billable event log database.
  按使用付费监控器与定价机制数据库进行交互，确定适用于此次更新的资源使用的扣费和使用指标。生成 **"使用变化"** 可计费事件，并存储到可计费事件日志数据库中。
7. The cloud consumer shuts down the virtual server.
  云用户关闭此虚拟机。
8. (a) and the VIM stops Virtual Server VM1. (b) The VIM's event-driven API generates a resource usage event with **timestamp = t3**, which is captured and forwarded to the pay-per-use monitor by the cloud usage monitor.
  (a) VIM 停止虚拟服务器 VM1。(b) VIM 的事件驱动 API 产生一个 **时间戳为 t3** 的资源使用事件，该事件被云使用监控器捕获并转发给按使用付费监控器。
9. The pay-per-use monitor interacts with the pricing scheme database to identify the chargeback and usage metrics that apply to the upadated TI resource usage. A **"finished usage"** billable event is generated and stored in the billable event log database.
  按使用付费监控器与定价机制数据库进行交互，确定适用于此次更新的资源使用的扣费和使用指标。生成 **"使用完成"** 可计费事件，并存储到可计费事件日志数据库中。
10. The billing system tool can now be used by the cloud provider to access the log database and calculate the total usage fee for the virtual server as (Fee(VM1)).
  此时云提供者可以使用计费系统工具来访问日志数据库，计算这个虚拟服务器的所有使用费用 (Fee(VM1))。

## AUDIT MONITOR 审计监控器

The **audit monitor** mechanism is used to collect audit tracking data for networks and IT resources in support of (or dictated by) *regulatory and contractual obligations*.
**审计监控器** 机制用来收集网络和 IT 资源的审计记录数据，用以满足 *管理需求或者合同义务*。

![审计监控器](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/shenjijiankongqi.PNG)

1. A cloud service consumer requests access to a cloud service by sending a login request message with security credentials.
  云服务用户请求访问云服务，发送一个带有安全证书的登录请求消息。
2. The audit monitor intercepts the message
  审计监控器截获该消息
3. and forwards it to the authentication service.
  将它转发给认证服务。
4. The authentication service processes the security credentials. A response message is generated for the cloud service consumer, in addition to the results from the login attempt.
  认证服务处理安全证书。除了登录尝试的结果之外，还为该云服务用户生成一个响应消息。
5. The audit monitor intercepts the response message and stores the entire collected login event details in the log database, as per the organization's audit policy requirements.
  审计监控器截获响应消息，按照该组织的审计策略要求，将收集到的整个登录事件都存储到日志数据库中。
6. Access has been granted, and a response is sent back to the cloud service consumer.
  访问已经被授权，响应被发回给云服务用户。

## FAILOVER SYSTEM 故障转移系统

The **failover system** mechanism is used to **increase the reliability and availability of IT resources** by using established clustering technology to provide **redundant** implementations.
**故障转移系统** 机制通过使用现有的集群技术提供 **冗余的** 实现来 **增加 IT 资源的可靠性和可用性**。

Failover systems are commonly used for *mission-critical programs* and *reusable services* that can introduce a single point of failure for multiple applications.
故障转移系统通常用于 *关键任务程序* 和 *可重用的服务*，这些程序和服务可能成为多个应用程序的单一失效点。
A failover system can span more than one *geographical region* so that each location hosts one or more redundant implementations of the same IT resource.
故障转移系统可以跨越多个 *地理区域*，这样每个地点都能有一个或多个同样 IT 资源的冗余实现。
The *resource replication mechanism* is sometimes utilized by the failover system to provide redundant IT resource instances, which are actively monitored for the detection of errors and unavailability conditions.
故障转移系统有时会利用 *资源复制机制* 提供冗余的 IT 资源实例，主动监控这些资源实例以探测错误和不可用的情况。

### Active-Active 主动-主动

In an active-active configuration, redundant implementations of the IT resource actively *serve the workload synchronously*.
在主动-主动这种配置中，IT 资源的冗余实现会 *主动地同步服务工作负载*。

![主动主动 1](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/zhudongzhudong1.PNG)

The failover system monitors the operational status of Cloud Service A.
故障转移系统监控云服务 A 的运行状态。

![主动主动 2](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/zhudongzhudong2.PNG)

When a failure is detected in one Cloud Service A implementation, the failover system commands the load balancer to switch over the workload to the redundant Cloud Service A implementation.
当察觉到云服务 A 的一个实现失效时，故障转移系统会命令负载均衡器将工作负载切换到云服务 A 的冗余实现上。

![主动主动 3](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/zhudongzhudong3.PNG)

The failed Cloud Service A implementation is recovered or replicated into an operational cloud service.
失效的云服务 A 实现被恢复，或者复制到一个可运行的云服务上。
The failover system now commands the load balancer to distribute the workload again.
这是故障转移系统命令负载均衡器再次分配工作负载。

### Active-Passive 主动-被动

In an active-passive configuration, a *standby* or *inactive* implementation is activated to take over the processing from the IT resource that becomes unavailable, and the corresponding workload is redirected to the instance taking over the operation.
在主动-被动配置中，*待机* 或 *非活跃* 的实现会被激活，从变得不可用的 IT 资源处接管处理工作，相应的工作负载就会被重定向到接管操作的这个实例上。

![主动被动 1](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/zhudongbeidong1.PNG)

The failover system monitors the operational status of Cloud Service A.
故障转移系统监控云服务 A 的运行状态。
The Cloud Service A implementation acting as the active instance is receiving cloud service consumer requests.
作为活跃实例的云服务 A 的实现接收云服务用户的请求。

![主动被动 2](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/zhudongbeidong2.PNG)

The Cloud Service A implementation acting as the active instance encounters a failure that is detected by the failover system, which subsequently activates the inactive Cloud Service A implementation and redirects the workload toward it.
作为活跃实例的云服务 A 的实现发生了故障，故障转移系统检测到了，接着就激活了云服务 A 的非活跃实例，并将工作负载重定向到这个实例。
The newly invoked Cloud Service A implementation now assumes the role of active instance.
这个新激活的云服务 A 的实现现在就承担起了活跃实例的角色。

![主动被动 3](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/zhudongbeidong3.PNG)

The failed Cloud Service A implementation is recovered or replicated an operational cloud service, and is now positioned as the standby instance, while the previously invoked Cloud Service A continues to serve as the active instance.
失效的云服务 A 的实现被恢复，或者复制到了一个可运行的云服务上，现在就被定位为待机的实例，而前面被激活的云服务 A 仍然保持为活跃的实例。

## HYPERVISOR 虚拟机监控器

The **hypervisor** mechanism is a fundamental part of virtualization infrastructure that is primarily used to generate *virtual server instances* of a physical server.
**虚拟机监控器** 机制是虚拟化基础设施的最基础部分，主要用来在物理服务器上生成 *虚拟服务器实例*。
A hypervisor is generally limited to *one physical server* and can therefore only create virtual images of that server.
虚拟机监控器通常限于 *一台物理服务器*，因此只能创建那台服务器的虚拟映像。

Similarly, a hypervisor can only assign virtual servers it generated to *resource pools that reside on the same underlying physical server*.
类似地，虚拟机监控器只能把它自己创建的虚拟服务器分配到 *位于同一底层物理服务器上的资源池里*。
The VIM provides a range of features for administering multiple hypervisors *across physical servers*.
VIM 提供了一组特性来管理 *跨物理服务器* 的多虚拟机监控器。

![虚拟机监控器](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/xunijijiankongqi.PNG)

Hypervisor software can be installed *directly in bare-metal servers* and provides features for controlling, sharing and scheduling the usage of hardware resources.
虚拟机监控器软件可以 *直接安装在裸机服务器上*，提供对硬件资源使用的控制、共享和调度功能。
These can appear to each virtual server's *operating system* as dedicated resources.
它们可以当作专有的资源，呈现在每台虚拟机服务器的 *操作系统* 里。

## RESOURCE CLUSTER 资源集群

The **resource cluster** mechanism is used to group multiple IT resource instances so that they can be operated as a single IT resource.
**资源集群** 机制是把多个 IT 资源实例分为一组，使得它们能像一个 IT 资源那样进行操作。
This increases the combined computing capacity, load balancing, and availability of the clustered IT resources.
这增强了集群化 IT 资源的组合计算能力、负载均衡能力和可用性。

Resource cluster architectures rely on **high-speed dedicated network connections**, or **cluster nodes**, between IT resource instances to communicate about *workload distribution, task scheduling, data sharing, and system synchronization*.
资源集群架构依赖于 IT 资源实例之间的 **高速专用网络连接** 或 **集群节点**，在 IT 资源实例间就 *工作负载分布、任务调度、数据共享和系统同步* 等进行通信。

A **cluster management platform** that is running as **distributed middleware** in all of the cluster nodes is usually responsible for these activities.
**集群管理平台** 是作为 **分布式中间件** 运行在所有的集群节点上的，它通常负责上述活动。
This platform implements a *coordination function* that allows distributed IT resources to appear as one IT resource, and also *executes IT resources* inside the cluster.
这个平台实现 *协调功能*，它使得能 *执行集群里的 IT 资源* 的同时，让分布式 IT 资源看上去像一个 IT 资源。

***Server Cluster 服务器集群***

- Physical or virtual servers are clustered to **increase performance and availability**.
  物理或虚拟服务器组成集群以 **提高性能和可用性**。
- **Hypervisors** running on different physical servers can be configured to *share virtual server execution state* in order to establish clustered virtual servers.
  运行在不同物理服务器上的 **虚拟机监控器** 可以被配置成 *共享虚拟服务器执行状态*，以此建立起集群化的虚拟服务器。
- In such configurations, which usually require physical servers to have access to shared storage,  virtual servers are able to **live-migrate** from one to another.
  在这种通常需要物理服务器访问共享存储的配置下，虚拟服务器能够从一个物理服务器 **在线迁移** 到另一个。
- In this process, the virtualization platform suspends the execution of a given virtual server at one physical server and resumes it on another physical server.
  在这个过程中，虚拟化平台挂起某个物理服务器上给定的虚拟服务器的执行，再在另一个物理服务器上继续执行它。
- The process is transparent to the virtual server operating system and can be used to increase scalability by live-migrating a virtual server that is running at an overloaded physical server to another physical server that has suitable capacity.
  这个过程对虚拟服务器操作系统来说是透明的，可以通过把运行在负载过重的物理服务器上的虚拟服务器在线迁移到容量适合的另一台物理服务器上，来增加可扩展性。

***Database Cluster 数据库集群***

- Designed to *improve data availability*, this high-availability resource cluster has a **synchronization feature** that maintains the **consistency** of data being stored at different storage devices used in the cluster.
  这种高可用资源集群用于 *改进数据可用性*，它具有 **同步的特性**，可以维持集群中使用到的各种存储设备上存储数据的 **一致性**。
- The **redundant capacity** is usually based on an *active-active or active-passive* failover system committed to maintaining the synchronization conditions.
  **冗余能力** 通常是基于致力于维护同步条件的 *主动-主动或主动-被动* 故障迁移系统的。

***Large Dataset Cluster 大数据集集群***

- **Data partitioning and distribution** is implemented so that the target datasets can be efficiently partitioned *without compromising data integrity or computing accuracy*.
  实现了 **数据的分区和分布**，这样目标数据集可以很有效地划分区域，而 *不需要破坏数据的完整性或计算的准确性*。
- Each cluster node processes workloads without communicating with other nodes as much as in other cluster types.
  每个集群节点都可以处理工作负载，而不需要像其他集群类型一样，与其他节点进行更多的通信。

![资源集群 1](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/ziyuanjiqun1.PNG)

Load balancing and resource replication are implemented through a **cluster-enabled hypervisor**.
负载均衡和资源复制是通过 **带集群功能的虚拟机监控器** 来实现的。
A dedicated **storage area network** is used to connect the clustered storage and the clustered servers, which are able to *share common cloud storage devices*.
一个专用的 **存储区域网络** 用来连接集群化的存储和集群化的服务器，它们能够 *共享共有的云存储设备*。

![资源集群 2](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/ziyuanjiqun2.PNG)

A **loosely coupled** server cluster that incorporates a load balancer.
一个带有负载均衡器的 **松耦合** 服务器集群。
Resource replication is used to replicate cloud storage devices through the network by the **cluster software**.
没有共享存储，**集群软件** 通过网络用资源复制来复制云存储设备。

Two basic types of resource clusters:
两种基本类型资源集群：

- **Load Balanced Cluster 负载均衡的集群**
  - This resource cluster specilaizes in **distributing workloads among cluster nodes** to increase IT resource capacity while perserving the centralization of TI resource management.
    这种资源集群的专场在于 **在集群节点中分布工作载荷**，既提高 IT 资源的容量，又保持 IT 资源的集中管理。
  - It usually implements a **load balancer** mechanism that is either *embedded* within the cluster management platform or set up as a *separate* IT resource.
    它通常要实现一个 **负载均衡器** 机制，要么是 *潜入* 集群管理平台，要么是设定为一个 *独立的* IT 资源。
- **HA Cluster HA 集群**
  - A **high-availability** cluster maintains system availability in the event of multiple node failures,and has redundant implementations of most or all of the clustered IT resources.
    **高可用** 集群在遇到多节点失效的情况时，仍然能够维持系统的可用性，而且大多数或者所有集群化的 IT 资源都有冗余实现。
  - It implements a **failover system** mechanism that monitors failure conditions and automatically redirects the workload away from any failed nodes.
    它实现一个 **故障转移系统** 机制，监控失效情况，并自动将工作负载重定向为远离故障节点。

## MULTI-DEVICE BROKER 多设备代理

The **multi-device broker** mechanism is used to facilitate *runtime data transformation* so as to make a cloud service accessible to a wider range of cloud service consumer programs and devices.
**多设备代理** 机制用来帮助 *运行时的数据转换*，使得云服务能够被更广泛的云服务用户程序和设备所使用。

Multi-device brokers commonly exist as **gateways** or **incorporate gatewa components**.
多设备代理通常是作为 **网关** 存在的，或者 **包含有网关组件**。

- **XML Gateway XML 网关**
- **Cloud Storage Gateway 云存储网关**
- **Mobile Device Gateway 移动设备网关**

![多设备代理](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/duoshebeidaili.PNG)

1. The multi-device broker intercepts incoming messages and detects the platform (Web browser, iOS, Android) of the source device.
  多设备代理截取进入的消息，确定源设备的平台（Web 浏览器、iOS、安卓）。
2. The multi-device broker transforms the message into the standard format required by the Innovartus cloud service.
  多设备代理将消息转换成 Innovartus 云服务要求的标准格式。
3. The cloud service processes the request and responds using the same standard format.
  云服务处理请求，并以同样的标准格式进行响应。
4. The multi-device broker transforms the response message into the format required by the source device and delivers the message.
  多设备代理将响应消息转换到源设备需要的格式，并传送该消息。

## STATE MANAGEMENT DATABASE 状态管理数据库

A **state management database** is a *storage device* that is used to **temporarily persist** state data for software programs.
**状态管理数据库** 是一种 *存储设备*，用来 **暂时地持久化** 软件程序的状态数据。

State management databases are commonly used by *cloud services*, especially those involved in **long-running runtime** activities.
状态管理数据库通常是由 *云服务* 使用的，特别是涉及 **长时间运行时** 活动的服务。

![状态管理数据库 1](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/zhuangtaiguanlishujuku1.PNG)

During the lifespan of a cloud service instance it may be required to remain stateful and keep state data *cached in memory*, even when idle.
在云服务实例的生命期内，它可能被要求保持有状态，即使在空闲时，也要把状态数据 *缓存在内存中*。

![状态管理数据库 2](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/zhuangtaiguanlishujuku2.PNG)

By *deferring state data to a state repository*, the cloud service is able to transition to a stateless condition (or a partially statless condition), thereby temporarily freeing system resources.
通过 *把状态数据推后到状态仓库中*，云服务能够转入一种无状态的情况（或者一种部分无状态的情况），因此暂时释放了系统资源。

![状态管理数据库 3](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/zhuangtaiguanlishujuku3.PNG)

![状态管理数据库 4](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/zhuangtaiguanlishujuku4.PNG)

1. The cloud consumer accesses the ready-made environment and requires three virtual servers to perform all activities.
  云用户访问已就绪环境，要求三个虚拟服务器来执行所有的活动。
2. The cloud consumer pauses activity. All of the state data needs to be preserved for future access to the ready-made environment.
  云用户暂停活动。需要保留所有的状态数据供今后访问该已就绪环境之用。
3. The underlying infrastructure is automatically scaled in by reducing the number of virtual servers. State dta is *saved* in the state management database and one virtual server remains active to allow for future logins by the cloud consumer.
  底层的基础设施自动收缩，减少虚拟服务器的数量。状态数据 *保存* 在状态管理数据库中，还有一个虚拟服务器保持活跃，允许今后云用户进行登录。
4. At a later point, the cloud consumer logs in and accesses the ready-made environment to contimue activity.
  之后某个时间点，云用户登录，访问这个已就绪环境继续活动。
5. The underlying infrastructure is automatically scaled out by increasing the number of virtual servers and by *retrieving* the state data from the state management database.
  底层的基础设施增加虚拟机的数量，从状态管理数据库 *检索* 出状态数据，并自动扩展。
