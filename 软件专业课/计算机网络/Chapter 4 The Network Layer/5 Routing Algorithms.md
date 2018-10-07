[toc]

- Typically a host is attached directly to one router, the **default router** for the host (also called the **first-hop router** for the host).
  一台主机通常直接与一台路由器相连接，该路由器即为该主机的 **默认路由器**，又称为该主机的 **第一跳路由器**。
- The default router of the source host as the **source router**. 源主机的默认路由器称为 **源路由器**。
- The default router of the destination host as the **destination router**. 目的主机的默认路由器称为 **目的路由器**。

The **least-cost problem** is clear: Find a path between the source and destination that has least cost.
**最低费用路径** 是显而易见的：找出源和目的之间具有最低费用的一条路径。

- Global routing algorithm 全局选路算法
- Decentralized routing algorithm 分布式选路算法

## The Link-State(LS) Routing Algorithm 链路状态选路算法

Global routing algorithm 全局选路算法

> Dijkstra Algorithm 迪杰斯特拉算法

- D(v): cost of the least-cost path from the source node to destination v as of this iteration of the algorithm.
  D(v)：随着算法进行本次迭代，从源节点到目的节点 v 的最低费用路径的费用。
- p(v): previous node (neighbor of v) along the current least-cost path from the source to v.
  p(v)：从源节点到目的节点 v 沿着当前最低费用路径的前一节点（v 的邻居）。
- N': subset of nodes; v is in N' if the least-cost path from the source to v is definitively known.
  N'：节点子集，如果从源节点到目的节点 v 的最低费用路径已确知，v 在 N' 中。

![Routing Algorithm](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/RoutingAlgorithm.png)

|N'|D(v),p(v)|D(w),p(w)|D(x),p(x)|D(y),p(y)|D(z),p(z)|
|-|-|-|-|-|-|
|u|2, u|5, u|<span style="text-decoration:underline;">1, u</span>|&infin;|&infin;|
|u,x|<span style="text-decoration:underline;">2, u</span>|4, x|&nbsp;|<span style="text-decoration:underline;">2, x</span>|&infin;|
|u,x,v|&nbsp;|3, y|&nbsp;|<span style="text-decoration:underline;">2, x</span>|4. y|
|u,x,v,y|&nbsp;|<span style="text-decoration:underline;">3, y</span>|&nbsp;|&nbsp;|4, y|
|u,x,v,y,w|&nbsp;|&nbsp;|&nbsp;|&nbsp;|<span style="text-decoration:underline;">4, y</span>|
|u,x,v,y,w,z|&nbsp;|&nbsp;|&nbsp;|&nbsp;|&nbsp;|

![Dijkstra](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/Dijkstra.png)

u's routing table  u 的路由表

|Dest. net|Next hop|
|-|-|
|u|-|
|v|v|
|w|x|
|x|x|
|y|x|
|z|x|

(Simplified) （简化后）

|Dest. net|Next hop|
|-|-|
|u|-|
|v|v|
|*|x|

## The Distance-Vector(DV) Routing Algorithm 距离向量选路算法

The **distance-vector** algorithm is iterative, asynchronous, and distributed.
**距离向量** 算法是一种迭代的、异步的和分布式的算法。

The topology of a network shown as below. Using DV routing algorithm to calculate the routing table in the node C. The vectors arrive to node C as below:
B(4, 0, 8, 12, 6, 2)
D(13, 10, 6, 0, 9, 10)
E(7, 6, 3, 9, 0, 14)
The delays measured from C to B, D, E are 4, 2 and 3 separately. Update router C's route table please.

d<sub>C</sub>(A) = min{c(C, B) + d<sub>B</sub>(A), c(C, D) + d<sub>D</sub>(A), c(C, E) + d<sub>E</sub>(A)}
                 = min{4 + 4, 2 + 13, 3 + 7} = 8
P<sub>C</sub>(A) = B

d<sub>C</sub>(B) = min{c(C, B) + d<sub>B</sub>(B), c(C, D) + d<sub>D</sub>(B), c(C, E) + d<sub>E</sub>(B)}
                 = min{4 + 0, 2 + 10, 3 + 6} = 4
P<sub>C</sub>(B) = B

d<sub>C</sub>(D) = min{c(C, B) + d<sub>B</sub>(D), c(C, D) + d<sub>D</sub>(D), c(C, E) + d<sub>E</sub>(D)}
                 = min{4 + 12, 2 + 0, 3 + 9} = 2
P<sub>C</sub>(D) = D

d<sub>C</sub>(E) = min{c(C, B) + d<sub>B</sub>(E), c(C, D) + d<sub>D</sub>(E), c(C, E) + d<sub>E</sub>(E)}
                 = min{4 + 6, 2 + 9, 3 + 0} = 3
P<sub>C</sub>(E) = E

d<sub>C</sub>(F) = min{c(C, B) + d<sub>B</sub>(F), c(C, D) + d<sub>D</sub>(F), c(C, E) + d<sub>E</sub>(F)}
                 = min{4 + 2, 2 + 10, 3 + 14} = 6
P<sub>C</sub>(F) = B

C's routing table  C 的路由表

|Dest. net|Next hop|
|-|-|
|A|B|
|B|B|
|C|-|
|D|D|
|E|E|
|F|B|

## Hierarchical Routing 层次选路

Scale and administrative autonomy problems can be solved by organizing routers into **autonomous system(ASs)**.
规模问题和管理自治问题都可以通过将路由器组织进 **自治系统** 来解决。

The routing algorithm running within an autonomous system is called an **intraautonomous system routing protocol**.
在一个自治系统内运行的选路算法叫做 **自治系统内部选路协议**。

One or more of the routers in an AS will have the addded task of being responsible for forwarding packets to destination outside the AS, which routers are called **gateway routers**.
在一个 AS 内的一台或多态路由器将有另外的任务，来负责向本 AS 之外的目的地转发分组，这些路由器被称为 **网关路由器**。
