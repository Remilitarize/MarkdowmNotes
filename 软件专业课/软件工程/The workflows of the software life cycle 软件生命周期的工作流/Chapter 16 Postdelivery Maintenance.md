[toc]

Any change to any component of the product (including documentation) after it has passed the acceptance test.
在通过验收测试之后，任何对产品的组件的更改（包括文档）。

## Why Postdelivery Maintenance Is Necessary 为什么交付后维护是必要的

- **Corrective maintenance 纠错性维护**
	- To correct residual faults 修正残留的错误
- **Perfective maintenance 完善性维护**
	- Client requests changes to improve product effectiveness. 客户需求更改来提高产品有效性。
- **Adaptive maintenance 适应性维护**
	- Responses to changes in the environment in which the product operates.
	  为适应产品运行环境的变化需要对产品进行修改。

## What Is Required of Postdelivery Maintenance Programmers? 就交付后维护程序员的要求是什么？

Maintenance is a major income source. 维护是主要收入来源。

Postdelivery maintenance is one of the most difficult aspects of software production because postdelivery maintenance incorporates aspects of all other workflows.
交互后维护是软件生产中最困难的方面之一，因为交付后维护工作涵盖了所有其他工作流的各个方面。

How to minimize regression faults: 如何最小化回归错误：

- Consult the detailed documentation for the product **as a whole**. 查询将产品 **作为一个整体** 的详细文档。
- Consult the detailed documentation for **each individual module**. 查询 **每个独立模块** 的详细文档。

The programmer now changes the source code. 程序员现在修改源代码。

- Test that the modification works correctly. 测试修改的部分是否工作正确。
	- Using specially constructed test cases. 使用专门构造的测试用例。
- Check for regression faults. 检查回归错误。
	- Using stored test data. 使用存储的测试用例。
- Add the specially constructed test cases to the stored test data for future regression testing.
  添加特别构造的测试用例到存储测试用例中，以备以后的回归测试。
- **Document all changes. 修改文档。**

No form of maintenance is a task for an unsupervised beginner, or should be done by a less skilled computer professional.
没有哪种形式的维护是无人看管的初学者的任务，或应当由缺乏技巧的程序员来做的。

## Postdelivery Maintenance Mini Case Study 交付后维护小型实例研究

略

## Management of Postdelivery Maintenance 交付后维护的管理

### Defect Reports 缺陷报告

If the product appears to function incorrectly, the user files a defect report.
如果产品运行不正确，用户提交一个缺陷报告。

The maintenance programmer should first consult the defect report file.
维护程序员应当首先参考缺陷报告文件。

It contains all reported defects not yet fixed, and suggestions for working around them.
它包含所有已经发现但尚未纠正的所有缺陷，以及如何绕开它们的建议。

The new defect is now filed in the defect report file, together with supporting documentation.
新的缺陷现在要连同所有支持其结论的稳当，一同加入缺陷报告文件中。

-	Listings 清单
- Designs 设计
- Manuals 手册

### Authorizing Changes to the Product 批准对产品的修改

Corrective maintenance 纠错性维护

- Assign a maintenance programmer to determine the fault and its cause, then repair it.
  分配一个维护程序员找出错误和起因，然后修复。
- Test the fix, test the product as a whole (regression testing).
  测试修复部分，测试整个产品（回归测试）。
- Update the documentation to reflect the changes made. 更新文档体现修改内容。
- Update the prologue comments to reflect. 更新序注释来体现。

Adaptive and perfective maintenance 适应性和完善性维护

- As with corrective maintenance, except there is no defect report.
  类似于纠错性维护，除了没有缺陷报告。
- There is a change in requirements instead. 只有对需求的变更。

### Ensuring Maintainability 确保可维护性

略

### The Problem of Repeated Maintenance 迭代维护造成的问题

The moving target problem is exacerbated during postdelivery maintenance
移动目标问题在交付后维护时会恶化。

## Maintenance of Object-Oriented Software 面向对象软件的维护

The object-oriented paradigm apparently promotes maintenance in four ways.
面向对象范型实际上提出了维护的四种方式。

- The product consists of independent units 产品包含独立单元
- Encapsulation (conceptual independence) 封装（概念独立）
- Information hiding (physical independence) 信息隐藏（物理独立）
- Message-passing is the sole communication. 消息传递是唯一的通信方式、

Three obstacles 三个障碍

- The complete inheritance hierarchy can be large. 完整的继承层次结构会很大。
- The consequences of polymorphism and dynamic binding. 多态和动态捆绑的关系。
- The consequences of inheritance. 继承之间的关系。

**Inheritance、Polymorphism and dynamic binding can have a positive effect on development, but a negative effect on maintenance.
继承、多态和动态隐藏会对开发有积极的影响，但对维护会十分消极。**

## Postdelivery Maintenance versus Development Skills 交付后维护技能与开发技能

Maintenance programmers must not merely be skilled in a broad variety of areas, they must be highly skilled in all those areas.
维护程序员不能仅掌握各个领域的技能，而是要高度熟练地掌握所有那些领域的技能。
Specialization is impossible for the maintenance programmer.
对维护程序员来讲，专攻是不可能的。

## Reverse Engineering 逆向工程

When the only documentation for postdelivery maintenance is the code itself:
当交付后维护的文档只有代码本身时：

- **Start with the code. 从代码开始。**
- **Recreate the design. 重新创建设计。**
- **Recreate the specifications (extremely hard). 重新创建规格说明文档。**
- **CASE tools can help (flowcharters, other visual aids). 使用 CASE 工具帮助。**

Reengineering 再工程

- Reverse engineering, followed by forward engineering. 即逆向工程，对比正向工程。
- **Lower to higher to lower levels of abstraction. 从低层次抽象发展到高层次抽象，再到低层次。**

Restructuring 重构

- **Improving the product without changing its functionality. 不改变产品功能的前提下，对产品加以改进。**

## Testing during Postdelivery Maintenance 交付后维护期间的测试

略

## CASE Tools for Postdelivery Maintenance 交付后维护的 CASE 工具

略

## Metrics for Postdelivery Maintenance 交付后维护的度量

Defect report metrics 缺陷报告度量

- Defect classifications 缺陷分类
- Defect status 缺陷数

## Postdelivery Maintenance: The MSG Foundation Case Study 交付后维护：MSG 基金实例研究

略

## Challenges of Postdelivery Maintenance 交付后维护面临的挑战

略
