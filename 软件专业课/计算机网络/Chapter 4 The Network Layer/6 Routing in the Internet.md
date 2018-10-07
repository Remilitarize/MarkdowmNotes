[toc]

## Intra-AS Routing in the Internet: RIP 因特网中自治系统内部选路：RIP

Intra-AS routing protocols are also known as **interior gateway protocols**.
AS 内部选路协议又称为 **内部网关协议**。

- Routing Information Protocol(RIP) 选路信息协议
- Open Shortest Path First(OSPF) 开放最短路径优先

RIP is a distance-vector protocol that operates in a manner very close to the idealized DV protocol.
RIP 是一种距离向量协议，其运行方式很像理想化 DV 协议。

## Intra-AS Routing in the Internet: OSPF 因特网中 AS 内部选路：OSPF

At its heart, OSPF is a link-state protocol that uses flooding of link-state information and a Dijkstra least-cost path algorithm.
OSPF 的核心就是一个使用洪泛链路状态信息的链路状态协议和一个 Dijkstra 最低费用路径算法。

## Inter-AS Routing: BGP 自治系统间的选路：BGP

The **Border Gateway Protocol** version 4 is the de facto standard inter-AS protocol in today's Internet.
**边界网关协议** 版本 4 是当今因特网中域间选路协议事实上的标准。
