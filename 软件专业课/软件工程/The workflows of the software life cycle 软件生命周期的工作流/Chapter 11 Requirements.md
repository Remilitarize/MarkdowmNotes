[toc]

The Aim of the Requirements Workflow：What must the product be able to do?
需求工作流的目的：产品必须能做什么？

## Determining What the Client Needs 确定客户需要什么

- Misconception 错误概念
	- We must determine what the client wants. 我们必须确定客户想要什么。
- We must determine what the client **needs**. 我们必须确认客户 **需要** 什么。
- The client is the **only source of this information**. 客户是 **信息的唯一来源**。
- The solution: 解决方案
	- Obtain initial information from the client. 从客户获取初始的信息。
	- Use this initial information as input to the Unified Process. 使用初始信息作为输入到统一过程中。
	- Follow the steps of the Unified Process to determine the client’s real needs. 跟着统一过程的步骤确定客户真实需求。

## Overview of the Requirements Workflow 需求流概述

1. Gain an understanding of the **application domain**(or domain, for short). 理解 **应用域**（简称域）
2. Build a **business model**. 建造 **业务模型**。
3. Use the business model to determine the client’s requirements. 使用商业模型确定那个客户需求。
4. **Iterate** the above steps. **迭代** 上述步骤。

### Definitions 定义

- Discovering the client’s requirements. 发现客户需求
	- **Requirements elicitation (or requirements capture) 需求启发（或需求捕获）**
	- Methods include interviews and surveys. 方法包括会谈和调查。
- Refining and extending the initial requirements. 推敲和扩充的过程。
	- **Requirements analysis 需求分析**

## Understanding the Domain 理解应用域

- Every member of the development team must become fully familiar with the application domain.
  开发小组的成员必须熟悉该应用领域。
- Construct a **glossary**. 建立一个 **术语表**。
	- A list of technical words used in the domain, and their meanings.
	  在该领域应用的技术词汇列表和对应的解释。

## Business Model 业务模型

**A business model** is a description of the business processes of an organization.
**业务模型** 是对公司的商业过程进行的描述。

- The business model gives an understanding of the client’s business **as a whole**.
  业务模型是对客户业务一个 **整体** 的理解。

### Interviewing 访谈

The requirements team meet with the client and users to extract all relevant information.
需求小组会见客户和用户并提炼所有关联的信息。

- There are two types of questions: 有两种基本类型的问题：
	- **Close-ended** questions require a specific answer. **受限回答** 的问题要求一个特定的答案。
	- **Open-ended** questions are posed to encourage the person being interviewed to speak out.
	  **自由回答** 的问题则鼓励受访人畅所欲言。
- There are two types of interviews: 有两种基本类型的访谈：
	- In a **structured interview**, specific preplanned questions are asked, frequently **close-ended**.
	  在 **程式化的访谈** 中，提出特定的、预先计划好的、通常是 **受限回答** 的问题。
	- In an **unstructured interview**, questions are posed in response to the answers received, frequently **open-ended**.
	  在 **非程式化的访谈** 中，问题根据受访者的回答而提出，大多数这些问题是 **自由回答** 的。

### Other Techniques 其他技术

- Interviewing is the primary technique. 访谈是主要技术。
- A **questionnaire** is useful when the opinions of hundreds of individuals need to be determined.
  当需要确定上百个人员的意见时， **调查问卷** 技术很有用。
- **Examination of business forms** shows how the client currently does business.
  **检查** 客户在业务上使用的各种 **表格**。
- **Direct observation** of the employees while they perform their duties can be useful.
  **直接观察** 雇员履行职责会很有用。

### Use Cases 用例

A **use case** models an interaction between the software product itself and the users of that software product (actors).
**用例** 为软件产品本身和软件产品的使用者（参与者）之间的交互建立模型。

- An actor is a member of the world **outside** the software product. 参与者是软件产品 **之外** 的成员。
- An actor is **frequently a user** of the software product. 参与者 **经常会是** 软件产品的 **使用者**。
- In general, an actor plays a role with regard to the software product. 通常，参与者扮演与软件产品有关的角色。
 	- As a user 作为使用者
	- As an initiator 作为发起者
	- As someone who plays a critical part in the use case 作为在用例中扮演重要角色的人
- A user of the system can play more than one role. 系统的使用者可以扮演不止一个角色。
- Conversely, one actor can be a participant in multiple use cases. 相反地，一个参与者可以参加多个用例。
- An actor need not be a human being. 参与者不必一定是人。
- A potential problem when identifying actors.  分辨参与者的潜在问题。
	- Overlapping actors. 重叠的参与者。

## Initial Requirements 初始需求

The initial requirements are based on the initial business model.
可基于初始的业务模型提出初始需求。

- There are two categories of requirements. 需求分为两类。
	- A **functional requirement** specifies an action that the software product must be able to perform.
	  **功能性需求** 指定目标产品必须能够执行的行为。
	- A **nonfunctional requirement** specifies properties of the software product itself, such as
	  **非功能性需求** 指定目标产品本身的属性，例如
		- **Platform constraints 平台限制**
		- **Response times 响应时间**
		- **Reliability 可靠性**

- **Functional requirements** are handled as part of **the requirements and analysis workflows**.
  **在需求和分析流** 进行 **功能性需求** 的处理。
- Some **nonfunctional requirements** have to wait until **the design workflow**.
  一些 **非功能性需求** 需要等到 **设计流** 才能处理。

## Initial Understanding of the Domain: MSG Case Study 对应用域的初始理解：MSG 基金实例研究

略

## Initial Business Model: MSG Case Study 初始业务模型：MSG 基金实例研究

略

## Initial Requirements: MSG Case Study 初始需求：MSG 基金实例研究

略

## Continuing the Requirements Workflow: MSG 继续需求流：MSG 基金实例研究

略

## Revising the Requirements: MSG Case Study 修订需求：MSG 基金实例研究

略

## The Test Workflow: MSG Case Study 测试流：MSG 基金实例研究

略

## The Classical Requirements Phase 传统的需求阶段

- There is **no** such thing as "object-oriented requirements". **没有** 像"面向对象的需求"这样的事情。
- The classical approach to requirements： 需求的经典步骤：
	- **Requirements elicitation 需求启发**
	- **Requirements analysis 需求分析**
	- **Construction of a rapid prototype 建造快速原型**
	- **Client and future users experiment with the rapid prototype 客户和未来的用户在快速原型上实验**

## Rapid Prototyping 快速原型开发

- Hastily built ("rapid"). 仓促建立（"快速"）
	- Imperfections can be ignored. 忽略不完美的地方。
- Exhibits only key functionality. 只展示主要功能。
- Emphasis on only what the client sees. 值强队奥客户看到的功能。
- Aim：To provide the client with an understanding of the product. 目的：提供客户对产品的理解。

## Human Factors 人的因素

- The client and intended users must interact with the user interface. 客户和预期的用户必须与用户界面交互。
- **Human-computer interface (HCI) 人机界面**
- Human factors must be taken into account. 必须考虑人类因素。
- Rapid prototype of the HCI of every product is **obligatory**. 每个产品的人机界面的快速原型是 **强制性的**。

## Reusing the Rapid Prototype 重用快速原型

- Reusing a rapid prototype is essentially code-and-fix. 重用快速原型本质上是编码-修补。
- One way to ensure that the rapid prototype is discarded： 确保丢弃快速原型的一种方法：
	- Implement it in a different language from that of the target product. 使用与目标产品不同的语言实现。
- Generated code can be reused. 生成的代码可以重用。

## CASE Tools for the Requirements Workflow 需求流的 CASE 工具

We need graphical tools for UML diagrams. 对于 UML 图表，我们需要图形化工具。

## Metrics for the Requirements Workflow 需求流的度量

Volatility and speed of convergence are measures of how rapidly the client’s needs are determined.
波动性和收敛速度用于测量如何很快确定客户的需求。

## Challenges of the Requirements Phase 需求流面临的挑战

- Employees of the client organization often feel threatened by computerization.
  一些客户组织的雇员经常感到计算机化的威胁。
- The requirements team members must be able to **negotiate**.
  需求小组成员必须有 **协商** 的能力。
- Key employees of the client organization may **not have the time** for essential in-depth discussions.
  客户组织的关键雇员可能 **没有时间** 进行重要的深入讨论。
- **Flexibility** and **objectivity** are essential.
  **灵活性** 和 **客观性** 是基本的。
