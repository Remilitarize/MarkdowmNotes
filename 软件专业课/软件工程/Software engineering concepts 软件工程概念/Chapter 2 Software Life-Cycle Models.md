[toc]

## Software Development in Theory

- ideally 理想情况下
  - **Linear 线性的**
  - **Starting from scratch 从零开始**

- In the real world 实际中
  - software development is **totally different**. 软件开发有 **很大不同**。
  - We make mistakes. 我们会犯错误。
  - The client's requirements change while the software product is being developed.
    当软件产品开发时客户需求会更改。

## Winburg Mini Case Study Winburg 小型实例研究

The simplified version of waterfall model 简化版瀑布模型

- The linear life cycle model with **feedback loops**. 带有 **反馈环** 的线性生命周期模型。
- The waterfall model **cannot** show the order of events. 瀑布生命周期 **不能** 展示事件的顺序。

![简化版瀑布模型](http://oxnec2zdn.bkt.clouddn.com/software-engineering/SimplifiedWaterfall.jpg)

Evolution-Tree Model 进化树模型

- The explicit order of events is shown. 表达出了事件的顺序。
- We have a **baseline**, a complete **set of artifacts**(constituent components).
  有一个 **基线**，一套完整的 **制品集**（或构成的组件）。

![进化树模型](http://oxnec2zdn.bkt.clouddn.com/software-engineering/Evolution-tree-model.jpg)

## Lessons of the Winburg Mini Case Study Winburg 小型实例研究心得

- Changes are always needed. 总是需要变动。
	- A software product is a model of the real world, which is continually changing.
	  软件产品是现实世界的反应，而现实世界是不断变化的。
	- Software professionals are human, and therefore make mistakes.
	  软件专业人员是人，会出错。

## Teal Tractors Mini Case Study 野鸭拖拉机公司小型实例研究

### Moving Target Problem 移动目标问题

- Any change made to a software product can potentially cause a **regression fault**.
  任何对软件产品的改动都会造成一个潜在的 **回归错误**。
	- A fault in an apparently unrelated part of the software.
	  在软件的一个不相关的部分产生的错误。
- **Change is inevitable. 改动不可避免**。
- **There is no solution to the moving target problem**.
  **对于移动目标问题没有解决办法**。

## Iteration and Incrementation 迭代和递增

- The basic software development process is **iterative**. **迭代** 是基础的软件开发过程。
	- Each **successive version** is intended to be closer to its target than its **predecessor**.
    每一 **后续版本** 比 **前一个版本** 更接近目标。

### Miller’s Law 米勒法则

- **At any one time, we can concentrate on only approximately seven chunks(units of information).**
  **在任何时间，我们只能将注意力集中在大约七桩事情（信息的单位）上。**
- To handle larger amounts of information, use **stepwise refinement**.
  为了处理庞大数量的信息，使用 **逐步求精法**。
 	- Concentrate on the aspects that are **currently the most important**.
    集中精力于 **目前的最重要** 的那些方面。
	- Postpone aspects that are currently less critical. 不那么紧急的方面拖延。
	- Every aspect is eventually handled, but in order of **current importance**.
    事情的每个方面最终都要处理，但是要按照 **目前的重要性** 依次进行。
- This is an **incremental** process. 这是一个 **递增** 过程。

> The number of increments will vary. 递增的数量将会很多。

> Iteration is performed during each incrementation. 迭代和递增相互结合使用。

### Classical Phases versus Workflows 经典阶段对比工作流

- Instead, the five core workflows (activities) are performed over the entire life cycle.
  然而，五个核心的工作流（活动）表现了整个生命周期。
	- **Requirements workflow 需求工作流**
	- **Analysis workflow 分析工作流**
	- **Design workflow 设计工作流**
	- **Implementation workflow 实现工作流**
	- **Test workflow 测试工作流**

### Workflow 工作流

- At most times one workflow **predominates**.
  在同一时间只有一个工作流占 **主导地位**。
- **Planning and documentation activities** are performed throughout the life cycle.
  **计划和文档活动** 贯穿整个迭代-递增生命周期模型。

## The Winburg Mini Case Study Revisited 修订的 Winburg 小型实例研究

略

## Risks and Other Aspects of Iter. and Increm. 迭代和递增的风险和其他方面

- We can consider the project as a whole as a set of mini projects (increments).
  我们可以将项目作为整体划分为更小的小项目（或增量）。
- Each iteration can be viewed as a small but complete waterfall life-cycle model.
  每个迭代可以看作是一个较小但完整的瀑布生命周期模型。

### Strengths of the Iterative-and-Incremental Model 迭代递增模型的优点

- There are multiple opportunities for checking that the software product is correct.
  为检查软件产品是否正确提供多个机会。
- The **robustness of the architecture** can be determined early in the life cycle.
  在生命周期的相对早期就可以确定其蕴含的 **结构的健壮性**。
	- Architecture — the various component modules and how they fit together.
	  结构 —— 各种制品组成以及如何组装在一起。
	- Robustness — the property of being able to handle extensions and changes without falling apart.
	  健壮性 —— 能够处理这样的扩展眼和改变，却没有支离破碎。
- We can **mitigate(resolve)** risks early.
  迭代-递增模型使我们能够较早地 **减轻风险**。
- We have a working version of the software product from the start.
  我们总是有该软件的一个工作版。
  - **Variation**: Deliver partial versions to smooth the introduction of the new product in the client organization.
    **可控复杂性**：交付部分版本平滑地为客户组织做新产品的介绍。

## Managing Iteration and Incrementation 迭代和递增的控制

- The iterative-and-incremental life-cycle model is as **gimented** the waterfall model.
  迭代递增生命周期模型与瀑布生命周期模型一样 **受严格控制**。
- Because the iterative-and-incremental life-cycle model is the waterfall model, **applied successively**.
  因为迭代递增生命周期模型是 **成功应用** 的瀑布生命周期模型。

## Other Life-Cycle Models 其他生命周期模型

### Code-and-Fix Model 编码-修补模型

![编码-修补模型](http://oxnec2zdn.bkt.clouddn.com/software-engineering/Code-and-fix.jpg)

- **No design, specification. 没有设计和规格说明书。**
- The **easiest** way to develop s-oftware - and by far the **worst** way.
  开发软件 **最简单** 的方式，也是迄今为止 **最糟糕** 的方式。

### Waterfall Model 瀑布模型

![瀑布模型](http://oxnec2zdn.bkt.clouddn.com/software-engineering/FullWaterfallModel.jpg)

- Characterized by 特点有
	- **Feedback loops 反馈环**
	- **Documentation-driven 文档驱动**
- Advantages 优点
  - Enforced disciplined approach 强制训练方法
	 - Documentation 有文档
	- Maintenance is easier 维护便捷
- Disadvantages 缺点
	- Specification document 规格说明文档

### Rapid Prototyping Model 快速原型模型

![快速原型模型](http://oxnec2zdn.bkt.clouddn.com/software-engineering/RapidPrototypingModel.jpg)

- Advantage 优点
	- Fast 快
	- Linear 线性的

### Open-Source Life-Cycle Model 开源生命周期模型

![开源模型](http://oxnec2zdn.bkt.clouddn.com/software-engineering/OpenSourceModel.jpg)

- Key point: Individuals generally work **voluntarily** on an open-source project in their spare time.
  关键点：个人在空闲时间 **自愿** 为开源项目工作。
- Two informal phases 两个非正式阶段
	- The first Informal Phase 第一个非正式阶段
		- One individual builds an initial version. 个人建立了一个初始版本。
		- Made available via the Internet. 发布到网上。
	- The Second Informal Phase 第二个非正式阶段
		- Reporting and correcting defects 报告并纠正缺陷
			- Corrective maintenance 纠错性维护
		- Adding additional functionality 添加额外功能
			- Perfective maintenance 完善性维护
		- Porting the program to a new environment 移植软件到新的环境
			- Adaptive maintenance 适应性维护
		- The second informal phase consists solely of postdelivery maintenance.
		  第二阶段仅仅包括交付后维护。
			- The word “co-developers” on the previous slide should rather be “co-maintainers”
			  前面说的“合作开发者”应该改为“合作维护者”。
- **Closed-source software** is maintained and tested by employees.
  **不开源的软件** 由雇员小组进行维护和测试。
	- Users can submit **failure** reports but never **fault** reports (the source code is not available).
	 用户可以提交 **故障** 报告，但不能提交 **错误** 报告。（源代码不可获取）
- Open-source software is generally maintained by unpaid volunteers.
  开源软件由不拿报酬的志愿者维护。
	- Users are **strongly encouraged** to submit defect reports, both failure reports and fault reports.
	  **鼓励** 用户提交检测报告，故障报告和错误报告。

- An initial working version is produced when using 当使用时就已经产生了初始测试版本的有
	- The rapid-prototyping model 快速原型模型
		- The initial version is **discarded**. 初始版本将被 **丢弃**。
	- The code-and-fix model and the open-source life-cycle model 编码-修补模型和开源生命周期模型
		- The initial version becomes the target product. 初始版本成为目标产品。
- In an open-source project, there are generally no specifications and no design.
  在开源项目中，没有规格说明和设计。

### Agile Processes 敏捷过程

- Somewhat controversial new approach
  一种具有争议的新方法
- Test-driven development(TTD) 测试驱动开发
- **Pair programming 结对编程**
- Continuous integration of tasks 集成可以连续地进行

#### Unusual Features of XP 极限编程的特性

- The computers are put in the center of a large room lined with cubicles.
  XP 小组的计算机设在一个大房间的中心，大房间中有许多彼此相连的小隔间。
- A client representative is always present. 一个客户代表一直与 XP 小组工作。
- Software professionals cannot work overtime for 2 successive weeks. 没有软件专业人员能够连续两周工作。
- No specialization. 没有规格说明文档。
- Refactoring (design modification) 重组（设计变更）

#### Agile Processes 敏捷过程

- XP is one of a number of new paradigms collectively referred to as agile processes.
  极限编程是敏捷过程范型中的一个。
- The Agile Alliance did not prescribe a specific life-cycle model.
  敏捷联盟不是一个制定的专业生命周期模型。
	- Instead, they laid out a group of underlying **principles**.
	  只是推出一组根本的 **原则**。
- Agile processes are a collection of new paradigms characterized by
  敏捷过程是新样例的集合，特点有
	- Less emphasis on analysis and design
	  不怎么强调分析和设计
	- Earlier implementation (Working software is considered more important than documentation.)
	  实现开始得很早（能工作的软件比具体的文档更重要。）
	- Responsiveness to change. 响应需求变化
	- Close collaboration with the client. 与客户协作很紧密
- A principle in the Manifesto is  原则上有
	- Deliver working software frequently, ideally every 2 or 3 weeks.
	  频繁地交付运行软件，最好每 2 周或 3 周一次。
	- One way of achieving this is to use **timeboxing**. 实现方式通过使用 **时光盒**。
	- Another common feature of agile processes is **stand-up meetings**.
	  敏捷过程的另一个普遍特性是 **站立会议**。
		- The aim of a stand-up meeting is 站立会议的目的是
			- **To raise problems 提出问题**
			- **Not solve them 不解决问题**

#### Evaluating Agile Processes 评估敏捷过程

- Agile processes have had some successes with small-scale software development.
  敏捷过程在一些小型软件开发中获得成功。
	- However, medium- and large-scale software development is very different.
	  然而，中型以及大型软件开发是不同的。
- The impact of agile processes on postdelivery maintenance. 敏捷过程对交付后维护的影响。
	- **Refactoring** is an essential component of agile processes. **重组** 是敏捷过程的固有组成部分。
	- Refactoring continues during maintenance. 当维护时重组仍继续。
- It is too soon to evaluate agile processes. 评估敏捷过程为时尚早。
	- There are not enough data yet. 还没有收集到足够的数据。

### Synchronize-and Stabilize Model 同步——稳定模型

- **Microsoft**’s life-cycle model **微软** 的生命周期模型
- Requirements analysis—interview potential customers. 潜在客户会谈。
- Draw up specifications. 提取出对顾客具有最高优先级的特性列表，拟制规格说明文档。
- Divide project into 3 or 4 builds. 按重要性划分为3-4个构件。
- Each build is carried out by small teams working in **paralle**. 每个构件由小组 **并行** 开发。
- At the end of the day — **synchronize** (test and debug) 每天结束 —— **同步**（测试和调试）
- At the end of the build — **stabilize** (freeze the build) 每个组件结束 —— **稳定**（冻结组件）
- Components always work together. 组件总能一同工作。

### Spiral Model 螺旋模型

![螺旋模型](http://oxnec2zdn.bkt.clouddn.com/software-engineering/SpiralModel.jpg)

#### A Key Point of the Spiral Model 螺旋模型的关键点

- **If all risks cannot be mitigated, the project is immediately terminated.**
  **如果不能减小该阶段所有重大的风险，则该项目立即停止。**

#### Full Spiral Model 完全螺旋模型

![完全螺旋模型](http://oxnec2zdn.bkt.clouddn.com/software-engineering/FullSpiralModel.jpg)

- Precede each phase by 每一阶段确定目标
	- **Alternatives 可选择办法**
	- **Risk analysis 风险分析**
- Follow each phase by 每一阶段后
	- **Evaluation 评估目标策略**
	- **Planning of the next phase 下一阶段的计划**
- Radial dimension: cumulative cost to date. 径坐标代表迄今累积的成本。
- Angular dimension: progress through the spiral. 角坐标代表螺旋形的进展。

#### Analysis of the Spiral Model 分析螺旋模型

- Strengths 优点
	- It is easy to judge how much to test. 很容易估算测试花销。
	- No distinction is made between development and maintenance. 开发和维护之间无明显区别。
- Weaknesses 缺点
	- For large-scale software only. 只适用于大型软件。
	- For internal (in-house) software only. 只对内部软件有效。

## Comparison of Life-Cycle Models 生命周期模型间的比较

|Life-cycle Model|Strengths|Weaknesses|
|-|-|-|
|Evolution-tree model<br/>进化树模型|Closely models real-world software production, Equivalent to the iterative-and-incremental model<br />与现实世界软件开发最接近的模型，与迭代-递增模型等价| |
|Iterative-and-incremental life-cycle model<br />迭代-递增生命周期模型|Closely models real-world software production, Underlies the Unified Process<br />与现实世界软件开发最接近的模型，蕴涵统一过程方法| |
|Code-and-fix life-cycle model<br />编码-修补生命周期模型|Fine for short programs that require no maintenance<br />适用于不需要任何维护的小程序<br />The easiest way to develop software<br />开发软件的最简单方式|Totally unsatisfactory for nontrivial program<br />总的来说不适合重要的程序|
|Waterfall life-cycle model<br />瀑布生命周期模型|Disciplined approach, Document driven<br />纪律性强制的方法，文档驱动|Delivered product may not meet client's needs<br />交付的产品可能不符合客户的要求|
|Rapid-prototyping life-cycle model<br />快速原型开发生命周期模型|Ensures that the delivered product meets the client's needs<br />确保交付的产品符合客户的要求|Not yet proven beyond all doubt<br />还没有证明无懈可击|
|Open-source life-cycle model<br />开源生命周期模型|Has worked extremely well in a small number of instances<br />少量实例中工作相当好|Limited applicability, Usually does not work<br />实用性有限，通常不太起作用|
|Agile processes<br />敏捷过程|Work well when the client's requirements are vague<br />客户的需求模糊时能很好地工作|Appear to work on only small-scale projects<br />似乎只适合小规模项目|
|Synchronize-and=stabilize life-cycle model<br />同步-稳定生命周期模型|Future users' needs are met, Ensures that components can be successfully integrated<br />能满足未来用户的要求，确保各组件能够成功集成|Has not been widely used other than at Microsoft<br />除了在Microsoft公司，还没有广泛地应用|
|Spiral life-cycle model<br />螺旋生命周期模型|Risk driven<br />风险驱动|Can be used for only large-scale, in-house products, Developers have to be competent in risk analysis and risk resolution<br />只能用于大型的内部软件产品，开发者必须精通风险分析和风险排除|

### Comparison of Life-Cycle Models (Conclusion) 生命周期模型的比较（结论）

- Different life-cycle models have been presented. 不同的生命周期模型表现
	- Each with its own strengths and weaknesses. 每个模型由自己的优点和缺点
- Criteria for deciding on a model include: 决定模型的因素包括：
	- The organization 组织
	- Its management 管理
	- The skills of the employees 雇员的机能
	- The nature of the product 产品的类型
- Best suggestion 最佳建议
	- **"Mix-and-match" life-cycle model 合适的就是最好的**
