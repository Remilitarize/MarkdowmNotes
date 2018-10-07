[toc]

## Approaches for Artificial Intelligence 人工智能的方法

### Cybernetics and Brain Simulation 控制论与大脑仿真

- 1940s - 1950s
    - Neurology, Information theory, Cybernetics 神经学、信息论、控制论
    - Electronic networks 电子网络
- 1960s Abandoned 抛弃

The results of psychological experiments &rarr; Soar, a cognitive architecture
心理学实验结果 &rarr; Soar，一个认知架构

### Symbolic vs. Sub-symbolic 符号与亚符号

**Symbolic AI** is based on high-level "symbolic" (human-readable) representations of *problems, logic and search*.
**符号 AI** 是基于人类易懂的高级 "符号" 来表现 *问题、逻辑和搜索*。

- The assumption: Many aspects of intelligence can be achieved by the **manipulation of symbols**.
    - 假设：智能的许多方面能够通过 **符号操作** 来获得。
- The most successful form: **Expert systems**
    - 最成功的形式：**专家系统**

**Sub-symbolic** 亚符号

- Neural networks 神经网络
- Statistics 统计学
- Numerical optimization 数值计算

### Logic-based vs. Anti-logic 基于逻辑与反逻辑

- Logic-based 基于逻辑的（**neat 整齐的**）
    - John McCarthy
        - Knowledge representation 知识表征
        - Planning 规划
        - Learning 学习
    - Work in Europe
        - The programming language Prolog 逻辑编程语言 Prolog
        - The science of logic programming 逻辑编程的科学
- Anti-logic 反逻辑的（**scruffy 不整齐的**）
    - Commonsense knowledge bases 常识知识库
- Knowledge-based 基于知识的
    - Expert systems 专家系统

### Symbolism vs. Connectionism 符号主义与连接主义

***Symbolist AI** 符号主义 AI

- It represents information through symbols and their relationships. 凭借符号及它们之间的关系来表征信息。
- **Specific algorithms** are used to process these symbols to solve problems or deduce new knowledge. **特定算法** 用于处理这些符号来解决问题和推导新的知识。

***Connectionist AI** 连接主义 AI

- It represents information in a distributed form within a network. 用网络内部的一种分布式形式来表征信息。
- It imitates **biological processes** underlying learing, task performance, and problem solving. 模仿 **生物学过程** 的基础学习、任务功效和问题求解。

### Statistical Approach 统计方法

Sophisticated mathematical tools —— the victory of the neats
复杂数学工具 —— 整齐观点的胜利

Too focused on panticular problems and failed to address the long term goal of general intelligence.
过于关注特定的问题，且未能解决通用智能的长期目标。

### Intelligent Agent Paradigm 智能 Agent 泛型

- Operate autonomously 自主操作
- Perceive their environment 感知环境
- Adapt to change 顺应变化
- Create and pursue goals 实现目标
- *The best outcome, or the best expected outcome (when there is uncertainty) 最佳结果，或最佳预期结果（存在不确定性时）*

Broadly, an agent is anything that can be viewed as 
概括地说，一个智能体可以被看作具有如下功能的任何事物：

- **Perceiving** its environment through **sensors**, and **acting** upon that environment through **actuators**. 通过 **感受器** *感知* 外部环境，并且通过 **执行器** *作用* 于外部环境。
- May also **learn** or **use knowledge** to achieve their goals. 还可以通过 **学习** 或者 **应用知识** 来实现其目标。

## Rational Agents 理性智能体

> Concrete on general principles of rational agents and on components for constructing them.
  专注于理性智能体的一般原理和构造智能体的组件。

Intelligent Agents include: 智能 Agent 包含：

- A human agent 人类智能体
- A robotic agent (robot) 机器智能体（机器人）
- A software agent (softbot) 软件智能体

- ***Abstract Intelligent agents 抽象智能体***

- An abstract functional system 抽象功能系统
- Sometimes called abstract intelligent agents 有时被称为抽象智能体
- Some definitions emphasize their **autonomy**, so they prefer the term **autonomous intelligent agents**. 一些定义强调其 **自主性**，因而更喜欢 **自主智能体** 这个术语。
- Others prefer the term **rational agent**. 其他的更喜欢用 **理性智能体** 这个术语。
  
- ***Rational agent 理性智能体***

- One that does the **right way**. 做 **正确的事**。
- **Every entry** in the table for the agent function is **filled out correctly**. 该功能表中 **每条路径** 都 **被挣正确填写**。

- ***Rational Action 理性行为***

**Maximized the expected value** of performance measure given the perfect sequence.
对给定的感知序列，**能使期待的性能指标最大化**。

- ***Rationality 理性***

Depends on:

- The performance measure that defines the criterion of success. 定义成功标准的性能指标。
- The agent's prior knowledge of the environment. 智能体对环境的先驱知识。
- The actions that the agent can perform. 智能体能够完成的动作。
- The agent's percept sequence to date. 智能体最新的感知序列。

## Task Environment 任务环境

### PEAS Description PEAS 描述

**PEAS** is a task environment specification, stands for:
**PEAS** 是一种任务环境的规范，代表：

- Performance 性能
- Environment 环境
- Actuators 动作器
- Sensors 感受器

### Environment Types 环境类型

- Fully observation vs. Partically observation 完全可观测与部分可观测
- Single agent vs. Multi-agent 单智能体与多智能体
- Deterministic vs. Stochastic 确定性与随机性
    - Deterministic: Completely determined by the current state and the action executed by the agent. 完全由当前的状态和由该智能体执行的动作所决定、
- Episodic vs. Sequential 阵发性与连续性
    - Episodic: Atomic episodes 原子的片段
- Dynamic vs. Static 动态与静态
    - Dynamic: Change while an agent is deliberatly. 随着智能体行为而改变。
    - Semi-dynamic 半动态
- Discrete vs. Continuous 离散型与连续型
- Known vs. Unknown 已知与未知
    - Known：given 给定
    - Unknown：learning 学习

## Intelligent Agent Structure 智能 Agent 结构

An agent's behavior can be described mathematically by an **agent function** which maps every **percept** to an  **action**.
一个智能体的行为可以数学上被描述为一个 **智能体函数**，将每个 **感知** 映射为 **动作**。

An **agent program** implements an agent function.
一个 **智能体程序** 实现了一个智能体函数。
It takes the current percept as input from the sensors, and return an action to the actuators.
它将感受器的输入作为当前的感知，然后返回一个动作给执行器。

The structure of agents: 智能体的结构

- **Agent = platform + agent program 智能体 = 平台 + 智能程序**
- **Platform = computing device + sensors + actuators 平台 = 计算设备 + 感受器 + 执行器**
- **Agent program &sup; agent function 智能体程序是智能体函数的子集**

Three ways to represent states for an agent: 表现智能体状态的三种方式：

- **Atomic 原子**
    - A black box with no internal structure. 无内部结构的黑盒。
- **Factored 因子**
    - A fixed set of attributed and values. 属性和值的固定集合。
- **Structured 结构**
    - Objects that have attributes and relationships to other objects. 拥有属性和与其他对象关系的对象。
  
## Category of Intelligent Agent 智能 Agent 类别

Based on their degree of perceived intelligence and capability.
基于感知的智能和能力的程度。

- **Simple reflex agent 简单反射智能体**
- **Model-based reflex agent 基于模型的反射智能体**
- **Goal-based agent 基于目标智能体**
- **Utility-based agent 基于效用智能体**
- **Learing agent 学习智能体**
- ...

### Simple reflex agent 简单反射智能体

Only on the basis of the current percept, **ignoring the rest of the percept history**.
仅仅在当前感知的基础上动作，**忽略其余的感知历史**。

Based on **condition-action rule**: `if` condition `else` action
基于 **条件动作表**：`if` 条件 `else` 动作

- Only succeeds when the environments is **fully observation**. 仅当外部环境为 **完全可观测**。
- Some can also contain information on their current state. 有些也可以包含关于当前状态的信息。
- *Infinite loops* are often unavoidable. *无限循环* 经常不可避免。
    - Randomize its actions 随机产生动作

### Model-based reflex agent 基于模型的反射智能体

Can handle **partically observation** environment. 可以处理 **部分可观测** 环境。

Its current state is **stored** inside the agent.
其当前状态 **存储** 在智能体中。

- This knowledge about "how the world works" is called **a model of the world**.
    - 关于 "外部环境如何运作" 的知识被称为 **外部环境模型**。
- Depends on the percept history. 依赖于感知历史。

### Goal-based agent 基于目标智能体

Expand on the capabilities of **the model-based reflex agents** by using "**goal**" information.
通过利用 **目标** 信息，进一步扩展了 **基于模型的智能体** 的功能。

- Goal information describes situations that are desirable. 目标信息描述所希望的情形。
- In some instances **less efficient, but more flexible**. 在某些情况下 **不太有效，但更灵活**。

### Utility-based agent 基于效用智能体

A partivular state can be obtained by a **utility function** which maps a state to a measure of the utility of the state.
一个特殊的状态可通过一个 **效用函数** 得到，该函数将一个状态映射到一个该状态效用的度量。

- A more general performance measure 更通用的性能度量
- A rational utility-based agent chooses the action that **maximizes the expected utility** of the action outcomes. 一个理性的基于效用的智能体选择动作，将动作结果的 **期待效用最大化**。

### Learing agent 学习智能体

**Learing** allows the agents to initally operate in **unknown environments** and to become more competent than its initial knowledge.
**学习** 允许智能体最初在 **未知的环境** 中运行，并且与其最初的知识相比，会变得越来越胜任。

- **Learning element 学习要素**
  
It uses **feedback** from the "*Critic*" on how the agent is doing, and determines how the performance element should be modified to do better in the future.
利用 *评论者* 对智能体如何动作的 **反馈**，然后决定应该如何修改性能要素以便未来做得更好。

- **Performance element 性能要素**

It is what we have previously considered to be the entire agent: it takes in percepts and decides on actions.
它是我们曾考虑过的什么是完整的智能体：获得感知并且决定动作。

- **Problem generator 问题发生器**

It is responsible for suggesting actions that will lead to new experiences.
对推荐的动作负责，这将形成新的经验。

### Other agents 其他智能体

- Decision agents 决策智能体
- Input agents 输入智能体
- Processing agents 加工智能体
- Spatial agents 空间智能体
- Temporal agents 时间智能体
- World agents 世界智能体
- Believable agents 可信智能体
- Data-mining agents 数据挖掘智能体

![第二章]()http://oxnec2zdn.bkt.clouddn.com/rengongzhineng/dierzhang.PNG)
