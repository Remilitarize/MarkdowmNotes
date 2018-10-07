[toc]

The two basic ways of designing a product

- Operation-oriented design 面向操作设计
- Data-oriented design 面向数据设计

## Design and Abstraction 设计和抽象

Classical design activities 传统设计活动

- **Architectural design 结构化设计**
	- Input:Specifications 输入：规格说明文档
	- Output:Modular decomposition 输出：模块化分解
- **Detailed design 详细设计**
	- Each module is designed. 设计每个模块。
- **Design testing 设计测试**

## Operation-Oriented Design 面向操作设计

- Data flow analysis 数据流分析
- Transaction analysis 事务分析

## Data Flow Analysis 数据流分析

Every product transforms input into output.
每个产品将输入转变为输出。

- "Point of highest abstraction of input." 输入的最高抽象点
- "Point of highest abstract of output." 输出的最高抽象点

Decompose the product into three modules: 将产品分解为三个模块：

- Input module 输入模块
- Transform module 转换模块
- Output module 输出模块

### Mini Case Study: Word Counting 小型实例研究：字数统计

Two formats for representing the detailed design: 两个形式的表示细节设计

- Tabular 表格
- **Pseudocode** (PDL — program design language) **伪代码**（PDL —— 程序设计语言）

### Data Flow Analysis Extensions 数据流分析扩展

In real-world products, there is more than one input stream, and more than one output stream.
在现实世界的产品中，有不止一个输入流和输出流。

![数据流图](http://oxnec2zdn.bkt.clouddn.com/software-engineering/DFD.png)

## Transaction Analysis 事务分析

A transation is an ooperation from the viewpoint of the user of the product.
事务是从产品用户的观点来看的一个操作。

## Data-Oriented Design 面向数据设计

The basic principle：To design the product according to the structure of the data on which it is to operate.
基本原则：根据对其运行的数据结构设计产品。

- Has never been as popular as action-oriented design.
  从来没有像面向操作设计那样流行过。
- With the rise of OOD, data-oriented design has largely fallen out of fashion.
  伴随着面向对象范型的出现，面向数据设计已经落伍了。

## Object-Oriented Design 面向对象设计

Aim：Design the product in terms of the classes extracted during OOA.
目的：按照在面向对象分析期间提取的类设计产品。

OOD consists of two steps: 面向对象设计包含两个步骤：

1. **Complete the class diagram. 完成类图。**
2. **Perform the detailed design. 进行详细设计。**

## Object-Oriented Design: The Elevator Problem Case Study 面向对象设计：电梯问题实例研究

略

## Object-Oriented Design: The MSG Foundation Case Study 面向对象设计：MSG 基金实例研究

略

## The Design Workflow 设计工作流

To refine the artifacts of the analysis workflow until the meterial is in a form that can be implemented by the programmers.
求精分析流制品直至程序员可以实现的形式。

Decisions to be made include: 需要做出的决定包括：

- Implementation language 实现语言
- Reuse 重用
- Portability 可移植性

The objective is to break up the upcoming implementation workflow into manageable pieces, termsed **subsystems**.
目标是即将面临的实现流分成可管理的小块，称为 **子系统**。

Why the product is broken into subsystems: 为什么产品分解为子系统：

- It is easier to implement a number of smaller subsystems than one large system.
  实现一些更小的子系统比实现一个大系统容易得多。
- If the subsystems to be implemented are indeed relatively independent, they can be implemented by programming teams working in parallel.
  如果要实现的子系统是真正相对独立的，那么可以由编程小组并行地实现。

The architect needs to make **trade-offs**. 设计师需要提出 **折衷办法**。
It is usually impossible to satisfy all the requirements, functional and nonfunctional, within the cost and time constraints.
几乎不可能开发出满足所有需求——功能上和非功能上——并在成本和时间限制内完成。

## The Test Workflow: Design 测试流：设计

Design reviews must be performed：设计检查必须进行：

- The design must correctly reflect the specifications. 规格书说明文档必须正确地体现在设计中。
- The design itself must be correct. 设计本身必须正确。

- **Transaction-driven inspections 事务驱动审查**
	- Essential for transaction-oriented products. 对面向事务产品是重要的。
	- Specification-driven inspections are also needed. 也需要规格说明驱动审查。

## The Test Workflow: The MSG Foundation Case Study 测试流：MSG 基金实例研究

Even if no faults are found, the design may be changed during the implementation workflow.
即使没有找到错误，也可能在实现流再次修改设计。

## Formal Techniques for Detailed Design 详细设计的形式化技术

略

## Real-Time Design Techniques 实时设计技术

略

## CASE Tools for Design 设计的 CASE 工具

略

## Metrics for Design 设计的度量

- Cohesion 内聚
- Coupling 耦合
- Fault statistics 错误统计数据

Cyclomatic complexity is problematic. 秩复杂度是不确定的。

## Challenges of the Design Phase 设计流面临的挑战

- The design team should not do too much. 设计团队不要做得过多。
	- The detailed design should not become code. 详细设计不应变为代码。
- The design team should not do too little. 设计团队不应做得过少。
	- It is essential for the design team to produce a complete detailed design.
	  必须由设计团队产生完整的详细设计。
