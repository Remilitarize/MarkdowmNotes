[toc]

## Overview of Artificial Intelligence

### What is Artificial Intelligence(AI)

- The intelligence exhibited by nachines or software 机器或软件所展现的只能
- The name of the academic field of research 学术研究领域的名称
    - How to create computers and computer software that are capable of intelligent behavior 如何创建计算机和计算机软件使之具有智能行为

The 1956 conference of "**Dartnouth Summer Research Project on Artificial Intelligence**" was the monent that AI gained its name, mission and major players, and is widely considered **the birth of AI**.
1956 年的 "**达特茅斯夏季人工智能研究计划**" 会议，是 AI 赢得其名称、使命和主要参与者的时刻，因此被广泛地认为是 **AI 的诞生**。

### Turing Test

**Turing test** was proposed by Alan turing (1950) in his paper "Computing Machinery and Intelligence".
**图灵测试** 是由艾伦·图灵在 1950 年发表的 "计算机器与智能" 论文中提出的。
It is designed to provide a **satisfactory operational definition of intelligence**.
旨在提供一种 **令人满意的关于智能的可操作定义**。

A computer passes the test if a human interrogator, after posing some written questions, can not tell whether the written responses come from a person or from a computer.
如果一个人类的提问管，在提出一些书面问题之后，无法分辨这些书面回答究竟是来自于人还是一台计算机，则认为计算机通过了该测试。

### Visual Turing Test

An *operator-assisted device* that produces a *stochastic sequence of binary questions* from a *given test image*.
采用一个 *操作员辅助设备*，根据 *给定的图像* 产生随机的 *二元问题序列*。

Current computer visual systems were tested by theiir accuracy for tasks, including *objection detection, segmentation and localization*. But still not close to the way humans do.
目前的计算机视觉系统是测试任务的精度，这些任务包括 *对象检测、图像分割和定位*。但仍然与人类的行为方式有差距。
**Visual Turing test** was motivated by *the ability of human to understand images*.
**视觉图灵测试** 是受 *人类理解图像能力* 的启发而提出的。

### Chinese Room

**Chinese Room** is a **rhought experiment**, also called *Sherle's Chinese Room Argument*.
**中文屋** 是一个 **思想实验**，也被称为 *希而勒的中文屋论证*。
It attempts to show that computer can never be properly described as having a "mind" or "understanding", regardless of how intelligently it maybe have.
试图解释计算机绝不能描述为有 "智力" 或 "知性"，不管它多么智能。

He imagines himself alone in a room following a computer program for responding to Chinese characters slipped under the door.
他设想他肚子一个房间，操作一套计算机程序来应付从门缝下塞进来的中文字符。
He understands nothing of Chinese, and yet, by following the program for manipulating symbols and numerals just as a computer does, he produces appropriate strings of Chinese characters that fool those outside into thinking there is a Chinese speaker in the room.
他对中文一窍不通，然而，正如同计算机所做的那样，通过操作处理符号和数字，他生成了合适的中文字符串，从而蒙骗了屋外的人，以为屋内有一个精通中文的人。
The narrow conclusion is that programming a digital computer may make it appear to understand language but does not produce real understanding.
唯一的结论是，按程序运行的计算机可以使它看起来理解了语言，但并没有产生真正的理解。

Hence the "Turing Test" is *inadequate*.
因此断定，图灵测试的结论是 *不充分的*。

## Foundations of Artificial Intelligence

### What are the Foundations of AI

- Philosophy 哲学
- Mathematics 数学
- Economics 经济学
- Neuroscience 神经科学
- Psychology 心理学
- Computer engineering 计算机工程
- Control theory and cybernetics 控制理论和控制论
- Linguistics 语言学

### Mathematics

- ***Logic 逻辑学***
    - What are the formal rules to draw valid conclusions? 得出正确结论的形式规则是什么？
    - **propositional logic**, also called **Boolean logic** **命题逻辑**，亦称为 **布尔逻辑**。
    - **first order logic 一阶逻辑**
    - **theory of reference 指称理论**
- ***Computation 计算***
    - What can be computed? 什么么是可计算的？
    - **computable 可计算的**
    - **tractability 易处理性**
    - **the theory of NP-completeness NP 完全性理论**
        - P: Polynomial time 多项式时间
        - NP: Non-deterministic Polynomial time 不确定性多项式时间
        - NP-complete: both in NP and NP-hard NP 与 NP 难的交集。
- ***Probability 概率***
    - How do we reason with uncertain information? 如何根据不确定信息进行推理？
    - **Probability 概率**
    - **statistical methods 统计学方法**
    - **Bayes' rule 贝叶斯规则**

### Neuroscience

Neuroscience is the study of the *nervous system*, particularly the brain.
神经科学研究 *神经系统*，尤其是大脑。

- Brains are very good at making **rational decisions** (but not perfect).
    - 大脑在 **理性决策方面** 非常优越（但并非完美无缺）。
- Brains aren't as *modular* as software.
    - 大脑不象软件那样 *模块化*。
- **Prediction** and **simulation** are key to decision making.
    - **预测** 和 **仿真** 是决策的关键。

### Cognitive Psychology

Views the brain as an infomation-processing device, studies mental processes.
把大脑看作是信息处理设备，是研究心智过程的学科。

- attention 注意机制
    - A state of focused awareness on *a subset of available perceptual information*.
        - 意识集中在 *某个有用感知信息子集的状态*。
- language 语言
    - Study language acquisitioin, individual components of language formation, how language use is involved in mood, or numerous other related areas.
        - 研究语言习得、语言形成的组件、语言使用时的语气，或者许多其他相关领域。
- memory 记忆
    - Three subclases: *procedural memory, semantic memory, episodic memory*.
        - 三个子集：*过程记忆、语义记忆、情景记忆*。
- perception 感知
    - Physical senses (sight, smell, hearing, taste, touch, and proprioception), as well as their cognitive processes.
        - 物理感知（视觉、嗅觉、味觉、知觉），及其认知过程。
- Metacognition 元认知
    - It is "cognition about cognition", "thinking about thinking", or "hnowing about knowing".
        - 它是 "关于认知的认知"、"关于思考的思考"、"关于认识的认识"。
    - There are generally two components of metacognition: *knowledge about cognition*, and *regulation of cognition*.
        - 元认知通常有两个组成部分：*关于认知的知识*，以及 *认知的调节*。

### Control theory and Cybernetics

- Control theory 控制理论
    - An interdisciplinary branch of *engineering* and *mathenmatics*. *工程* 与 *数学* 的交叉学科分支。
    - Deal with the behavior of dynamical systems with inputs, and how their behavior is modified by feedback.
        - 处理动态系统的输入行为，以及该行为如何通过反馈进行调节。
- Cybernetics 控制论
    - A transdisciplinary approach for exploring regulatory systems, their structures, constraints, and possibilities.
        - 跨学科的研究途径，探索调控系统、它们的结构、约束和可能性。
    - In the 21th century, "**control any system using technology**".
        - 21 世纪，"**用技术控制任何系统**"。

## History of Artificial Intelligence

| Years | Description |
|---|---|
| 1950-1956 | The Birth of AI |
| 1956-1974 | The Golden Years |
| 1974-1980 | The First AI Winter |
| 1980-1987 | The Boom of AI |
| 1987-1993 | The Second AI Winter |
| 1993-Present | The Breakthrough |

## The state of The Art

### Categories of Artificial Intelligence

- **Humanly** to measure success in terms of fidelity to human performance.
    - **类人**：以对人类表现的逼真度来衡量。
- **Rationally** to measure against an ideal performance neasure.
    - **理性**：用理想的性能表现来衡量。

Four Categories of AI

| &nbsp; | **Humanly** | **Rationally** |
|---|---|---|
| **Acting** | Acting humanly | Acting ratinally |
| **Thinking** | Thinking humanly | Thinking rationally |

- **Weak AI 弱人工智能**
    - Also called **Artificial Narrow Intelligence(ANI)**.
        - 也被称为 **人工狭义智能（ANI）**。
    - It is **non-sentient** AI that is focused on one narrow task (just a specific problem).
        - 它是 **无意识的** AI，专注于一个具体的任务（仅针对一个特定的问题）。
- **Strong AI 强人工智能**
    - Also called **Artificial General Intelligence(AGI**.
        - 也被称为 **人工广义智能（AGI）**。
    - It means a machine with the ability to apply intelligence to **any** problem. It is a primary goal of artificial intelligence research.
        - 意味着及其具有将智能用于处理 **任何** 问题的能力，它是人工智能研究的主要目标。
- **Super AI 超人工智能**
    - Also called **Artificial Super Intelligence(ASI)**.
        - 也被称为 **人工超级智能（ASI）**。
    - It is a *hypothetical agent* that possesses intelligence for surpassing that of the brightest and most gifted human minds.
        - 是一个 *特定的智能体*，拥有远远超过聪明和最有天赋的人类大脑的智能。

### Applications of Artificial Intelligence

略

### Typical Papers on Artificial Intelligence

略

## Appendix 1

Research Area of AI 人工智能研究领域

- **Searching 搜索**
    - Problem spaces 问题空间
- **Reasoning 推理**
    - Knowledge 知识
- **Planning 规划**
    - Rules 规则
- **Learing 学习**
    - Data 数据
- **Applying 应用**
    - Communicating 交流
        - NLP、Machine Trans
    - Perceiving 感知
        - Vision、Speech、Sensing
    - Acting 动作
        - Robot
