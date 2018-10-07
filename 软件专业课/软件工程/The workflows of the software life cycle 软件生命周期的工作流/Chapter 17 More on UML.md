[toc]

## UML Is Not a Methodology UML 不是一种方法

UML is an acronym for Unified Modeling Language. UML 是统一建模语言的缩写。

UML is a notation, not a methodology. UML 是一种符号，不是一个方法。

## Class Diagrams 类图

![ClassDiagram](http://oxnec2zdn.bkt.clouddn.com/software-engineering/ClassDiagram.png)

<span style="text-decoration:underline">`bank account : Bank Account Class`</span>

- `bank account` is an object, an instance of a class `Bank Account Class`.
  `bank account` 是一个对象，是类 `Bank Account Class` 的一个实例。
- The **underlining** denotes an object. 用 **下划线** 表示对象。
- The **colon** denotes "an instance of". 用 **冒号** 表示 "一个实例"。
- The **boldface** and **initial upper case letters** denote that this is a class.
  用 **黑体字** 和 **首字母大写** 表示这是一个类。

UML allows a shorter notation when there is no ambiguity. 当不会产生混淆时，UML 允许使用一个较短的表示。
<span style="text-decoration:underline">`bank account`</span>

UML visibility prefixes UML 可见性前缀

- Prefix **+** indicates that an attribute or operation is **public**. 前缀 **+** 表示一个属性或操作是 **`public`**。
- Prefix **–** denotes that the attribute or operation is **private**. 前缀 **-** 表示一个属性或操作是 **`private`**。
- Prefix **#** denotes that the attribute or operation is **protected**. 前缀 **#** 表示一个属性或操作是 **`protected`**。

![ClassDiagram1](http://oxnec2zdn.bkt.clouddn.com/software-engineering/ClassDiagram1.png)

### Aggregation 聚合

Aggregation is the UML term for the **part-whole** relationship. 聚合是 UML 中表示 **局部-整体** 关系的术语。

![Aggregation](http://oxnec2zdn.bkt.clouddn.com/software-engineering/Aggregation.png)

The **open diamonds** denote aggregation. 使用空心菱形表示聚合。

### Multiplicity 多重性

![Multiplicity](http://oxnec2zdn.bkt.clouddn.com/software-engineering/Multiplicity.png)

The numbers next to the ends of the lines denote **multiplicity**. 线的端点处旁边的数字表示 **多重性**。

The number of times that the one class is associated with the other class.
数字表示一个类与其他类关联的次数。

**Two dots ..** denote a range. **两个点** 表示范围。
The **asterisk by itself** means zero or more. **星号本身** 表示零或多个。
An **asterisk in a range** denotes means "or more".
在 **一个范围后的星号** 表示 "或多个"。

### Composition 组合

Composition is a stronger form of aggregation.
组合是聚合的更强的形式。

- Association 聚合
	- Models the part–whole relationship. 建立部分-整体关系模型。
- Composition 组合
	- Also models the part–whole relationship. 也是建立部分-整体关系模型。
	- Every part may belong to only one whole. 每个部分可能只属于一个整体。
	- **If the whole is deleted, so are the parts. 如果删除了整体，部分也被删除。**

Composition is depicted by a **solid diamond**. 组合用实心菱形表示。

![Composition](http://oxnec2zdn.bkt.clouddn.com/software-engineering/Composition.png)

### Generalization 泛化

![Generalization](http://oxnec2zdn.bkt.clouddn.com/software-engineering/Generalization.png)

Inheritance is a special case of generalization.
继承是泛化的一个特例。

The UML notation for generalization is an **open triangle**.
泛化在 UML 标记中使用 **空心三角形**。

### Association 关联

![Association](http://oxnec2zdn.bkt.clouddn.com/software-engineering/Association.png)

The **optional navigation triangle** shows the direction of the association.
**可选的实心三角形** 表示关联的方向。

Now consults has become a class, Consults Class, which is called an association class.
现在咨询业成为一个类，咨询类，称为 **关联类**。

## Notes 注解

A comment in a UML diagram is called a **note**.
UML 中注释称为 **注解**。

Depicted as a **rectangle** with the top right-hand corner bent over.
使用一个右上角折起的 **矩形** 框表示。

## Use-Case Diagrams 用例图

A use case is a model of the interaction between external users of a software product (actors) and the software product itself.
用例是软件产品的外部用户和软件产品自身的交互模型。

The open triangle points toward the more general case.
空心三角形指向更普通的实例。

## Stereotypes 构造型

![Stereotype](http://oxnec2zdn.bkt.clouddn.com/software-engineering/Stereotype.png)

The names of stereotypes appear between **guillemets**. 构造型的名字出现在 **书名号** 之间。

## Interaction Diagrams 交互图

Interaction diagrams show how objects interact with one another.
交互图显示软件产品中的对象与另一个对象交互的方式。

UML supports two types of interaction diagrams: UML 支持两种类型的交互图：

- Sequence diagrams 顺序图
- Collaboration diagrams 通信图

![Sequence Diagram](http://oxnec2zdn.bkt.clouddn.com/software-engineering/SequenceDiagram.png)

**Lifeline**: An active object is denoted by a **thin rectangle** (activation box) in place of the **dashed line**.
**生命线**：一个活跃对象由 **虚线** 位置的 **窄矩形**（激活框）表示。
Destruction of that object after it receives message is denoted by the **heavy X**.
在对象发送消息之后销毁该对象用 **重 X** 表示。

A message is optionally followed by a message sent back to the object that sent the original message.
一个消息可以选择是否发出原消息之后返回一个消息。

Even if there is a reply, it is not necessary that a specific new message be sent back.
即使有回复，也不必返回一个新消息。
Instead, a **dashed line ending in an open arrow** indicates a return from the original message, as opposed to a new message.
相反，画出 **一个终止于开口箭头的虚线** 表示从最初的消息返回，与一个新的消息相对。

A **guard (condition)** is something that is true or false. **保护（条件）** 是某件事是真或假。
The message sent only if the guard is true. 仅为真时消息才发送。

A self-call：An object can send a message to itself.
自调用：对象可以向本身发送消息。

Collaboration diagrams are equivalent to sequence diagrams.
通信图等效于顺序图。

- Use a sequence diagram when the transfer of information is the focus of attention.
  当信息转换是注意的焦点时使用顺序图。
- Use a collaboration diagram when concentrating on the classes.
  当集中在类上时使用通信图。

## Statecharts 状态图

![Statechart](http://oxnec2zdn.bkt.clouddn.com/software-engineering/Statechart.png)

An event also causes transitions between states.
事件也在状态间引起转移。

## Activity Diagrams 活动图

![Activity Diagram](http://oxnec2zdn.bkt.clouddn.com/software-engineering/ActivityDiagram.png)

Activity diagrams show how various events are coordinated.
活动图显示各种事件是如何协调的。

A **fork** has one incoming transition, and many outgoing transitions, each of which starts an activity to be executed in parallel with the other activities.
一个 **交叉** 有一个输入转移和多个输出转移，每个转移开始一个与其他活动并行执行的活动，当全部并行活动完成时，开始一个输出转移。

A **join** has many incoming transitions, each of which lead from an activity executed in parallel with the other activities, and one outgoing transition that is started when all the parallel activities have been completed.
一个 **结合** 有多个输入转移（每个转移都来自与其他活动并行执行的活动）和一个输出转移（当所有并行活动完成后开始）。

Swinlane 泳道

## Packages 包

![Packages](http://oxnec2zdn.bkt.clouddn.com/software-engineering/Package.png)

A large information system is decomposed into relatively independent **packages**.
大信息系统分解为相对独立的 **包**。

## Component Diagrams 组件图

![Component Diagram](http://oxnec2zdn.bkt.clouddn.com/software-engineering/ComponentDiagram.png)

A component diagram shows dependencies among software components, including
组件图显示软件组件之间的依赖度，包括

- Source code (represented by a note) 源代码
- Compiled code 编译代码
- Executable load images 可执行载入映像

## Deployment Diagrams 部署图

![Deployment Diagram](http://oxnec2zdn.bkt.clouddn.com/software-engineering/DeploymentDiagram.png)

A deployment diagram shows on which hardware component each software component is installed (or deployed).
部署图显示每个软件组件安装（或部署）在哪个硬件组件上。
It also shows the communication links between the hardware components.
它也显示了在硬件组件间的通信链接。

## Review of UML Diagrams UML 图回顾

A use case models the interaction between actors and the information system.
用例建模参与者（软件产品和外部用户）间以及软件产品本身的交互。
A use-case diagram is a single diagram that incorporates a number of use cases.
用例图是结合了一些用例的单个图。
A class diagram is a model of the classes showing the static relationships between them.
类图是类的模型，显示类之间的静态关系，包括关联和泛化。
A statechart shows states (specific values of attributes of objects), events that cause transitions between states (subject to guards), and actions taken by objects.
状态图显示状态（对象属性的特定值）、导致状态（受保护约束）之间转移的事件，以及对象采取的动作和活动。
An interaction diagram (sequence diagram or collaboration diagram) shows how objects interact as messages are passed between them.
交互图（顺序图或通信图）显示当消息在对象之间传递时，对象相互之间交互的方式。
An activity diagram shows how events that occur at the same time are coordinated.
活动图显示发生在同一时间的事件是如何协调的。

## UML and Iteration UML 和迭代

略
