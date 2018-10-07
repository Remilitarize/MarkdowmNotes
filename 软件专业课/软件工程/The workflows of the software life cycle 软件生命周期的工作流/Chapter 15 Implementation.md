[toc]

## Choice of Programming Language  编程语言的选择

The language is usually specified in the contract. 合同中通常规定好了语言。
The product is to be implemented in the "most suitable" programming language.
合同规定产品要用 "最合适的" 编程语言实现。

How to choose a programming language： 如何选择编程语言：

- Cost–benefit analysis. 成本效益分析
- Compute costs and benefits of all relevant languages. 计算所有相关语言的成本和效益。

## Fourth Generation Languages 第四代语言

- **First generation languages 第一代语言**
	- Machine languages 机器语言
- **Second generation languages 第二代语言**
	- Assemblers 汇编语言
- **Third generation languages 第三代语言**
	- High-level languages 高级语言
- Fourth generation languages 第四代语言
	- Each 4GL statement was intended to be equivalent to 30 or even 50 assembler statements.
	  每个 4GL 语句应当等效于 30 或 50 条机器代码指令。

In particular, many 4GLs are **nonprocedural**. 特别地，许多 4GL 是 **非过程的**。

## Good Programming Practice 良好的编程实践

Use of **consistent and meaningful** variable names. 使用 **一致和有意义的** 变量名。

**Comments** are essential whenever the code is written in a non-obvious way, or makes use of some subtle aspect of the language.
**行内注释** 应当仅用在代码是用一种不显而易见的方式编写，或者使用了该语言中某些难理解的方面的时候。

There are almost **no genuine constants**.  **很少有真正的常量**。

Use **indentation**. 使用 **缩进**。

`if` statements nested to a depth of greater than three should be avoided as poor programming practice.
`if` 语句嵌套超过 3 级是一个较差的编程习惯，应当避免。

## Programming Standards 编码标准

Standards can be both a blessing and a curse. 编码标准既是好事也是坏事。
The aim of standards is to make maintenance easier. 标准的目的是使维护更容易。

## Code Reuse 代码重用

略

## Integration 集成

![Integration](http://oxnec2zdn.bkt.clouddn.com/software-engineering/Integration.png)

- To test artifact a, artifacts b, c, d must be **stubs**.
  为了测试制品 a，必须把制品 b/c 当成 **存根**。
- To test artifact h on its own requires a **driver**, which calls it once, or several times, or many times, each time checking the value returned.
  测试制品 h 需要一个调用它自身一次或多次的 **驱动**，如果可能，要检查接受测试的代码制品的返回值。

### Top-down Integration 自顶向下的继承

If code artifact `mAbove` sends a message to artifact `mBelow`, then `mAbove` is implemented and integrated before `mBelow`.
如果代码制品 `mAbove` 给代码制品 `mBelow` 发消息，那么代码制品 `mAbove` 在代码制品 `mBelow` 之前实现与继承。

### Bottom-up Integration 自底向上的集成

If code artifact `mAbove` calls code artifact `mBelow`, then `mBelow` is implemented and integrated before `mAbove`.
如果制品 `mAbove` 发送一个消息给制品 `mBelow`，那么制品 `mBelow` 在制品 `mAbove` 之前实现与集成。

### Sandwich Integration 三明治集成

- Logic artifacts are integrated top-down. 逻辑制品自顶向下集成。
- Operational artifacts are integrated bottom-up. 操作制品自底向上集成。
- Finally, the interfaces between the two groups are tested. 最后，两组制品之间的接口进行测试。

|Approach 方法|Strengths 优点|Weaknesses 缺点|
|-|-|-|
|Implementation then integration<br />实现然后集成| |No fault isolation.<br />没有错误隔离。<br />Major design faults show up late.<br />主要设计错误发现迟。<br />Potentially resuable code artifacts are not adequately tested.<br />潜在可重用代码制品不能被充分地测试。|
|Top-down integration<br />自顶向下的集成|Fault isolation.<br />错误隔离。<br />Major design faults show up early.<br />主要涉及错误发现早。|Potentially resuable code artifacts are not adequately tested.<br />潜在可重用代码制品不能被充分地测试。|
|Bottom-up integration<br />自底向上的集成|Fault isolation.<br />错误隔离。<br />Potentially reusable code artifacts are adequately tested.<br />潜在可重用的代码制品能被充分地测试。|Major design faults show up late.<br />主要设计错误发现迟。|
|Sandwich integration<br />三明治集成|Fault isolation.<br />错误隔离。<br />Major design faults show up early.<br />主要涉及错误发现早。Potentially reusable code artifacts are adequately tested.<br />潜在可重用的代码制品能被充分地测试。|&nbsp;|

### Integration of Object-Oriented Products 面向对象产品的集成

- Almost always sandwich implementation and integration. 几乎都使用三明治实现和集成。
- Objects are integrated bottom-up. 对象使用自底向上集成。
- Other artifacts are integrated top-down. 其他制品使用自顶向下集成。

### Management of Integration 继承的管理

The integration process must be run by the SQA group. 整个集成过程必须在 SQA 小组的管理下进行。
They have the most to lose if something goes wrong. 如果集成测试工作进行得不正确，则 SQA 小组没有完成主要工作。

## The Implementation Workflow 实现工作流

The aim of the implementation workflow is to implement the target software product.
实现工作流的目的是实现目标软件产品。

- A large product is partitioned into subsystems. 大型软件产品被分成小一些的子系统。
- Subsystems consist of components or code artifacts. 子系统由组件或代码制品组成。

As soon as a code artifact has been coded, the programmer test it, termed **unit texting**.
只要代码制品完成编码，程序员就对其进行测试，这称为 **单元测试**。
Then the module is passed on to the SQA group for further testing.
一旦程序员确认代码制品是正确的，就上交给质量保证小组做进一步的测试。

## The Implementation Workflow: The MSG Foundation Case Study 实现流：MSG 基金实例研究

略

## The Test Workflow: Implementation 测试流：实现

There are two types of methodical unit testing： 有两种类型的单元测试：

- Non-execution-based testing 非执行测试
- Execution-based testing 执行测试

## Test Case Selection 测试用例选择

Worst way — **random testing** 最差的方法——**随机测试**

### Testing to Specifications versus Testing to Code 规格说明测试与代码测试

There are two extremes to testing： 有两个极端的测试：

- **Test to specifications 规格说明测试**
	- Black-box testing 黑盒测试
	- Behavioral testing 行为测试
	- Data-driven testing 数据驱动测试
	- Functional testing 功能测试
	- Input/Output driven testing 输入/输出驱动测试
- **Test to code 代码测试**
	- Glass-box testing 玻璃盒测试
	- White-box testing 白盒测试
	- Logic-driven testing 逻辑驱动测试
	- Structured testing 结构测试
	- Path-oriented testing 面向路径测试

### Feasibility of Testing to Specifications 规格说明测试的可行性

略

### Feasibility of Testing to Code 代码测试的可行性

Each path through a artifact must be **executed at least once**.
代码制品通过的每条路 **最少执行一次**。

Criterion "exercise all paths" is not reliable.
"试验产品中全部路径" 的准则是不可靠的。

## Black-Box Unit-testing Techniques 黑盒单元测试技术

Select a small, manageable set of test cases to **maximize the chances of detecting a fault**, while **minimizing the chances of wasting a test case**.
设计一个较小、可管理的测试用例集，**使检测出错误的机会最大**，**使浪费一个测试用例的机会最小**。
Every test case must detect a previously **undetected** fault.
每个测试用例必须能够检出一个先前 **未检出** 的错误。

- First black-box test cases (testing to specifications). 先使用黑盒测试用例（检测规格说明文档）。
- Then glass-box methods (testing to code). 再使用玻璃盒方法（检测代码）。

### Equivalence Testing and Boundary Value Analysis 等价测试和边界值分析

Range (1..16,383) defines three different equivalence classes:
从 1 到 16383 定义了三个等价类：

- Equivalence Class 1: Fewer than 1 record  等价类1：少于 1 条记录
- Equivalence Class 2: Between 1 and 16,383 records  等价类2：从 1 到 16383 条记录
- Equivalence Class 3: More than 16,383 records  等价类3：多于 16383 条记录

Select test cases on or just to one side of the boundary of equivalence classes.
选取处在或接近一个等价类的边界的测试用例。

- Test case 1: 0 records  测试用例1：0 条记录
	- Member of equivalence class 1 and adjacent to boundary value  等价类 1 的成员且临近边界值
- Test case 2: 1 record  测试用例2：1 条记录
	- Boundary value 边界值
- Test case 3: 2 records  测试用例3：2 条记录
	- Adjacent to boundary value  临近边界值
- Test case 4: 723 records  测试用例4：723 条记录
	- Member of equivalence class 2  等价类 2 的成员
- Test case 5: 16,382 records  测试用例5:16382 条记录
	- Adjacent to boundary value  临近边界值
- Test case 6: 16,383 records  测试用例6:16383 条记录
	- Boundary value  边界值
- Test case 7: 16,384 records  测试用例7:16384 条记录
	- Member of equivalence class 3 and adjacent to boundary value  等价类 3 的成员且临近边界值

### Functional Testing 功能测试

- Test data are devised to test each (lower-level) function separately.
  设计测试数据类分别测试每个功能（低层）。
- Then, higher-level functions composed of these lower-level functions are tested.
  然后测试由这些低层功能组成的高层功能

## Black-Box Test Cases: The MSG Foundation Case Study 黑盒测试用例：MSG 基金实例研究

略

## Glass-Box Unit-Testing Techniques 玻璃盒单元测试技术

- **Statement coverage 语句覆盖**
- **Branch coverage 分支覆盖**
- **Path coverage 路径覆盖**
- Linear code sequences 线性代码序列
- All-definition-use path coverage 完全定义-使用路径覆盖

### Structural Testing: Statement, Branch, and Path Coverage 结构测试：语句、分支和路径覆盖

- Statement coverage 语句覆盖
	- Running a set of test cases in which **every statement is executed at least once**.
	  运行一系列测试用例，在运行期间 **每个语句最少执行一次**。
	- Weakness 缺点
		- Branch statements 分支语句

- Branch coverage 分支覆盖
	- Running a set of test cases in which **every branch is executed at least once** (as well as all statements).
	  运行一系列测试用例，确保 **所有的分支最少测试一次**（和所有语句）。

- Path coverage 路径覆盖
	- Running a set of test cases in which every path is executed at least once (as well as all statements).
	  运行一系列测试用例，确保 **所有的路径最少测试一次**（和所有语句）。
	- Problem 问题
		- The number of paths may be very large. 路径数量会非常大。

- Linear code sequences 线性代码序列
	- Identify the set of points L from which control flow may jump, plus entry and exit points.
	  标识出控制流可以跳出的点的集合 L，集合 L 包括入口和出口点。
	- Restrict test cases to paths that begin and end with elements of L.
	  将测试用例局限于始于 L 的一个元素且终止于 L 的一个元素的路径。
	- This uncovers many faults without testing every path.
	  这项技术发现许多错误而不必测试每条路径。

- All-definition-use-path Coverage 完全定义-使用路径覆盖
	- Identify all paths from **the definition of a variable to the use of that definition**.
	  在 **变量定义和定义的使用** 之间的全部路径都标出。
	- **A test case is set up for each such path. 为每个这样的路径建立一个测试用例。**
	- Disadvantage 缺点
		- Upper bound on number of paths is 2<sup>d</sup>, where d is the number of branches.
		  路径数的上边界是 2<sup>d</sup>，这里 d 是产品中分支语句的个数。

We may have an infeasible path ("dead code") in the artifact.
一条不可能路径（"死代码"）存在于代码制品中。

### Complexity Metrics 复杂性度量

A quality assurance viewpoint provides another approach to glass-box unit testing.
质量保证观点提供另一个玻璃盒单元测试的方法。
If the complexity is unreasonably high, **redesign** and then **reimplement** that code artifact.
如果发现一个代码制品的复杂度不合理地高，**重新设计** 和 **重新实现** 这个代码制品。

- The simplest measure of complexity: 最简单的复杂度度量：
	- Underlying assumption: There is a constant probability p that a line of code contains a fault.
	  隐含假定：一行代码包含一个错误，且存在一个恒定概率 p。
	- The number of faults is indeed related to the size of the product as a whole.
	  错误数确实与整体上软件产品的规模有关。
- Cyclomatic complexity 秩复杂性
	- Essentially the number of decisions (branches) in the artifact.
	  本质上是代码制品中的分支数。

## Code Walkthroughs and Inspections 代码走查和审查

Code reviews lead to rapid and thorough fault detection.
通过代码走查，可以快速并彻底地检测出错误。

## Comparison of Unit-Testing Techniques 单元测试技术的比较

Code inspection is at least as successful at detecting faults as glass-box and black-box testing.
代码审查与白盒和黑盒测试在检测错误方面一样成功。

## Cleanroom 净室

A different approach to software development.
一些不同软件开发技术的组合。

Incorporates 包括

- An incremental process model 递增声明周期模型
- Formal techniques 分析技术
- Reviews 走查

## Potential Problems When Testing Objects 测试对象时潜在的问题

略

## Management Aspects of Unit Testing 单元测试的管理方面

略

## When to Rewrite Rather Than Debug 何时该重实现而不是调试代码制品

For every artifact, management must predetermine the maximum allowed number of faults during testing.
对于每个制品，管理者必须预先确定一个测试期间可允许的最大错误数量。

If this number is reached 如果达到该数字

- Discard 丢弃
- Redesign 重新设计
- Recode 重新编码

The maximum number of faults allowed after delivery is **ZERO**.
在交付后的最大允许检测错误数是 **零**。

## Integration Testing 集成测试

The testing of each new code artifact when it is added to what has already been tested.
每个新的代码制品加入到已集成的模块中时都必须进行测试。

## Product Testing 产品测试

The SQA group must test the product using tests that the SQA group believes closely approximate the forthcoming acceptance tests.
SQA 小组必须使用自认为最接近即将到来的验收测试的方式进行产品测试。

- Black-box test cases for the product as a whole must be run.
  必须对产品进行黑盒测试。
- The robustness of the product as a whole must be tested.
  必须对产品进行健壮性测试。
		- Stress testing 强度测试
		- Volume testing 容量测试
- The SQA group must check that the product satisfies all its constraints.
  SQA 小组必须检查产品是否满足所有限制条件。
- The SQA group must review all documentation to be handed over to the client together with the code.
  SQA 小组必须检查所有的随代码一起交给客户的文档。

## Acceptance Testing 验收测试

The client determines whether the product satisfies its specifications.
客户判定产品是否确实满足规格说明文档。

The four major components of acceptance testing are
验收测试的四个主要元素

- **Correctness 正确性**
- **Robustness 健壮性**
- **Performance 性能**
- **Documentation 文档**

The key difference between product testing and acceptance testing is
产品测试和验收测试的关键不同点是

- Acceptance testing is performed on **actual data**. 验收测试使用 **真实数据**。
- Product testing is preformed on **test data**. 产品测试使用 **测试数据**。

## The Test Workflow: The MSG Foundation Case Study 测试流：MSG 基金实例研究

略

## CASE Tools for Implementation 实现的 CASE 工具

- Version-control tools 版本控制工具
- Configuration-control tools 配置控制工具
- Build tools 搭建工具

### CASE Tools for the Complete Software Process 软件开发全过程的 CASE 工具

A large organization needs an environment. 大型公司需要环境。
A medium-sized organization can probably manage with a workbench.中型公司可能使用工作平台进行管理。
A small organization can usually manage with just tools. 小型公司通常使用工具管理。

### Integrated Development Environments 集成化开发环境

The usual meaning of "integrated" is **user interface integration**.
集成化的最普通的含义是 **用户接口集成**。

- Tool integration 工具集成
	- All tools communicate using the same format. 所有工具通过相同数据格式进行通信。
- Process integration 过程集成
	- The environment supports one specific process. 支持一个具体软件过程的环境。
	- Subset: Technique-based environment 子集：基于技术的环境
	- Advantage of a technique-based environment 基于技术的环境的优点
		- The user is forced to use one specific method, correctly. 可以使用户正确地使用指定的技术。
	- Disadvantages of a technique-based environment 基于技术的环境的缺点
		- The user is forced to use one specific method, so that the method must be part of the software process of that organization. 由于用户使用指定的技术，所以公司的软件过程必须集成了这项指定的技术。

### Environments for Business Application 商业应用环境

略

### Public Tool Infrastructure 公共工具基础结构

PCTE — Portable common tool environment 可移植公共工具环境

- **Not an environment. 不是一个环境。**
- An infrastructure for supporting CASE tools. 提供 CASE 工具所需服务的一种基础结构。

### Potential Problems with Environments 环境的潜在问题

No one environment is ideal for all organizations.
没有任何一种环境对所有的公司是最理想的。

## Metrics for the Implementation Workflow 实现流的度量

The five basic metrics, plus complexity metrics. 五种基本度量，加复杂性度量。

## Challenges of the Implementation Workflow 实现流面临的挑战

略
