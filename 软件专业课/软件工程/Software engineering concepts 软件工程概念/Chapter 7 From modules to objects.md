[toc]

## What Is a Module? 什么是模块？

A lexically contiguous **sequence of program statements**, bounded by **boundary elements**, with **an aggregate identifier**.
词汇上邻接的 **程序语句序列**，由 **边界元素** 限制范围，有一个 **聚合标识符**。

- Maximal relationships within modules, and minimal relationships between modules.
  模块内联系最大，模块间联系最小。

- Composite/Structured Design 组合化/结构化设计
	- **Module cohesion 模块内聚**
		- **Degree of interaction within a module. 模块内部交互的程度。**
	- **Module coupling 模块耦合**
		- **Degree of interaction between modules. 两个模块之间交互的程度。**

- In C/SD, the name of a module is its function. 在组合化/结构化设计，一个模块的名字就是它的功能。

## Cohesion 内聚

**The degree of interaction within a module. 模块内部交互的程度。**

Seven categories or levels of cohesion(non-linear scale). 内聚的 7 个分类或级别（非线性）。

- **Informational cohesion(GOOD) 信息性内聚（较好）**
- **Functional cohesion 功能性内聚**
- **Communicational cohesion 通信性内聚**
- **Procedual cohesion 过程性内聚**
- **Temporal cohesion 时间性内聚**
- **Logical cohesion 逻辑性内聚**
- **Coincidental cohesion(BAD) 偶然性内聚（较差）**

### Coincidental Cohesion 偶然性内聚

A module has coincidental cohesion if it performs **multiple, completely unrelated actions**.
一个模块执行 **多个完全不相关的操作**。

Bad

- It degrades maintainability. 产品的可维护性产生退化。
- A module with coincidental cohesion is not reusable. 具有偶然性内聚的模块是不可重用的。
- The problem is easy to fix. 很容易纠正具有偶然性内聚的模块。
	- Break the module into separate modules, each performing one task.
    将模块分成更小的模块，每个小模块执行一个操作。

### Logical Cohesion 逻辑性内聚

A module has logical cohesion when it performs a series of related actions, one of which is **selected by the calling module**.
当一个模块进行一系列相关的操作，每个操作 **由调用模块来选择** 时，该模块就具有逻辑性内聚。

Bad

- The interface is difficult to understand. 接口难于理解
- Code for more than one action may be intertwined. 完成多个操作的代码互相纠缠在一起。
- Difficult to reuse. 难于重用。

### Temporal Cohesion 时间性内聚

A module has temporal cohesion when it performs a series of actions **related in time**.
当模块执行一系列 **与时间有关** 的操作时，该模块具有时间性内聚。

Bad

- The actions of this module are weakly related to one another, but strongly related to actions in other modules.
  这个模块的操作之间的关系很弱，但与其他模块的操作却有很强的关联。
- Not reusable. 不可重用。

### Procedural Cohesion 过程性内聚

A module has procedural cohesion if it performs a series of **actions related by the procedure** to be followed by the product.
如果一个模块执行一系列与产品要遵循的 **步骤顺序有关** 的操作，则该模块具有过程性内聚。

Bad

- The actions are still weakly connected, so the module is not reusable.
  操作之间仍是弱连接，所以模块不可重用。

### Communicational Cohesion 通信性内聚

A module has communicational cohesion if it performs a series of actions related by the procedure to be followed by the product, but in addition **all the actions operate on the same data**.
如果一个模块执行一系列与产品要遵循的步骤顺序有关的操作，并且如果 **所有操作都对相同的数据进行**，则该模块具有通信性内聚。

Bad

- Still lack of reusability. 仍缺乏重用性。

### Functional Cohesion 功能性内聚

A module with functional cohesion performs **exactly one action**.
**只执行一个操作或只达到单一目标** 的模块具有功能性内聚。

Good

- More reusable. 尽可能地重用。
- Corrective maintenance is easier. 进行正确性维护更容易。
- Easier to extend a product. 更容易扩展产品。

### Informational Cohesion 信息性内聚

A module has informational cohesion if it performs a number of actions, **each with its own entry point, with independent code for each action, all performed on the same data structure**.
如果模块进行许多操作，**每个都有各自的入口点，每个操作的代码相对独立，而且所有操作都对相同的数据结构完成**，则该模块具有信息性内聚。

## Coupling 耦合

**The degree of interaction between two modules. 模块之间交互的程度。**

Five categories or levels of coupling(non-linear scale). 耦合的 5 个分类或级别（非线性）。

- **Data coupling(GOOD) 数据耦合（较好）**
- **Stamp coupling 印记耦合**
- **Control coupling 控制耦合**
- **Common coupling 共用耦合**
- **Content coupling(BAD) 内容耦合（较差）**

### Content coupling 内容耦合

Two modules are content coupled if one **directly references** contents of the other.
如果一个模块 **直接引用** 了另一个模块的内容，两个模块具有内容耦合。

Bad

- Almost any change to module q, even recompiling q with a new compiler or assembler, requires a change to module p.
  几乎任何对模块 q 的修改，甚至用新的编译器或汇编语言重新编译，都需要对模块 p 进行修改。

### Common coupling 共用耦合

Two modules are common coupled if they have **write access to global data**.
两个模块使用了 **全局数据** 就具有共用耦合。

Bad

- It contradicts the spirit of structured programming.
  违背了结构化编程的精髓。
- Modules can have side-effects. 模块具有副作用。
- A change during maintenance to the declaration of a global variable in one module necessitates corresponding changes in other modules.
  在维护期间，一个模块中的全局变量的声明被修改，必须对另外的模块进行同步修改。
- Common-coupled modules are difficult to reuse. 共用耦合模块不易于重复使用。
- Common coupling between a module p and the rest of the product can change without changing p in any way.
  模块 p 和剩余产品之间的共用耦合能够不在模块 p 中进行修改。
- A module is exposed to more data than necessary.
  一个模块暴漏了更多的不必要的数据。

### Control coupling 控制耦合

Two modules are control coupled if one **passes an element of control to the other**.
如果一个模块 **传递了一个控制另外一个模块的元素**，这两个模块就具有控制耦合。

Bad

- The modules are not independent.
  模块不独立。
- **Associated with modules of logical cohesion**.
  **与逻辑性内聚相关**。

### Stamp coupling 印记耦合

Two modules are stamp coupled if a data structure is passed as a parameter, but the called module **operates on some but not all of the individual components of the data structure**.
一个数据结构通过参数传递，但调用模块 **操作了一些但不是所有的数据结构的单个组件**，这两个模块具有印记耦合。

Bad

- It is not clear, without reading the entire module, which fields of a record are accessed or changed.
- Difficult to understand. 难于理解。
- Unlikely to be reusable. 不可能重用。
- More data than necessary is passed. 传递了更多不必需的数据。

### Data coupling 数据耦合

Two modules are data coupled if all parameters are **homogeneous data items (simple parameters, or data structures all of whose elements are used by called module)**.
如果所有参数是 **同类数据项（简单参数，或数据结构中所有的元素被调用模块使用）**，两个模块就具有数据耦合。

Good

- The difficulties of content, common, control, and stamp coupling are not present.
  内容耦合、共用耦合、控制耦合和印记耦合的难点都不再出现。
- Maintenance is easier. 维护更加简单。

### The importance of coupling 耦合的重要性

- As a result of tight coupling 紧密耦合的结果
  - If the corresponding change is not made, this leads to faults.
    如果没有相应改变，将会导致错误。

- Good design has **high cohesion and low coupling**.
  好的设计是 **高内聚低耦合**。

## Data encapsulation 数据封装

A data structure together with the operations performed on that data structure.
数据结构与对数据结构的操作放在一起。

- Advantages 优点
  - Development 易于开发
  - Maintenance 易于维护
- Data encapsulation is an example of abstraction. 数据封装是抽象的一个例子。

## Abstract data types 抽象数据类型

A data type together with the operations performed on instantiations of that data type.
数据类型与对这个数据类型实例化的操作放在一起。

## Information hiding 信息隐藏

略

## Objects 对象

- First refinement 第一次精炼
  - The product is designed in terms of abstract data types. 产品是根据抽象设计类型设计的。
- Second refinement 第二次精炼
  - Class: an abstract data type that supports **inheritance**. 支持 **继承** 的抽象数据类型。
  - An **instantiation** of a class. 一个类的 **实例**。

### UML notation UML 标记

- Inheritance is represented by **a large open triangle**. 继承用 **空心三角形** 表示。
- Aggregation —— **A open diamond**. 集成 —— **空心菱形**。
- Association —— **A line**. 联系 —— **一条线**。

## Inheritance, polymorphism and dynamic binding 继承/多态/动态绑定

Polymorphism and dynamic binding can have a negative impact on maintenance.
多态和动态绑定会对维护产生负面的影响。

## The object-oriented paradigm 面向对象范型

略
