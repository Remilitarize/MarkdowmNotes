[toc]

## REMOTE ADMINISTRATION SYSTEM 远程管理系统

The **remote administration system** mechanism provides *tools* and *user-interfaces* for **external** cloud resource administrators to configure and administer cloud-based IT resource.
**远城管理系体** 向 **外部** 云资源管理者提供 *工具* 和 *用户界面* 来配置并管理基于云的 IT 资源。

![远程管理系统](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/yuanchengguanlixitong.PNG)

The remote administration system abstracts underlying management systems to expose and centralize administration controls to external cloud resource administrators.
远程管理系统将底层管理系统抽象为公开的集中式管理控制，并提供给外部云资源管理者。
The system provides a customizable user console, while programmatically interfacing with underlying management systems via their APIs.
该系统提供定制的用户控制台，通过底层管理系统的 API 实现编程交互。

![管理系统架构](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/guanlixitongjiagou.PNG)

The following are the two primary types of portals that are created with the remote administration system:
远程管理系统主要创建如下两种类型的入口：

- **Usage and Administration Portal 使用与管理入口**
    - A general purpose portal that centralizes management controls to different cloud-based IT resources and can further provide IT resource usage reports.
      一个通用入口，集中管理不同的基于云的 IT 资源，并提供 IT 资源使用报告。

![使用与管理入口](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/shiyongyuguanlirukou.PNG)

- **Self-Service Portal 自助服务入口**
    - This is essentially a shopping portal that allows cloud consumers to search an up-to-date list of cloud services and IT resources that are available from a cloud provider (usually for lease).
      该入口本质上是一个购买门户，它允许云用户搜索云提供者提供的最新云服务和 IT 资源（通常是租赁的）列表。
    - The cloud consumer submits its chosen items to the cloud provider for provisioning.
      云用户向云提供者提交其选项进行资源调配。

![自助服务入口](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/zizhufuwurukou.PNG)

![远程管理系统 1](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/yuanchengguanlixitong1.PNG)

1. A cloud resource administrator uses the usage and administration portal to configure an already leased virtual server (not shown) to prepare it for hosting.
  云资源管理者通过使用与管理入口对一个已被租用的虚拟服务器（图中未显示）进行配置，以便托管。
2. The cloud resource administrator then uses the self-service portal to select and request the provisioning of a new cloud service.
  云资源管理者通过自助服务入口选择并请求供给一个新的云服务。
3. The cloud resource administrator then accesses the usage and administration portal again to configure the newly provisioned cloud service that is hosted on the virtual server.
  云资源管理者再次访问使用与管理入口，完成对新供给云服务的配置，该云服务托管于上面所提到的虚拟服务器上。
4. Throughout these steps, the remote administration system interacts with the necessary management systems to perform the requested actions.
  通过上述步骤，远程管理系统与必要的管理系统进行交互，实现对请求的处理。

## RESOURCE MANAGEMENT SYSTEM 资源管理系统

The **resource management system** mechanism helps *coordinate* IT resources in response to management actions performed by both cloud consumers and cloud providers.
**资源管理系统** 机制帮助 *协调* IT 资源，以便响应云用户和云提供者执行的管理操作。
Core to this system is the **virtual infrastructure manager(VIM)** that coordinates the server hardware so that virtual server instances can be created from the most expedient underlying physical server.
此系统的核心是 **虚拟基础设施管理器（VIM）**，它用于协调服务器硬件，这样就可以从最合适的底层物理服务创建虚拟服务器实例。

![资源管理系统](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/ziyuanguanlixitong.PNG)

- **Manage 管理**
- **Allocate and release 分配和释放**
- **Coordinate 协调**
- **Enforce usage and security policies 强制执行使用策略与安全规定**
- **Monitor 监控**

![资源管理系统 1](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/ziyuanguanlixitong1.PNG)

1. The cloud consumer's cloud resource administrator accesses a usage and administration portal externally to administer a leased IT resource.
  为了管理一个租用的 IT 资源，云用户的云资源管理器从外部访问使用与管理入口。
2. The cloud provider's cloud resource administrator uses the native user-interface provided by the VIM to perform internal resource management tasks.
  云提供者的云资源管理器使用 VIM 提供的本地用户界面来执行内部资源管理任务。

## SLA MANAGEMENT SYSTEM SLA 管理系统

The **SLA management system** mechanism represents a range of commercially available cloud management products that provide features pertaining to the *administration, collection, storage, reporting and runtime notification of SLA data*.
**SLA 管理系统** 机制代表的是一系列商品化的可用云管理产品，这些产品提供的功能包括：*SLA 数据的管理、收集、存储、报告以及运行时通知*。

![SLA 管理系统](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/slaguanlixitong.PNG)

![SLA 管理系统 1](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/slaguanlixitong1.PNG)

1. A cloud service consumer interacts with a cloud service.
  云服务用户与云服务交互。
2. (a) An SLA monitor intercepts the exchanged messages, evaluates the interaction, and collects relevant runtime data in relation to quality-of-service guarantees defined in the cloud service's SLA. (b) The data collected is stored in a repository.
  (a) SLA 监控器截获交换消息，评估此次交互，收集相关运行时数据。这些数据与定义在云服务 SLA 中的服务质量保证有关。
  (b) 收集到的数据存储在库中。
3. The repository is part of the SLA management system.
  库是 SLA 管理系统的一部分。
4. Queries can be issues and reports can be generated for an external cloud resource administrator via a usage and administration portal.
  通过使用与管理入口，外部云资源管理者可以发出查询和生成报告。
5. Or for an internal cloud resource administrator via the SLA management system's native user-interface.
  或者通过 SLA 管理系统的本地用户界面，内部云资源管理者可以发出查询和生成报告。

## BILLING MANAGEMENT SYSTEM 计费管理系统

The **billing management system** mechanism is dedicated to the **collection and processing** of usage data as it pertains to cloud provider accounting and cloud consumer billing.
**计费管理系统** 机制专门用于 **收集和处理** 使用数据，它涉及云提供者的结算和云用户的计费。

![计费管理系统](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/jifeiguanlixitong.PNG)

Billing arrangements be based on **pre-usage and post-usage payments**.
计费是根据 **使用前支付** 和 **使用后支付** 来安排的。

![计费管理系统 1](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/jifeiguanlixitong1.PNG)

1. A cloud service consumer exchanges messages with a cloud service.
  云服务用户与云服务交互。
2. (a) A pay-per-use monitor keeps track of the usage and collects data relevant to billing, (b) which is forwarded to a repository that is part of the billing management system.
  (a) 按使用付费监控器跟踪使用情况，并收集与计费相关的数据，(b) 然后将数据发送到计费管理系统中的库。
3. The system periodically calculates the consolidated cloud service usage fees and generates an invoice for the cloud consumer.
  系统定期计算综合云服务使用费用，并为云用户生成发票。
4. The invoice may be provided to the cloud consumer through the usage and administration portal.
  发票可以通过使用与管理入口提供给云用户。
