[toc]

## Stepwise Refinement 逐步求精

Postpone decisions as to details as late as possible to be able to concentrate on the important issues.
尽可能将细节的定义推延到最后，以便集中精力在重要的事项上。

- Miller’s law 米勒法则
	- A human being can concentrate on 7 ± 2 items at a time.
	  一个人在同一时间可以将注意力集中在 7 ± 2 项事上。

## Cost–Benefit Analysis 成本-收益分析

- Compare costs and future benefits. 比较成本和未来的收益。
	- **Estimate costs. 估计成本。**
	- **Estimate benefits. 估计收益。**
	- **State all assumptions explicitly. 明确叙述所有推断。**
- Tangible costs/benefits are easy to measure. 能够确定的成本/收益容易度量。
- Make assumptions to estimate intangible costs/benefits. 推断来估计无法确定的成本/估计。

## Divide-and-Conquer 分治

Solve a large, hard problem by breaking up into smaller subproblems that hopefully will be easier to solve.
把不好解决的大问题分解成小的问题，这样有望更容易解决。

- Problem
	- The approach does not tell us how to break up a software product into appropriate smaller components.
	  这个方法不能告诉我们"如何"将软件产品分解为核实的小组件。

## Separation of Concerns 关注分离

The process of breaking a software product into components with minimal overlap of functionality.
将软件产品分成组件的过程，这些组件在功能上尽可能少地重叠。

- Minimizes regression faults. 最小化回归错误
- Promotes reuse. 提倡重用

## Software Metrics 软件度量

To detect problems early, it is essential to measure.
为了更早检测到问题，度量是至关重要的。

- Different Types 不同类别
	- **Product metrics 产品度量**
	- **Process metrics 过程度量**

- The Five Basic Metrics 五个基本度量单位
	- **Size 规模**
		- In lines of code, or better 以代码行或以更好的度量计
	- **Cost 成本**
		- In dollars 以美元计
	- **Duration 持续时间**
		- In months 以月计
	- **Effort 工作量**
		- In person months 以人月计
	- **Quality 质量**
		- Number of faults detected 以检测出的错误数计

## CASE(Computer-Aided Software Engineering) 计算机辅助软件工程

CASE can support the entire life-cycle.
计算机辅助软件工程可以支持整个生命周期。

## Taxonomy of CASE 计算机辅助软件工程的分类

- UpperCASE (front-end tool) 高端 CASE（前端工具）
- LowerCASE (back-end tool) 低端 CASE（后端工具）

- **Tools 工具**
  - A CASE tool assists in **just one aspect** of the production of software.
    CASE 工具是只在软件生产的 **某一方面** 起帮助作用的软件产品。
- **Workbench 工作平台**
	- A CASE workbench is a collection of tools that **together support one or two activities**.
    CASE 工作平台是一些工具的集合，**共同支持一个或两个活动**。
- **Environment 环境**
	- A CASE environment supports **the complete software process**.
    CASE 环境支持 **整个软件开发过程**。

## Scope of CASE 计算机辅助软件工程的范围

略

## Software Versions 软件版本

There are two types of versions. 有两个版本.

- **Revisions 修订版**
- **Variations 变种版**

### Revisions 修订版

- A version to **fix a fault** in the artifact. **修复软件制品中的错误** 的版本。
- We **cannot** throw away an incorrect version. 我们 **不能** 丢弃不正确的版本。
- Perfective and adaptive maintenance also result in revisions.
  完善性维护和适应性维护也导致一个修订版。

### Variations 变种版

- A variation is a version for **a different operating syste or hardware**.
  一个变种版是对应 **不同操作系统或硬件** 的版本。

- Variations are designed to coexist in parallel.
  变种版是为共存而设计的。

![修订版和变种版](http://oxnec2zdn.bkt.clouddn.com/software-engineering/Revision-Variation.png)

## Configuration Control 配置控制

- Every code artifact exists in three forms.
  每个代码制品以三种形式存在。
	- Source code 源代码
	- Compiled code 编译代码
	- Executable load image 可执行载入映像
- Configuration 配置
	- A version of each artifact from which a given version of a product is built.
	  某个产品的给定版本所赖以建造的每个制品的特定版本。

- A version-control tool must handle 一个版本控制工具必须处理
	- Updates 更新
	- Parallel versions 同步版本

### Configuration Control during Postdelivery Maintenance 交付后维护期间的配置控制

略

### Baselines 基准

When an artifact is to be changed, **the current version is frozen**.
当一个制品将要修改时，**当前版本将被冻结**。

### Configuration Control during Development 产品开发过程中的配置控制

略

## Build Tools 搭建工具

略

## Productivity Gains with CASE Technology 使用 CASE 技术提高生产力

略
