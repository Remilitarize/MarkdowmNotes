[toc]

## Vector space

**向量空间** 是一些对象的集合，称为 **向量**。
允许有两个操作：

- 与向量相加。
- 与标量相乘。

8 种性质：

- 交换律：u + v = v + u
- 结合律：(u + v) + w = u + (v + w)
- **零向量**：&forall; v &in; V，v + 0 = v。
- **反向量**：&forall; v &in; V，&exists; w &in; V，v + w = 0。
    - 即 w = -v。
- 乘法单元：&forall; v &in; V，1v = v。
- 乘法结合律：&forall; v &in; V，&forall; &alpha;, &beta;，(&alpha;&beta;)v = &alpha;(&beta;v)。
- &forall; v, w &in; V，&forall; &alpha;，&alpha;(v + w) = &alpha;v + &alpha;w。
- &forall; v &in; V，&forall; &alpha;, &beta;，(&alpha; + &beta;)v = &alpha;v + &beta;v。

>  0 向量是唯一的，反向量也是唯一的。

若标量是普通的实数，我们称该向量空间为 **实向量空间**。
若标量是复数，我们称该向量空间为 **复向量空间**。

> 任何复数向量空间也是实数向量空间，反过来则不是。

一个 m&times;n 的 **矩阵** 是一个 **m 行 n 列** 的矩形数列。
数列中的元素称为矩阵的 **元**。

- A<sub>i,j</sub> 表示一个 i 行 j 列的矩阵 A。
- a<sub>i,j</sub> 表示位于第 i 行第 j 列的元 a。

一个矩阵 A 的 **转置** A<sup>T</sup> 是将矩阵 A 中的行转换成列。
A<sup>T</sup> 的列是 A 的行，反之亦然。

> 在写一列向量时可以书写其转置形式节省空间。

## Linear combinations, bases

若存在向量系 v<sub>1</sub>、v<sub>2</sub>、...、v<sub>n</sub> &in; V，&forall; v &in; V 满足
v = &alpha;<sub>1</sub>v<sub>1</sub> + &alpha;<sub>2</sub>v<sub>2</sub> + ... + &alpha;<sub>n</sub>v<sub>n</sub> = &Sigma;<sub>k=1</sub><sup>n</sup> &alpha;<sub>k</sub>v<sub>k</sub>
且唯一，则称 v<sub>1</sub>、v<sub>2</sub>、...、v<sub>n</sub> 为 **基**。
其中系数 &alpha;<sub>1</sub>、&alpha;<sub>2</sub>、...、&alpha;<sub>n</sub> 称为向量 v 的 **坐标**。

考虑向量

- e<sub>1</sub> = (1, 0, 0, ..., 0)<sup>T</sup>
- e<sub>2</sub> = (0, 1, 0, ..., 0)<sup>T</sup>
- e<sub>3</sub> = (0, 0, 1, ..., 0)<sup>T</sup>
- ...
- e<sub>n</sub> = (0, 0, 0, ..., 1)<sup>T</sup>，
- 其中 e<sub>k</sub> 中除第 k 元为 1 外，其他所有元均为 0。

显然，e<sub>1</sub>、e<sub>2</sub>、...、e<sub>n</sub> 是 R 的一个基。
（&forall; v = (x<sub>1</sub>, x<sub>2</sub>, ..., x<sub>n</sub>)<sup>T</sup> &in; R，均有
v = x<sub>1</sub>v<sub>1</sub> + x<sub>2</sub>v<sub>2</sub> + ... + x<sub>n</sub>v<sub>n</sub> = &Sigma;<sub>k=1</sub><sup>n</sup> x<sub>k</sub>v<sub>k</sub>
且表达式唯一。）
e<sub>1</sub>、e<sub>2</sub>、...、e<sub>n</sub> 在 R 上的一个 **标准基**。

对于任意向量 v，均可以分解为 v = &Sigma;<sub>k=1</sub><sup>n</sup> &alpha;<sub>k</sub>v<sub>k</sub>。
若将系数 &alpha;<sub>k</sub> 写作一个列向量，则可以对系数进行操作。
**如果 v = &Sigma;<sub>k=1</sub><sup>n</sup> &alpha;<sub>k</sub>v<sub>k</sub>，w = &Sigma;<sub>k=1</sub><sup>n</sup> &beta;<sub>k</sub>v<sub>k</sub>，则 v + w = &Sigma;<sub>k=1</sub><sup>n</sup> (&alpha;<sub>k</sub> + &beta;<sub>k</sub>)v<sub>k</sub>。**

若存在向量系 v<sub>1</sub>、v<sub>2</sub>、...、v<sub>n</sub> &in; V，&forall; v &in; V 满足
v = &alpha;<sub>1</sub>v<sub>1</sub> + &alpha;<sub>2</sub>v<sub>2</sub> + ... + &alpha;<sub>n</sub>v<sub>n</sub> = &Sigma;<sub>k=1</sub><sup>n</sup> &alpha;<sub>k</sub>v<sub>k</sub>，
则称 v<sub>1</sub>、v<sub>2</sub>、...、v<sub>n</sub> 为 **生成系**。

> 生成系与基的唯一区别在于基满足表达唯一而生成系并不。
> 向基中添加一些其他向量使得其变为生成系。

线性组合 &alpha;<sub>1</sub>k<sub>1</sub>、&alpha;<sub>2</sub>k<sub>2</sub>、...、&alpha;<sub>p</sub>k<sub>n</sub> 是 **平凡的**，当且仅当 &alpha;<sub>k</sub> = 0 &forall;k。

> 一个平凡线性组合总是等于 0。

向量系 v<sub>1</sub>、v<sub>2</sub>、...、v<sub>n</sub> &in; V 是 **线性无关的** 当且仅当向量的平凡线性组合等于 0。
换句话说，若向量系 v<sub>1</sub>、v<sub>2</sub>、...、v<sub>n</sub> &in; V 是线性无关的当且仅当等式
x<sub>1</sub>v<sub>1</sub> + x<sub>2</sub>v<sub>2</sub> + ... + x<sub>p</sub>v<sub>p</sub> = 0
只有 **平凡解**（零解）x<sub>1</sub> = x<sub>2</sub> = ... = x<sub>p</sub> = 0。

若向量系不是线性无关的，则称为 **线性相关的**。
向量系 v<sub>1</sub>、v<sub>2</sub>、...、v<sub>n</sub> &in; V 是 **线性相关的** 若零向量可以表示为一个 **非平凡线性组合**。
**非平凡线性组合** 指的是至少有一个系数 &alpha;<sub>k</sub> 是非零的，即 &Sigma;<sub>k=1</sub><sup>n</sup> |&alpha;<sub>k</sub>| &ne; 0。

> 这里零向量可以表示为一个非平凡线性组合可以理解为线性组合中某几个向量在系数不为零时同样可以加和得到零向量。

向量系 v<sub>1</sub>、v<sub>2</sub>、...、v<sub>n</sub> &in; V 是 **线性相关的** 当且仅当其中一个向量 v<sub>k</sub> 可以表示成其他向量的线性组合，v<sub>k</sub> = &Sigma;<sub>j=1,j&ne;k</sub><sup>p</sup> &beta;<sub>j</sub>v<sub>j</sub>。

> 这里可以理解为 v<sub>k</sub> 可以继续拆。

向量系 v<sub>1</sub>、v<sub>2</sub>、...、v<sub>n</sub> &in; V 是 **线性无关的** 当且仅当向量系 **线性无关** 且 **生成的**。

**任何（有限）生成系包含一个基。**
也就是说，（有线）生成系包含一个生成线性无关子集。
