[toc]

## WORKLOAD DISTRIBUTION ARCHITECTURE 负载分布架构

IT resources can be **horizointally scaled** via the additiion of one or more identical IT resources, and a **load balancer** that provides runtime logic capable of evenly distributing the workload among the available IT reosurces.
通过增加一个或多个相同的 IT 资源可以进行 IT 资源 **水平扩展**，而提供运行时逻辑的 **负载均衡器** 能够在可用 IT 资源上均匀分配工作负载。

The resulting **workload distribution architecture** *reduces* both IT resource *over-utilization* and *under-utilization* to an extent dependent upon the sophistication of the load balancing algorithms and runtime logic.
由此产生的 **负载分布架构** 在一定程度上依靠复杂的负载均衡算法和运行时逻辑，*减少* IT 资源的 *过度使用* 和 *使用率不足* 的情况。

This fundamental architectural model can be applied to *any IT resource*.
这种基本架构模型可以应用于 *任何 IT 资源*。

## RESOURCE POOLING ARCHITECTURE 资源池架构

A **resource pooling architecture** is based on the use of one or more resource pools, in which identical IT resources are grouped and maintained by a system that automatically ensures that they remain synchronized.
**资源池架构** 以使用一个或多个资源池为基础，其中相同的 IT 资源由一个系统进行分组和维护，以自动确保它们保持同步。

![物理服务器池](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/wulifuwuqichi.PNG)

- 物理服务器池

![虚拟服务器池](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/xunifuwuqichi.PNG)

- 虚拟服务器池

![存储池](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/cunchuchi.PNG)

- 存储池

![网络池](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/wangluochi.PNG)

- 网络池

![CPU 池](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/cpuchi.PNG)

- CPU 池

![内存池](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/neicunchi.PNG)

- 内存池

![更大的资源池](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/gengdadeziyuanchi.PNG)

**Dedicated pools** can be created for each type of IT resource and individual pools can be grouped into a larger pool, in which case each individual pool becomes a **sub-pool**.
可以为每种类型的 IT 资源创建 **专用池**，也可以将单个池集合为一个更大的池，在这个更大的资源池中，每个单独的池成为了 **子资源池**。

![同级资源池](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/tongjiziyuanchi.PNG)

**Sibling resource pools** are usually drawn from **physically** grouped IT resources, as opposed to IT resources that are spread out over different data centers.
**同级资源池** 通常来自于 **物理上** 分为一组的 IT 资源，而不是来自于分布在不同数据中心内的 IT 资源。
Sibling pools are **isolated** from one another so that each cloud consumer is only provided access to its respective pool.
同级资源池之间是相互 **隔离** 的，因此云用户只能访问各自的资源池。

![嵌套资源池](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/qiantaoziyuanchi.PNG)

In the **nested pool model**, larger pools are divided into smaller pools that individually group the **same type** of IT resources together.
在 **嵌套资源池模型** 中，较大的资源池被分解为较小的资源池，每个小资源池分别包含了与大资源池 **相同类型** 的 IT 资源。

## DYNAMIC SCALABILITY ARCHITECTURE 动态可扩展架构

The **dynamic scalability architecture** is an architectural model based on a system of *predefined* scaling conditions that *trigger* the dynamic allocation of IT resources from resource pools.
**动态可扩展架构** 是一个架构模型，它基于 *预先定义* 扩展条件的系统，*触发* 这些条件会导致从资源池中动态分配 IT 资源。

The following types of dynamic scaling are commonly used:
下面是常用的动态扩展类型：

- *Dynamic Horizontal Scaling 动态水平扩展*
- *Dynamic Vertical Scaling 动态垂直扩展*
- *Dynamic Relocation 动态重定位*

![动态可扩展架构 1](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/dongtaikekuozhanjiagou1.PNG)

1.Cloud service consumers are sending requests to a cloud service.
  云服务用户向云服务发送请求。
2.The automated scaling listener monitors the cloud service to determine if predefined capacity thresholds are being exceeded.
  自动扩展监听器监视该云服务，判断预定义的容量阈值是否已经被超过。

![动态可扩展架构 2](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/dongtaikekuozhanjiagou2.PNG)

3.The number of requests coming from cloud service consumers increases.
  云服务用户的请求数量增加。
4.The workload exceeds the performance thresholds. The automated scaling listener determines the next course of action based on a predefined scaling policy.
  工作负载已超过性能阈值。根据预先定义的扩展规则，自动扩展监听器决定下一步的操作。
5.If the cloud service implementation is deemed eligible for additional scaling, the automated scaling listener initiates the scaling process.
  如果云服务的实现被认为适合扩展，则自动扩展监听器启动扩展过程。

![动态可扩展架构 3](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/dongtaikekuozhanjiagou3.PNG)

6.The automated scaling listener sends a signal to the resource replication mechanism.
  自动扩展监听器向资源复制机制发送信号。
7.Which creates more instances of the cloud service.
  创建更多的云服务实例。
8.Now that the increased workload has been accommodated, the automated scaling listener resumes monitoring and detracting and adding IT resources, as required.
  现在，增加的工作负载可以得到满足，自动扩展监听器根据请求，继续监听并增加或减少 IT 资源。

## ELASTIC RESOURCE CAPACITY ARCHITECTURE 弹性资源容量架构

The **elastic resource capacity architecture** is primarily related to the *dynamic* provisioning of virtual servers, using a system that *allocates and reclaims* CPUs and RAM in *immediate response* to the fluctuating processing requirements of hosted IT resource.
**弹性资源容量架构** 主要与虚拟服务器的 *动态* 供给相关，利用 *分配和回收* CPU 与 RAM 资源的系统，*立即响应* 托管 IT 资源的处理请求变化。

![智能自动化引擎](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/zhinengzidonghuayinqing.PNG)

The **intelligent automation engine** automates administration tasks by executing scripts that contain workflow logic.
**智能自动化引擎** 通过执行包含工作流逻辑的脚本来自动执行管理任务。

![弹性资源容量架构 1](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/tanxingziyuanrongliangkuangjia1.PNG)

1.Cloud service consumers are actively sending requests to a cloud service.
  云服务用户主动向云服务发送请求。
2.Which are monitored by an automated scaling listener.
  自动扩展监听器对此进行监控。
3.An intelligent automation engine script is deployed with workflow logic
  智能自动化引擎脚本与工作流逻辑一起部署。
4.That is capable of notifying the resource pool using allocation requests.
  能够通过分配请求通知资源池。

![弹性资源容量架构 2](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/tanxingziyuanrongliangkuangjia2.PNG)

5.Cloud service consumer requests increase.
  云服务用户增加请求。
6.Causing the automated scaling listener to signal the intelligent automation engine to execute the script.
  使得自动扩展监听器向智能自动化引擎发送执行脚本的信号。
7.The scripts runs the workflow logic that signals the hypervisor to allocate more IT resources from the resource pools.
  脚本运行工作流逻辑，虚拟机监控器从资源池分配更多 IT 资源。
8.The hypervisor allocates additional CPU and RAM to the virtual server, enabling the increased workload to be handled.
  虚拟机监控器给虚拟服务器分配额外的 CPU 和 RAM，使得增加的工作负载得以处理。

## SERVICE LOAD BALANCING ARCHITECTURE 服务负载均衡架构

The **service load balancing architecture** can be considered a specialized variatin of the workload distribution architecture that is geared specifically for **scaling cloud service** implementations.
**服务负载均衡架构** 可以被认为是工作负载分布架构的一个特殊变种，它是专门针对 **扩展云服务** 实现的。
The duplicate cloud service implementations are orgainized into a resource pool, while the *load balancer* is positioned as either an *external* or *built-in* component to allow the host servers to balance the workloads themselves.
云服务实现的副本被组织为一个资源池，而 *负载均衡器* 则作为 *外部* 或 *内置* 组件，允许托管服务器自行平衡工作负载。

![服务负载均衡架构](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/fuwufuzaijunhengjiagou.PNG)

1. Cloud service consumer requests are sent to Cloud Service A on Virtual Server A.
  云服务用户的请求发送给虚拟服务器 A 上的云服务 A 上。
2. The cloud service implementation includes built-in load balancing logic that is capable of distributing requests to the neighboring Cloud Service A implementations on Virtual Servers B and C.
  内置负载均衡逻辑包含在云服务实现中，它可以将请求分配给相邻的云服务 A，这些云服务 A 的实现位于虚拟服务器 B 和 C 上。

## CLOUD BURSTING ARCHITECTURE 云爆发架构

The **cloud bursting architecture** establishes a form of dynamic scaling that *scales or "bursts out" on-premise IT resources into a cloud* whenever predefined capacity thresholds have been reached.
**云爆发架构** 建立了一种动态扩展的形式，只要达到预先是额定的容量阈值，就 *从企业内部的 IT 资源扩展或 "爆发" 到云中*。

**Cloud bursting** is a *flexible* scaling architecture that provides cloud consumers with the option of using cloud-based IT resources only to meet higher usage demands.
**云爆发** 是 *弹性* 扩展架构，它向云用户提供一个使用基于云的 IT 资源的选项，但这个选项只用于应对较高的使用需求。
The foundation of this architecture model is based on the **automated scaling listener** and **resource replication mechanisms**.
这种架构模型的基础是 **自动扩展监听器** 和 **资源复制机制**。

![云爆发架构](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/yunbaofajiagou.PNG)

1. An automated scaling listener monitors the usage of on-premise Service A, and redirects Service Consumer C's request to Service A's redundant implementation in the cloud(Cloud Service A) once Service A's usage threshold has been exceeded.
  自动扩展监听器监控企业内部服务 A 的使用情况，当服务 A 的使用阈值被突破时，将服务用户 C 的请求重定向到服务 A 在云中的冗余实现（云服务 A）。
2. A resource replication system is used to keep state management databases synchronized.
  资源复制系统用于保持状态管理数据库的同步。

## ELASTIC DISK PROVISIONING ARCHITECTURE 弹性磁盘供给架构

The **elastic disk provisioning architecture** establishes a dynamic storage provisioning system that ensures that the cloud consumer is granularly billed for the exact amount of storage that it actually uses.
**弹性磁盘供给架构** 建立了一个动态存储供给系统，它确保按照云用户实际使用的存储量进行精确计费。
This system uses **thin-provisioning technology** for the dynamic allocation of storage space, and is further supported by runtime usage monitoring to collect accurate usage data for billing purposes.
该系统采用 **自动精简供给技术** 实现存储空间的自动分配，并进一步支持运行时使用监控来收集准确的使用数据以便计费。

![弹性磁盘供给架构 1](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/tanxingcipangongjijiagou1.PNG)

1. The cloud consumer requests a virtual server with three hard disks, each with a capacity of 150 GB.
  云用户请求一个虚拟服务器，要求带有 3 个硬盘，每个硬盘的容量为 150 GB。
2. The virtual server is provisioned according to the elastic disk provisioning architecture, with a total of 450 GB of disk space.
  根据弹性磁盘供给架构，这个虚拟服务器预备了 450 GB 的总容量。
3. The 450 GB is allocated to the virtual server by the cloud provider.
  云提供者分配 450 GB 给虚拟服务器。
4. The cloud consumer has not installed any software yet, meaning the actual used space is currently 0 GB.
  云用户还未安装任何软件，这就意味着其当前使用空间为 0 GB。
5. Because the 450 GB are **already allocated** and reserved for the cloud consumer, it will be charged for 450 GB of disk usage as of the point of allocation. 
  由于 450 GB **已经分配了**，并为该云用户保存下来，因此，从容量分配开始，磁盘的使用就按照 450 GB 收费。

![弹性磁盘供给架构 2](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/tanxingcipangongjijiagou2.PNG)

1. The cloud consumer requests a virtual server with three hard disks, each with a capacity of 150 GB.
  云用户请求一个虚拟服务器，要求带有 3 个硬盘，每个硬盘的容量为 150 GB。
2. The virtual server is provisioned by this architecture with a total of 450 GB of disk space.
  根据弹性磁盘供给架构，这个虚拟服务器被分配了 450 GB 的容量。
3. The 450 GB are set as *the maximum disk usage* that is allowed for this virtual server, although no physical disk space has been reserved or allocated yet.
  450 GB 为该虚拟服务器 *最大磁盘使用量*。
4. The cloud consumer has not installed any software, meaning the actual used space is currently at 0 GB.
  云用户还未安装任何软件。
5. Because **the allocated disk space is equal to the actual used space (which is currently at zero)**, the cloud consumer is not charged for any disk space usage.
  由于 **分配的磁盘空间与实际使用空间相等（当前都为 0）**，因此，云用户不用支付任何磁盘空间的使用费用。

![弹性磁盘供给架构 3](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/tanxingcipangongjijiagou3.PNG)

1. A request is received from a cloud consumer, and the provisioning of a new virtual server instance begins.
  收到云用户请求，开始供给一个新虚拟服务器实例。
2. As part of the provisioning process, the hard disks are chosen as dynamic or thin-provisioned disks.
  作为供给处理的一部分，磁盘被选择为动态的或自动精简供给的磁盘。
3. The hypervisor calls a dynamic disk allocation component to create thin disks for the virtual server.
  虚拟机监控器调用动态磁盘分配组件，为虚拟服务器创建薄盘。
4.  Virtual server disks are created via the thin-provisioning program and saved in a folder of near-zero size. The size of this folder and its files grow as operating applications are installed and additional files are copied onto the virtual server.
  由自动精简供给程序创建的虚拟服务器磁盘保存在一个大小几乎为 0 的文件夹中。随着运行应用程序的安装以及向该虚拟服务器复制其他的文件，这个文件夹的大小和其中文件的数量也会增加。
5. The pay-per-use monitor tracks the actual dynamically allocated storage for billing purposes.
  按使用付费监控器实际动态分配的存储量以便计费。

## REDUNDANT STORAGE ARCHITECTURE 冗余存储架构

The **redundant storage architecture** introduces a **secondary duplicate cloud storage device** as part of a **failover system** that synchronizes its data with the data in the primary cloud storage device.
**冗余存储架构** 引入了复制的 **辅云存储设备** 作为 **故障系统** 的一部分，它要与主云存储设备中的数据保持同步。
A *storage service gateway* diverts cloud consumer requests to the secondary device whenever the primary device fails.
当主设备失效时，*存储设备网关* 就把云用户请求转向辅设备。

![LUN](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/lun.PNG)

A **logical unit number(LUN)** is a **logical drive** that represents a *partition* of a *physical drive*.
**逻辑单元号（LUN）** 是一个 **逻辑驱动器**，它代表了 *物理驱动器* 的一个 *分区*。

![存储设备网关](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/cunchushebeiwangguan.PNG)

The **storage service gateway** is a component that acts as the *external interface* to cloud storage services, and is capable of automatically *redirecting* cloud consumer requests whenever the location of the requested data has changed.
**存储设备网关** 是一个组件，是连接到云存储设备的 *外部接口*。当云用户请求的数据位置发生变化时，它可以自动将云用户请求进行 *重定位*。

![冗余存储架构 1](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/rongyucunchujiagou1.PNG)

![冗余存储架构 2](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/rongyucunchujiagou2.PNG)

1. The primary cloud storage device is routinely replicated to the secondary cloud storage device.
  主云存储设备定期复制到辅云存储设备。
2. The primary storage becomes unavailable and the storage service gateway forwards the cloud consumer requests to the secondary storage device.
  主存储设备变为不可用，存储设备网关将云用户请求发送到辅存储设备。
3. The secondary storage device forwards the requests to the LUNs, allowing cloud consumers to continue to access their data.
  辅存储设备将请求发送到 LUN，允许云用户继续访问它们的数据。

![存储复制](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/cunchufuzhi.PNG)

**Storage replication** is a variation of the *resource replication* mechanisms used to synchronously or asynchronously replicate data from a primary storage device to a secondary storage device.
**存储复制** 是 *资源复制* 机制的一种变体，用于将数据从主存储设备同步或异步地复制到辅存储设备。
It can be used to replicate *partial and entire LUNs*.
它可用于复制 *部分或全部 LUN*。

![冗余存储设备 3](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/rongyucunchujiagou3.PNG)

This cloud architecture primarily relies on a **storage replication system** that keeps the primary cloud storage device synchronized with its duplicate secondary cloud storage devices.
该云架构主要依靠的是 **存储复制**，它使得主云存储设备与其复制的辅云存储设备保持同步。
