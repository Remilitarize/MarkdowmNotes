[toc]

The specification document must be 规格说明文档必须

- **Informal** enough for the client. 对客户足够 **非形式化**。
- **Formal** enough for the developers. 对开发者足够 **形式化**。

## The Specification Document 规格说明文档

**The specification document** is a **contract** between the client and the developers.
**规格说明文档** 是客户和开发者之间的一种 **合同**。

- Typical constraints 典型约束
	- **Deadline 最后期限**
	- **Parallel running 并行运行**
	- **Portability 可移植性**
	- **Reliability 可靠性**
	- **Rapid response time 快速响应时间**
- For real-time software 对于实时软件
	- Hard real-time constraints must be satisfied. 必须满足硬实时约束。
- **Acceptance criteria 验收标准集**
- If the product passes the tests, it is deemed have **satisfied its specifications**.
  如果产品通过测试，认为 **满足了规格说明文档**。
- Solution Strategy 解决策略
	- A general approach to building the product. 建造产品的一个通用方法。
	- Find strategies without worrying about constraints. 找到策略不考虑约束。
	- Keep a written record of all discarded strategies, and why they were discarded.
	  保存所有丢弃的策略以及拒绝他们的原因的记录。

## Informal Specifications 非形式化规格说明

Informal specifications are written in **a natural language**.
非形式化规格说明使用 **自然语言** 书写。
Conclusion：Natural language is **not a good way** to specify a product.
结论：自然语言 **不是** 一个规定产品的 **好方法**。

## Structured Systems Analysis 接过话系统分析

The data flow diagram (DFD) shows the logical data flow.
数据流图（DFD）展示逻辑数据流。

Symbols: 符号

![DFD symbols](http://oxnec2zdn.bkt.clouddn.com/software-engineering/DFDsymbols.png)

- Double square 双方框：源数据或目的数据
- Arrow 箭头：数据流
- Rounded rectangle 圆角矩阵：转换数据流的处理
- Open-ended rectangle 开口矩形：数据存储

### Sally’s Software Shop Mini Case Study

1. Draw the DFD 画数据流图
	- The final DFD is larger. 最终的数据流图是巨大的。
2. Decide what parts to computerize and how. 决定哪部分计算机化以及如何计算机化
3. Determine the Details of the Data Flows. 确定数据流的细节
	- We need a **data dictionary** for larger products. 在产品较大时，我们需要一个 **数据字典**。
4. Define the Logic of the Processes. 定义处理的逻辑
	- Translate this into a **decision tree**. 把这些翻译成 **判决树**。
5. Define the Data Stores. 定义数据存储
6. Define the Physical Resources. 定义物理资源。
7. Determine Input/Output Specifications. 确定输入-输出规格说明
8. Determine the Sizing. 确定大小。
9. Determine the Hardware Requirements. 确定硬件要求。

## Structured Systems Analysis: The MSG Foundation Case Study 接过话系统分析：MSG 基金实例研究

略

## Other Semiformal Techniques 其他半形式化技术

**Semiformal (graphical) techniques** for classical analysis include
半形式化（图形化）技术

- PSL/PSA
- SADT
- SREM

## Entity-Relationship Modeling 实体-联系（E-R)建模

**Semi-formal technique 半形式化技术**

## Finite State Machines 有穷状态机

- The set of states J 状态集 J
- The set of inputs K 输入集 K
- The transition function T 转换函数 T
- The initial state J 初始状态 S
- The set of final states J 最终状态集 F

Transition rules then take the form. 转换规则具有如下形式：

- current state and event and predicate &rarr; new state 当前状态与事件与谓词 &rarr; 下一个状态

The power of an FSM to specify complex systems. FSM 指定复杂系统的能力。
There is no need for complex preconditions and postconditions.
不需要复杂的前置条件和后置条件。

### Finite State Machines: The Elevator Problem Case Study 有穷状态机：电梯问题实例研究

略

## Petri Nets  Petri 网

A powerful technique for specifying systems that have potential problems with interrelations.
用于说明隐含有定时问题的系统的一个功能强大的技术。

A Petri net consists of four parts: Petri 网由四部分组成：

- A set of places P 位置集 P
- A set of transitions T 转换集 T
- An input function I 输入函数 I
- An output function O 输出函数 O

![Petri 网例题](http://oxnec2zdn.bkt.clouddn.com/software-engineering/PetriNet.png)

- Set of places P is {P<sub>1</sub>, P<sub>2</sub>, P<sub>3</sub>, P<sub>4</sub>}.
- Set of transitions T is {T<sub>1</sub>, T<sub>2</sub>}.
- Input functions:
	- I(T<sub>1</sub>) = {P<sub>2</sub>, P<sub>4</sub>}
	- I(T<sub>2</sub>) = {P<sub>2</sub>}
- Output functions:
	- O(T<sub>1</sub>) = {P<sub>1</sub>}
	- O(T<sub>2</sub>) = {P<sub>3</sub>, P<sub>3</sub>}


### Petri Nets: The Elevator Problem Case Study Petri 网：电梯问题实例研究

略

## Z

Z is a **formal** specification language.Z 是 **正式** 规格说明文档语言。

A Z specification consists of four sections: Z 规格说明由下面四部分组成：

- **Given sets, data types, and constants 给定的集合、数据类型和常数。**
-	**State definition 状态定义**
-	**Initial state 初始状态**
-	**Operations 操作**

### Z: The Elevator Problem Case Study Z：电梯问题实例研究

略

### Analysis of Z Z 的分析

Z is the most widely used formal specification language. Z 已经在范围广泛的项目中使用。

- CICS(part)
- An oscilloscope 示波器
- A CASE tool CASE 工具
- Many large-scale projects (especially in Europe) 许多大规模项目（特别在欧洲）

## Other Formal Techniques 其他的形式化技术

- Anna
- Gist, Refine
- VDM
- CSP

## Comparison of Classical Analysis Techniques 传统分析技术的比较

- Formal methods are 形式化的方法
	- Powerful 功能强大
	- Difficult to learn and use 难于学习和使用
- Informal methods have 非形式化的方法
	- Little power 缺乏强大功能
	- Easy to learn and use 易于学习
- There is therefore a trade-off. 因此做出权衡。
	- Ease of use versus power. 易用性和功能。

|Classical Analysis Method|Category|Strengths|Weaknesses|
|-|-|-|-|
|Natural language<br />自然语言|Informal<br />非形式化|Easy to learn<br />易于学习<br />Easy to use<br />易于使用<br />Easy for the client to understand<br />客户易于理解|Imprecise<br />不精确<br />Specifications can be ambiguous, contradictory or imcomplete<br />规格说明可能是模糊、矛盾或不完整的|
|Entity-relationship modeling<br />实体-关系模型<br />PSL/PSA<br />SADT<br />SREM<br />Structured systems analysis<br />结构化系统分析|Semiformal<br />半形式化|Can be understood by the client<br />可以为客户所理解<br />More precise than informal techiques<br />比非形式化方法更精确|Not as precise as formal techniques<br />不如形式化方法精确<br />Generally cannot handle timing<br />通常不能处理定时问题|
|Anna<br />CSP<br />Extended finite state machines<br />有限状态机<br />Gist<br />Petri nets<br />Petri 网<br />VDM<br />Z|Formal<br />形式化|Extremely precise<br />非常精确<br />Can reduce analysis faults<br />可以减少分析错误<br />Can reduce development cost and effort<br />可以减少开发成本和工作量<br />Can support correctness proving<br />可以支持正确性证明|Hard for the development team to learn<br />开发小组难于学习<br />Hard to use<br />难于使用<br />Almost impossible for most clients to understand<br />多数客户几乎不可能理解|

## Testing during Classical Analysis 在传统分析阶段测试

略

## CASE Tools for Classical Analysis 传统分析阶段的 CASE 工具

略

## Metrics for CASE Tools 传统分析阶段的度量

Five fundamental metrics. 五个基本度量

Quality 质量

- Fault statistics 错误统计
- The number, type of each fault 错误的数量和种类
- The rate of fault detection 错误检测率

Metrics for "predicting" the size of a target product 预测目标产品规模的度量

- Total number of items in the data dictionary 数据字典中项目总数
- The number of items of each type 项目种类数目
- Processes vs. modules 过程与模块

## Software Project Management Plan: The MSG Foundation Case Study 软件项目管理计划：MSG 基金实例研究

略

## Challenges of Classical Analysis 传统分析阶段面临的挑战

A specification document must be 规格说明文档必须

- **Informal** enough for the client 对客户足够 **非形式化**
- **Formal** enough for the development team 对开发团队足够 **形式化**

Analysis (“what”) should **not** cross the boundary into design (“how”).
分析（什么）和（如何）设计之间的限界 **不** 应当跨越。

Do not try to assign modules to process boxes of DFDs until the **classical design phase**.
不要试图分配模块给 DFD 中的过程块直至 **经典设计阶段**。
