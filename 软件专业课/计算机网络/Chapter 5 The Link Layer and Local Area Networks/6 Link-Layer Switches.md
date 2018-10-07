[toc]

## Forwarding and Filtering 交换机转发和过滤

**Filtering** is the switch function that determines whether a frame should be forwarded to some interface or should just be dropped.
**过滤** 是交换机决定一个帧是应该转发到某个接口还是应当将其丢弃的功能。

**Forwarding** is the switch function that determines the interfaces to which a frame should be directed, and then moves the frame to those interfaces.
**转发** 是决定一个帧应该被导向哪个接口，并把该帧接口移动到这些接口的交换机功能。

|Function<br />功能|Hubs<br />集线器|Routers<br />路由器|Switches<br />交换机|
|-|-|-|-|
|Traffic isolation<br />流量隔离|No|Yes|Yes|
|Plug and play<br />即插即用|Yes|No|Yes|
|Optimal routing<br />优化选路|No|Yes|No|
|Cut-through<br />直通交换|Yes|No|Yes|
