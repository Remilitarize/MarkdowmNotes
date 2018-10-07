[toc]

## Reuse Concepts 重用的概念

Reuse is the use of components of one product to facilitate the development of **a different product with different functionality**.
重用指使用一个产品中的组件来简化 **另一个功能不同的产品** 的开发。

- Thte two types of reusable 两种类型的重用
	- **Opportunistic (accidental) reuse 机会（偶然）重用**
	- **Systematic (deliberate) reuse 系统（有意）重用**

## Impediments to Reuse 重用的障碍

- Not invented here (NIH) syndrome NIH 综合症
- Concerns about faults in potentially reusable routines. 关心潜在可重用程序中的错误。
- Storage–retrieval issues 存储—检索问题
- Cost of reuse 重用的开销
- Legal issues (contract software only) 法律问题（仅合同软件）
- Lack of source code for COTS components 缺乏商业软件组件的源代码

## Reuse Case Studies 重用实例研究

Software developed in one context needs to be **retested** when integrated into another context.
在一种环境下开发出的额软件用于另一个环境时，必须 **重新进行测试**。

## Objects and reuse 对象和重用

We cannot reuse a module unless the data are identical. 除非数据完全相同，我们不能重用模块。

## Reuse During Design and Implementation 设计和实现的重用

### Design Reuse 设计重用

Opportunistic reuse of designs is common when an organization develops software in only one application domain.
当组织开发软件只在一个应用领域中时，设计的偶然重用是普遍的。

- **Library or Toolkit 库或工具包**
	- A set of reusable routines. 一组可重用的程序。
- **Application framework 框架**
	- A framework incorporates the control logic of the design. 框架包含设计的控制逻辑。
- **Design patterns 设计模式**
	- A pattern is a solution to a general design problem. 大体上解决设计问题的解决方案。
- **Software architecture 软件体系结构**
	- Encompasses a wide variety of design issues, include 包含各种设计问题
		- Organization in terms of components. 关于组件的组织。
		- How those components interact. 组件之间如何联系。

### Component-Based Software Engineering 基于组件软件工程

略

## More on Design Patterns 更多设计模式

略

## Categories of Design Patterns 设计模式的种类

略

## Strengths and Weaknesses of Design Patterns 设计模式的优缺点

- Strengths 优点
	- Design patterns promote reuse by solving a general design problem.
	  设计模式通过解决通常的设计问题来促进重用。
	- Design patterns provide high-level design documentation, because patterns specify design abstractions.
	  设计模式提高高层次的设计文档，因为这些模式把设计抽象列为条件。
	- Implementations of many design patterns exist.
	  许多设计模式的实现已经存在。
	- A maintenance programmer who is familiar with design patterns can easily comprehend a program that incorporates design patterns.
	  如果维护程序员对设计模式很熟悉，将更容易领会加入了设计模式的程序，即使他以前从没有看到过该特定的程序。
- Weaknesses 缺点
	- The use of the 23 standard design patterns may be an indication that the language we are using is not powerful enough.
	  在软件产品中使用的 23 个标准设计模式可能意味着我们正使用的语言不够强大。
	- There is as yet no systematic way to determine when and how to apply design patterns.
	  还没有系统化的方式确定应用设计模式的实际和方法。
	- Multiple interacting patterns are employed to obtain maximal benefit from design patterns.
	  要想从设计模式中获取最大收益，需要使用多个互相关联的模式。
	- It is all but impossible to retrofit patterns to an existing software product.
	  对使用传统范型构件的软件产品维护时，改进类和对象基本不可能。

## Reuse and the World Wide Web 重用与万维网

略

## Reuse and Postdelivery Maintenance 重用和交付后维护

略

## Portability 可移植性

- Product P 产品 P
	- Compiled by compiler C<sub>1</sub>, then runs on machine M<sub>1</sub> under operating system O<sub>1</sub>.
	  由编译器 C<sub>1</sub> 进行编译，然后运行在硬件配置为 H<sub>1</sub> 源计算机上，操作系统为 O<sub>1</sub>。
- Need product P', functionally equivalent to P 需要功能上等价于 P 的产品 P'
	- Compiled by compiler C<sub>2</sub>, then runs on machine M<sub>2</sub> under operating system O<sub>2</sub>.
	  由编译器 C<sub>2</sub> 进行编译，然后运行在硬件配置为 H<sub>2</sub> 源计算机上，操作系统为 O<sub>2</sub>。
- P is **portable** if it is **cheaper** to convert P into P' than to write P' from scratch.
  如果把 P 转换为 P' 的成本比从头开始编写 P' 的 **成本少很多**，则产品 P 是 **可移植的**。

### Hardware Incompatibilities 硬件的不兼容性

- Storage media incompatibilities 存储媒介不兼容
- Character code incompatibilities 字符编码不兼容
- Word size 字大小

### Operating System Incompatibilities 操作系统的不兼容性

- Job control languages (JCL) can be vastly different. 作业控制语言（JCL）有巨大的不同。
- Virtual memory vs. overlays 虚拟内存与平台

### Numerical Software Incompatibilities 数值计算软件的不兼容性

Differences in word size can affect accuracy. 不同的字大小可能影响精度。

### Compiler Incompatibilities 编译器的不兼容性

略

## Why Portability? 为什么要可移植性？

- Portability is essential. 可移植性是必要的。
	- Good software lasts 15 years or more. 好的软件产品可有 15 年或更长的生存期。
	- Hardware is changed every 4 years. 硬件每隔 4 年将更新一次。
- Portability can lead to increased profits. 可移植性可以增加收益。
	- Multiple copy software. 多次复制软件。
	- Documentation (especially manuals) must also be portable. 文档（特别是用户手册）也必须是可移植的。

##Techniques for Achieving Portability 实现可移植性的技术

Obvious technique：Use standard constructs of a popular high-level language.
明显的原则：使用一种流行的高级编程语言的标准版。

### Portable System Software 可移植的系统软件

- Isolate implementation-dependent pieces. 隔离依赖于实现的程序段。
- Utilize levels of abstraction. 使用抽象层次。

### Portable Application Software 可移植的应用软件

- Use a popular programming language. 使用流行编程语言。
- Use a popular operating system. 使用流行操作系统。
- Adhere strictly to language standards. 严格遵守语言标准。
- Avoid numerical incompatibilities. 避免数值的不兼容性。
- Document meticulously. 精心设计文档。

### Portable Data 可移植的数据

- File formats are often operating system-dependent. 不同的操作系统通常使用不同的格式。
- Porting structured data. 移植结构化数据。
	- Construct a sequential (unstructured) file and port it. 建造一个顺序的（非结构化的）文件并移植。
	- Reconstruct the structured file on the target machine. 在目标机器上重建结构化的文件。
	- This may be nontrivial for complex database models. 对于复杂的数据库模型是不简单的。

## Strengths of and Impediments to Reuse and Portability 重用和可移植的优点和障碍

- Strengths 优点
	- Reuse 重用
		- Shorter development time 较短开发时间
		- Lower development cost 较低开发开销
		- High-quality software 高质量软件
		- Shorter maintenance time 较短维护时间
		- Lower maintenance cost 较低维护开销
	- Portability 可移植性
		- Software has to be ported to new software every 4 yeares or so. 大约每 4 年软件必须移植到新的硬件。
		- More copies of COTS software can be sold. 可以卖更多的 COTS 软件的副本。
- Impediments 障碍
	- Reuse 重用
 		- NIH syndrome NIH 综合症
		- Potential quality issues 潜在质量问题
		- Retrieval issues 修补问题
		- Cost of making a component reusable(opportunistic reuse) 建造一个可重用组件的成本（机会重用）
		- Cost of making a component reusable(systematic reuse) 建造一个未来可重用组件的成本（系统重用）
		- Legal issues(contract software only) 法律问题（仅合同软件）
		- Lack of source code for COTS components 缺乏 COTS 组件的源代码
	- Portability 可移植性
		- Potential incompatibilities 潜在的不兼容性
			- Hardware 硬件
			- Operating systems 操作系统
			- Numerical software 数值计算软件
			- Compilers 编译器
			- Data formats 数据格式
