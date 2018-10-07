[toc]

## The Unified Process 统一过程

- The Unified Process is **not a series of steps for constructing a software product**.
  统一过程 **不是一系列建立软件产品的步骤**。

- The Unified Process is **an adaptable methodology**.
  统一过程是一种 **自适应的方法论**。

- UML diagrams enable software engineers to communicate quickly and accurately.
  UML 图表使软件专业人员相互之间能够更快速和准确地沟通。

## Iteration and Incrementation within the Object-Oriented Paradigm 面向对象中的迭代和递增

- The Unified Process is a modeling technique.
  统一过程是一个建模技术。

- UML stands for **unified modeling language**.
  UML 代表 **统一建模语言**。

- The object-oriented paradigm is iterative and incremental in nature.
  面对对象范型是迭代与递增的。

## The Requirements Workflow 需求工作流

Aim：**To determine the client’s needs.** 目的：**确定客户的需求。**

- First, gain an understanding of the application domain.
  首先，对应用领域获得基本的了解。

- Second, build a business model.
  其次，建立业务模型。

- It is vital to determine the client’s constraints.
  准确确定客户的限制条件。
	- **Deadline 最终期限**
	- **Parallel running 并行运行**
	- **Portability 可移植性**
	- **Reliability 可靠性**
	- **Rapid response time 快速反应时间**
	- **Cost 花销**

- The aim of this concept exploration is to determine
  概念探究的目的是为了确定
	- What the client **needs** 客户 **需要** 什么
	- Not what the client **wants** 而不是客户 **想要** 什么

## The Analysis Workflow 分析工作流

Aim：**To analyze and refine the requirements**. 目的：**分析并提取需求**。

- Why not do this during the requirements workflow?
  为什么在需求工作流时不做分析？
	- The requirements artifacts must be totally comprehensible by the client.
	  需求制品必须能够完全被客户所理解。

- The artifacts of the requirements workflow must therefore be expressed in a natural (human) language.
  需求工作流的制品因此必须用自然（人类）语言表达。
	- All natural languages are **imprecise**.
	  所有自然语言都是 **不精确的**。

- **Specification document ("pecifications") 规格说明文档**
	- It constitutes a contract. 由一个协议构成。
	- It must **not have imprecise phrases**. **不允许含有不精确的短语**。

- Having complete and correct specifications is essential for testing and maintenance.
  规格说明文档对于测试和维护都是必需的。

- The specification document must not have 规格说明文档一定不能有
	- **Contradictions 矛盾**
	- **Omissions 模糊**
	- **Incompleteness 不完备**

### Software Project Management Plan 软件项目管理计划

- Once the client has **signed off the specifications**, detailed planning and estimating begins.
  当客户 **批准了规格说明之后**，就要开始进行详细计划和评估。

- We draw up the software project management plan, including
  我们起草了软件项目管理计划，包含
	- Cost estimate 花销估计
	- Duration estimate 时间估计
	- Deliverables 可交付性
	- Milestones 里程碑
	- Budget 预算

- This is the **earliest possible time** for the SPMP. 这是 SPMP **最早可能的时间**。

## The Design Workflow 设计工作流

Aim：**Refine the analysis workflow until the material is in a form that can be implemented by the programmers.**
目的：**细化分析工作流，直至材料处于程序员可实现的形式。**

### Classical Design 经典设计

- **Architectural Design 结构设计**
	- Decompose the product into modules. 分解产品至模块。
- **Detailed Design 详细设计**
	- Design each module. 设计每个模块。

### Object-Oriented Design 面向对象设计

Classes are extracted during the object-oriented analysis workflow and designed during the design workflow.
类已经在面向对象分析工作流时获取到并在设计工作流中设计。

## The Implement Workflow 实现工作流

Aim：**To implement the target software product in the selected implementation language.**
目的：**用选择的实现语言实现目标软件产品。**

- A large software product is partitioned into subsystems.
  大型软件产品被划分为较小的子系统。

- The subsystems consist of components or code artifacts.
  子系统由组件或代码制品组成。

## The Test Workflow 测试工作流

- The test workflow is the responsibility of every developer, maintainer, and the quality assurance group.
  测试工作流由每个开发人员，维护人员和质量保证小组负责。

- Traceability of artifacts is an important requirement for successful testing.
  制品的可追踪性是测试成功的一个重要的需求。

### Requirements Artifacts 需求制品

Every item in the analysis artifacts must be traceable to an item in the requirements artifacts.
必须能够对分析制品中的每一项追踪到需求制品。

### Analysis Artifacts 分析制品

- The analysis artifacts should be checked by means of a **review**. 分析制品应当 **重新核对**。
- The SPMP must be similarly checked. SPMP 必须同样检查。

### Design Artifacts 设计制品

Design reviews are essential. 设计回顾是至关重要的。

### Implementation Artifacts 实现制品

- Each component is tested as soon as it has been implemented.
  每个组件在实现后就测试。
	- **Unit testing** 单元测试

- At the end of each iteration, the completed components are combined and tested。
  每次迭代结束，所有完成的组件合并并测试。
	- **Integration testing** 集成测试

- When the product appears to be complete, it is tested as a whole.
  当产品即将完成，整体测试。
	- **Product testing** 产品测试

- Once the completed product has been installed on the client’s computer, the client tests it.
  一旦完成的产品被安装在客户的电脑上，客户对它测试。
	- **Acceptance testing** 验收测试

- COTS software is released for testing by prospective clients.
  商业化软件由潜在的用户进行版本测试
	- Alpha release &alpha; 版本
	- Beta release &beta; 版本

## Postdelivery Maintenance 交付后维护

- Postdelivery maintenance is an essential component of software development。
  交付后维护是软件开发至关重要的一部分。

- Two types of testing are needed 需要做两种测试
	- Testing the changes made during postdelivery maintenance. 测试在交付后维护期间的更改。
	- **Regression testing** 回归测试

> Once the programmer has determined that the desired changes have been implemented, the product must be tested against previous test cases to make certain that the functionality of the rest of the product has not been compromised.
在程序员确定要求的改变已经完成后，必须用各种测试用例对产品进行测试，以确保产品其他的功能不受影响。

## Retirement 退役

True retirement is a rare event. 真正的退役是个极少发生的事件。

## The Phases of the Unified Process 统一过程的阶段

- The four increments are labeled 被标记了四个递增过程
	- **Inception phase** 开始阶段
    - Determine whether the proposed software product is economically viable. 决定是否值得开发目标软件产品。
	- **Elaboration phase** 细化阶段
    - Refine the initial requirements. 细化最初的需求。
	- **Construction phase** 建设阶段
    - Produce the first operational-quality version of the software product. 产生软件产品的第一个可工作版本。
	- **Transition phase** 过渡阶段
    - Ensure that the client’s requirements have indeed been met. 确保客户的需求切实得到满足。

- The phases of the Unified Process are the increments。 统一过程的阶段是递增的。
- In theory, there could be any number of increments. 理论上，可能有无数个递增。
- Every step performed in the Unified Process falls into 统一过程的每个步骤从形式上可以分为
	- One of the five core workflows and also  五个核心工作流
	- One of the four phases 四个阶段
- **Workflow 工作流**
	- **Technical context of a step 技术上的一步**
- **Phase 阶段**
	- **Business context of a step 业务上的一步**

## One- and Two-Dimensional Life-Cycle Models 一维二维生命周期模型

![一维与二维生命周期模型](http://oxnec2zdn.bkt.clouddn.com/software-engineering/TwoDimesionalModel.png)

- A **traditional** life cycle is a **one-dimensional** model. **传统** 生命周期是 **一维** 模型。
- The **Unified Process** is a **two-dimensional** model. **统一** 过程是 **二维** 模型。
- The two-dimensional figure shows 二维图像展现的是
	- The workflows (technical contexts) 工作流（技术方面）
	- The phases (business contexts) 阶段（商业方面）
- The Unified Process handles the inevitable changes well. 统一过程对不可避免的改变处理得很好。
- The Unified Process is the best solution found to date for treating a large problem as a set of smaller, largely independent subproblems.
  統一过程是迄今为止将大型文体作为一些较小、较独立的子问题解决的最好办法。

## Improving the Software Process 改进软件过程

- Software process improvement initiatives 软件过程改进计划
	- Capability maturity model (CMM) 软件能力成熟度模型
	- ISO 9000-series ISO 9000 系列
	- ISO/IEC 15504

## Capability Maturity Models 软件能力成熟度模型

**Not life-cycle models 不是生命周期模型**
Rather, a set of strategies for improving the software process.
而是一组用于改进软件过程的相关策略。

- SW–CMM for software 软件
  - Initial Level 初始级
  - Repeatable Level 可重复级
  - Defined Level 定义级
  - Managed Level 管理级
  - Optimizing Level 最优级
- P–CMM for human resources (“people”) 人力资源管理
- SE–CMM for systems engineering 系统工程
- IPD–CMM for integrated product development 集成产品开发
- SA–CMM for software acquisition 软件获取

These strategies are unified into CMMI (capability maturity model integration).
这些策略合称为 CMMI（软件能力成熟度模型集成）。
