[toc]

OOA is a **semiformal** analysis technique for the object-oriented paradigm.
面向对象分析是面向对象范型的 **半形式化** 分析技术。

## The Analysis Workflow 分析工作流

- The analysis workflow has two aims: 分析工作流有两个目标：
	- Obtain a deeper understanding of the requirements. 得到对需求更深的理解。
	- Describe them in a way that will result in a maintainable design and implementation.
	  按设计和实现易于维护的思路描述需求。

- There are three types of classes: 有三种类：
	- **Entity classes 实体类**
		- Models long-lived information. 长期存在的模型。
	- **Boundary classes 边界类**
		- Models the interaction between the product and the environment.
		  为软件产品和它的参与者之间的交互行为建模。
		- A boundary class is generally associated with input or output.
		  边界类通常与输入和输出相关。
	- **Control classes 控制类**
		- Models complex computations and algorithms.
		  为复杂的计算和算法建模。

![三种类的 UML 标识](http://oxnec2zdn.bkt.clouddn.com/software-engineering/ThreeClassTypes.png)

## Extracting the Entity Classes 提取实体类

Perform the following three steps incrementally and iteratively.
包括三个迭代和递增地完成的步骤：

- **Functional modeling 功能建模**
- **Class modeling 实体类建模**
- **Dynamic modeling 动态建模**

## Object-Oriented Analysis: The Elevator Problem Case Study 面向对象分析：电梯问题实例研究

略

## Functional Modeling: The Elevator Problem Case Study 功能建模：电梯问题实例研究

A use case describes the interaction between **he product** and **the actors (external users)**.
用例描述了 **产品** 和 **参与者（即产品的外部用户）** 之间的交互行为。

### Scenarios 场景

A use case provides a generic description of the overall functionality.
用例提供了整个功能的一般描述。

A scenario is an instance of a use case.
场景是用例的一个实例。

## Entity Class Modeling : The Elevator Problem Case Study 实体类建模：电梯问题实例研究

### Noun Extraction 名词抽取

1. **Concise problem definition. 精炼问题定义。**
2. **Identify the nouns. 分辨名词。**
3. **Delete which is outside the problem boundary and abstract. 删除问题边界外和抽象名词。**

### CRC Cards 类职责协作卡片

For each class, fill in a card showing: 对于每个类，填写卡片：

1. Name of Class 类名
2. Functionality (Responsibility) 功能（职责）
3. List of classes it invokes (Collaboration) 调用其他类的列表（协作）

- Strength 优点
	- When acted out by team members, CRC cards are a powerful tool for highlighting missing or incorrect items.
	  当一个小组利用它时，在小组成员之间的交互可以突出显示一个类中遗漏的或不正确的字段。

- Weakness 缺点
	- If CRC cards are used to identify entity classes, domain expertise is needed.
	  如果 CRC 卡片用于定义实体类，则需要领域经验。

## Dynamic Modeling: The Elevator Problem Case Study 动态建模：电梯问题实例研究

略

## The Test Workflow: Object-Oriented Analysis 测试流：面向对象分析

Distribute the control. 分离控制。
Instead of having one central controller. 而不是有一个中心控制器。

We may need to return to the object-oriented analysis workflow during the object-oriented design workflow.
在面向对象设计流有必要返回面向对象分析流。

## Extracting the Boundary and Control Classes 抽取边界类和控制类

Each nontrivial computation is modeled by a control class.
每个重要的计算由控制类进行建模。
Each input screen, output screen, and report is modeled by its own boundary class.
每个输入屏幕、输出屏幕和打印的报表由它自己的边界类建模。

## The Initial Functional Model: MSG Foundation 初始功能模型：MSG 基金实例研究

略

## The Initial Class Diagram: MSG Foundation 初始类图：MSG 基金实例研究

The aim of entity modeling step is to extract the entity classes, determine their interrelationships, and find their attributes.
实体类建模步骤的目的是提取实体类、确定它们的交互关系，并找出他们的属性。

## The Initial Dynamic Model: MSG Foundation 初始动态建模：MSG 基金实例研究

A **statechart** is drawn that reflects all the operations performed by or to the system, indicating the events that cause the transition from state to state.
**状态图** 反映系统或对系统完成的所有操作，指出引起从一个状态转向另一个状态的时间。
The operations are determined from the scenarios.
操作由场景决定。
An **event** causes a transition between states.
一个 **事件** 引起状态之间的转变。

## Revising the Entity Classes: MSG Foundation 修订实体类：MSG 基金实例研究

The only way a value can be stored on a long-term basis is as an attribute of an instance of that class or its subclasses.
长期存储一个值的唯一方式是把它作为那个类或它的子类的一个实例或一个属性。

## Extracting the Boundary Classes: MSG Foundation 抽取边界类：MSG 基金实例研究

略

## Extracting the Control Classes: MSG Foundation 抽取控制类：MSG 基金实例研究

略

## Use-Case Realization: The MSG Foundation Case Study 用例实现：MSG 基金实例研究

The process of extending and refining use cases is called ****use-case realization.
扩展和求精用例的这个过程称为 **用例实现**。
The realization of a specific scenario of a use case is depicted using an **interaction diagram**.
**交互图** 描述了用例的一个特定场景的实现。

The strength of a **sequence diagram** is that it shows the flow of messages and their order unambiguously.
**顺序图** 的好处是它明确地显示出消息流，消息的次序特别清楚。
A **collaboration diagram** is similar to a class diagram.
**协作图** 类似于类图。

## Incrementing the Class Diagram: The MSG Foundation 类图递增：MSG 基金实例研究

略

## The Test Workflow: MSG Foundation 测试流：MSG 基金实例研究

略

## The Specification Document in the Unified Process 统一过程中的规格说明文档

The Unified Process is **use-case driven**.
统一过程是 **用例驱动** 的。
The client can therefore appreciate how the product works equally well from a use case together with its scenarios, or
a rapid prototype.
客户通过场景中的用例或快速原型理解产品将如何运行。

- The use cases are successively refined, with more information added each time.
  用例通过每次添加更多信息而得到成功地求精。
- The rapid prototype is discarded.
  快速原型会被抛弃。

## More on Actors and Use Cases 关于参与者和用例更详细的内容

- Construct the use-case business model. 建造用例业务模型。
- Consider only those parts of the business model that correspond to the proposed software product.
  只考虑与提议中的软件产品对应的业务模型中的哪些部分。
- The actors in this subset are the actors we seek. 在这个子集中的参与者就是我们寻找的参与者。

## CASE Tools for the Object-Oriented Analysis Workflow 面向对象分析流的 CASE 工具

略

## Metrics for the Object-Oriented Analysis Workflow 面向对象分析流的度量

A measure of size of the object-oriented analysis is **number of pages of UML diagrams**.
面向对象分析的一种测量规模大小的方法是 **计算 UML 图的页面**。

## Challenges of the Object-Oriented Analysis Workflow 面向对象分析流面临的挑战

略
