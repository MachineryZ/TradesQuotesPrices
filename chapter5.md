# Part 3 Limit order books: Models

In this part, we will start our deep-dive into the mechanisms of price formation at the most microscopic scale. In the coming chapters, we will zoom in - in both space and time - to consider how the interactions between single orders contribute to the price-formation process in an LOB

Single-Queue Dynamics: Simple Models
1. Aggregated order flows are simply assumed to be governed by stochastic processes
2. Models adopt this approach ignore the strategies employed by individual market participants, and instead regard order flow as random. Zero-intelligence modelling
3. 说白了就是，把 order flow 看成一种纯随机的随机过程（认为其他的交易者都是 zero intelligence）

Modelling an order Queue
1. Let V(t) denote the total volume of the orders in the queue at time t. Because we consider only a single order queue, the models studied in this chapter can be used for both the bid-queue and for the ask -queue. Assume that:
    1. all orders are of unit size v0=1
    2. limit orders arrive at the queue as a Poisson process with rate $\lambda$
    3. market orders arrive at the queue as a Poisson process with rate $\mu$
    4. limit orders in the queue are cancelled as a Poisson process with some state-dependent rate (which we will specify in the following sections)
2. 解释：将 bid 和 ask 订单提交认为是一个泊松过程，然后订单取消的概率是一个固定概率的随机时间

The Simplest Model: Constant Cancellation Rate
1. 对于 t 到 t + dt 这段时间，假设 queue length 是 V(t)
    1. 有 $\lambda dt$ 的概率，订单数量会从 V -> V + 1
    2. 有 $(\mu + v) dt$ 的概率（订单被执行或者订单被取消）
2. 在这个模型里，我们认为呢，queue length 就是一个 random walk 的过程，当前泊松过程是 $(\lambda + \mu + v)$ ，当一个 upward move的概率是 $\lambda / (\lambda + \mu + v)$ downward move的概率是 $(\mu + v) / (\lambda + \mu + v)$

