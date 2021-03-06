[toc]

## Matlab 程序文件

Matlab 的程序文件扩展名为 `.m`。
分为 **脚本文件** 和 **函数文件**。

- 脚本文件是可以在命令行窗口直接执行的文件，也叫命令文件。
- 函数文件是定义一个函数，不能直接执行，而必须以函数调用的方式来调用它。

***文件的建立：***

- 用命令按钮创建文件。
- 用 `edit` 命令创建文件。
    - 例：`edit test`，在当前文件夹中创建一个 `test.m` 文件并打开脚本编辑器。

### 建立脚本文件

f1.m
```matlab
A = [1 2 3; 4 5 6];
B = [1 2; 3 4; 5 6];
C = A * B
```

命令行窗口
```matlab
f1
```

### 建立函数文件

f2.m
```matlab
function C = f2(A, B)
C = A * B
```

命令行窗口
```matlab
A = [1 2 3; 4 5 6];
B = [1 2; 3 4; 5 6];
C = f2(A, B)
```

## 顺序结构程序

数据的输入：
`A = input(提示信息, 选项);`

数据的输出：
`disp(输出项);`

> 在一行末尾不加分号时输出的结果与使用 `disp` 函数输出的结果在格式上有差异。

程序的暂停：
`pause(延迟秒数)`
省略秒数时会暂停程序，直至用户输入任意键。

强行中止程序：
Ctrl + C 组合键。

### 例题

有一线段 AB，A 的坐标为 (1, 1)，B 的坐标为 (4.5, 4.5)，求 AB 的长度，以及黄金分割点 C 的坐标。

> 将 A 点和 B 点的坐标用复数形式存储，其模就是 AB 的长度。
> (1, 1) &rarr; 1 + i
> (4.5, 4.5) &rarr; 4.5 + 4.5i
> 黄金分割点将线段分隔为 0.618 : (1-0.618)。

```matlab
a = input('a = ');
b = input('b = ');
c = a + 0.618 * (b - a);
s = abs(a - b);
disp(s)
disp(c)
```

## 选择结构程序

### 单分支 if 语句

语句格式：

```matlab
if 条件     % 关系表达式或逻辑表达式
    语句组
end
```

- 当条件结果为标量时，**非零** 表示条件成立，零表示条件不成立。
- 当条件结果为矩阵是，如果矩阵 **非空且不包含零元素**，则条件成立，否则不成立。

> 建议条件尽量使用标量。

### 双分支 if 语句

语句格式：

```matlab
if 条件
    语句组 1
else           % 当条件不成立时
    语句组 2
end
```

例：输入一个整数，若为奇数则输出其平方根，否则输出其立方根。

```matlab
x = input('请输入 x 的值');
if rem(x, 2) == 1    % 等价于 rem(x, 2)
    y = sqrt(x);
else
    y = x ^ (1/3);
end
disp(y);
```

### 多分支 if 语句

语句格式：

```matlab
if 条件 1
    语句组 1
elseif 条件 2
    语句组 2
...
elseif 条件 m
    语句组 m
else
    语句组 m+1
end
```

例：输入一个字符，若为大写字母，则输出其对应的小写字母；若为小写字母，则输出其对应的大写字母；若为数字字符，则输出其对应数的平方根；若为其他字符，则原样输出。

```matlab
c = input('请输入一个字符：', 's');
if c >= 'A' && c <= 'Z'
    disp(lower(c))
elseif c >= 'a' && c <= 'z'
    disp(upper(c))
elseif c >= '0' && c <= '9'
    disp(str2double(c) ^ 2);
else
    disp(c);
end
```

### switch 语句

```matlab
switch 表达式
    case 结果表 1
        语句组 1
    case 结果表 2
        语句组 2
    ...
    case 结果表 m
        语句组 m
    otherwise
        语句组 n
end
```

- `switch` 表达式应该是一个其值 *可以列举* 的表达式。
- `case` 结果表为 `switch` 表达式的取值。
    - 当取值有多个值时，用单元数据表示。
- `case` 结果表是 **单元矩阵**。

## 循环结构程序

### for 语句

```matlab
for 循环变量 = 表达式 1 : 表达式 2 : 表达式 3
    循环体语句
end
```

- `for` 语句针对向量的每一个元素执行一次循环体。
- `for` 退出循环之后，循环变量的值就是向量最后的元素值。
- 当向量为空时，不执行循环语句。

***一般格式：***

```matlab
for 循环变量 = 矩阵表达式
    循环体语句
end
```

- 矩阵的各列元素赋给循环变量。
    - 上面的 `for` 语句相当于一种特例。

> 下面两个 `for` 语句引导的循环结构，其循环体执行次数不相同。
> ```matlab
> for k = [1, 2, 3, 4]  % 执行 4 次
> for k = [1; 2; 3; 4]  % 执行 1 次
> ```

例；计算圆周率 &pi;。

- 利用无穷级数展开式求 &pi; 的近似值。

```matlab
y = 0;
x = 1;
n = input('n = ');
for i = 1 : n
    y = y + x / (2 * i - 1);
    x = -x;
end
disp(y * 4);
```

- 利用向量求和简化运算

```matlab
n = input('n = ');
x = 1 : 2 : 2n-1;
y = (-1) ^ (2 : n+1) ./ x;
disp(sum(y) * 4);
```

- 利用定积分的近似值求 &pi; 的近似值。

设 $latex f(x) = \sqrt{1 - x^2} $，求 $latex \frac{x}{4} = \int_0^1 f(x)\mathrm{d}x $。
即求四分之一单位圆的面积。

```matlab
a = 0;
b = 1;
n = input('n = ');
h = (b - a) / n;
x = a : h : b;
f = sqrt(1 - x .* x);
s = [];
for k = 1 : n
    s1 = (f(k) - f(k-1)) * h / 2;
    s = [s, s1];
end
disp(sum(s) * 4);
```

- 利用蒙特卡洛法求 &pi; 的近似值。

画一个边长为 2 的正方形，一个单位圆内切于正方形。
在正方形内随机投点，设落在圆内的概率为 P，即 P = 落在圆内的点数/所投点的总数。
根据面积关系，$latex P = \frac{\pi * 1^2}{2^2} = \frac{\pi}{4}$。
故有 $latex \pi = 4P$。

令单位圆的圆心为坐标原点，所投点在圆内的充要条件为 $latex x^2+y^2\le 1 $。

```matlab
s = 0;
n = input('n = ');
for i = 1 : n
    x = rand(1);
    y = rand(1);
    if x^2 + y^2 <= 1
        s = s + 1;
    end
end
disp(s / n * 4);
```

### while 语句

```matlab
while 条件
    循环体语句
end
```

- `while` 语句多用于循环次数不能确定的情况，而对于循环次数确定的情况，`for` 语句会更方便。
- 针对不同情况可以选择不同的循环语句，但从功能上将两种循环语句可以相互替代。

### break 语句和 continue 语句

- `break` 语句用来跳出循环体，结束整个循环。
- `continue` 语句用来结束本次循环，接着进行下次是否执行循环的判断。

### 循环的嵌套

如果一个循环结构的循环体又包含一个循环结构，就称为 *循环的嵌套*，或称为 *多重循环结构*。

例：用筛选法求某自然数范围内的所有素数。

筛选法求素数的基本思路：
要找出 2 ~ m 之间的全部素数，首先在 2 ~ m 中划去 2 的倍数（不包括 2），然后划去 3 的倍数（不包括 3）。
由于 4 已被划去（2 的倍数），故划去 5 的倍数（不包括 5），直到划去不超过 $latex \sqrt{m} $ 的倍数，剩下的数都是素数。

```matlab
m = input('m = ');
p = 1 : m;
p(1) = 0;

for i = 2 : sqrt(m)
    for j = 2 * i : i : m
        p(j) = 0;
    end
end

n = find(p ~= 0);
disp(p(n));
```

## 函数文件的定义与调用

### 函数文件的基本结构

```matlab
function 输出形参表 = 函数名(输出形参表)
注释说明部分
函数体语句
```

- 在函数定义时，输入输出参数均没有分配空间，故都称为 **形式参数**，简称 **形参**。
- 在有多个形参时，形参之间用 *逗号* 分隔，组成形参表。
- 当输出形参多于一个时，应该用 **方括号 `[]`** 括起来，构成一个输出矩阵。

> 函数文件名通常由函数名再加上扩展名 `.m` 组成，也可以不相同。
> 当不相同时，系统将忽略函数名，调用时将使用函数文件名。

- `return` 语句表示结束函数的执行。
    - 不使用时默认执行完整个函数。

例：编写函数文件，求半径为 r 的圆的面积与周长。

fcircle.m
```matlab
function [s, p] = fcircle(r)
s = pi * r * r;
p = 2 * pi * r;
```

### 函数调用

调用格式：`[输出实参表] = 函数名(输出实参表)`

- 在调用函数时，函数输入输出参数称为 **实际参数**，简称 **实参**。
- 实参的顺序和个数应与函数定义时形参的顺序和个数一致。

例：
命令行窗口
```matlab
[s, p] = fcircle(10)
```

### 匿名函数

基本格式：`函数句柄变量 =@(函数输入参数) 匿名函数表达式`

例：

```matlab
f = @(x, y) x^2+y^2

f(3, 4)
```

给已经存在的函数创建函数句柄：`函数句柄变量 =@函数名`

例：

```matlab
h = @sin

h(pi / 2)
```

## 函数的递归调用

如果在一个函数的定义中，调用了其他函数，这就是 **函数的嵌套调用**。
一个函数调用它自身称为 **函数的递归调用**。

- 直接递归调用
    - 在函数定义中直接调用函数本身。
- 间接递归调用
    - 在函数定义中嵌套调用其它函数，在其他函数中再嵌套调用该函数。

例 1：利用函数的递归调用，求 $latex n! $。

$$ n! = 
\begin{cases}
1 &, n \le 1 \\\\
n * (n-1)! &, n &gt; 1
\end{cases}
$$

fact.m
```matlab
function f = fact(n)
if n <= 1
    f = 1;
else
    f = fact(n - 1) * n;
end
```

例 2：Fibonacci 数列定义如下：

$$ F(n) = 
\begin{cases}
1&, n = 1, 2 \\\\
F(n-1) + F(n-2) &, n \ge 3 
\end{cases}
$$

编写递归调用函数求 Fibonacce 数列的第 n 项，然后调用该函数验证 Fibonacci 数列的如下性质：

$$F(1)^2 + F(2)^2 + \cdots + F(n)^2 = F(n) * F(n+1)$$

fibonacci.m
```matlab
function f = fibonacci(n)
if n > 2
    f = fibonacci(n) + fibonacci(n-1)
else
    f = 1
end
```

test.m
```matlab
for k = 1 : 20
    F = [F, fibonacci(k)*fibonacci(k)]
end
sum(F) == fibonacci(k) * fibonacci(k+1)
```

## 函数参数与变量的作用域

### 函数参数的可调性

Matlab 中，函数所传递的参数数目是 **可调的**。

***两个预定义变量：***

- `nargin`：调用函数时，输入实参的个数。
- `nargout`：调用函数时，输出实参的个数。

test.m
```matlab
function fout = test(a, b, c)

if nargin == 1
    fout = a;
elseif nargin == 2
    fout = a + b;
elseif nargin == 3
    fout = a * b * c / 2;
end
```

### 变量的作用域

**局部变量** 是指在程序中只在特定过程或函数中可以访问的变量。

> 函数文件中定义的变量就是局部变量，不能被其他函数文件调用。

**全局变量** 的作用域为整个 Matlab 工作空间，即全局有效，所有的函数都可以对它进行存取和修改。

- 定义格式：`global 变量名`

例：
wad.m
```matlab
function f = wad(x, y)
global ALPHA BETA
f = ALPHA * x + BETA * y;
```

命令行窗口
```matlab
global ALPHA BETA
ALPHA = 1;
BETA = 2;
s = wad(1, 2)
```

> 在函数文件中定义全局变量后，也要在工作空间中定义对应的全局变量。
