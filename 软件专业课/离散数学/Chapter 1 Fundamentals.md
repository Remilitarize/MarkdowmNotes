[toc]

## Sets and Subsets 集合和子集

### Sets 集合

**集合（Sets）** 是任何有 **明确定义的** 对象的集合。  
这些对象称为集合的 **元素（elements）** 或 **成员（members）**。  
明确定义的是指能够确定一个已知对象是否属于该集合。  

- 集合中元素的顺序是否有序是无关紧要的。
- 集合中重复的元素可以被忽视。
- 集合中的元素可以是任何类型的事物，包括集合。

 x 是集合 A 中的元素，写作 x &in; A。  
 x 不是集合 A 中的元素，写作 x &notin; A。  

集合的表示方法：

- *枚举法*：在花括号之间列举出集合的元素。
    - {1, 2, 3}
- *描述法*：提炼出集合中元素具有共同性质进行描述。{x | P(x)}
    - {x | x is a positive integer less than 4}

常用集合的标识符号：

- Z<sup>+</sup> = {x | x is a **positive integer**} 正整数集（positive number）
- N = {x | x is a **posivitive integer or zero**} 自然数集（natural number）
- Z = {x | x is an **integer**} 整数集（integer）
- Q = {x | x is a **rational number**} 有理数集（rational number）
- R = {x | x is a **real number**} 实数集（real number）
- &empty; = {} 空集（empty set）

如果集合 A 与集合 B 具有相同的元素，则称集合 A 和 B **相等（equal）**，写作 A = B。

### Subsets 子集

如果集合 A 中每个元素也是集合 B 中的元素，也就是说，任何 x &in; A 都有 x &in; B，我们称 A 是 B 的 **子集（subsets）** 或 A **包含于（contained in）** B，写作 A &sube; B。  
集合 A 不是集合 B 的子集，写作 A &nsube; B。

我们使用 **维恩图（Venn diagrams）** 表示集合之间的关系。

![维恩图](http://oxnec2zdn.bkt.clouddn.com/DiscreteMath/weientu.PNG)

- Z<sup>+</sup> &sube; N &sube; Z &sube; Q &sube; R
- 每个集合都是自己的子集。
- 空集是任何集合的子集。
- A = B 当且仅当 A &sube; B 并且 B &sube; A。
- **全集（Universal set）** 是指在论述范围内包含所有对象的集合，用符号 U 表示。
    - 默认在论述范围内任何集合都是全集的子集。

![全集](http://oxnec2zdn.bkt.clouddn.com/DiscreteMath/quanji.PNG)

- 一个集合是 **有限集（finite set）** 是指集合中包含 n 个不同的元素，其中 n &in; N。
    - 如果一个集合是有限的，n 称为集合 A 的 **基数（cardinality）**，用 |A| 表示。
- 如果集合不是有限的称为 **无限集（infinite set）**。
- 如果 A 是一个集合，则所有集合 A 的子集的集合称为集合 A 的 **幂集（power set）**，用 P(A) 表示。
    - 如果 |A| = n，则 |P(A)| = 2<sup>n</sup>。

### 附带程序

> 程序地址 https://github.com/Remilitarize/ExerciseForBooks/tree/master/Discrete_Mathematical_Structures/Chapter_1_Fundamentals

1. 用枚举法表示集合（不包含元素为集合的集合）并判断一个元素是否属于该集合。
    - 程序名：`1_1_Enumeration_Method_And_Judge.exe`
2. 给出一串英文字母序列，用枚举法表示其对应的集合。
    - 程序名：`1_1_List_Letters.exe`
3. 给出所包含的子集，求具有最小基数的集合。
    - 程序名：`1_1_The_Set_of_Smallest_Cardinality.exe`
4. 给出集合，打印对应的幂集。
    - 程序名：`1_1_Power_Set.exe`

## Operations on Sets 集合运算

![集合操作](http://oxnec2zdn.bkt.clouddn.com/DiscreteMath/jihecaozuo.PNG)

集合的 **并集（union）**：A &cup; B = {x | x &in; A or x &in; B}
集合的 **交集（intersiction）**：A &cap; B = {x | x &in; A and x &in; B}

如果两个集合没有公共元素，则称它们为 **不相交集（disjoint sets）**。

集合 B 相对与 A 的 **补集（complement）**：A - B = {x | x &in; A and x &notin; B}
集合 A 的 **补集**：U - A = <span style = "text-decoration: overline">A</span> = {x | x &notin; A}

集合的 **对称差集（symmetric difference）**：A &oplus; B = {x | (x&in;A and x&notin;B) or (x&in;B and x&notin;A)}
**A &oplus; B = (A - B) &cup; (B - A)**

### Algebraic Properties of Set Operations 集合运算的代数性质

Commutative Properties 交换性

- A &cup; B = B &cup; A
- A &cap; B = B &cap; A

Associative Properties 结合性

- A &cup; (B &cup; C) = (A &cup; B) &cup; C
- A &cap; (B &cap; C) = (A &cap; B) &cap; C

Distributive Properties 分配性

- A &cap; (B &cup; C) = (A &cap; B) &cup; (A &cap; C)
- A &cup; (B &cap; C) = (A &cup; B) &cap; (A &cup; C)

Idempotent Properties 等幂性

- A &cup; A = A
- A &cap; A = A

Properties of the Complement 补集性质

- <span style = "text-decoration: overline">(<span style = "text-decoration: overline">A</span>)</span> = A
- A &cup; <span style = "text-decoration: overline">A</span> = U
- A &cap; <span style = "text-decoration: overline">A</span> = &empty;
- <span style = "text-decoration: overline">&empty;</span> = U
- <span style = "text-decoration: overline">U</span> = &empty;
- <span style = "text-decoration: overline">A&cup;B</span> = <span style = "text-decoration: overline">A</span> &cap; <span style = "text-decoration: overline">B</span>
- <span style = "text-decoration: overline">A&cap;B</span> = <span style = "text-decoration: overline">A</span> &cup; <span style = "text-decoration: overline">B</span>

> 后两条称为 **De Morgan's laws 德摩根定律**。

Properties of a Universal Set 全集性质

- A &cup; U = U
- A &cap; U = A

Properties of the Empty Set 空集性质

- A &cup; &empty; = A
- A &cap; &empty; = &empty;

### The Addtion Principle 加法原理

![加法原理](http://oxnec2zdn.bkt.clouddn.com/DiscreteMath/jiafayuanli.PNG)

> 又称为 **包含排除原理（inclusion-exclusion）**（**容斥原理**）。

**A、B 和 C 为有限集，则 |A&cup;B&cup;C| = |A| + |B| + |C| - |A&cap;B| - |B&cap;C| - |A&cap;C| + |A&cap;B&cap;C|。**

### 附带程序

> 程序地址 https://github.com/Remilitarize/ExerciseForBooks/tree/master/Discrete_Mathematical_Structures/Chapter_1_Fundamentals

1. 两集合求交集
    - 程序名：`1_2_Intersection.exe`
2. 两集合求并集
    - 程序名：`1_2_Union.exe`
3. 两集合求补集
    - 程序名：`1_2_Complement.exe`
4. 两集合求对称差集
    - 程序名：`1_2_Symmetric_Diffeence.exe`
5. 加法原理实现
    - 程序名：`1_1_Addtional_Principle.exe`

## Sequences 序列

**序列（sequence）** 是按一定顺序排列的一列对象。

- 如果在 n 步之后停止（n &in; N），则该序列是 *有限的（finite）*。
- 如果永远继续下去，则该序列是 *无限的（infinite）*。

> 序列中的元素可以不同，可以重复。

- 若公式由前项来定义后项，则称该公式是 **递归的（recursive）**。
    - a<sub>1</sub> = 1
    - a<sub>n</sub> = a<sub>n-1</sub> + 2 (n &ge; 2)
- 若公式以所在位置描述序列中的各项，则称该公式是 **直接的（explicit）**。
    - a<sub>n</sub> = 2n - 1

若不用逗号分隔开，由字母或其他符号所组成的序列又称为 **字符串（string）**。

**序列的集合（the set correspoonding to a sequence）** 是指由序列中所有不同元素所组成的集合。

> 在计算机科学中，序列有时称为 **线性数组（linear array）** 或 **列表（list）**。

已知序列 S: s<sub>1</sub>, s<sub>2</sub>, s<sub>3</sub>, ...，我们认为 S 的所有元素是 *完全确定的*。
例如，元素 s<sub>4</sub> 是 S 的某个固定元素，定位在第四个位置上。
当我们改变任何一个元素，我们将会得到一个新的序列，并将可能用其他名字来命名，例如 S&prime;。

|Position:1 S[1]|Position:2 S[2]|Position:3 S[3]|...|
|-|-|-|-|

一个数组，可以看作是 *位置的序列*。
位于位置 n 上的元素将会定义为 S[n]，则序列 S[1], S[2], S[3], ... 称为数组 S 的 **值序列**。

### Characteristic Functions 特征函数

如果 A 是全集 U 的一个子集，则 A 的 **特征函数（characteristic function） f<sub>A</sub>** 定义为以下形式：

- **f<sub>A</sub>(x) = 1  if x &in; A**
- **f<sub>A</sub>(x) = 0  if x &notin; A**

子集的特征函数满足以下性质：

- *f<sub>A&cap;B</sub> = f<sub>A</sub>f<sub>B</sub>，即对于所有 x，f<sub>A&cap;B</sub>(x) = f<sub>A</sub>(x)f<sub>B</sub>(x)*
- *f<sub>A&cup;B</sub> = f<sub>A</sub> + f<sub>B</sub> - f<sub>A</sub>f<sub>B</sub>，即对于所有 x，f<sub>A&cup;B</sub>(x) = f<sub>A</sub>(x) + f<sub>B</sub>(x) - f<sub>A</sub>(x)f<sub>B</sub>(x)*
- *f<sub>A&oplus;B</sub> = f<sub>A</sub> + f<sub>B</sub> - 2f<sub>A</sub>f<sub>B</sub>，即对于所有 x，f<sub>A&oplus;B</sub>(x) = f<sub>A</sub>(x) + f<sub>B</sub>(x) - 2f<sub>A</sub>(x)f<sub>B</sub>(x)*

### Computer Representation of Sets and Subsets 集合与子集的计算机表示

U = {1, 2, 3, 4, 5, 6}
A &sube; U, B &sube; U, C &sube; U
A = {1, 2}
B = {2, 4, 6}
C = {4, 5, 6}

f<sub>A</sub> = 1, 1, 0, 0, 0, 0
f<sub>B</sub> = 0, 1, 0, 1, 0, 1
f<sub>C</sub> = 0, 0, 0, 1, 1, 1

全集 U 可表示为长度为 6 的数组：

|1|1|1|1|1|1|
|-|-|-|-|-|-|

子集 A 可表示为长度为 6 的数组：

|1|1|0|0|0|0|
|-|-|-|-|-|-|

如果集合可以对应到某个序列，则称该集合是 **可数的（countable）**。
一个集合如果不是可数的，则称该集合是 **不可数的（uncountable）**。

### Strings and Regular Expressions 字符串与正则表达式

对于给定的集合 A，可以构造一个集合 A<sup>\*</sup> 包含集合 A 中元素的所有有限序列。
此时，A 称为 **字母表（alphabet）**，A<sup>\*</sup> 中的有限序列称为 **单词（words）**，或者 *字符串（strings）*。

> 特别地，A<sup>\*</sup> 中的序列不能用逗号分隔。

我们假设 A<sup>\*</sup> 包含 **空序列（empty sequence）** 或 **空字符串（empty string）**，即没有包含任何符号。
使用 &Lambda; 表示该字符串。

> A 中所有有限序列都包含在 A<sup>\*</sup>，无论是否有意义。

如果 w<sub>1</sub> = s<sub>1</sub>s<sub>2</sub>...s<sub>n</sub> 和 w<sub>2</sub> = t<sub>1</sub>t<sub>2</sub>...t<sub>n</sub> 是集合 A 的 A<sup>\*</sup> 中的元素，则 w<sub>1</sub> 和 w<sub>2</sub> 的 **并置** 定义为 s<sub>1</sub>s<sub>2</sub>...s<sub>n</sub>t<sub>1</sub>t<sub>2</sub>...t<sub>n</sub>，写作 w<sub>1</sub>&sdot;w<sub>2</sub> 或 w<sub>1</sub>w<sub>2</sub>，且为 A<sup>\*</sup> 的另一个元素。

注意：如果 w 属于 A<sup>\*</sup>，则 **w&sdot;&Lambda; = w** 且 **&Lambda;&sdot;w = w**。

> 在形式语言和有限状态机中，正则表达式的概念起着重要作用。

集合 A 上的 **正则表达式（regular expression）** 是由 A 中元素和一些符号 (, ), &or;, \*, &Lambda;（根据下面的定义）构成的字符串。

- **符号 &Lambda; 是正则表达式。**
- **如果 x &in; A，则符号 x 是正则表达式。**
- **如果 &alpha; 和 &beta; 是正则表达式，则表达式 &alpha;&beta; 是正则的。**
- **如果 &alpha; 和 &beta; 是正则表达式，则表达式 (&alpha;&or;&beta;) 是正则的。**
- **如果 &alpha; 是正则表达式，则表达式 (&alpha;)\* 是正则的。**

注意第一条和第二条提供初始的正则表达式。
其他定义依次在已经存在的定义上重复定义更大的正则表达式集合。
因此该定义是 *递归的*。

方便地，如果正则表达式 &alpha; 存在一个单独的符号 x（x &in; A），或者 &alpha; 由圆括号起始和结束，则可以将 (&alpha;)\* 简写为 &alpha;\*。

当不存在混淆结果时，我们将适用于 A 上的正则表达式简单定义为 **正则表达式**（忽略提及 A）。

有关 A 上的每个正则表达式，存在一个 A<sup>\*</sup> 的对应子集。如果不需要提及 A，则这样的子集称为 **正则集（regular sets）**。

计算正则集的相关规则：

- A<sup>\*</sup> 的空字符串 &Lambda; 与集合 {&Lambda;} 相关。
- 如果 x &in; A，则正则表达式 x 与集合 {x} 相关。
- 如果 &alpha; 和 &beta; 与 A<sup>\*</sup> 的子集 M 和 N 相关，则 &alpha;&beta; 与 M&sdot;N 相关。
    - 因此 M&sdot;N 是所有 M 和 N 中字符串并置的集合。
- 如果正则表达式 &alpha; 和 &beta; 与 A<sup>\*</sup> 的子集 M 和 N 相关，则 (&alpha;&or;&beta;) 与 M&cup;N 相关。
- 如果正则表达式 &alpha; 与 A<sup>\*</sup> 的自己 M 相关，则 (&alpha;)\* 与集合 M\* 相关。

### 附带程序

1. 给出全集和一个集合，生成该集合的特征函数。
2. 应用特征函数实现集合的并集。
3. 应用特征函数实现集合的交集。
4. 应用特征函数实现集合的补集。
5. 应用特征函数实现集合的对称差集。

## Properties of Integers 整数的性质

**如果 n 和 m 是整数且 n &gt; 0，可以用整数 q 和 r 写作 m = qn + r（0 &le; r &le; n）。**

如果 r 为 0，那么 m 是 n 的 **倍数（multiple）**，写作 n | m。读作 n 整除（divide） m。
如果 n | m，则 m = qn 且 n &le; |m|。

m 不是 n 的倍数，写作 n ∤ m，读作 n 不整除 m。

整除的性质（a, b 和 c 为整数）：

- 如果 a | b 且 b | c，则 a | (b + c)。
- 如果 a | b 且 a | c（b &gt; c），则 a | (b - c)。
- 如果 a | b 或 a | c，则 a | bc。
- 如果 a | b 且 b | c，则 a | c。

作为上面性质的总结，**如果 a | b 且 a | c，则 a | (mb + nc)**。

如果数字 p（p &gt; 1 且 p &in; Z<sup>+</sup>）只能被 p 和 1 整除，则该数字称为 **质数（prime）**。

很容易写一系列的步骤或者 **算法** 来确定一个正整数 n（n &gt; 1）是否是一个质数。

1. 检查 n 是否是 2。
2. 如果 n &gt; 2，则从 2 到 n-1 中每个整数与 n 相除，且没有一个是 n 的因子，则 n 是质数。

注意：

- 若 mk = n，则 **m 或 k 均小于等于 &radic;n**。
    - 这意味着如果 n 不是一个质数，则存在一个因子 k 满足 1 &lt; k &le; &radic;n。
- 如果 n 具有任何一个偶数因子，则必然存在因子 2。
    - 因此在检查完 2 是否可以整除后，**跳过所有偶数的整数**。

### Algorithm 算法

检测 N &gt; 1 是否是一个质数：

1. 检查 N 是否为 2。
    - 如果是，N 是一个质数。
    - 如果不是，继续执行。
2. 检查是否 2 | N。
    - 如果是，N 不是一个质数。
    - 否则，继续执行。
3. 计算 K &le; &radic;N。
4. 检查是否 D | N，其中 D 是奇数且 1 &lt; D &le; K。
    - 如果是，N 不是一个质数。
    - 否则，N 是质数。

> 这个算法对于测试非常大的数字效率十分差，但存在许多其他算法来测试一个整数是否是质数。

任何正整数 n &gt; 1 可以唯一地写作 p<sub>1</sub><sup>k<sub>1</sub></sup>p<sub>2</sub><sup>k<sub>2</sub></sup>...p<sub>s</sub><sup>k<sub>s</sub></sup>，此时 p<sub>1</sub> &lt; p<sub>2</sub> &lt; ... &lt; p<sub>s</sub> 是可以整除 n 的不同质数，且 k 是一个正整数，表示每个质数出现在 n 的因子中的次数。

- 9 = 3 &sdot; 3 = 3&sup2;
- 24 = 8 &sdot; 3 = 2&sup3; &sdot; 3
- 30 = 2 &sdot; 3 &sdot; 5

### Greatest Common Divisor 最大公约数

如果 a, b, k &in; Z<sup>+</sup>，且 k | a 和 k | b，则称 k 是 a 和 b 的 **公约数（common divisor）**。
如果 d 是 k 中最大者，d 称为 a 和 b 的 **最大公约数（the greatest common divisor）** 或 **GCD**，写作 d = GCD(a, b)。

如果 d 是 GCD(a, b)，则

- 对于一些正整数 s 和 t，有 d = sa + tb（可以不是正的）。
- 如果 c 是 a 和 b 的任意其他公约数，则 c | d。

如果 GCD(a, b) = 1，则称 a 和 b 是 **互质数（relatively prime）**。
可以使用一个过程，称为 **欧几里得算法（Euclidean algorithm）**，来寻找 GCD(a, b)。

1. 对于任意的 a &gt; b &gt; 0，必有 a = k<sub>1</sub>b + r<sub>1</sub>。
    - 因为 r<sub>1</sub> = a - k<sub>1</sub>b，则 a 和 b 的最大公约数一定整除 r<sub>1</sub>。
    - 即 GCD(a, b) = GCD(b, r<sub>1</sub>)。
2. 则 b &gt; r<sub>1</sub> &gt; 0，必有 b = k<sub>2</sub>r<sub>1</sub> + r<sub>2</sub>。
    - 即 GCD(b, r<sub>1</sub>) = GCD(r<sub>1</sub>, r<sub>2</sub>)。
3. 以此类推，直至 r<sub>n+1</sub> = 0。
    - 则 GCD(r<sub>n-1</sub>, r<sub>n</sub>) = GCD(r<sub>n</sub>, r<sub>n+1</sub>) = r<sub>n</sub>。
4. **GCD(a, b) = r<sub>n</sub>**。

> 例：计算 GCD(273, 98)。

> - 273 = 2 &sdot; 98 + 77
> - 98 = 1 &sdot; 77 + 21
> - 77 = 3 &sdot; 22 + 14
> - 21 = 1 &sdot; 14 + 7
> - 14 = 2 &sdot; 7 + 0

> GCD(273, 98) = 7。

对于整个欧几里得算法过程，我们可以从 r<sub>n</sub> 反推回去，得到 GCD(a, b) = k<sub>1</sub>a + k<sub>2</sub>b。

> GCD(273, 98) = 7 
> - = 21 - 1 &sdot;14
> - = 21 - 1(77 - 3 &sdot; 21)
> - = 4 &sdot; 21 - 1 &sdot; 77
> - = 4(98 - 1 &sdot; 77) - 1 &sdot; 77
> - = 4 &sdot; 98 - 5 &sdot; 77
> - = 4 &sdot; 98 - 5(273 - 2 &sdot; 98)
> - = 14(98) - 5(273)

**如果 a, b &in; Z<sup>+</sup>，则 GCD(a, b) = GCD(b, b&plusmn;a)。**

### Least Common Multiple 最小公倍数

如果 a, b, k &in; Z<sup>+</sup>，且 a | k，b | k，则 k 是 a 和 b 的一个 **公倍数（common multiple）**。
如果 c 是 k 中最小者，则 c 称为 a 和 b 的 **最小公倍数（the least common multiple）**，或 **LCM**，写作 c = LCM(a, b)。

**如果 a 和 b 是两个正整数，则 GCD(a, b) &sdot; LCM(a, b) = ab。**

对于每个 n &in; Z<sup>+</sup>，定义一个函数 **f<sub>n</sub> 模 n 函数（mod-n function）**，描述如下：
如果 z 是一个非负整数，f<sub>n</sub>(z) = r，即 当 z 被 n 除得到的余数。

### Pseudocode Versions 伪代码

判断质数：

```
SUBROUTINE PRIME(N)

1. IF (N = 2) THEN
    a. PRINT ('PRIME')
    b. RETURN
2. ELSE
    a. IF (N/2 = INT(N/2)) THEN
        1. PRINT ('NOT PRIME')
        2. RETURN
    b. ELSE
        1. FOR D = 3 THRU SQR(N) BY 2
            a. IF (N/D = INT(N/D)) THEN
                1. PRINT ('NOT PRIME')
                2. RETURN
        2. PRINT ('PRINT')
        3. RETURN
END OF SUBROUTINE PRIME 
```

欧几里得算法

```
FUNCTION GCD(X, Y)

1. WHILE (X ≠ Y)
    a. IF (X > Y) THEN
        1. X ← X - Y
    b. ELSE
        1. Y ← Y - X
2. RETURN (X)
END OF FUNCTION GCD
```

### Representations of Integers 整数的表示

对于 3264 可以分解为以下形式：
3264 = 3 \* 10&sup3; + 2 \* 10&sup2; + 6 \* 10<sup>1</sup> + 4 \* 10<sup>0</sup>
则称 3264 是 **n 的基数为 10 的展开式（base 10 expansion of n）** 或 **n 的十进制展开（decimal expansion of n）**。
10 称为该展开的 **基数（base）**。

> 基数为 2，8，16 常用于计算机科学，基数为 26 常用于密码学（cryptology）。

如果 b &gt; 1 且 b &in; Z，那么任何正整数 n 能够唯一地表示为下面形式：
**n = d<sub>k</sub>b<sup>k</sup> + d<sub>k-1</sub>b<sup>k-1</sup> + ... + d<sub>1</sub>b + d<sub>0</sub>**
这里 0 &le; d<sub>k</sub> &lt; b, i = 0, 1, ..., k 且 d<sub>k</sub> &ne; k。
序列 d<sub>k</sub>d<sub>k-1</sub>...d<sub>1</sub>d<sub>0</sub> 称为 **n 的基数为 b 的展开式**。
通常写作 **(d<sub>k</sub>d<sub>k-1</sub>...d<sub>1</sub>d<sub>0</sub>)<sub>b</sub>**。

例：求 158 的基数为 4 的展开式。

![158jishuwei4zhankaishi](http://oxnec2zdn.bkt.clouddn.com/DiscreteMath/158jishuwei4zhankaishi.PNG)

```
SUBROUTINE EXPANSION(N)

1. Q ← N
2. K ← 0
3. WHILE (Q ≠ 0)
    a. Dk ← Q mod B
    b. Q ← INT(Q/B)
    c. K ← K + 1
4. RETURN
END OF SUBROUTINE EXPANSION
```

- 由于被 2 除的余数只有 0 和 1，所以每个数的二进制展开式只需要 0 和 1，容易通过计算机的 *开关数字电路* 来实现和操作。
- 对于十六进制展开式，通常需要使用 0-9 这 10 个数字以及 ABCDEF 表示，其中 A-F 分别对应 10-16。
- 对于二十六进制展开式，通常使用 A-Z 表示 0-25。

密码学的例子 1：

- 待编码的消息：FLEE NOW
- 转换为二进制：00101 01011 00100 00100 01101 01110 10110
- 假消息（dommy message）：ONCE UPON A TIME IN THE WEST THERE WAS A TOWN
- 整理形式（加密消息）：ON*C*E*U* P*O*N*AT* IM*E*IN TH*E*WE S*TT*H*E* R*EWA*S *A*T*OW*N
    - 斜体对应二进制中的 1，其余对应二进制中的 0。

密码学的例子 2：

- 待解码信息（假消息）：*N*OW *I*S *T*HE *TI*ME FOR *A*LL G*OO*D M*EN* T*O* AI*D* T*HE C*OUNTR*Y*
- 整理形式：*N*OW*I*S *T*HE*TI* MEFOR *A*LLG*O O*DM*EN* T*O*AI*D* T*HEC*O UNTR*Y*
- 转换为二进制：10010 10011 00000 10001 10011 01001 01110 00001
- 转换为二十六进制：START JOB

> 上述两个例子使用的是 *速记式加密*。

### 附带程序

1. 判断一个正整数是否是素数。
2. 将一个正整数质因数分解。
3. 求两个正整数的最大公约数。
4. 实现一个十进制数转换成任意进制数。
5. 给出一串假消息（用大小写字母表示，大写对应 0，小写对应 1），通过速记式加密进行解码。
6. 二进制数、四进制数、八进制数、十六进制数相互转换。

## Matrix 矩阵

**矩阵（matrixes）** 是一系列将数字排列成 m 行 n 列的矩形数列。

A = 

![矩阵形式](http://oxnec2zdn.bkt.clouddn.com/DiscreteMath/juzhenxingshi.PNG)

通常称矩阵 A 是 **m &times; n** 的。

- 对于矩阵中每个元素 a<sub>ij</sub>，表示矩阵 A 在第 i 行第 j 列的 **元素（entry）**，或 **(i, j) 元**。
- 如果 m = n，则称矩阵 A 是 **方阵（square matrix）**。
    - a<sub>11</sub>, a<sub>22</sub>, ..., a<sub>nn</sub> 构成矩阵 A 的 **主对角线（main diagonal）**。
    - 方阵中除主对角线上的元外的其他元均为 0（a<sub>ij</sub> = 0，i &ne; j），则称为 **对角矩阵（diagonal matrix）**。

> 为了简便，通常将矩阵写作 A = [a<sub>ij</sub>]。

矩阵 A = [a<sub>ij</sub>] 和矩阵 B = [b<sub>ij</sub>] **相等** 仅当 a<sub>ij</sub> = b<sub>ij</sub>，1 &le; i &le; m，1 &le; j &le; n。
矩阵 A = [a<sub>ij</sub>] 和矩阵 B = [b<sub>ij</sub>] 的 **和** 为矩阵 C = [c<sub>ij</sub>]，其中 c<sub>ij</sub> = a<sub>ij</sub> + b<sub>ij</sub>，1 &le; i &le; m，1 &le; j &le; n。

例：

![矩阵加法](http://oxnec2zdn.bkt.clouddn.com/DiscreteMath/juzhenjiafa.PNG)

所有元均为 0 的矩阵称为 **零矩阵（zero matrix）**，记为 **0**。

![零矩阵](http://oxnec2zdn.bkt.clouddn.com/DiscreteMath/lingjuzhen.PNG)

矩阵的加法性质：

- A + B = B + A
- (A + B) + C = A + (B + C)
- A + 0 = 0 + A = A

矩阵 A = [a<sub>ij</sub>] 是一个 m &times; p 矩阵，矩阵 B = [b<sub>ij</sub>] 是一个 p &times; n 矩阵，则两者之 **积（product）** 为矩阵 C = [c<sub>ij</sub>]，其中 c<sub>ij</sub> = a<sub>i1</sub>b<sub>1j</sub>+a<sub>i2</sub>b<sub>2j</sub>+ ... +a<sub>ip</sub>b<sub>pj</sub>，1 &le; i &le; m，1 &le; j &le; n。

![矩阵乘法](http://oxnec2zdn.bkt.clouddn.com/DiscreteMath/juzhenchengfa.PNG)

对角元素均为 1 的对角矩阵称为 **单位矩阵（identity matrix）**。

![单位矩阵](http://oxnec2zdn.bkt.clouddn.com/DiscreteMath/danweijuzhen.PNG)

矩阵的乘法性质：

- **AB &ne; BA**（一般情况下）
- A(BC) = (AB)C
- A(B + C) = AB + AC
- (A + B)C = AC + BC
- 如果 A 是一个 m &times; n 的矩阵，I<sub>m</sub>A = AI<sub>n</sub> = A。
- 定义 A<sup>p</sup> = A &sdot; A &sdot; ... &sdot; A 且 A<sup>0</sup> = I<sub>n</sub>。
    - A<sup>p</sup>A<sup>q</sup> = A<sup>p+q</sup>
    - (A<sup>p</sup>)<sup>q</sup> = A<sup>pq</sup>
    - 当 AB = BA 时，(AB)<sup>p</sup> = A<sup>p</sup>B<sup>p</sup>

矩阵 A = [a<sub>ij</sub>] 是一个 m &times; n 的矩阵，则其 **转置（transpose）** A<sup>T</sup> = [a<sub>ij</sub><sup>T</sup>] 是一个 n &times; m 的矩阵，其中 a<sub>ij</sub><sup>T</sup> = a<sub>ji</sub>，1 &le; i &le; m，1 &le; j &le; n。

![矩阵转置](http://oxnec2zdn.bkt.clouddn.com/DiscreteMath/juzhenzhuanzhi.PNG)

矩阵的转置性质：

- (A<sup>T</sup>)<sup>T</sup> = A
- (A + B)<sup>T</sup> = A<sup>T</sup> + B<sup>T</sup>
- (AB)<sup>T</sup> = B<sup>T</sup>A<sup>T</sup>

矩阵 A = [a<sub>ij</sub>] 是 **对称的（symmetric）** 仅当 A<sup>T</sup> = A。

如果 x 是非零数，存在一个 y 使得 xy = 1，则数字 y 称为 x 的 **乘法逆元（multiplicative inverse）**。
如果矩阵 A 和 B 均为 n &times; n 矩阵且 AB = I<sub>n</sub> 且 BA = I<sub>n</sub>，矩阵 B 称为矩阵 A 的 **逆（inverse）**。

> 矩阵的逆不一定存在。

![22 矩阵求逆](http://oxnec2zdn.bkt.clouddn.com/DiscreteMath/22juzhenqiuni.PNG)

> 2 &times; 2 的矩阵存在逆的条件：**ad-bc &ne; 0**。

### Boolean Matrix Operations 布尔矩阵运算

**布尔矩阵（Boolean matrix）**（或 **位矩阵（bit matrix）**）是所有元不是 0 就是 1 的矩阵。

- 令 A = [a<sub>ij</sub>] 且 B = [b<sub>ij</sub>] 为 m &times; n 矩阵。
- 定义矩阵 A 与矩阵 B 的 **并** 为矩阵 C = [c<sub>ij</sub>]，记为 A &or; B = C。
    - 当 a<sub>ij</sub> = 1 或 b<sub>ij</sub> = 1，c<sub>ij</sub> = 1。
    - 当 a<sub>ij</sub> 和 b<sub>ij</sub> 均为 0 时，c<sub>ij</sub> = 0。
- 定义矩阵 A 与矩阵 B 的 **交** 为矩阵 C = [c<sub>ij</sub>]，记为 A &and; B = C。
    - 当 a<sub>ij</sub> 和 b<sub>ij</sub> 均为 1 时，c<sub>ij</sub> = 1。
    - 当 a<sub>ij</sub> = 0 或 b<sub>ij</sub> = 0 时，c<sub>ij</sub> = 0。
- 定义矩阵 A 与矩阵 B 的 **布尔积** 为矩阵 C = [c<sub>ij</sub>]，记为 A ⊙ B = C。
    - 当 1 &le; k &le; p 时，存在 a<sub>ik</sub> = 1 且 b<sub>kj</sub> = 1，则 c<sub>ij</sub> = 1。
    - 其他情况时，c<sub>ij</sub> = 0。

![布尔积](http://oxnec2zdn.bkt.clouddn.com/DiscreteMath/buerji.PNG)

例：

![矩阵布尔运算](http://oxnec2zdn.bkt.clouddn.com/DiscreteMath/juzhenbueryunsuan.PNG)

矩阵的布尔运算性质：

- A &or; B = B &or; A
- A &and; B = B &and; A
- (A &or; B) &or; C = A &or; (B &or; C)
- (A &and; B) &and; C = A &and; (B &and; C)
- A &and; (B &or; C) = (A &and; B) &or; (A &and; C)
- A &or; (B &and; C) = (A &or; B) &and; (A &or; C)
- (A ⊙ B) ⊙ C = A ⊙ (B ⊙ C)

### 附带程序

1. 计算两个矩阵 A、B 的和 A+B 与差 A-B。
2. 计算两个矩阵 A、B 的积 AB 和 BA，并判断是否相等。
3. 实现一个矩阵的转置。
4. 计算一个 2&times;2 矩阵的逆。
5. 给出两个布尔矩阵 A、B，计算 A&and;B 和 A&or;B。
6. 给出两个布尔矩阵 A、B，计算 A⊙B。

## Mathematical Structures 数学结构

一系列对象与定义在对象之上的操作、附带的性质形成 **数学结构（mathematical structure）** 或 **系统（system）**。

例如矩阵的数学结构：(matrics, +, *, <sup>T</sup>)。

每个结构 **对于运算是封闭的（closed with respect to an operation）**，指的是执行一次操作，得到的结果总是结构中的对象内。

- 一个运算具有两个操作对象，则该运算是 **二元运算符（binary operation）**。
- 一个运算只需要一个对象，则该运算是 **一元运算符（unary operation）**。

如果二元运算符中操作对象的顺序不影响结果，则称该运算是 **可交换的（commutative）**。
例：布尔矩阵中的交和并操作是可交换的，矩阵中的乘法是不可交换的。

如果 □ 是一个二元运算符，那么 □ 具有 **可结合的（associative）** 或 **具有结合性** 仅当 (x □ y) □ z = x □ (y □ z)。

如果一个数学结果具有两个二元运算符 □ 和 ○，那么 **分配性（distributive property）** 具有下面形式：
x □ (y ○ z) = (x □ y) ○ (x □ z)

如果一个具有二元操作符的数学结构中具有一个对象 e，且对于数学结构中的所有 x 具有性质 x □ e = e □ x = x，则称 e 是 □ 的 **单位元（identity）**。
例如：矩阵加法中零矩阵就是单位元，矩阵乘法中单位矩阵就是单位元。

如果一个二元操作符 □ 具有一个单位元 e，则称 y 是 x 对于 □ 的 **逆（inverse）** 仅当 x □ y = y □ x = e。

### 附带程序

空

## 课后习题解答

### 1.1 Exercises

1. T F F F T F
    - 空集是 A 的子集，但不属于 A。
    - A 是 A 的子集，但不属于 A。
2. T F F T T F
3. （注意顺序无关紧要，但不能存在重复元素）
    1. A = {A, R, D, V ,K}
    2. B = {B, O, K}
    3. C = {M, I, S, P}
4. 
    1. A = {1, 2, 3, 4, 5, 6, 7, 8, 9}
    2. B = {-3, -2, -1, 0, 1, 2, 3}
5. F T F T F F
    - 注意 b、c 的区别以及 a、e 的区别。
6. {x | x = 2n, n &le; 5 and n &in; Z<sup>+</sup>}
7. {x | x is a vowel.}
8. {x | x = n&sup3;, n &le; 5 and n &in; Z<sup>+</sup>}
9. {x | x &in; Z and x&sup2; &lt; 5}
10. a e
    - d 中包含 0。
11. b c e
12. &empty; {a} {b} {a, b}
13. &empty; {JAVA} {PASCAL} {C++} {JAVA, PASCAL} {JAVA, C++} {PASCAL, C++} {JAVA, PASCAL, C++}
14. &empty;
15. T F F T T T T T
16. T T T T T
17. &sube; &sube; &nsube; &sube; &nsube; &sube;
18. {a, b, c, d, e, f, g}
19. {1, 2, 3}
20. {2, 3, 4, 6, 8, 9, 10, 12, 14, 15, 16, 18, 20, 21}
21. Yes. Yes, the complement of a set would not be defined unambiguously.
    - 从定义上来讲，全集只是论述范围内的全集，当论述范围改变时，全集也会改变。
    - 如果全集不同，则集合的补集会产生歧义。
22. F T F T T F
23. F F F F T T
24. 
    1. 2
        - 集合本身以及集合外部区域，
    2. 4
        - 两个集合不相交的区域（2 个），两个集合相交的区域，两个集合以外的区域。
25. 8
26. 
    1. P(A) = {{ }, {3}, {7}, {3, 7}}
    2. 2
    3. 4
27. {m, n}
28. 
    1. P(A) = {{ }, {3}, {7}, {2}, {3, 7}, {3, 2}, {7, 2}, {3, 7, 2}}
    2. 3
    3. 8
29. {a, b, c}
30. 见下面。
31. 见下面。
32. 见下面。
33. &empty; &sube; Z<sup>+</sup> &sube; N &sube; Z &sube; Q &sube; R
34. 见下面。
35. B B
36. 
    - 由题意可知，|P(A)| = n = 2<sup>|A|</sup>。
    - 那么 |P(B)| = 2<sup>|B|</sup> = 2<sup>|A|+1</sup> = 2<sup>|A|</sup> + 2<sup>|A|</sup> = 2n。
37. 4 8

![1-1 Exercise 1](http://oxnec2zdn.bkt.clouddn.com/DiscreteMath/1-1exercises1.PNG)

### 1.2 Exercises

1. 
    1. {a, b, c, d, e, f, g}
    2. {a, c, d, e, f, g}
    3. {a, c}
    4. {f}
    5. {b, d, e, g}
    6. {a, b, c}
    7. {d, e, f, h, k}
    8. {a, b, c, d, e, f}
    0. {b, g, f}
    10. {g}
2. 
    1. {a, b, c, f, g, h, k}
    2. {d, e, f, g, h, k}
    3. {f}
    4. &empty;
    5. {b}
    6. {d, e, g}
    7. {a, b, c, h, k}
    8. {a, c}
    0. {a, c, h, k}
    10. {g}
3. 
    1. {a, b, c, d, e, f, g}
    2. &empty;
    3. {a, c, g}
    4. {a, c, f}
    5. {h, k}
    6. {a, b, c, d, e, f, h, k}
4. 
    1. {a, b, c, g}
    2. {a, b, c, d, e, f, g, h, k}
    3. {d, e, f, g}
    4. &empty;
    5. {b, d, e, g}
    6. {a, b, c, d, e, f, g, h, k}
5. 
    1. {1, 2, 4, 5, 6, 8, 9}
    2. {1, 2, 3, 4, 6, 8}
    3. {1, 2, 4, 6, 7, 8}
    4. {1, 2, 3, 4, 5, 9}
    5. {1, 2, 4}
    6. {8}
    7. {2, 4}
    8. &empty;
6. 
    1. {1, 6, 8}
    2. {5, 9}
    3. {1, 2, 3, 4}
    4. {5, 6, 7, 8, 9}
    5. {3, 5, 7, 9}
    6. {1, 5, 6, 8, 9}
    7. {1, 2, 3, 4, 7, 8}
    8. {1, 3, 5, 9}
7. 
    1. {1, 2, 3, 4, 5, 6, 8, 9}
    2. {2, 4}
    3. {1, 2, 4}
    4. {8}
    5. {3, 7}
    6. {1, 3, 5, 6, 7, 8, 9}
8. 
    1. {1, 2, 3, 4, 5, 7, 8, 9}
    2. &empty;
    3. {1, 2, 4, 6, 8}
    4. &empty;
    5. {1, 2, 3, 4, 5, 6, 7, 8, 9}
    6. {6, 8}
9. 
    1. {b, d, e, h}
    2. {b, c, d, f, g, h}
    3. {b, d, h}
    4. {b, c, d, e, f, g, h}
    5. &empty;
    6. {c, f, g}
10. 
    1. {b, d, h}
    2. {a, b, c, d, e, f, g, h}
    3. {b, d, e, h}
    4. {a, c, d, e, f, g}
    5. {c, e, f, g}
    6. {a, b, e, h}
11. 
    1. {x | x &in; R and x &ne; &plusmn;1}
    2. {x | x &in; R and x &ne; -1, 4}
    3. {x | x &in; R and x &ne; &plusmn;1, 4}
    4. {x | x &in; R and x &ne; -1}
12. FTFT
13. TTFF
14. (A&cap;B)&cup;C（答案不唯一）
15. 1
16. 
    1. |A|=4 |B|=5 |A&cap;B|=2 |A&cup;B|=7
    2. |A|=4 |B|=5 |A&cap;B|=0 |A&cup;B|=9 
17. 
    1. |A|=6 |B|=7 |A&cap;B|=4 |A&cup;B|=10
    2. |A|=5 |B|=6 |A&cap;B|=0 |A&cup;B|=11
18. 
    1. A={1, 2, 3, 4, 5, 6, 7} B={2, 3, 4, 5} |A|=7 |B|=4 |A&cap;B|=4 |A&cup;B|=7
    2. A={1, 2, 3, 4} B={-1, -2, -3, -4, -5} |A|=4 |B|=5 |A&cap;B|=0 |A&cup;B|=9
19. B = &empty;
20. 略
21. 略
22. |A|=5 |B|=7 |C|=8 |A&cap;B|=2 |A&cap;C|=4 |B&cap;C|=3 |A&cap;B&cap;C|=2 |A&cup;B&cup;C|=13
23. |A|=6 |B|=5 |C|=6 |A&cap;B|=2 |A&cap;C|=3 |B&cap;C|=3 |A&cap;B&cap;C|=2 |A&cup;B&cup;C|=11
24. |A|=7 |B|=3 |C|=7 |A&cap;B|=3 |A&cap;C|=3 |B&cap;C|=2 |A&cap;B&cap;C|=2 |A&cup;B&cup;C|=11
25. 103 60
26. 20 325
27. 16 23
28. 30 28
29. 162 118 236 290 254
30. 245 388 677
31. 见下图
32. (A&cup;B)&cap;A=A
33. TTFF
34. Not Not Not Not Not Not
35. Not Not Not Not Not Not
36. T Not Not F T T
37. Not Not Not Not Not
38. Not Not Not Not T
39. A and to B
40. 
    1. 见下图
    2. C
    3. 略
41. 
    1. 见下图
    2. A, B
    3. 略
42. 略
43. Yes 略
44. 略
45. No A={1, 2, 3, 4} B={1, 2, 3} C={1, 2, 4}
46. No A={1, 2, 3, 4} B={1, 5} C={1, 6}
47. 略
48. A = B 略
49. 略
50. |A&cup;B&cup;C&cup;D| = |A| + |B| + |C| + |D| - |A&cap;B| - |A&cap;C| - |A&cap;D| - |B&cap;C| - |B&cap;D| - |C&cap;D| + |A&cap;B&cap;C| + |A&cap;B&cap;D| + |A&cap;C&cap;D| + |B&cap;C&cap;D| - |A&cap;B&cap;C&cap;D|
51. 略

![1-2 Exercises](http://oxnec2zdn.bkt.clouddn.com/DiscreteMath/1-2exercises.PNG)

### 1.3 Exercises

1. {1, 2}
2. {0, 2, 4, 6, 8, 10, ...}
3. {a, b, ..., z}
4. {a, b, c, d}
5. xyz xxyyzz xxxyz（答案不唯一）
6. 1, 2, 3, ...   1, 1, 2, 2, 3, 3, ...   1, 2, 2, 3, 3, 3, ...（答案不唯一）
7. 5, 25, 125, 625
8. -1, 10, 27, 50
9. 1, 2, 6, 24
10. 1, a+1, a&sup2;+a+1, (a&sup2;+1)(a+1)
11. 2.5, 4, 6.5, 8
12. -3, 7, -13, 27
13. 0, -2, -4, -6
14. 4, 8, 24, 96
15. 
    - recursive：a<sub>1</sub>=1  a<sub>n</sub>=a<sub>n-1</sub>+2
    - explicit：a<sub>n</sub>=2n-1
16. 
    - recursive：a<sub>1</sub>=0  a<sub>n</sub>=a<sub>n-1</sub>+(2n-1)
    - explicit：a<sub>n</sub>=n&sup2;-1
17. 
    - recursive：a<sub>1</sub>=1  a<sub>n</sub>=-a<sub>n-1</sub>
    - explicit：a<sub>n</sub>=(-1)<sup>n-1</sup>
18. 
    - recursive：a<sub>1</sub>=0  a<sub>n</sub>=a<sub>n-1</sub>+(-1)<sup>n</sup>&sdot;2
    - explicit：a<sub>n</sub>=`1+(-1)<sup>n</sup>
19. 
    - recursive：a<sub>1</sub>=1  a<sub>n</sub>=a<sub>n-1</sub>+3
    - explicit：a<sub>n</sub>=-1+3n
20. 
    - recursive：a<sub>1</sub>=1  a<sub>n</sub>=a<sub>n-1</sub>/2
    - explicit：a<sub>n</sub>=1/2<sup>n-1</sup>
21. a<sub>n</sub> = -1 + 3n
22. a<sub>1</sub> = 2   a<sub>n</sub> = a<sub>n-1</sub> + a<sub>n-2</sub>
23. A：uncountable B：finite C：countable D：finite E：finite
24. A：uncountable B：finite C：countable D：uncountable E：uncountable
25. TFTTFF
26. 
    1. {analysis, topology, calculus, algebra, trigonometry}
    2. {algebra, calculus}
    3. {calculus}
    4. {arithmetic, algebra, calculus, geometry, trigonometry, analysis, statistics}
    5. {geometry, topology}
27. 
    1. 1
    2. 0
    3. f<sub>B</sub>=1,0,0,0,0,0,0,0  f<sub>C</sub>=0,1,0,1,0,0,1,1 f<sub>D</sub>=0,1,0,0,0,1,0,1
    4. f<sub>B&cup;C</sub>=1,1,0,1,0,0,1,1 f<sub>C&cup;D</sub>=0,1,0,1,0,1,1,1 f<sub>C&cap;D</sub>=0,1,0,0,0,0,0,1
28. 1 0 0 1 0 1 0 1 A&cap;B 0
29. 证明过程如下：
    - f<sub>(A&oplus;B)&oplus;C</sub>
    - = f<sub>A&oplus;B</sub>+f<sub>C</sub>-2f<sub>A&oplus;B</sub>f<sub>C</sub>
    - = f<sub>A</sub>+f<sub>B</sub>-2f<sub>A</sub>f<sub>B</sub>+f<sub>C</sub>-2(f<sub>A</sub>+f<sub>B</sub>-2f<sub>A</sub>f<sub>B</sub>)+f<sub>C</sub>
    - = f<sub>A</sub>+f<sub>B</sub>+f<sub>C</sub>-2f<sub>A</sub>f<sub>B</sub>-2f<sub>A</sub>f<sub>C</sub>-2f<sub>B</sub>f<sub>C</sub>+4f<sub>A</sub>f<sub>B</sub>f<sub>C</sub>
    = f<sub>A</sub>+f<sub>B&oplus;C</sub>-2f<sub>A</sub>(f<sub>B</sub>+f<sub>C</sub>-2f<sub>B</sub>f<sub>C</sub>)
    = f<sub>A</sub>+f<sub>B&oplus;C</sub>-2f<sub>A</sub>f<sub>B&oplus;C</sub>
    = f<sub>A&oplus;(B&oplus;C)</sub>
30. 
    1. 
        - a, +, &times; and b are regular expressions.
        - ab, b&or;aare regular.
        - (ab)<sup>\*</sup>, a&times;b&or;a are regular.
        - a+b(ab)<sup>\*</sup>(a&times;b&or;a) is regular.
    2. 
        - a, +, &times; and b are regular expressions.
        - a<sup>\*</sup> is regular.
        - a<sup>\*</sup>&or;b is regular.
        - a+b&times;(a<sup>\*</sup>&or;b) is regular.
    3. 
        - a, +, &times; and b are regular expressions.
        - a<sup>\*</sup>, b<sup>\*</sup> are regular.
        - a<sup>\*</sup>b, &times;b<sup>\*</sup> are regular.
        - a<sup>\*</sup>b&or;+ is regular.
        - (a<sup>\*</sup>b&or;+)<sup>\*</sup> is regular.
        - (a<sup>\*</sup>b&or;+)<sup>\*</sup>&or;&times;b<sup>\*</sup> is regular.
31. Yes Yes Yes
32. No No Yes
33. ba ca cba（答案不唯一）
34. {pr, prq, prqq, ..., qr, qrq, qrqq, ...} {pr, pqqr, pqqqqr, ...}
35. 01<sup>\*</sup>0 0((00)<sup>\*</sup>&or;(01))
36. {0, 3, 6, 9, ...}
37. {..., 1/16, 1/8, 1/4, 1/2, 1, 2, 4, 8, 16, ...}
38. 0, 1, 1, 3, 5, 11
39. 1, 2, 3, 7, 16, 65

### 1.4 Exercises

1. 20 = 6(3) + 2
2. 64 = 1(37) + 27
3. 3 = 0(22) + 3
4. 48 = 4(12) + 0
5. 
    1. 2&sup2; &sdot; 3&sup2; &sdot; 23
    2. 2 &sdot; 7&sup2; &sdot; 17
    3. 13 &sdot; 137
    4. 3&sup2; &sdot; 5&sup3;
    5. 107
6. GCD(60, 100) = 20 = 2(60) - 1(100)
7. GCD(45, 33) = 3 = 3(45) - 2(33)
8. GCD(34, 58) = 2 = 12(34) - 7(58)
9. GCD(77, 128) = 1 = 5(77) - 3(128)
10. 216
11. 1050
12. 1225
13. 864
14. 3 6 3 4 2 1
15. 6 1 0 1 20 14
16. 5 5 6 6
17. 10 22 2 14
18. k&sdot;f(a) mod n = f(k&sdot;a)
19. 
    - f(a+b)&lt;n
    - f(a)&lt;n f(b)&lt;n f(a)+f(b)&lt;2n
20. a mod n + b mod n &lt; n
21. {2, 7, 12, 17, ...} {4, 9, 14, 19, ...}
22. {3, 9, 15, 21, ...} {1, 7, 13, 19, ...}
23. 略
24. 略
25. 
    - The only divisors of p are &plusmn;p and &plusmn;1
    - p | sab and p | tpb
26. 略
27. 略
28. 略
29. 略
30. 略
31. 略
32. 略
33. 略
34. 略
35. 略
36. 略
37. 略
38. 563 337 153
39. 
    1. 112
    2. 10
    3. 30
40. 
    1. 788
    2. 870
41. 
    1. (104)<sub>5</sub> (243)<sub>5</sub> (1330)<sub>5</sub> (10412)<sub>5</sub>
    2. 49 85 197 816
42. 
    1. (41)<sub>7</sub> (133)<sub>7</sub> (425)<sub>7</sub> (2064)<sub>7</sub>
    2. 51 92 238 647
43. 
    1. (11101)<sub>2</sub> (1001001)<sub>2</sub> (11010111)<sub>2</sub> (1011011100)<sub>2</sub>
    2. (131)<sub>4</sub> (1021)<sub>4</sub> (3113)<sub>4</sub> (23130)<sub>4</sub>
    3. (1D)<sub>16</sub> (49)<sub>16</sub> (D7)<sub>8</sub> (2DC)<sub>16</sub>
44. 
    1. 16 = 4<sup>2</sup> = 2<sup>4</sup>
    2. 
        1. 每两位 2 进制位得到一位 4 进制位。
        2. 每一位 16 进制位得到四位 2 进制位。
        3. 每两位 4 进制位得到一位 16 进制位。
45. 
    1. AAA*A*AA*AAA*AA*AA*AAAA*A*AAAAAA*A*AAAAAAAA*A*AA*A*A*A*A（答案不唯一）
    2. STUDY WELL
46. 
    1. 大写或小写英文字母有 26 个，26 可以转换为 5 位二进制数。
    2. 略
47. BIJS
48. 
    - 10011 00111 00100 00100 00000 10001 10011 00111 01000 10010 10001 01110 10100 01101 00011
    - THE EARTH IS ROUND

### l.5 Exercises


