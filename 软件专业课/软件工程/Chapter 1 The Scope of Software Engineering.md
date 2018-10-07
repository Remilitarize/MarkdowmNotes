[toc]

- Software engineering  软件工程
 - is a discipline. 是一个学科。
 - aim is the production of software 目的是生产软件
  - **Fault-free 无错**
  - **Delivered on time 交付及时**
  - **Within budget 预算之内**
  - **Satisfied the client's needs 满足客户的需求**
  - **Be easy to modify when the needs change 当需求更改是容易修改**

## Historical Aspects 历史方面

### 1968 NATO Conference, Garmisch, Germany

- Aim: to solve the **software crisis**
 目的：解决 **软件危机**

Software is delivered
软件提交时：

- **Late 延期**
- **Over budget 超出预算**
- **With residual faults 仍有残余的错误**

**The software crisis has not been solved.**
**软件危机仍未解决。**
Perhaps it should be called the **software depression**.
应当称之为 **软件萧条**。

- Long duration 持续时间长
- Pore prognosis 缺乏预测

## Economic Aspects 经济方面

CM：Coding method 编程方法

When using a new CM, we should need consider about  aspects below:
当使用一个新的编程方法时，我们应当需要考虑如下方面：

- The cost of training
  培训成本
- The impact of introducing a new technology
  引入新技术的影响
- The effect of new CM on maintenance
  在维护上新编程方法的效果

## Maintenance Aspects 维护方面

- Life-cycle Model 生命周期模型
	- The **steps (phases)** to follow when building software.
	  当搭建软件时遵循的 **步骤（阶段）**。
	- A **theoretical description** of what should be done.
	  对应当做什么的 **理论描述**。
- Life Cycle 生命周期
	- The **actual** steps performed on a specific product.
	  对具体的软件产品所执行的一系列 **实际** 步骤。

Waterfal Life-cycle Model 瀑布周期模型

**1. Requirements phase 需求阶段**
**2. Analysis(Specification) phase 分析（规格说明）阶段**
**3. Design phase 设计阶段**
**4. Implementation phase 实现阶段**
**5. Postdelivery maintenance 交付后维护**
**6. Retirement 退役**

- Requirements phase 需求阶段
	- Explore the concept 研究概念
	- Elicit the client's requirements 提取客户需求
- Analysis phase 分析阶段
	- Analyze the client's requirements 分析客户需求
	- Draw up the **specification document** 定制 **规格说明文档**
	- Draw up the **software project management plan（SPMP）** 定制 **软件项目管理计划**
	- "What the product is supposed to do" “产品应当做什么”
- Design phase 设计阶段
	- **Architectural design 结构设计**
	- **Detailed design 详细设计**
	- “How the product does it“ ”产品如何做的“
- Implementation phase 实现阶段
	- Coding 编程
	- Unit testing 单元测试
	- Integration 集成
	- Acceptance testing 验收测试
- Postdelivery maintenance 交付后维护
	- **Corrective maintenance 纠错性维护**
	- **Enhancement 增强型维护**
		- **Perfective maintenance 完善性维护**
		- **Adaptive maintenance 适应性维护**
- Retirement 退役

### Classical and Modern View of Maintenance 维护的传统和现代观点

#### Classical Maintenance Definition 经典维护定义

**Development-then-maintenance model 先开发后维护模型**
This is a **temporal** definition. 这是个 **时间** 上的定义。

- Before installation 安装前
	- Development 开发阶段
- Installed 安装后
	- Maintenance 维护阶段

#### Modern Maintenance Definition 现代维护定义

**Maintenance is the process that occurs when "software undergoes modifications to code and associated documentation due to a problem or the need for improvement or adaptation"**
**维护是一个过程，是“软件因存在问题或因有改进或适应性需求时，对代码及相应文档所进行的修改”过程。**

This is a **operational** definition. 这是个 **操作性** 定义。

### The Importance of Postdelivery Maintenance 交付后维护的重要性

略

## Requirements, Analysis, and Design Aspects 需求、分析、设计方面

The **earlier** we detect and correct a fault, the **less** it costs us.
发现并更正错误 **越早**，花费的时间和金钱就 **越少**。

### Conclusion 结论

- **It is vital to improve our requirements, analysis, and design techniques**.
  **提高需求、分析和设计技术是非常重要的**。
	- To find faults as early as possible
	  可以尽早发现错误
	- To reduce the overall number of faults (and, hence, the overall cost)
	  可以减少错误总数（进而减少总支出）

## Team Programming Aspects 小组编程方面

Software is built by teams. 软件是由小组搭建的。

- Interfacing problems between modules 模块之间的接口问题
- Communication problems among team members 小组成员间的沟通问题

## Why There Is No Planning Phase 为什么没有计划阶段

We cannot plan at the beginning of the project — we do not yet know exactly what is to be built.
我们无法在项目刚开始时计划 —— 我们还不知道项目实际会搭建成什么样。

### Conclusion 结论

- **Planning activities are carried out throughout the life cycle.**
  **计划活动贯穿于软件生命周期的始终。**
- **There is no separate planning phase.**
  **没有独立的计划阶段。**

## Why There Is No Testing Phase 为什么没有测试阶段

It is far too late to test after development and before delivery.
准备好交付给客户时才检查软件产品实在是太晚了。

> **Verification** **验证**

> - Testing at the end of each phase 每个阶段结束后测试

> **Validation** **确认**

> - Testing at the end of the project 项目结束后测试

### Conclusion 结论

- **Continual testing activities must be carried out throughout the life cycle.**
  **测试活动连续贯穿于软件生命周期的始终。**
- This testing is the responsibility of **every software professional** and **the software quality assurance(SQA) group**.
  测试是每个 **软件专业人员** 和 **软件质量保证群体** 的责任。
- **There is no separate testing phase.**
  **没有独立的测试阶段。**

## Why There Is No Documentation Phase 为什么没有文档阶段

It is far too late to document after development and before delivery.
开发后递交前写文档太晚了。

### Conclusion

- **Documentation activities must be performed in parallel with all other development and maintenance activities.**
  **文档活动必须伴随着所有其他开发和维护活动进行。**
- **There is no separate documentation phase.**
  **没有独立的文档阶段。**

## The Object-Oriented Paradigm　面对对象范型

- The structed paradigm was successful **initially**. 结构化范型在 **初期** 是成功的
	- Action oriented 面向操作
	- Data oriented 面向数据
	- But not both 但并不是两者兼备
- Both data and actions are of equal importance.
  数据和过程具有等同的重要性。

![传统范型与面向对象范型](http://oxnec2zdn.bkt.clouddn.com/software-engineering/Classical-Object-oriented.png)

- Strengths of the Object-Oriented Paradigm 面向对象范型的优点
	- With **information hiding**, postdelivery maintenance is safer.
	  有了 **信息隐藏**，交付后维护更安全。
		- The chances of a **regression fault** are reduced.
		  减少了 **回归错误** 的机会。
	- **Responsibility-driven design 职责驱动设计**
		- Also called **design by contract** 又被称为 **按合同设计**
	- Well-designed objects are independent units.
	  设计良好的对象是独立的单元。
		- Everything in the product that relates to the portion of the real world modeled by that object can be found in the object itself.
		  产品中与现实世界有关的、被该对象模拟的部分都可以在对象本身中找到。
		- **Encapsulation 封装**
	- The object-oriented paradigm **reduces complexity** because the product generally consists of independent units.
	  由于产品大体上由独立的单元组成，使得面对对象范型 **降低了软件产品的复杂度**。
	- The object-oriented paradigm **promotes reuse**.
	  面向对象范型 **提倡重复利用**。

### Classical Phases vs Object-Oriented Workflows 经典阶段 vs 面对对象工作流

|Classical Paradigm|Object-Oriented Paradigm|
|-|-|
|1. Requirements Phase|1. Requirements Workflow|
|2. Analysis(specification) Phase|2'.Object-Oriented Analysis Workflow|
|3. Design Phase|3'. Object-Oriented Design Workflow|
|4. Implementation Phase|4'. Object-Oriented Implementation Workflow|
|5. Postdelivery Maintenance|5. Postdelivery Maintenance|
|6. Retirement|6. Retirement|

|传统范型|面向对象范型|
|-|-|
|1. 需求阶段|1. 需求工作流|
|2. 分析（规格说明）阶段|2'. 面向对象分析工作流|
|3. 设计阶段|3'. 面向对象设计工作流|
|4. 实现阶段|4'. 面向对象实现工作流|
|5. 交付后维护|5. 交付后维护|
|6. 退役|6. 退役|

- There is **no correspondence** between phases and workflows.
  阶段与工作流之间 **没有对应关系**。

<table border="1">
    <tr>
        <td>Classical Paradigm</td>
        <td>Object-oriented Paradigm</td>
    </tr>
    <tr>
        <td>2. Analysis(specification) phase
            <ul>
                <li>Determine what the product is to do</li>
            </ul>
        </td>
        <td>2'. Object-oriented analysis workflow
            <ul>
                <li>Determine what the product is to do</li>
                <li>Extract the classes</li>
            </ul>
        </td>
    </tr>
    <tr>
        <td>3. Design phase
            <ul>
                <li>Architectural design(extract the modules)</li>
                <li>Detailed design</li>
            </ul>
        </td>
        <td>3'. Object-oriented design workflow
            <ul>
                <li>Detailed design</li>
            </ul>
        </td>
    </tr>
    <tr>
        <td>4. Implementation phase
            <ul>
                <li>Code the modules in a appropriate programming language</li>
                <li>Integrate</li>
            </ul>
        </td>
        <td>4'. Object-oriented implementation workflow
            <ul>
                <li>Code the classes in an appropriate object-oriented programming language</li>
                <li>Integrate</li>
            </ul>
        </td>
    </tr>
</table>

<table border="1">
    <tr>
        <td>传统范型</td>
        <td>面向对象范型</td>
    </tr>
    <tr>
        <td>2. 分析（规格说明）阶段
            <ul>
                <li>确定产品要做什么</li>
            </ul>
        </td>
        <td>2'. 面向对象分析工作流
            <ul>
                <li>确定产品要做什么</li>
                <li>提取类</li>
            </ul>
        </td>
    </tr>
    <tr>
        <td>3. 设计阶段
            <ul>
                <li>结构设计（提取模块）</li>
                <li>详细设计</li>
            </ul>
        </td>
        <td>3'. 面向对象设计工作流
            <ul>
                <li>详细设计</li>
            </ul>
        </td>
    </tr>
    <tr>
        <td>4. 实现阶段
            <ul>
                <li>用恰当的编程语言编码模块</li>
                <li>集成</li>
            </ul>
        </td>
        <td>4'. 面向对象实现工作流
            <ul>
                <li>用恰当的面向对象编程语言编码类</li>
                <li>集成</li>
            </ul>
        </td>
    </tr>
</table>

- Structured paradigm 结构化样例
	- There is major consequences between analysis (what) and design (how).
	  在分析阶段和设计阶段之间会有一个很大的转变。
- Object-oriented paradigm 面向对象样例
	- Objects enter the life cycle **from the very beginning**.
	  对象 **从一开始** 就进入了软件生命周期。

### Conclusion 结论

- Modules (objects) are introduced as early as the object-oriented analysis workflow.
  模块（对象）在面向对象分析工作流中尽早地引入。
	- This ensures **a smooth transition** from the analysis workflow to the design workflow.
	  这确保了从分析工作流到设计工作流之间 **平滑的过度**。
- The objects are then coded during the implementation workflow.
 在实现工作流中就可以编写对象。
	- Again, the transition is smooth.
	  再次确保平滑的过度。

## The Object-Oriented Paradigm in Perspective 面向对象范型的前景

- The object-oriented paradigm has to be used correctly
  必须正确使用面向对象范型。
- When used correctly, the object-oriented paradigm can solve some (but not all) of the problems of the classical paradigm.
  当正确使用的时候，面向对象范型可以解决一些（但不是全部）传统范型遇到的问题。
- The object-oriented paradigm has problems of its own.
  面向对象范型有自己的问题。
- The object-oriented paradigm is the best alternative available today
  面向对象范型是目前可用的最好方法。

## Terminology 术语

- Client, Developer, User 客户 / 开发者 / 用户
	- The client is the individual who **wants** a product to be built(developed).
	  客户是 **想** 建造（开发）某一产品的个体。
	- The developers are the members of a team **responsible for building that product**.
	  开发者是小组的成员，**负责建造该产品**。
	- The **third party** involved in software production is the user.
	  涉及软件生产的 **第三方** 是用户。
- **Commercial off-the-shelf (COTS) software 商用现货软件**
	- The manufacturers of software recover the cost of developing a product by volume selling.
	  软件制造商通过大量的销售填补产品开发的费用。
- **Internal software 内部软件**
	- Both the client and developers may be **part of the same organization**.
	  客户和开发者可能是 **同一组织的一部分**。
- **Contract software 合同软件**
	- The client and developers are members of totally independent organizations.
	  客户和开发者是完全独立的组织中的成员。
- **Open-source software 开源软件**
	- An open-source software product is developed and maintained by a team of volunteers and may be downloaded and used free of charge by anyone.
	  一个开源软件产品由一组自愿者开发和维护，任何人都可以下载并免费使用。
- Program, System, Product 程序 / 系统 / 产品
- **Mistake 过错**
  - Made by programmers. 由程序员产生的。
- **Fault 差错**
  - The consequence of that mistake in the code. 过错在代码中的结果。
- **Failure 故障**
  - Executing the software product as a consequence of the fault. 执行有差错的软件产品。
- **Error 错误**
  - The result incorrect. 结果不正确。
- Methodology, Paradigm 方法 / 范型
- Technique 技术
- Object-Oriented Terminology 面向对象术语
	- Data component of an object 一个对象的数据组件
		- Attribute (generic) 属性
	- Action component of an object 一个对象的动作组件
		- Method (generic) 方法

## Ethical Issues 道德问题

略
