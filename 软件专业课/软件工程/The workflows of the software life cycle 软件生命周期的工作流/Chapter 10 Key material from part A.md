[toc]

## Software Development: Theory vs. Practice 软件开发：理论与实践

- Ideally, software is developed as described in Chapter 1. 在理想世界里，软件应如第一章所描述的那样开发。
	- **Linear. 线性的。**
	- **Starting from scratch. 从零开始。**
- In the real world, software development is totally different. 在现实世界，软件开发是完全不一样的。
	- We make mistakes. 我们会犯错。
	- The client’s requirements change while the software product is being developed.
	  软件产品开发过程中客户的需求经常会变。
		- **Moving target problem. 移动目标问题。**

## Iteration and Incrementation 迭代和递增

- In real life, we **cannot** speak about "the design phase". 在现实生活中，我们 **不能** 谈论"设计工作流"。
	- Instead, the operations of the design phase are **spread out over the life cycle**.
	  然而，设计工作流的操作 **散布在整个生命周期的各个阶段**。
	- We keep returning to earlier workflows. 我们总是会返回到更早的工作流。
- The basic software development process is **iterative**. 基本软件开发过程是 **迭代** 的。
	- Each **successive** version is closer to its target than its **predecessor**.
	  每个 **连续的** 版本比 **前一个** 版本离我们的目标更进一步。

### Miller’s Law 米勒法则

- At any one time, we can concentrate on only approximately **seven chunks** (units of information).
  在任何时候，我们最多只能将精力集中在 **7 桩**（信息的单位）事情上。

- To handle larger amounts of information, use **stepwise refinement**.
  处理大量信息的方法是使用 **逐步求精**。
	- Concentrate on the seven aspects that are currently the most important. 集中注意在当前最重要的七个方面。
	- Postpone aspects that are currently less critical.  推延当前次重要的方面。
	- Every aspect is eventually handled, but in order of current importance. 最终每个方面都被处理，但以当前重要性顺序。
- This is an **incremental** process. 这是个 **递增** 的过程。

### Incrementation 递增

- The number of increments will vary — it does not have to be four.
  递增的数量会很多 - 它不一定只有四个。
- **Sequential phases do not exist** in the real world. 在现实世界 **不存在序列化的阶段**。
- Instead, the five **core workflows (activities)** are performed over the entire life cycle.
  然而。有 **五个核心工作流（活动）** 在整个生命周期进行的。
	- **Requirements workflow 需求工作流**
	- **Analysis workflow 分析工作流**
	- **Design workflow 设计工作流**
	- **Implementation workflow 实现工作流**
	- **Test workflow 测试工作流**

### Workflows 工作流

- However, at most times one workflow **predominates**. 然而，同时只有一个工作流 **占主导地位**。
- **Planning and documentation activities are performed throughout the life cycle. 计划和文档活动贯穿生命周期。**

### Iteration 迭代

- **Iteration is performed during each incrementation. 迭代在每个递增中执行**。
- Again, the number of iterations will vary — it is not always three. 迭代的数量会很多 - 总是不止三个。

## The Unified Process 统一过程

The software process is the way we produce software. 软件过程是我们生产软件的方式。

It incorporates 它包含

- The methodology 方法学
- The tools we use 我们所使用的工具
- The individuals building the software 建造这些软件的人

The Unified Process is an **adaptable methodology**. 统一过程是 **可适应的方法论**。

- **Despite its name, the Unified Process is not a process. 尽管它的名字叫做过程，但统一过程不是一个过程。**
- The Unified Process uses a graphical language, **the Unified Modeling Language (UML)** to represent the software being developed.
  统一过程使用图形化语言 - **统一建模语言（UML）** 来表示要开发的软件。

- **A model** is a set of UML diagrams that represent various aspects of the software product we want to develop.
  **模型** 是一套 UML 图标，表示要开发的软件产品的一个或多个方面。

- The object-oriented paradigm is **iterative and incremental** in nature.
  面向对象范型是 **迭代和递增的**。
	- There is no alternative to repeated iteration and incrementation until the UML diagrams are satisfactory.
	  不断重复迭代和递增，直至满意地认为 UML 图表是要开发的软件产品的准确表示。

## Workflow Overview 工作流概述

- **Requirements workflow 需求工作流**
	- Determine exactly what the client **needs**. 明确客户 **需要** 什么。
- **Analysis workflow 分析工作流**
	- Analyze and refine the requirements. 分析和提炼需求。
- **Design workflow 设计工作流**
	- Refine the artifacts of the analysis workflow until the material is in a form that can be implemented by the programmers.
	  细化分析工作流的制品，知道材料处于程序员可实现的形式。
- **Implementation workflow 实现工作流**
	- Implement the target software product in the chosen implementation language(s).
	  用选择的实现语言实现目标软件产品。
- **Test workflow 测试工作流**
	- Testing is carried out in parallel with the other workflows, from the beginning.
	  测试从始至终与其他工作流并行进行。
	- Every developer and maintainer is personally responsible for ensuring that his or her work is correct.
	  每个开发者和维护者都要确保自己的工作是正确的。
	- Once the software professional is convinced that an artifact is correct, it is handed over to the software quality assurance group for independent testing.
	  一旦软件人员确信一个制品是正确的，就将它交给质量保证小组进行独立测试。

## Teams 软件小组

- Software products are usually too large (or too complex) to be built by one software engineering professional within the given time constraints.
  软件产品通常太大（或太复杂）而不可能由一个软件专业人员在有限时间内单独完成。

- The work has to be shared among a group of professionals organized as **a team**.
  工作必须分配给一组专业人员，形成一个 **小组**。

- The team approach is used for each of the workflows. 小组方法应用于整个生命周期。
- In larger organizations there are specialized teams for each workflow. 在规模大的公司对于每个工作流有专门的小组、

## Cost–Benefit Analysis 成本-效益分析

Cost–benefit analysis is a way of determining whether a possible course of action would be profitable.
成本-效益分析是一种确定是否有利可图的一种方法。
Cost–benefit analysis is a fundamental technique in deciding whether a client should computerize his or her business.
成本-效益分析是确定客户是否应当进行业务计算机化的基本技术。

## Metrics 度量

We need measurements (or metrics) to detect problems early in the software process.
在软件过程的早期，我们需要测度（或度量）检测问题。

There are five fundamental metrics. 有五个基本度量

- **Size (in lines of code or, better, in a more meaningful metric) 规模（以代码行或更好、更有意义的计）**
- **Cost (in dollars) 成本（以美元计）**
- **Duration (in months) 持续时间（以月计）**
- **Effort (in person-months) 工作量（以人月计）**
- **Quality (number of faults detected) 质量（以检测到的错误数计）**

Metrics serve as an early warning system for potential problems. 度量对于潜在的问题可起到早警示的作用。
Management uses the fundamental metrics to identify problems. 管理层使用基本的度量来发现问题。
More specialized metrics are then utilized to analyze these problems in greater depth.
更专门的度量来更深入第分析这些问题。

## CASE 计算机辅助软件工程

CASE stands for **Computer-Aided Software Engineering**. CASE 代表 **计算机辅助软件工程**。

### CASE Taxonomy CASE 分类

- A CASE **tool** assists in **just one aspect** of the production of software.
  CASE **工具** 只在软件生成的 **某一方面** 起帮助作用的软件。

- A CASE **workbench** is a collection of tools that together support **one or two activities**.
  CASE **工作平台** 是一些工具的集合，共同支持 **一个或两个活动**。

- A CASE **environment** supports **the complete software process**.
  CASE **环境** 支持 **完成的软件过程**。

## Versions and Configurations 版本和配置

- During development and maintenance, there are at least two versions of the product.
  不管是在开发阶段还是在维护阶段，都会有该制品的两个版本。
	- **The old version 老版本**
	- **The new version 新版本**

- There will also be two or more versions of each of the component artifacts that have been changed.
  修改过的每个组件制品也会有两个或更多的版本。

- The new version of an artifact may be less correct than the previous version.
  新版本的制品可能不比来版本的制品正确。

- It is therefore essential to keep all versions of all artifacts. 有必要保留素有版本的制品。
	- A CASE tool that does this is called **a version control tool**. 可完成此功能的 CASE 工具是 **版本控制工具**。

A configuration is 配置是

- A set of specific versions of each artifact from which a given version of the complete product is built.
  每个制品从这个集合中构件了整个产品的给定版本的特定版本集。
- A **configuration-control tool** can handle problems caused by development and maintenance by teams.
  **配置控制工具** 可处理小组成员在开发和维护阶段产生的问题。

A **baseline** is a configuration of all the artifacts in the product.
**基线** 是产品中所有制品的配置。

## Testing Terminology 测试术语

- A **fault** is injected into a software product when a human makes a **mistake**.
  **差错** 是一个人犯了 **过错** 时添加到软件中的。
- A **failure** is the observed incorrect behavior of the software product as a consequence of a fault.
  **故障** 是观察到的软件产品的不正确行为。
- The **error** is the amount by which a result is incorrect. **错误** 是不正确结果的累积。
- The word **defect** is a generic term for a fault, failure, or error.
  **缺陷** 是一个通用词汇，反之差错、故障或错误。

The **quality** of software is **the extent to which the product satisfies its specifications**.
软件 **质量** 是 **产品满足规格说明的程度**。
Within a software organization, the primary task of the **software quality assurance (SQA) group** is to test that the developers’ product is correct.
在软件公司组织，**软件质量保证（SQA）小组** 的主要任务是测试开发人员的产品是正确的。

## Execution-Based and Non-Execution-Based Testing 执行测试和非执行测试

### Non-Execution-Based Testing 非执行测试

In a **review**, a team of software professionals carefully checks through a document.
在 **评审** 中，软件专业人员小组仔细检查文档。

There are two types of review. 有两种评审。

- **Walkthrough − Informal 走查 - 非正式**
- **Inspection  − Formal 审查 - 正式**

**Non-execution-based testing** has to be used when testing artifacts of the **requirements, analysis, and design workflows**.
**当测试需求、分析和设计工作流** 测试制品时，必须使用 **非执行测试**。

### Execution-Based Testing 执行测试

**Execution-based testing** can be applied to only the code of the **implementation workflow**.
**执行测试** 只能在 **实现工作流** 的代码中应用。

## Modularity 模块性

A module is a **lexically contiguous sequence of program statements**, bounded by **boundary elements** (that is, {…} pairs), having an **aggregate identifier**.
模块是词汇上 **邻接的程序语句序列**，由 **边界元素** 限制范围（大括号对），有一个 **聚合标识符**。

- Ensure that the **coupling (degree of interaction between two modules)** is as **low** as possible.
  确保 **耦合（两个模块之间的交互程度）** 尽可能地 **低**。
- Ensure that the **cohesion (degree of interaction within a module)** is as **high** as possible.
  确保 **内聚（模块内部的交互程度）** 尽可能地 **高**。
- **Maximize information hiding. 最大化信息隐藏。**
	- Ensure that implementation details are not visible outside the module in which they are declared。
	  确保实现细节在声明它们的模块外是不可见的。

## Reuse 重用

**Reuse** refers to using components of one product to facilitate the development of a different product **with a different functionality**.
**重用** 指使用一个产品中的组件来简化 另一个 **功能不同** 的产品的开发。
If we reuse a component, we must **retest** the component in its new context.
如果我们重用一个组件，必须在新的环境中 **重新测试** 组件。

## Software Project Management Plan 软件项目管理计划

The components of a software project management plan: 软件管理计划的组件：

- **The work to be done. 要做的工作。**
- **The resources with which to do it. 需要的资源。**
- **The money to pay for it. 需要花费的资金。**

### Resources 资源

Resources needed for software development: 软件开发的资源：

- People 人
- Hardware 硬件
- Support software 支持软件

The entire software development plan must be **a function of time**.
整个软件项目管理计划必须是 **时间的函数**。

### Three Work Categories 三个工作类别

- **Project function 项目功能**
	- Work carried on throughout the project. 贯穿项目始终的工作。
- **Activity 活动**
	- Work that relates to a specific phase. 与某个特定工作流相关的工作。
	- A major unit of work. 主要工作单元。
- **Task 任务**
	- An activity comprises a set of tasks (the smallest unit of work subject to management accountability).
	  包含一系列任务（受管理责任控制的最小工作单元）。

### Completion of Work Products 工作产品的完成

A **milestone** is the **date** on which the work product is to be completed.
**里程碑** 是确认工作产品完成的 **日期**。
Once the work product has been reviewed and agreed upon, it becomes a **baseline**.
一旦工作产品经过了评审，并得到认可，它就成为一个 **基线**。

### Software Project Management Plan 软件项目管理计划

A **work package** is a work product, plus 一个 **工作包** 是一个软件产品，包含

- Staffing requirements 人员配备要求
- Duration 周期
- Resources 资源
- The name of the responsible individual 责任人的姓名
- Acceptance criteria for the work product 工作产品的验收标准
- The detailed budget as a function of time, allocated to 详细的预算并作为时间的函数，分配给
	- Project functions 项目功能
	- Activities 活动

Key components of the plan include 计划的关键部分包括

- **The cost estimate 成本估计**
- **The duration estimate 周期估计**
