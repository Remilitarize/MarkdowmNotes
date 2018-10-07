[toc]

**TCP congestion control algorithm TCP 拥塞控制算法**

- Additive-increase, multiplicative-decrease 加性增乘性减
- Slow start 慢启动
- Reaction to timeout events 对超时事件做出反应

## Additive-increase, multiplicative-decrease 加性增乘性减

For the sender to reduce its sending rate when a loss event occurs.
当出现丢包事件时，让发送方降低其发送速率。

- Multiplicative-decrease 乘性减
	- Halving the current value of congestion window after a loss enent.
	  每发生一次丢包事件就将当前的拥塞窗口值减半。
	- It is not allowed to drop below 1 MSS. 不能降到低于 1 个 MSS。
- Additive-increase 加性增
	- Increasing congesion window by 1 MSS every round-trip time.
	  每个往返时延内拥塞窗口增加一个 MSS。
- A TCP sender additively increases its rate when it perceives that the end-end path is congestion-free, and multiplicatively decreases its rate when it detects that the path is congested.
  当 TCP 发送方感受到端到端路径无拥塞时就加性地增加其发送速率，当察觉到路径拥塞时就乘性地减小其发送速率。

TCP congestion control is often referred to as an **additive-increase, multiplicative-decrease(AIMD) algorithm**.
TCP 拥塞控制算法常被称为 **加性增、乘性减算法**。
The linear icrease phase of TCP's congestion-control protocol is known as **congestion avoidance**.
TCP 拥塞控制协议的线性增长阶段被称为 **避免拥塞**。

## Slow start 慢启动

- When a TCP connection begins, the value of congestion window is typically initialized to 1 MSS.
  当一个 TCP 连接开始时，拥塞窗口的值初始置为 1 个 MSS。
- During this initial phase, which is called **slow start(SS)**, the TCP sender begins by transmiting at a slow rate but increases its sending rate **exponentially**.
  在这个被称为 **慢启动** 的初始化阶段期间，TCP 发送方以慢速率发送，但是以 **指数** 的速度快速增加其发送速率。

![Slow Start](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/SlowStart.png)

## Reaction to timeout events 对超时事件做出反应

- After a **triple duplicate ACK**, TCP behaves as we have just described —— the **congestion window is cut in half** and then **increases linearly**.
  收到 **3 个冗余 ACK** 后，TCP 的行为和我们刚描述的一样，将 **拥塞窗口减小一半**，然后 **线性地增长**。
- After a **timeout event**, a TCP sender enters a **slow-start phase** —— that is, it sets the congestion window to 1 MSS and then grows the window exponentially.
  **超时事件** 发生时，TCP 发送方进入一个 **慢启动阶段**，即它将拥塞窗口设置为 1 MSS，然后窗口长度以指数速度增长。
  The window continues to grow exponentially until congestion window **reaches one half of the value it had before the timeout event**.
	拥塞窗口持续以指数速率增长，直到 **达到超时事件前窗口值的一半** 为止。
  At that point, congestion window grows **linearly**. 此后，拥塞窗口以 **线性速率** 增长。
- Whenever a loss event occurs, the value of **Threshold** is set to **one half of the current value of congestion window**.
  每当发生一个丢包事件时，**阈值** 就会被设置为 **当前拥塞窗口值的一半**。

![TCP Congestion Window](http://oxnec2zdn.bkt.clouddn.com/Computer-networking/TCPCongestionWindow.png)
