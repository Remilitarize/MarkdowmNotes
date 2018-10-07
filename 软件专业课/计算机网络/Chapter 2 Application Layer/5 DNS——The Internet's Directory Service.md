[toc]

One identifier for a host is its **hostname**.
主机的一种识别方法是用它的 **主机名**。

Hosts are also identified by so-called **IP address**.
主机也可以使用所谓的 **IP 地址** 进行识别。

## Services Provided by DNS DNS 提供的服务

The Internet's **domain name system(DNS)** is a directory service that translates hostname to IP address.
**域名系统** 是进行主机名到 IP 地址转换的目录服务。

- A distributed database implimented in **a hierarchy of DNS servers**.
  一个由 **分层的 DNS 服务器** 实现的分布式数据库。
- An application-layer protocol taht allows hosts to query the distributed database.
  一个允许主机查询分布式数据库的应用层协议。

DNS provides a few other important services in addition to translating hostnames to IP address:
除了进行主机名到 IP 地址的转换外，DNS 还提供了一些重要的服务：

- **Host aliasing 主机别名**
- **Mail server aliasing 邮件服务器别名**
- **Load distribution 负载分配**

## Overview of How DNS Works DNS 工作机理概述

The problems with a centralized design include: 这种集中式设计的问题包括：

- **A single point of failure 单点故障**
- **Traffic volumn 通信容量**
- **Distant centralized database 远距离的集中式数据库**
- **Maintenance 维护**

### A Distributed, Hierarchical Database 分布式、层次数据库

![层次数据库](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/DistributedHierarchyDatabase.png)

- **Root DNS servers 根 DNS 服务器**
	- In the Internet there are 13 root DNS servers. 在因特网上有 13 个根 DNS 服务器。
- **Top-level domain(TLD) servers 顶级域（TLD）服务器**
	- These servers are responsible for **top-level domains**. 这些服务器负责 **顶级域名**。
- **Authoritative DNS servers 权威 DNS 服务器**
	- Every organization with publicly accessible hosts on the Internet must provide publicly accessible DNS records that map the names of those hosts to IP addresses.
	  在因特网上具有公共可访问主机的每一个组织机构必须提供公共可访问的 DNS 记录，这些记录将这些主机的名字映射为 IP 地址。
	- An organization can choose to implement its own **authoritative DNS server** to hold these records.
	  组织机构可以选择实现它自己的 **权威 DNS 服务器** 来保持这些记录、
- **Local DNS server 本地 DNS 服务器**
	- A local DNS server does not strictly belong to the hierarchy of servers but is nevertheless central to the DNS architecture.
	  本地 DNS 服务器严格来说并不属于 DNS 服务器的层次结构，但它对 DNS 层次结构是很重要的。
	- Each ISP has a local DNS server (also called a default name server).
	  每个 ISP 都有一台本地 DNS 服务器（也叫默认名字服务器）。

**Iterative query 迭代查询**

![Recursive Query](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/Recursivequery.png)

**Recursive query 递归查询**

![Iterative Query](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/IterativeQuery.png)

### DNS Caching DNS 缓存

DNS extensively exploits DNS caching in order to improve the delay performance and to reduce the number of DNS messages recocheting around the Internet.
为了改善时延性能并减少在因特网上到处传输的 DNS 报文数量，DNS 广泛使用了缓存技术。

The idea behind DNS caching: DNS 缓存原理：

- In a query chain, when a DNS server receives a DNS reply, it can cache the mapping in its local memory.
  在请求链中，当一个 DNS 服务器接收一个 DNS 回答时，DNS 服务器能将回答中的信息缓存在本地存储器。

## DNS Records and Messages DNS 记录和报文

The DNS servers that together implement the DNS distributed database store **resource records(RRs)**, including RRs that provide hostname-to-IP address mappings.
实现 DNS 分布式数据库的所有 DNS 服务器共同存储着 **资源记录**，RR 提供了主机名到 IP 地址的映射。

A resource record is a four-tuple that contains the following fields: 资源记录是一个包含了下列字段的 4 元组：

- (Name, Value, Type, TTL)
- TTL is the time of the resource record. TTL 是该记录的生存时间。
- The meaning of Name and Value depend on Type. Name 和 Value 的值取决于 Type。
	- If Type = **A**, then Name is a **hostname** and Value is the **IP address** for the hostname.
	  如果 Type = **A**，则 Name 是 **主机名**，Value 是该主机名的 **IP 地址**。
	- If Type = **NS**, then Name is a **domain** and Value is the hostname of an **authoritative DNS server** that knows how to obtain the IP addresses for hosts in the domain.
	  如果 Type = **NS**，则 Name 是 **域**，而 Value 是知道如何获取该域中主机 IP 地址的 **权威 DNS 服务器** 的主机名。
	- If Type = **CNAME**, then Value is a **cononical hostname** for the **alias** hostname Name.
	  如果 Type = **CNAME**，则 Value 是 **别名** 为 Name 的主机对应的 **规范主机名**。
	- If Type = **MX**, then Value is the **cononical name of a mail server** that has an **alias** hostname Name.
	  如果 Type = **MX**，则 Value 是 **别名** 为 Name 的 **邮件服务器的规范主机名**。

### DNS Message DNS 报文

- **DNS query message DNS 查询报文**
- **DNS reply message DNS 回答报文**

<table border = "1">
	<tr>
		<td>Identification<br />标识符</td><td>Flags<br />标志</td>
	</tr>
	<tr>
		<td>Number of questions<br />问题数</td><td>Number of answer RRs<br />回答 RR 数</td>
	</tr>
	<tr>
		<td colspan = "2">Questions(variable number of questions)<br />问题（问题的变量数）</td>
	</tr>
	<tr>
		<td colspan = "2">Answer(variable number of resource records)<br />回答（资源记录的变量数）</td>
	</tr>
	<tr>
		<td colspan = "2">Authority(variable number of resource records)<br />权威（资源记录的变量数）</td>
	</tr>
		<td colspan = "2">Additional information(variable number of resource records)<br />附加信息（资源记录的变量数）</td>
	</tr>
</table>

- The first 12 bytes is the **header section**. 前 12 个字节是 **首部区域**。
- The **question section** contains information about the query that is being made.
  **问题区域** 包含着正在进行的查询信息。
- In a reply from a DNS server, the **answer section** contains the resource records for the name that was originally queried.
  在来自 DNS 服务器的回答报文中，**回答区域** 包含了对最初请求的名字的资源记录。
- The **authority section** contains records of other authoritative servers.
  **权威区域** 包含了其他权威 DNS 服务器的记录。
- The **additional section** contains other helpful records.
  **附加区域** 包含了其他一些有帮助的记录。

### Inserting Records into the DNS Database 在 DNS 数据库中插入记录

略
