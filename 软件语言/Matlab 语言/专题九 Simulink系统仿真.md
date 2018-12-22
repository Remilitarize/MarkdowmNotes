[toc]

## Simulink 仿真基础

### Simulink 的启动

- 在 Matlab 主窗口选择“主页”选项卡，单击“文件”命令组中的“新建”命令按钮，然后从下拉菜单中选择“Simulink Model”命令。
- 在 Matlab 主窗口选择“主页”选项卡，单击“Simulink”命令组中的“Simulink”命令按钮。
- 在 Matlab 的命令行窗口输入 `simulink` 命令。

在打开的 Simulink 的起始页中，单击 “Blank Model” 按钮，打开模型编辑窗口。

- 利用 File &rarr; New 命令，建立新的仿真模型。
- 利用 File &rarr; Open 命令，打开已经建立好的模型文件。
- 单击 Library Browser 按钮，将打开 Simulink 模块库浏览器窗口。

### 系统仿真模型的创建

Simulink 模块库大致分为两类：

- 基本模块库 Simulink
- 专业模块库

Simulink 模块的操作：

- 添加：首先在 Simulink 模块库浏览器窗口中找到该模块，然后用鼠标将这个模块拖拽到模型编辑窗口中。
- 删除：选中模块，按删除键。
- 剪切/复制/粘贴：类似于文本编辑。
- 两个模块的连接：先将鼠标指针移动到一个模块的输出端，当鼠标指针变成十字光标时按住鼠标左键，移动鼠标指针到另一个模块的输入端，当连接线由虚线变成实线时，释放鼠标左键即可。
- 分支：在先连好的一条线后，把鼠标指针移到分支点的位置，先按下 Ctrl 键，然后按住鼠标拖拽到目标模块的输入端，释放鼠标和 Ctrl 键。

模型存储：

- 选择 File &rarr; Save/Save as 命令。
- 单击模型编辑窗口工具栏中的 Save 命令按钮。

模块参数的设置：

- 双击要设置的模块。
- 选择要设置的模块，再选择 Diagram &rarr; Block Parameters 命令。
- 右击要设置的模块，从快捷菜单中选择 Block Parameters 命令。

### 仿真参数的设置

- 选择 Simulation &rarr; Model Configuration Parameters 命令。
- 单击工具栏中的 Medel Configuration Parameters 按钮。

在 Solve 参数下，可以设置

- 起始时间
- 终止时间
- 微分方程求解算法
- 规定微分方程具体参数
- 输出选项

## 子系统的创建与封装

### 子系统的创建

> `Scope` 表示示波器，`XY-Graph` 表示坐标图。

- 通过 Subsystem 模块建立子系统
- 将已有的模块转换为子系统
    - 先选择构成子系统的全部模块，然后执行创建子系统的命令（Ctrl + G），这样原来的全部模块变成一个子系统。

例：创建 $latex y = kx + b$ 子系统。

1. 打开 Simulink Library Browser，选择 Ports & Subsystems，将 Sybsystem 模块添加到模型编辑窗口中。
2. 双击 Subsystem 模块，找到已经自动添加的一个输入模块（输入端口）和一个输出模块（输出端口）。
3. 将模块 k 和模块 b 分别以乘法和加法形式插入到输入模块和输出模块中间，并顺次连接。

### 子系统的封装

选中所要封装的子系统，执行 Diagram &rarr; Mask &rarr; Create Mask 命令（Ctrl + M），出现封装编辑器对话框。

- 第一个选项卡用于设置被封装模块的图标。
- 第二个选项卡用于设置子系统参数设置对话框。
    - 控件 Edit 用于输入。
- 第三个选项卡用于设置初始化命令。
- 第四个选项卡用于定义封装模块的类型、描述和帮助文本。

### 子系统的条件执行

条件执行子系统：

- 使能子系统
    - 表示控制信号由负变正时子系统开始执行，直到控制信号再次变为负时结束。
    - 若控制信号为标量，则标量大于 0 时开始执行。
    - 若控制信号为向量，则向量中任意一个值大于 0 时开始执行。

> 使能子系统对应 Enabled Subsystem。

- 触发子系统
    - 指当触发事件发生时开始执行子系统。
    - 在触发之前，总会保持上一次触发值。
    - 触发形式：
        - rising（上升沿触发）：控制信号从负值或 0 上升到正值时子系统开始执行。
        - falling（下降沿触发）：控制信号从正值或 0 下降到负值时子系统开始执行。
        - either（双边缘触发）：控制信号满足上升沿或下降沿触发条件时，子系统开始执行。
        - function-call（函数调用触发）：与 S 函数配合使用。

> 触发子系统对应 Triggered Subsystem。

- 使能加触发子系统
    - 当使能控制信号和触发控制信号共同作用时执行子系统。

## S 函数的设计与应用

### S 函数的概念

S 函数时 *系统函数* 的简称，是指采用一种程序设计语言描述的一个功能模块。
用户可以采用 Matlab 语言，也可采用 C、C++ 或 FORTRAN 等语言来编写 S 函数。

S 函数有自己特定的语法构成规则，可以用来描述并实现连续系统、离散系统以及复合系统。

S 函数能够接受来自 Simulink 求解算法的相关信息，并对求解算法发出的命令做出适当的响应。

### 用 MATLAB 语言编写 S 函数

在 Matlab 命令行窗口输入命令，打开模板文件：

`edit sfuntmpl.m`

模板文件 sfuntmpl.m 包括：

- 1 个主函数
- 6 个子函数

### 主函数

`function [sys, x0, str, ts] = fname(t, x, u ,flag)`

- `fname` 是 S 函数的函数名。
- 输入形参 `t`、`x`、`u`、`flag` 分别为仿真时间、状态向量、输入向量和子函数调用标志。
- 输出形参 `sys` 代表一种返回参数，`x0` 是初始状态值。
- 对于 m 文件的 S 函数，`str` 将被置为一个空阵。
- `ts` 是一个两列矩阵。
    - 一列是各状态变量的采样周期。
    - 另一列是相应时间的偏移量。
    - 对于连续系统，均为 0。

### 子函数

前缀为 `mdl`，由 `flag` 的值来控制在仿真的各阶段调用 S 函数的哪一个子函数。

- `flag` 取 0，调用初始化子函数 `mdlInitializeSizes`。
- `flag` 取 1，调用子函数 `mdlDerivatives` 实现连续状态的更新。
- `flag` 取 2，调用子函数 `mdlUpdate` 实现离散状态的更新。
- `flag` 取 3，调用输出子函数 `mdlOutputs`。
- `flag` 取 4 和 9 的情况较少使用。

例：采用 S 函数实现 $latex y = kx + b$。

主函数

```matlab
function [sys, x0, str, ts] = timekb(t, x, u, flag, k, b)

switch flag
    case 0
        [sys, x0, str, ts] = mdlInitializeSizes;
    case 1
        sys = mdlOutputs(t, x, u, k, b);
    case {1, 2, 4, 9}
        sys = [];
    otherwise
        error(num2str(flag));
end
```

初始化子函数

```matlab
function [sys, x0, str, ts] = mdlInitializeSizes()

sizes = simsizes;         % 与 Simulink 交互

% 下面四个参数置为 -1 表示大小动态改变
sizes.NumContStates = 0;   % 无连续状态
sizes.NumDiscStates = 0;   % 无离散状态
sizes.NumOutputs = 1;      % 有一个输出量
sizes.NumInputs = 1;       % 有一个输入信号

sizes.DirFeedthrough = 1;  % 输出量中含有输入量
sizes.NumSampleTimes = 1;  % 单个采样周期

sys = simsizes(sizes);
x0 = [];
str = [];
ts = [-1, 0];     % 假定继承输入信号的采样周期
```

输出子函数

```matlab
function sys = mdlOutputs(t, x, u, k, b)

sys = k * u + b;
```
