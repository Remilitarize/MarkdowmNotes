[toc]

## Team Organization 小组组织

- Team organization is a managerial issue.
  小组组织是一个管理问题。

- Brooks’s Law 布鲁克斯法则
	- Adding additional programming personnel to a team when a product is late has the effect of making the product even later.
	  向一个已经延期的软件项目增加人员会使该项目完成得更晚。

- Two extreme approaches to team organization. 两个小组组织的极端方法。
	- **Democratic teams** 民主小组
	- **Chief programmer teams** 主程序员小组

## Democratic Team Approach 民主小组方法

- Basic underlying concept — **egoless programming** 基本概念 - **无我编程**
  - Restructure the social environment. 重新建立社会化环境。
  - Restructure programmers' values. 重新建立程序员的建立。
  - Encourage team members to find faults in code. 鼓励小组成员在代码中查找错误。
  - A fault must be considered a normal and accepted event. 错误必须看成是一个正常并可接受的事实。
  - The team as whole will develop an ethos, a group identity. 小组作为一个整体形成一种群体精神、一种群体特征。
  - Modules will “belong” to the team as whole. 模块属于整体。
- A group of **up to 10 egoless programmers** constitutes a democratic team.
  一个 **多达 10 个无我程序员** 的小组组成一个民主小组。

- Democratic teams are hard to introduce into an undemocratic environment.
  民主小组很难在不民主的环境下提出。

- Strengths of Democratic Team Approach 民主小组方法的优点
	- Democratic teams are enormously productive. 民主小组具有巨大的生产力。
	- They work best when the problem is difficult. 当遇到困难问题时可以做得更好。
	- They function well in a research environment. 在科研的环境下可以很好发挥作用。
- Problem 问题
	- Democratic teams have to spring up spontaneously. 民主小组必须自愿地提出。

## Classical Chief Programmer Team Approach 经典主程序员小组方法

- Two key aspects 两个关键特性
	- **Specialization** 专业化
	- **Hierarchy** 等级化
- Chief programmer 主程序员
  - Successful manager and highly skilled programmer. 成功的管理者且训练有序的程序员。
  - Does the **architectural design**. 做 **结构设计**。
  - Allocates coding among the team members. 分配组员间的代码。
  - Writes the critical (or complex) sections of the code. 编写代码关键（或复杂）的部分。
  - Handles all the interfacing issues. 处理所有接口问题。
  - Reviews the work of the other team members. 审查其他组员的工作。
  - Is personally responsible for every line of code. 对每行代码负责。
- Back-up programmer 备程序员
  - Necessary only because the chief programmer is human. 因为主程序员是人，所以必要。
  - Be in every way as competent as the chief programmer. 在各个方面与主程序员一样有能力。
  - Must know as much about the project as the chief programmer. 必须与主程序员一样了解这个项目。
  - Does **black-box test case planning** and other tasks that are independent of the design process. 做 **黑盒测试的用例规划** 并承担其他与设计过程独立的任务。
- Programming secretary 编程秘书
  - A highly skilled, well paid, central member of the chief programmer team. 主程序员团队的精通专业、收入颇丰的核心人物。
  - Responsible for maintaining the program production library. 负责维护项目产品库。
  - Programmers hand their source code to the secretary who is responsible for conversion to machine-readable form,  compilation, linking, loading, execution, and running test cases.
    程序员将他们的源程序交给编程秘书，由变成秘书负责将它们转换为及其可识别的形式，编译、链接、装载、执行并运行测试用例。
- Programmers 程序员
  - Do nothing but program. 只是编程。
  - All other aspects are handled by the programming secretary. 其他的工作都交给编程秘书来做。
- Strengths of the chief programmer team approach 主程序员方法的优点
	- It works. 有效
	- Numerous successful projects have used variants of CPT. 许多成功的项目使用了变种版。
- Classical CPT is **impractical**. 经典主程序员小组是不切实际的。

## Beyond CP and Democratic Teams 主程序员小组和民主小组之外的编程小组

- Solution
	- Reduce the managerial role of the chief programmer. 去掉主程序员的大部分管理职能。

The **team leader** is responsible for the **technical** aspects. **小组领导** 负责 **技术方面** 的事务。
The **team manager** is responsible for all **nontechnical** aspects decisions. **小组经理** 负责所有 **非技术性** 的决定。

## Synchronize-and-Stabilize Teams 同步-稳定小组

- Rules 规定
	- Programmers must adhere to the time for entering the code into the database for that day’s synchronization.
	  程序员必须按时上传代码至数据库保证每日的同步。
- If a developer's code prevents the product from being compiled for that day's synchronization, the problem must be fixed immediately so that the rest of the team can test and debug that day's work.
    如果一个开发者的代码阻碍了该产品当天的同步编译，则问题必须立刻解决，这样小组的其他人才能测试并调试当天的工作。

## Teams For Agile Processes 敏捷过程小组

- Feature of agile processes 敏捷过程特性
	- All code is written by two programmers sharing a computer.
	  两个程序员组成的小组编写的所有代码，共享一台计算机。
	- "Pair programming" 结对编程

- Strengths of Pair Programming 结对编程特点
	- One programmer draws up the test cases, the other tests the code.
	  一个程序员编写测试用例，另一个测试代码。
	- If one programmer leaves, the other is sufficiently knowledgeable to continue working with another pair programmer.
	  如果结对编程小组的一个成员离开，另一个完全可以继续和另一个新伙伴完成相同部分的软件开发。
	- An inexperienced programmer can learn from his or her more experienced team member.
	  可以使经验不太丰富的软件安业人员从经验丰富的伙伴那里学到更多的技艺。
	- Centralized computers promote egoless programming.
	  集中式计算机提倡无我编程。

- Conclusion 结论
	- It depends on both the programmer's expertise and the complexity of the system and the specific tasks to be solved.
	  效率高低取决于程序员的经验和软件产品及所要解决的任务的复杂度。

## Open-Source Programming Teams 开源程序员小组

- Individuals volunteer to take part in an open-source project for two main reasons：
  参加开源项目的个人志愿者主要基于两个原因：
	- For the sheer enjoyment of accomplishing a worthwhile task.
	  完成一项值得做的任务后的成就感。
	- For the learning experience.
	  得到培训经验。

- In summary, an open-source project succeeds because of
  换句话说，一个开源项目的成功是因为
	- The nature of the target product 目标项目的特性
	- The personality of the instigator 组织者的个性
	- The talents of the members of the core group 核心小组成员的天资

## People Capability Maturity Model 人员能力成熟度模型

- P–CMM is a framework for improving an organization’s processes for managing and developing its workforce.
  P-CMM 是提高一个组织的软件过程的框架。

## Choosing an Appropriate Team Organization 选择合适的小组组织

- The “correct” way depends on 组织一个小组的最佳方法是
	- The product 产品本身
	- The outlook of the leaders of the organization 先前对于各种小组结构的经验
	- Previous experience with various team structures 该软件组织的文化

- Without relevant experimental results, it is hard to determine optimal team organization for a specific product.
  如果不在软件工业内获得有关小组组织的实验数据，就不容易为某个具体产品确定最优的小组组织。

|Team Organization|Strengths|Weaknesses|
|-|-|-|
|Democratic teams<br />民主小组|High-quality code as consequence of positive attitude to finding faults<br />由于积极地查找错误，因而代码质量高<br />Particulayly good with hard problems<br />特别适用于解决难的问题|Experienced staff resent their code being appraised by beginners<br />有经验的人方案新手的评价<br />Cannot be externally imposed<br />不能从外部强加|
|Classical chief programmer teams<br />传统主程序员小组|It works<br />有效<br />Numerous successful projects have used variants of CPT<br />许多成功项目应用了其变体|Impractical<br />不实用|
|Modified chief programmer teams<br />修改的主程序员小组|Many success<br />有许多成功的范例|No success comparable to The New York Times project<br />没有与《纽约时报》项目可比拟的成功范例|
|Modern hierarchical programming teams<br />现代分级编程小组|Team manager/team leader structure obviates need for chief programmer<br />小组经理/小组领导结构避免对主程序猿需求<br />Scales up<br />可扩展<br />Supports decentralization when needed<br />必要时支持分散决策|Problems can arise unless areas of responsibility of the team manager and the team leader are clearly delineated<br />除非明确小组经理和小组领导间的负责范围，否则容易产生问题|
|Synchronize-and-stabilize teams<br />同步-稳定小组|Encourages creativity<br />鼓励创造性<br />Ensures that a huge number of developers can work toward a common goal<br />确保大量开发者为共同目标工作|No evidence so far that this method can be utilized outside Microsoft<br />在 Microsoft 公司之外还没有该方法应用的实例|
|Agile process teams<br />敏捷过程小组|Programmers do not test their own code<br />程序员不测试自己的代码<br />Knowledge is not lost if one programmer leaves<br />如果一个程序员离开不会有损失<br />Less-experienced programmers can learn from others<br />经验欠缺的程序员可以向其他人学习<br />Group ownership of code<br />代码具有小组所有权|Still too little evidence regarding efficacy<br />还没有更多的实例证实它的功效|
|Open-source teams<br />开源小组|A few projects are extremely successful<br />少数项目非常成功|Narrowly applicable<br />应用面窄<br />Must be led by a superb motivator<br />需由出色的有号召力的人领导<br />Requires top-caliber participants<br />需顶尖高手参与|
