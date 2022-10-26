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


