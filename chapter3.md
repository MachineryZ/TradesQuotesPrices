# Limit order Book

An order is a commitment, declared at a given submission time, to buy or sell a given volume of an asset at no worse than a given price. An order x is thus described by four attributes. We succinct notation
$x = (\epsilon_x, p_x, v_x, t_x)$, $\epsilon$ is sign prefered buy or sell, price p, volume v, time t

1. market orders: orders that match upon arrival
2. limit orders: orders that do not match upon arrival
3. limit order book: simply a collection of revealed, unsatisfied intentions to buy or sell an asset at a given time

bid-price, ask-price, mid-price and spread
1. bid-price: the highest stated price among buy limit orders at time t
2. ask-price: the lowest stated price among sell limit orders at time t
3. mid-price: mean of bid-price and ask-price
4. bid-ask spread: the difference between ask-price and bid-price

lot size and tick size. When submitting an order x, a trader must choose the size $v_x$ and price $p_x$ according to the relevant lot size and tick size of the given lob
1. lot size $v_0$ is the smallest amount of the asset that can be traded within the given lob $v_x\in kv_0$
2. tick size $\theta$ is the smallest permissible price interval between different orders within a given lob. All orders must arrive with a price that is a multiple of $\theta$

Most studies of LOBs perform this aggregation in same-side quate-relative coordinates, in which prices are measured relative to the same-side best quote. Specifically, the same-side quate relative price of an order x at time t is

1. $d(p_x, t) = b(t) - p_x$ if x is a buy limit order
2. $d(p_x, t) = p_x - a(t)$ if x is a sell limit order

on contrary, opposite-site quote relative coordinates

1. $d(p_x, t) = a(t) - p_x$ if x is a buy limit order
2. $d(p_x, t) = p_x - b(t)$ if x is a sell limit order


Volume Profile
1. Buy Side Volume at price p and time t $V_+(p, t) = \sigma_{x\in B(t)|p_x=p} v_x$


Price Change in an LOB. In an LOB, the rules that govern matching dictate how prices evolve through time. Consider a buy(or sell) order x that arrives at time t
1. if $p_x \leq b(t)$ (respectively, $p_x \geq a(t)$), then x is a limit order, it does not cause b(t) or a(t) to change
2. if $b(t) < p_x < a(t)$ then x is also a limit order

1. bid4: 1.47, 3
2. bid3: 1.48, 3
3. bid2: 1.48, 1
4. bid1: 1.50, 2
5. ask1: 1.53, -2
6. ask2: 1.54, -3
7. ask3: 1.55, -1
<table>
    <tr>
        <td> Arriving Order </td>
        <td> Values before arrival </td>
        <td> Values after arrival </td>
    </tr>
    <tr>
        <td> (+1, 1.48, 3, t)</td>
        <td> (b=1.5, a=1.53, m=1.515, s=0.03)</td>
        <td> (b=1.5, a=1.53, m=1.515, s=0.03 )</td>
    </tr>
        <tr>
        <td> (+1, 1.51, 3, t)</td>
        <td> (b=1.5, a=1.53, m=1.515, s=0.03)</td>
        <td> (b=1.51, a=1.53, m=1.52, s=0.02 )</td>
    </tr>    <tr>
        <td> (+1, 1.55, 3, t)</td>
        <td> (b=1.5, a=1.53, m=1.515, s=0.03)</td>
        <td> (b=1.50, a=1.54, m=1.52, s=0.04 )</td>
    </tr>    <tr>
        <td> (+1, 1.55, 3, t)</td>
        <td> (b=1.5, a=1.53, m=1.515, s=0.03)</td>
        <td> (b=1.50, a=1.52, m=1.525, s=0.05 )</td>
    </tr>    <tr>
        <td> (-1, 1.54, 4, t)</td>
        <td> (b=1.5, a=1.53, m=1.515, s=0.03)</td>
        <td> (b=1.50, a=1.53, m=1.515, s=0.03 )</td>
    </tr>    <tr>
        <td> (+1, 1.48, 3, t)</td>
        <td> (b=1.5, a=1.53, m=1.515, s=0.03)</td>
        <td> (b=1.50, a=1.52, m=1.51, s=0.02 )</td>
    </tr>    <tr>
        <td> (+1, 1.48, 3, t)</td>
        <td> (b=1.5, a=1.53, m=1.515, s=0.03)</td>
        <td> (b=1.48, a=1.53, m=1.505, s=0.05 )</td>
    </tr>    <tr>
        <td> (+1, 1.48, 3, t)</td>
        <td> (b=1.5, a=1.53, m=1.515, s=0.03)</td>
        <td> (b=1.49, a=1.50, m=1.495, s=0.01 )</td>
    </tr>
</table>

Priority Rules
LOBs also employ a priority system for limit orders within each individual price level:
1. Most common rule currently is price-time priority:
    1. For buy(respectively, sell) limit orders, priority is given to the limit orders with the highest(respectively, lowest) price, and ties are broken by selecting the limit order with the earliest submission time t
2. Another priority mechanism, commonly used in short-rate futures markets, is pro-rata priority
    1. Under this mechanism, when a tie occurs at agiven price, each relevant limit order receives a share of the matching equal to its fraction of the available volume at that price

Order Types:
1. Stop Orders
    1. 就是，达到某一价格时，立刻下单的 order 形式
2. Iceberg Orders
    1. 隐藏大 volume 订单的方式
    2. only a fraction of the order size, called peak volume
    3. hidden part has lower time priority; regular limit orders ath the same price that are submitted later will be executed first
3. Immediate-or-cancel orders
    1. 下单之后，不被 executed 之前，不会在 lob 上有痕迹
4. Market-on-close orders:

Opening and Closing Auctions
1. 也就是开盘的集合竞价和收盘的集合竞价的过程
2. For example, the LSE’s flagship order book SETS has three distinct trading phases in each trading day
    1. Opening auction between 07:50 ~ 08:00
    2. Continuous trading period between 08:00 ~ 16:30
    3. Closing auction between 16:30 ~ 16:35


