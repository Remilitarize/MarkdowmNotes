[toc]

- Careful planning at the beginning of the project perhaps is the single most important factor that distinguishes success from failure.
  在项目开始阶段仔细地规划可能是决定成败的最重要的因素。
- Planning continues throughout development and then postdelivery maintenance.
  计划在软件开发和维护过程中不断地进行。
- The earliest possible time that detailed planning can take place is **after the specifications are complete**.
  最早可能产生详细计划的时间是在 **规格说明文档完成之后**。

## Planning and the Software Process 计划和软件过程

Cone of uncertainty 不确定锥区

![不确定锥区](http://oxnec2zdn.bkt.clouddn.com/software-engineering/ConeOfUncertainty.png)

## Estimating Duration and Cost 周期和成本估算

- **Accurate duration estimation** is critical. 进行 **准确的周期估算** 是重要的。
- **Accurate cost estimation** is critical. 进行 **精确的成本估算** 是重要的。
	- Internal costs 内部成本
	- External costs 外部成本
- There are too many variables for accurate estimate of cost or duration.
  要准确估算成本和周期，需要考虑太多的变量。

### Metrics for the Size of a Product 产品规模的度量

- Lines of code 代码行数
	- LOC 代码行
	- KDSI：Thousand delivered source instructions. 千行交付源代码指令
	- KLOC 千代码行
- FFP
- Function Points 功能点
- COCOMO

#### Lines of code 代码行数

- LOC is not defined for **nonprocedural languages**. 代码行对于 **非过程语言** 没有定义。
- Estimation based on LOC is therefore doubly dangerous. 根据代码行的成本估算具有双重危险。

#### Metrics for the Size of a Product 产品规模的度量

Metrics based on measurable quantities that can be determined early in the software life cycle.
基于可测量量的度量可以在软件开发过程的初期确定。

- **FFP**：For cost estimation of **medium-scale** data processing products.
  为 **中等规模** 的数据处理产品的成本估算。
	- **Files 文件**
	- **Flows 信息流**
	- **Processes 过程**
- **Function Points 功能点**
	- This is an oversimplification of a 3-step process.
	  这是过于简化的三步计算过程。
		- Classify each component of the product as simple, average, or complex.
		  产品的所有组件必须归类为简单的、一般或复杂的。
		- Assign the appropriate number of function points.
		  根据每个组件的级别给每个组件分配一个功能点数。
	 	- The sum gives UFP (unadjusted function points).
		  再对分配给每个组件的功能点求和。
	- Compute the technical complexity factor (TCF).
	  计算技术复杂因子。
		- Assign a value from 0 (“not present”) to 5 (“strong influence throughout”) to each of 14 factors such as transaction rates,portability.
		  这 14 个因子中每一个都分配一个值，从 0（"不存在或没有影响"）到 5（"从始至终的影响都很强烈"）。
		- Add the 14 numbers. This gives the total degree of influence (DI).
		  把所有产生的 14 个数相加，得到总的影响度（DI）。
			- TCF = 0.65 + 0.01 * DI
		- The number of function points (FP) is then given by FP = UFP * TCF.
		  功能点数 FP 可由 FP = UFP * TCF 得出。
	- Function points are usually better than KDSI — but there are some problems.
	  使用功能点比使用 KDSI 更合适 - 但是有一些问题。
	- Cost per function point is meaningful. 每个功能点的成本是有意义的。

### Techniques of Cost Estimation 成本估算技术

- Expert judgment by analogy 用类推法进行专家评判
- Bottom-up approach 自底向上的方法
- Algorithmic cost estimation models 算法成本估算模型

#### Expert judgment by analogy 用类推法进行专家评判

- Experts compare the target product to completed products. 专家通过将目标产品与他积极参与完成的产品进行对比。
- The Delphi technique is sometimes needed to achieve consensus. Delphi 技术优势需要达成一致。

#### Bottom-up approach 自底向上的方法

Break the product into smaller components. 把产品分割成更小的组件。

#### Algorithmic Cost Estimation Models 算法成本估算模型

A metric is used as an input to a model to compute cost and duration.
作为确定产品成本的模型的输入计算成本和周期的度量。

- SLIM Model
- Price S Model
- COnstructive COst MOdel (COCOMO) 构造性成本模型

### Intermediate COCOMO 中间 COCOMO

- COCOMO consists of three models. COCOMO 包含三个模型。
	- A macro-estimation model for the product as a whole. 把产品作为整体看待的宏观估算模型。
	- Intermediate COCOMO. 中间 COCOMO。
	- A micro-estimation model that treats the product in detail. 具体化看待产品的微观估算模型。
- Intermediate COCOMO 中间 COCOMO。
	- Estimate the length of the product in KDSI. 产品以 KDSI 计算的长度。
	- Estimate the product development mode (organic, semidetached, embedded). 产品的开发模式（有组织的，半分离的，嵌入式的）。
	- Compute the nominal effort. 计算额定工作量。
	- Multiply the nominal value by 15 software development cost multipliers. 额定值必须乘以 15 个软件开发工作量因子。

### COCOMO II

COCOMO II is **far more complex** than the first version. COCOMO II 比第一个版本 **更复杂** 了。

- Application composition model applied at the earliest workflows. 应用组合模型应用于最早的工作流。
	- Based on feature points (similar to function points). 基于对象点（类似于功能点）
- Early design model 早期设计模型
	- Based on function points. 基于功能点。
- Post-architecture model 后结构模型
	- Based on function points or KDSI. 基于功能点或 KDSI。

**COCOMO II supports reuse. COCOMO II 支持重用。**

### Tracking Duration and Cost Estimates 跟踪周期和成本估算

Whatever estimation method used, careful tracking is vital. 必须进行仔细地跟踪，无论预测应用了何种技术。

## Components of a Software Project Management Plan 软件项目管理计划的组成

- **The work to be done. 要做的工作。**
- **The resources with which to do it. 做这个工作所用的资源。**
- **The money to pay for it. 需要付出的金钱。**

### Resources 资源

Resources needed for software development. 软件开发需要资源。

- People 人
- Hardware 硬件
- Support software 支持软件

The entire software development plan must be **a function of time**. 整个软件开发计划是个 **时间的函数**。

### Work Categories 工作类别

- **Project function 项目函数**
	- Work carried on throughout the project. 在整个项目中持续进行。
- **Activity 活动**
	- Work that relates to a specific phase. 与某个特定工作流相关的工作。
- **Task 任务**
	- An activity comprises a set of tasks (the smallest unit of work subject to management accountability).
	  活动包含一系列任务（受管理责任控制的工作的最小单元）。

### Completion of Work Products 工作产品的完成

- **Milestone**: The **date** on which the work product is to be **completed**. **里程碑**：确认工作产品 **完成的日期**。
- Once the work product has been reviewed and agreed upon, it becomes a **baseline**.
  一旦工作产品经过了评审，并得到通过，它就成为一个 **基准**。

### Work Package 工作包

Work product, plus 工作产品包括

- Staffing requirements 人员配备需求
- Duration 周期
- Resources 资源
- The name of the responsible individual 责任人的姓名
- Acceptance criteria for the work product 工作产品的验收标准

## Software Project Management Plan Framework 软件项目管理计划框架

Some of the sections are **inapplicable** to **small-scale software**. 一些章节与 **小型软件无关**。

## IEEE Software Project Management Plan IEEE 软件项目管理计划

![IEEE Software Project Management Plan 1](http://oxnec2zdn.bkt.clouddn.com/software-engineering/IEEE%20Software%20Project%20Management%20Plan1.png)
![IEEE Software Project Management Plan 2](http://oxnec2zdn.bkt.clouddn.com/software-engineering/IEEE%20Software%20Project%20Management%20Plan2.png)

## Planning Testing 计划测试

- The SPMP must **explicitly** state what testing is to be done. SPMP 必须 **明确** 的指示要进行的测试。
- **Traceability** is essential. **可跟踪性** 是必要的。
- **All black box test cases must be drawn up as soon as possible after the specifications are complete.**
  **提出黑河测试用例的最好时间是在规格说明文档完成之后。**

## Planning Object-Oriented Projects 计划面向对象的项目

略

## Training Requirements 培训需求

Training is generally needed by the members of the development group, starting with training in software planning。
开发小组的成员需要培训，从软件细化和估算就开始培训。
When new software development techniques, such as new design techniques ot testing procedures, are used, training must be provided to every member of the team using the new technique.
当使用诸如新的设计技术或测试过程这样的新软件开发技术时，必须给使用新技术的每个小组成员提供培训。

## Documentation Standards 文档标准

- Types of Documentation 文档类别
	- **Planning 计划方面**
	- **Control 控制方面**
	- **Financial 商业方面**
	- **Technical 技术方面**
	- **Source code 源代码**
	- **Comments within source code 代码内的注释**
- Documentation Standards 文档标准
	- Reduce misunderstandings between team members. 减少小组成员之间的误会。
	- Aid SQA. 帮助 SQA 小组。
	- Only new employees have to learn the standards. 仅新雇员需要培训文档标准。
	- Standards assist maintenance programmers. 编码标准有助于维护程序员。
	- Standardization is important for user manuals. 对于用户手册，标准化是重要的。
	- Standards must be set up for all documentation. 必须为生成的所有文档建立标准。
	- In a very real sense, **the product is the documentation**. 从非常现实的意义来说，**产品就是文档**。

## CASE Tools for Planning and Estimating 用于计划和估算的 CASE 工具

It is essential to have 一些工具是必须的。

- A word processor 文字处理器
- A spreadsheet 管理信息工具

## Testing the Software Project Management Plan 测试软件项目管理计划

We must check the SPMP as a whole. 我们必须将 SPMP 作为整体进行检查。
Paying particular attention to the duration and cost estimates. 特别注意周期和成本的估计。
