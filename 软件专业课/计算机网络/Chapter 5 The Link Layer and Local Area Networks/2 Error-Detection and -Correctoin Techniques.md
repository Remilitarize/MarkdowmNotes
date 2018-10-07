[toc]

## Parity Checks 奇偶校验

0111000110101011 | 1

Suppose that the information above to be sent has d bits. 假设上面要发送的信息有 d 个比特。

- In an **even parity scheme**, the sender simply includes one additional bit and choose its value such that **the total number** of 1s in the d+1 bits is **even**.
  在 **偶校验方案** 中，发送方只需包含一个附加的比特，选择它的值，使得这 d+1 个比特中 **1 的总数** 是 **偶数**。
- For **odd parity schemes**, the parity bit value is chosen such that there is an **odd number of 1s**.
  对于 **奇校验方案**，选择校验比特值使得有 **奇数个 1**。

The receiver need only count the number of 1s in the received d+1 bits.
接收方只需要数一数接收的 d+1 比特中 1 的数目即可。

- If an odd number of 1-valued bits are found with an even parity scheme, the receiver knows that at least one bit errors have occurred.
  如果在采用了偶校验方案中发现了奇数个值为 1 的比特，接收方知道了至少出现了一个比特差错。
- More precisely, it knows that some odd number of bit errors have occurred.
  更精确的说法是，出现了奇数个比特差错。

![Two-dimensional parity](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/TwoDimensionalParity.png)

With this **two-dimensional parity** scheme, the parity of both the column and the row containing the flipped bit will be in error.
使用这种 **二维奇偶校验** 方案，包含比特值改变的列和行的校验值都将会出现差错。

The ability of the receiver to both detect and correct errors is known as **forward error correction(FEC)**.
接收方检测和纠正差错的能力被称为 **前向纠错**。

## Checksumming Methods 检验和方法

Simply sum these k-bit integers and use the resulting sum as the error-detection bits.
将这 k 比特整数加起来，并且用得到的和作为差错检测比特。

The receiver checks the checksum by taking the 1s complement of the sum of the received data and checking whether the result is all 1 bits.
接收方通过对接收的数据的和取反码，并且检测其结构是否为全 1 比特来检侧检验和。

If any of the bits are 0, an error is indicated. 如果这些比特中有任何比特是 0，就可以指示出差错。

## Cyclic Redundancy Check(CRC) 循环冗余检测

An error-detection technique used widely in today's computer networks is based on **cyclic redundancy check(CRC) codes**.
现今的计算机网络中广泛应用的差错检测技术是基于 **循环冗余检测编码**。
CRC codes are also known as **polynomial codes**. CRC 编码也称为 **多项式编码**。

CRC codes operate as follows: CRC 编码操作如下：

- Consider the d-bit piece of data, D, that the sending node wants to send to the receiving node.
  考虑 d 比特的数据 D，发送节点要将它发送给接收节点。
- The sender and receiver must first agree on an r+1 bit pattern, known as a **generator**, which we will denote as G.
  发送方和接收方首先必须协商一个 r+1 比特模式，称为 **生成多项式**，我们将其表示为 G。
- We will require that the most significant(leftmost) bit of G be a 1.
  我们将要求 G 的最高有效位（最左边）的比特是 1.
- **For a given piece of data, D, the sender will choose r additional bits, R, and append them to D such that the resulting d+r bit pattern(interpreted as a binary number) is exactly divisible by G using modulo-2 arithmetic.**
  **对于一个给定的数据段 D，发送方要选择 r 的附加比特 R，并将它们附加到 D 上，使得得到的 d+r 比特模式（被解释为一个二进制数）用模 2 算术恰好能被 G 整除。**
- The receiver divides the d+r received bits by G. 接收方用 G 去除接收到的 d+r 比特。
	- If the remainder is nonzero, the receiver knows that an error has occurred. 如果余数为非零，接收方知道了出现差错。
	- Otherwise the data is accepted as being correct. 否则认为数据正确而被接受。

Find R such that there is an n such that **D &sdot; 2<sup>r</sup> XOR R = nG**.
求出 R 使得对于 n 有：**D &sdot; 2<sup>r</sup> XOR R = nG**。

We can calculate R as **R = D &sdot; 2<sup>r</sup> XOR G**.
我们可以这样计算 R：**R = D &sdot; 2<sup>r</sup> XOR G**。

![CRC](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/CRC.png)
