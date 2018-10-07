[toc]

## HYPERVISOR CLUSTERING ARCHITECTURE 虚拟机监控器集群架构

**Hypervisor clustering architecture** establishes a high-availability cluster of hypervisors across multiple physical servers.
**虚拟机监控器集群架构** 建立了一个跨多个物理服务器的高可用虚拟机监控器集群。

![心跳](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/xintiao.PNG)

**Heartbeats** are system-level messages exchanged ②between hypervisors, hypervisors and virtual servers, and hypervisors and VIMs.
**心跳** 是虚拟机监控器之间、虚拟机监控器和虚拟服务器之间、虚拟机监控器和 VIM 之间相互交换的系统级消息。

![VM 在线迁移](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/vmzaixianqianyi.PNG)

**Live VM migration** is a system that is capable of relocating virtual servers or virtual server instances at runtime.
**VM 在线迁移** 是一个具有在运行时将虚拟服务器或虚拟服务器实例重新放置能力的系统。

![虚拟机监控器集群架构 1](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/xunijijainkongqijiqunjiagou1.PNG)

1.Hypervisors are installed on Physical Servers A, B, and C.
  虚拟机监控器安装在物理服务器 A、B 和 C 上。
2.Virtual servers are created by the hypervisors.
  虚拟机监控器创建虚拟服务器。
3.A shared cloud storage device containing virtual server configuration files is positioned in a shared cloud storage device for access by all hypervisors.
  部署一个包含虚拟服务器配置文件且所有虚拟机监控器可以访问到的共享云存储设备。
4.The hypervisor cluster is enabled on the three physical server hosts via a central VIM.
  通过中心 VIM，虚拟机监控器集群在三个物理服务器上可用。

![虚拟机监控器集群架构 2](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/xunijijainkongqijiqunjiagou2.PNG)

5.The physical servers exchange heartbeat messages with one another and the VIM according to a pre-defined schedule.
  按照预先定义好的计划，物理服务器之间以及和 VIM 之间相互交换心跳信息。

![虚拟机监控器集群架构 3](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/xunijijainkongqijiqunjiagou3.PNG)

6.Physical Server B fails and becomes unavailable, jeopardizing Virtual Server C.
  物理服务器 B 失效且变得不可用，危及到虚拟服务器 C。
7.The other physical servers and the VIM stop receiving heartbeat messages from Physical Server B.
  其余的物理服务器和 VIM 停止收到来自物理服务器 B 的心跳信息。

![虚拟机监控器集群架构 4](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/xunijijainkongqijiqunjiagou4.PNG)

8.The VIM chooses Physical Server C as the new host to take ownership of Virtual Server C after assessing the available capacity of other hypervisors in the cluster.
  在评估了集群中其他虚拟机监控器的可用容量之后，VIM 选择物理服务器 C 作为虚拟服务器 C 的新主机。
9.Virtual Server C is live-migrated to the hypervisor running on Physical Server C, where *restarting* may be necessary before normal operations can be resumed.
  虚拟服务器 C 在线迁移到物理服务器 C 上运行的虚拟机监控器上，在正常操作继续进行前，可能需要 *重启* 虚拟服务器 C.

## LOAD BALANCED VIRTUAL SERVER INSTANCES ARCHITECTURE 负载均衡的虚拟服务器实例架构

The **load balanced virtual server instances architecture** establishes a **capacity watchdog system** that dynamically calculates virtual server instances and associated workloads, before distributing the processing across available physical server hosts
**负载均衡的虚拟服务器实例架构** 建立了一个 **容量看门狗系统**，在把处理任务分配到可用的物理服务器主机之前，会动态地计算虚拟服务器实例及其相关的工作负载。

The capacity watchdog system is comprised of:
容量看门狗系统由以下部分组成：

- **a capacity watchdog cloud usage monitor 容量看门狗云使用监控器**
- **the live VM migration program VM 在线迁移程序**
- **a capacity planner 容量计划器**

![负载均衡的虚拟服务器实例架构 1](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/fuzaijunhengdexunifuwiqishilijiagou1.PNG)

1.The hypervisor cluster architecture provides the foundation upon which the load-balanced virtual server architecture is built.
  虚拟机监控器集群提供了一个基础，在此基础之上构建了负载均衡的虚拟服务器架构。
2.Policies and thresholds are defined for the capacity watchdog monitor.
  为容量看门狗监控器设定策略和阈值。
3.Which compares physical server capacities with virtual server processing.
  监控器比较物理服务器的容量以及虚拟服务器要求的处理能力。
4.The capacity watchdog monitor reports an over-utilization to the VIM.
  容量看门狗监控器向 VIM 报告过度使用的情况。

![负载均衡的虚拟服务器实例架构 2](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/fuzaijunhengdexunifuwiqishilijiagou2.PNG)

5.The VIM signals the load balancer to redistribute the workload based on pre-defined thresholds.
  VIM 给负载均衡器发信号，让它根据预先定义的阈值重新分配工作负载。
6.The load balancer initiates the live VM migration program to move the virtual servers.
  负载均衡器启动 VM 在线迁移程序来移动虚拟服务器。
7.Live VM migration moves the selected virtual servers from one physical host to another.
  VM 在线迁移把选中的虚拟服务器从一台物理主机移到另一台物理主机。

![负载均衡的虚拟服务器实例架构 3](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/fuzaijunhengdexunifuwiqishilijiagou3.PNG)

8.The workload is balanced across the physical servers in the cluster.
  集群中的物理服务器之间的工作负载是均衡的。
9.The capacity watchdog continues to monitor the workload and resource consumption.
  容量看门狗继续监控工作负载和资源消耗。

## NON-DISRUPTIVE SERVICE RELOCATION ARCHITECTURE 不中断服务重定位架构

A **non-disruptive service relocation architecture** establish a system by which a *predefined event triggers* the duplication or migration of a cloud service implementation at runtime, thereby avoiding any disruption.
**不中断服务重定位架构** 是这样的一个系统，通过这个系统，*预先定义的时间触发* 云服务实现的运行时复制或迁移，因而避免了终端。

![不中断服务重定位架构 1](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/buzhongduanfuwuchongdingweijiagou1.PNG)

1. The automated scaling listener monitors the workload for a cloud service.
  自动伸缩监听器监控云服务的工作负载。
2. The cloud service’s predefined threshold is reached as the workload increases.
  工作负载增加，达到云服务预先设定的阈值，
3. causing the automated scaling listener to signal the VIM to initiate relocation.
  导致自动伸缩监听器给 VIM 发送重定位信号。
4. The VIM uses the live VM migration program to instruct both the *origin and destination hypervisors* to carry out runtime relocation.
  VIM 用 VM 在线迁移程序指示 *源和目的虚拟机监控器* 执行运行时重定位。

![不中断服务重定位架构 2](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/buzhongduanfuwuchongdingweijiagou2.PNG)

5.A second copy of the virtual server and its hosted cloud service are created via the destination hypervisor on Physical Server B.
通过物理服务器 B 上的目标虚拟机监控器创建了虚拟服务器及其承载的云服务的第二副本。

![不中断服务重定位架构 3](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/buzhongduanfuwuchongdingweijiagou3.PNG)

6.The state of both virtual server instances is synchronized.
  两个虚拟服务器实例的状态是同步的。
7.The first virtual server instance is removed from Physical Server A after cloud service consumer requests are confirmed to be successfully exchanged with the cloud service on Physical Server B.
  当确认云服务用户的请求可以成功地与物理服务器 B 上的云服务通信之后，就从物理服务器 A 上删除第一个虚拟服务器实例。
8.Cloud service consumer requests are now only sent to the cloud service on Physical Server B.
  现在，云服务用户的请求就只被发送到位于物理服务器 B 上的云服务。

## ZERO DOWNTIME ARCHITECTURE 零宕机架构

A **zero downtime architecture** establish a sophisticated failover system，allows virtual servers to be dynamically moved to different physical server hosts, in the event that their ③original physical server host fails.
**零宕机架构** 是一个非常复杂的故障转移系统，在虚拟服务器原始的物理服务器主机失效时，允许它们动态地迁移到其他物理服务器主机上。

Multiple physical servers are assembled into a group that is ①controlled by a *fault tolerance system* capable of ②switching activity from one physical server to another, without interruption.
多个物理服务器汇聚成一组，由 *容错系统* 控制，而容错系统具有把活动从一台物理服务器切换到另一台却不引起中断的能力。
The **live VM migration** component is typically a core part of this form of high availability cloud architecture.
**VM 在线迁移** 组件通常是这种形式的高可用云架构的核心部分。
All virtual servers are stored on a **shared volume** so that other physical server hosts in the same group can access their files.
所有的虚拟服务器都存储在 **共享的介质** 上，这样同一组中的其他物理服务器主机就能够访问它们的文件。

![零宕机架构](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/lingdangjijiagou.PNG)

Physical Server A fails triggering the live VM migration program to dynamically move Virtual Server A to Physical Server B.
物理服务器 A 故障，引发 VM 在线迁移程序动态地把虚拟服务器 A 迁移到物理服务器 B 上。

## CLOUD BALANCING ARCHITECTURE 云负载均衡架构

The **cloud balancing architecture** establishes a specialized architectural model in which IT resources can be load-balanced across multiple clouds.
**云负载均衡架构** 是一个特殊的架构模型，借助这个模型，IT 资源可以在多个云之间进行负载均衡。

The cross-cloud balancing of cloud service consumer requests can help:
云服务用户请求的跨云负载均衡可以帮助：

- **improve the performance and scalability of IT resources**
  **提高 IT 资源的性能和可扩展性**
- **increase the availability and reliability of IT resources**
  **增加 IT 资源的可用性和可靠性**
- **improve load-balancing and IT resource optimization**
  **改进负载均衡和 IT 资源优化**

Cloud balancing functionality is primarily based on the combination of the **automated scaling listener** and **failover system mechanisms**.
云负载均衡功能主要建立在 **自动伸缩监听器** 和 **故障转移系统** 机制结合的基础上。

- Automated scaling listener *redirects* cloud service consumer requests to one of several redundant IT resource implementations.
  自动伸缩监听器把云服务用户的请求 *重定向* 到几个冗余的 IT 资源实现中的一个。
- Failover system mechanisms ensures that redundant IT resources are capable of cross-cloud failover in the event of a failure within an IT resource or its underlying hosting environment.
  故障转移系统保证在 IT 资源内或其底层的承载环境出现故障时，冗余的 IT 资源能够进行跨云的负载均衡。

Need  manual synchronization of cross-cloud IT resource implementations or use the *resource replication* mechanism to automate the synchronization.
如果跨云的 IT 资源实现不能手动同步，可能就需要使用 *资源复制* 机制进行自动同步。

![云负载均衡架构](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/yunfuzaijunhengjiagou.PNG)

1. An automated scaling listener controls the cloud balancing process by ①routing cloud service consumer requests to redundant implementations of Cloud Service A distributed across multiple clouds.
  一个自动伸缩监听器控制云资源均衡的过程，这需要把云服务用户的请求路由到分布在多个云的云服务 A 的冗余实现上。
2. The failover system instills resiliency增加弹性 within this architecture by providing cross-cloud failover.
  故障转移系统通过提供跨云的故障转移来增加这个架构的弹性。

## RESOURCE RESERVATION ARCHITECTURE 资源预留架构

The **resource constraint** is condition that occurs when two or more cloud consumers have been allocated to share an IT resource that does not have the capacity to accommodate the total processing requirements of the cloud consumers. Cconcurrent access can lead to a runtime exception condition.
根据 IT 资源共享使用的设计方式以及它们可用的容量等级，并发访问可能会导致运行时异常情况，这称为 **资源受限**。

Nested and sibling resource pools introduce the notion of **resource borrowing**, whereby one pool can temporarily borrow IT resources from other pools.
嵌套的或兄弟资源池引入了 **资源借用** 的概念，也就是一个资源池可以临时从其他资源池借用 IT 资源。
A runtime conflict can be triggered when the borrowed IT resource is not returned due to prolonged usage by the cloud service consumer that is borrowing it.
当借用该 IT 资源的云服务用户拖延了使用时间而没有归还借用的 IT 资源时，就会引发运行时冲突。

The **resource reservation architecture** establishes a system, one of the following is set aside *exclusively* for a given cloud consumer:
**资源预留架构** 建立了一个系统，*专门* 为给定的云用户保留下述的某种资源：

- single IT resource 单个 IT 资源
- portion of an IT resource 一个 IT 资源的一部分
- multiple IT resources 多个 IT 资源

This protects cloud consumers from each other by avoiding the aforementioned **resource constraint** and **resource borrowing** conditions.
这就避免了前述的 **资源受限** 和 **资源借用** 情况，从而使云用户免受互相的影响。

![资源预留架构 1](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/ziyuanyuliujiagou1.PNG)

1.A physical resource group is created.
  创建物理资源组。
2.from which a parent resource pool is created as per the resource pooling architecture.
  根据资源池的架构，在资源组中创建父资源池。
3.Two smaller child pools are created from the parent resource pool, and resource limits are defined using the resource management system.
  从父资源池创建出两个较小的子池。
4.Cloud consumers are provided with access to their own exclusive resource pools.
  向云用户提供对它们专有资源池的访问权限。

![资源预留架构 2](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/ziyuanyuliujiagou2.PNG)

5.An increase in requests from Cloud Consumer A results in more IT resources being allocated to that cloud consumer.
  来自云用户 A 的请求增加，导致给改该用户分配更多的 IT 资源。
6.Meaning some IT resources need to be borrowed from Pool 2. The amount of borrowed IT resources is confined by the resource limit that was defined in Step 3, to ensure that Cloud Consumer B will not face any resource constraints.
  这意味着要从池 2 中借用一些 IT 资源。借用的 IT 资源量受第 3 步中定义的资源限度的制约，这样做是为了保证云用户 B 不会出现资源受限的情况。

![资源预留架构 3](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/ziyuanyuliujiagou3.PNG)

6.Cloud Consumer B now imposes more requests and usage demands and may soon need to utilize all available IT resources in the pool.
  现在，云用户 B 发起了更多的请求和使用需求，可能很快就要用掉池中所有可用的 IT 资源了。
7.The resource management system forces Pool 1 to release the IT resources and move them back to Pool 2 to become available for Cloud Consumer B.
  资源管理系统迫使池 1 释放它借用的 IT 资源并移回池 2 中，使得云用户 B 可以使用。

The resource management system mechanism is used to *define* the usage thresholds for individual IT resources and resource pools.
资源管理系统机制来 *定义* 对每个 IT 资源和资源池的使用阈值。
*Reservations lock* the amount of IT resources that each pool needs to keep.
*预留锁定* 每个池需要保留的 IT 资源量。

## DYNAMIC FAILURE DETECTION AND RECOVERY ARCHITECTURE 动态故障检测与恢复架构

The **dynamic failure detection and recovery architecture** is establishes a *resilient* watchdog system to **monitor and respond** to a wide range of pre-defined failure scenarios.
**动态故障检测和恢复架构** 建立起了一个 *弹性的* 看门狗系统，以 *监控* 范围广泛的预先定义的故障场景，并对之作出 *响应*。
This system *notifies* and *escalates* the failure conditions that it **cannot** automatically resolve itself.
对于自己 **不能** 自动解决的故障情况，该系统会 *发出通知*，并作 *升级处理*。
It relies on the **intelligent watchdog monitor** to actively track IT resources and take pre-defined actions in response to pre-defined events.
它依赖于一个特殊的云使用监控器，称为 **智能看门狗监控器**，主动地追踪 IT 资源，对预先定义的事件采取预先定义的措施。

![动态故障检测与恢复架构 1](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/dongtaiguzhangjianceyuhuifujiagou1.PNG)

1. The intelligent watchdog monitor keeps track of cloud consumer requests.
  智能看门狗监控器记录云用户的请求。
2. and detects that a cloud service has failed.
  检测到云服务失效了。

![动态故障检测与恢复架构 2](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/dongtaiguzhangjianceyuhuifujiagou2.PNG)

3.The intelligent watchdog monitor notifies the watchdog system.
  智能看门狗监控器通知看门狗系统，
4.which restores the cloud service based on pre-defined policies. The cloud service resumes its runtime operation.
  后者会根据预先定义的策略恢复该云服务。云服务继续它的运行时操作。

The resilient watchdog system performs the following five core functions:
弹性看门狗系统执行以下五个核心功能：

- **Watching 监视**
- **deciding upon an event 基于事件做决定**
- **acting upon an event 对事件作出行动**
- **Reporting 报告**
- **Escalating 升级**

Some of the actions the intelligent watchdog monitor commonly takes to escalate an issue include:
智能看门狗监控器升级一个问题的处理最常采用的措施包括：

- running a batch file 运行一个批处理文件
- sending a console message 发送一个控制台消息
- sending a text message 发送一条短信消息
- sending an email message 发送一封电子邮件信息
- sending an SNMP trap 发送一个 SNMP 陷阱
- logging a ticket 记录一个通知单

## BARE-METAL PROVISIONING ARCHITECTURE 裸机供给架构

The **bare-metal servers** is physical servers that do not have pre-installed operating systems or any other software.
**裸机服务器** 是指没有预装操作系统或其他任何软件的物理服务器。

A **bare-metal provisioning architecture** establishes a system that utilizes this feature with specialized service agents, which are used to discover and effectively provision entire operating systems remotely.
**裸机供给架构** 建立起的系统利用了这个特性以及特殊的服务代理，后者用来发现并有效地远程提供整个操作系统。

Bare-metal provisioning system provides an auto-deployment feature, by using:
裸机供给系统用下面的组件来解决上述问题：

- Discovery Agent 发现代理
- Deployment Agent 部署代理
- Discovery Section 发现区
- Management Loader 管理加载器
- Deployment Component 部署组件

![裸机供给架构 1](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/luojigongjijiagou1.PNG)

1. The cloud consumer connects to the deployment solution
  云用户连接到部署解决方案，
2. to perform a search using the discovery agent.
  用发现代理进行搜索。
3. The available physical servers are shown to the cloud consumer.
  可用的物理服务器展现给云用户。

![裸机供给架构 2](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/luojigongjijiagou2.PNG)

4.The cloud consumer selects a physical server to provision.
  云用户选择一个物理服务器来使用。
5.The deployment agent is loaded to the physical server’s RAM via the remote management system.
  通过远程管理系统，部署代理被加载到该物理服务器的 RAM 中。
6.The cloud consumer selects an operating system and method of configuration via the deployment solution.
  通过部署解决方案，云用户选择一种操作系统和配置方法。
7.The operating system is installed and the server becomes operational.
  操作系统安装完成，服务器可以运行了。
  
## RAPID PROVISIONING ARCHITECTURE 快速供给架构

The **rapid provisioning architecture** establishes a system that automates the provisioning of a wide range of IT resources, either individually or as a collective. 
**快速供给架构** 建立的系统将大范围的 IT 资源供给进行了自动化，这些 IT 资源可以是单个的，也可以是联合起来的。

The underlying technology architecture for rapid IT resource provisioning can be sophisticated and complex, and relies on:
快速 IT 资源供给的底层技术架构可以是非常精密和复杂的，它依赖于以下组件组成的系统。

- automated provisioning program 自动供给程序
- rapid provisioning engine 快速供给引擎
- scripts and templates for on-demand provisioning 按需供给的脚本和模板

![快速供给架构](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/kuaisugongjijiagou.PNG)

1. A cloud resource administrator requests a new cloud service through the self-service portal.
  云资源管理员通过自助服务入口请求一个新的云服务。
2. The self-service portal passes the request to the automated service provisioning program installed on the virtual server.
  自助服务入口把请求传递给安装在虚拟服务器上的自动化服务供给程序，
3. which passes the necessary tasks to be performed to the rapid provisioning engine.
  这个程序把需要执行的任务传递给快速供给引擎。
4. The rapid provisioning engine announces when the new cloud service is ready.
  当新的云服务准备好时，快速供给引擎发出通知。
5. The automated service provisioning program finalizes and publishes the cloud service on the usage and administration portal for cloud consumer access.
  自动化服务供给程序完成这个过程，在使用与管理入口上把云服务发布出去供云用户使用。

- **Server Templates 服务器模板**
    - Templates of *virtual image files* that are used to automate the instantiation of new *virtual servers*.  *虚拟影像文件* 模板，用来自动化新 *虚拟服务器* 的实例。
- **Server Images 服务器映像**
    - These images are similar to virtual server templates, but are used to provision *physical servers*.  这些映像类似于虚拟服务器模板，但是用户供给 *物理服务器*。
- **Application Packages 应用包**
    - Collections of applications and other software that are packaged for automated deployment.  打包用于自动部署的各种应用以及其他一些软件。
- **Application Packager 应用打包程序**
    - The software used to create application packages.  用来创建应用包的软件。
- **Custom Scripts 自定义脚本**
    - Scripts that automate administrative tasks, as part of an intelligent automation engine.  自动化管理任务的脚本，作为智能自动化引擎的一部分。
- **Sequence Manager 顺序管理器**
    - A program that organizes sequences of automated provisioning tasks.  组织自动化供给任务顺序的程序。
- **Sequence Logger 顺序日志记录器**
    - A component that logs the execution of automated provisioning task sequences.  日志记录自动化供给任务顺序的组件。
 - **Operating System Baseline 操作系统基准**
    - A configuration template that is applied after the operating system is installed, to quickly prepare it for usage.  在操作系统安装好之后，应用这个配置模板快速准备好操作系统供用户使用。
 - **Application Configuration Baseline 应用配置基准**
    - A configuration template with the settings and environmental parameters that are needed to prepare new applications for use.  一个配置模板，带有准备新应用供使用时需要的设置和环境参数。
 - **Deployment Data Store 部署数据存储**
    - The repository that stores virtual images, templates, scripts, baseline configurations, and other related data.  存储虚拟映像、模板、脚本、基准配置和其他相关数据的库。

The following step-by-step description helps provide some insight into the inner workings of a rapid provisioning engine:
为了帮助对快速供给引擎内部工作原理的理解，下面将按步骤描述其工作过程，其中还包括了一些之前列出的系统组件：

1. A cloud consumer requests a new server through the self-service portal.
  云用户通过自助服务入口请求一个新的服务器。
2. The sequence manager forwards the request to the deployment engine for the preparation of an operating system.
  顺序管理器把请求转发给部署引擎，让它准备好操作系统。
3. The deployment engine uses the virtual server templates for provisioning if the request is for a virtual server. Otherwise, the deployment engine sends the request to provision a physical server.
  如果请求的是虚拟服务器，部署引擎就使用虚拟服务器模板来做供给。否则，部署引擎就发送请求，请求供给一个物理服务器。
4. The pre-defined image for the requested type of operating system is used for the provisioning of the operating system, if available. Otherwise, the regular deployment process is executed to install the operating system.
  如果可用，就使用所请求类型的操作系统预先定义的映像来提供该操作系统。否则，就要执行常规的部署处理来安装该操作系统。
5. The deployment engine informs the sequence manager when the operating system is ready.
  当操作系统准备好之后，部署引擎就通知顺序管理器。
6. The sequence manager updates and sends the logs to the sequence logger for storage.
  顺序管理器更新日志并发送到顺序日志记录器，存储起来。
7. The sequence manager requests that the deployment engine apply the operating system baseline to the provisioned operating system.
  顺序管理器请求部署引擎对要提供的操作系统应用操作系统基准。
8. The deployment engine applies the requested operating system baseline.
  部署引擎应用所请求的操作系统基准。
9. The deployment engine informs the sequence manager that the operating system baseline has been applied.
  部署引擎通知顺序管理器操作系统基准已经应用完成。
10. The sequence manager updates and sends the logs of completed steps to the sequence logger for storage.
  顺序管理器更新和发送已经完成步骤的日志到顺序日志记录器并存储起来。
11. The sequence manager requests that the deployment engine install the applications.
  顺序管理器请求部署引擎安装应用程序。
12. The deployment engine deploys the applications on the provisioned server.
  部署引擎在要提供的服务器上安装应用程序。
13. The deployment engine informs the sequence manager that the applications have been installed.
  部署引擎通知顺序管理器应用已经安装完成。
14. The sequence manager updates and sends the logs of completed steps to the sequence logger for storage.
  顺序管理器更新和发送已经完成步骤的日志到顺序日志记录器并存储起来。
15. The sequence manager requests that the deployment engine apply the application’s configuration baseline.
  顺序管理器请求部署引擎实施应用程序的配置基准。
16. The deployment engine applies the configuration baseline.
  部署引擎实施配置基准。
17. The deployment engine informs the sequence manager that the configuration baseline has been applied.
  部署引擎通知顺序管理器配置基准已经实施完毕。
18. The sequence manager updates and sends the logs of completed steps to the sequence logger for storage.
  顺序管理器更新和发送已经完成步骤的日志到顺序日志记录器并存储起来。

## STORAGE WORKLOAD MANAGEMENT ARCHITECTURE 存储负载管理架构

**Over-utilized cloud storage devices** increase the workload on the storage controller.
**过渡使用云存储设备** 增加了存储控制器的工作负载。
**Under-utilized cloud storage devices** lost processing and storage capacity potential, wasteful.
**对云存储设备使用过低** 是一种浪费，损失了处理和存储容量的潜能。

![LUN 迁移](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/lunqianyi.PNG)

**LUN migration** is a specialized storage program that is used to move LUNs from one storage device to another without interruption, while remaining transparent to cloud consumers.
**LUN 迁移** 是一种特殊的存储程序，用来把 LUN 从一个存储设备移动到另一个上而无需终端，同时还对云用户保持透明。

**Storage workload management architecture** enables LUNs to be evenly distributed across available cloud storage devices, while a storage capacity system is established to ensure that runtime workloads are evenly distributed across the LUNs.
**存储负载管理架构** 使得 LUN 可以均匀地分布在可用的云存储设备上，而存储容量系统则用来确保运行时工作负载均匀地分布在 LUN 上。

![存储负载管理架构 1](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/cunchufuzaiguanlijiagou1.PNG)

1. The storage capacity system and storage capacity monitor are configured to survey three storage devices in realtime, whose workload and capacity thresholds are pre-defined. 
  存储容量系统和存储容量监控器被配置成实时地检查三个存储设备，这些设备的工作负载和容量阈值是预先定义好的。
2. The storage capacity monitor determines that the workload on Storage 1 is reaching its threshold.
  存储容量监控器发现存储 1 上的工作负载达到了它的阈值。

![存储负载管理架构 2](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/cunchufuzaiguanlijiagou2.PNG)

3.The storage capacity monitor informs the storage capacity system that Storage 1 is over-utilized.
  存储容量监控器通知存储容量系统存储 1 使用过度了。
4.The storage capacity system identifies the LUNs to be moved from Storage 1.
  存储容量系统确认出要从存储 1 中移出的 LUN。
  
![存储负载管理架构 3](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/cunchufuzaiguanlijiagou3.PNG)

5.The storage capacity system calls for LUN migration to move some of the LUNs from Storage 1 to the other two storage devices.
  存储容量系统调用 LUN 迁移程序，把一些 LUN 从存储 1 移动到另外两个存储设备。
6.LUN migration transitions LUNs to Storage 2 and 3 to balance the workload.
  LUN 迁移把 LUN 迁移到存储 2 和 3，平衡了工作负载。
