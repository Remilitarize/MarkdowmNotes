[toc]

- There are two basic types of testing. 有两种基本测试。
	- **Execution-based testing 执行测试**
	- **Non-excution-based testing 非执行测试**
- **V & V**
	- **Verification 核实**
		- Determine if the workflow was **completed correctly**.
		  决定工作流是否 **正确完成**。
	- **Validation 确认**
		- Determine if the product as a whole **satisfies its requirements**.
		  决定产品作为整体 **满足需求**。

## Software Quality 软件质量

The extent to which software **satisfies its specifications**.
软件 **满足规格说明文档** 的程度。

- Every software professional is responsible for ensuring that his or her work is correct.
  每个软件专业人员的任务是随时保证高质量的软件。

- Quality must be built in **from the beginning**.
  质量必须 **从一开始** 由开发者建立。

### Software Quality Assurance 软件质量保证

- The members of the SQA group must ensure that the developers are doing high-quality work.
  SQA 小组确保开发者的产品是正确的。
	- **At the end of each workflow** 在每个工作流结束时
	- **When the product is complete** 在产品完成时

### Managerial Independence 管理独立

- There must be managerial independence between 在两者之间必须使管理独立。
	- **The development group 开发小组**
	- **The SQA group SQA 小组**

## Non-Execution-Based Testing 非执行测试

Underlying principles 潜在的原则

- We should not review our own work. 我们不应该检查我们自己的工作。
- Group synergy. 团队协作

### Walkthroughs 走查

It includes representatives of 包含的代表有

- The team responsible for the current workflow 负责当前工作流的小组
- The team responsible for the next workflow 负责下个工作流的小组
- The SQA group SQA 小组

The walkthrough is preceded by preparation. 走查之前准备

- Items not understood. 不明白的事项。
- Items that appear to be incorrect. 认为不正确的事项。

### Managing Walkthroughs 管理走查

- In a walkthrough we **detect** faults, **not correct** them.
  走查中我们 **检测** 错误，但 **不改正** 他们。

- A walkthrough must be **document-driven**, rather than **participant-driven**.
  走查必须是 **文档驱动**，而不是 **参与者驱动**。

### Inspections 审查

An inspection team has four members. 审查团队有四个成员。

- Moderator 主持者
- A member of the team performing the current workflow 执行当前工作流团队中的一个成员
- A member of the team performing the next workflow 执行下个工作流团队中一个成员
- A member of the SQA group SQA 小组的一个成员

**Fault statistics should never be used for performance appraisal.**
**错误统计数据应从不用于做业绩估计。**

## Comparison of Inspections and Walkthroughs 走查与审查的比较

- **Walkthrough 走查**
	- **Two-step, informal process 两个步骤，非正式过程**
	- **Preparation 准备**
	- **Analysis 分析**
- **Inspections 审查**
	- **Five-step, formal process 五个步骤，正式过程**
	- **Overview 概要**
	- **Preparation 准备**
	- **Inspection 审查**
	- **Rework 修订**
	- **Follow-up 跟踪**

## Strengths and Weaknesses of Reviews 评审的优点和缺点

- Reviews can be effective. 评审十分有效。
- Reviews are less effective if the process is inadequate. 当过程不充分时检查就不是很有效。

## Metrics for Inspections 审查的度量

- **Inspection rate 审查速率**
- **Fault density 错误密度**
- **Fault detection rate 错误检测率**
- **Fault detection efficiency 错误检测效率**

## Execution-Based Testing 执行测试

Program testing can be a very effective way to show the presence of bugs, but it is hopelessly inadequate for showing their absence.
程序测试可以使显示 bug 存在的非常有效的方式，但显示它们额不存在却是绝对不允许的。

## What Should Be Tested? 应该测试什么？

- Definition of execution-based testing 执行测试的定义
	- **The process of inferring certain behavioral properties of the product based, in part, on the results of executing the product in a known environment with selected inputs.**
	  **推断某产品的特定行为特性的过程，基于或部分基于在已知环境下用经过选择的输入执行产品得到的结果。**
- This definition has troubling implications. 这个定义有令人困扰的含义。
	- **Inference 推断**
		- We have a fault report, the source code, and — often — nothing else.
		  我们会有错误报告、源代码并且经常会什么都没有。
	- **Known environment 已知环境**
		- We never can really know our environment.
		  我们永远不会真正知道我们的环境。
	- **Selected inputs 选定的输入**
		- Sometimes we cannot provide the inputs we want.
		  有时我们可能提供不了我们想要的输入。
		- Simulation is needed.
		  模拟是需要的。
- We need to test 我们需要测试的有
	- **Correctness 正确性**
	- **Utility 实用性**
	- **Reliability 可靠性**
	- **Robustness 健壮性**
	- **Performance 性能**

### Utility 实用性

The extent to which the product meets the user’s needs.
产品满足客户需求的程度。

### Reliability 适应性

A measure of the frequency and criticality of failure.
出错频率和严重性的度量。

- **Mean time between failures（MTBF） 平均故障间隔时间**
- **Mean time to repair（MTR） 平均修复时间**
- **Time (and cost) to repair the results of a failure 修复故障的结果用了多长时间**

### Robustness 健壮性

A function of 健壮性是一些因素的函数。

- **The range of operating conditions. 运行条件的范围。**
- **The possibility of unacceptable results with valid input. 有效输入带来不可接受的结果的可能性。**
- **The effect of invalid input. 输入无效时结果的可接受性。**

### Performance 性能

- The extent to which **space and time constraints** are met.达到 **空间和时间约束** 的程度。
- Real-time software is characterized by hard real-time constraints.
  实时软件的特点是硬件时间限制严格。
- If data are lost because the system is too slow, there is no way to recover those data.
  如果系统不够快，那么将丢失数据，且没有办法恢复该数据。

### Correctness 正确性

**A product is correct if it satisfies its specifications.**
**如果满足它的规格说明文档，产品就是正确的。**

- Techniccally, correctness is **not necessary, not sufficient**.
  技术上，正确性是 **不必须，不充分的**。

## Testing versus Correctness Proofs 测试与正确性证明

Even if a product has been proven correct, it must **still** be tested.
即使产品被证明是增却的，它 **仍** 必须被测试。

## Who should perform execution-based testing? 谁应当完成执行测试？

Programmers should not test their own code artifacts.
程序员不应该测试他们自己的代码制品。

- Solution 解决方案
	- **The programmer does informal testing. 程序员做非正式测试。**
	- **The SQA group then does systematic testing. SQA 小组做系统性测试。**
	- **The programmer debugs the module. 程序员修复模块。**
- All test cases must be 所有测试案例必须
	- Planned beforehand, including the expected output, and retained afterwards
	  先手计划，包含期望的输出和保留之后。

## When Testing Stops? 什么时候测试停止？

**Only when the product has been irrevocably discarded.**
**只有当产品已经不可逆转地丢弃时。**
