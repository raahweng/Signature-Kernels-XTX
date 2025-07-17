# Signature-Kernels-XTX

Let $P_X$ be a set of paths in a topological space $X$. We define the truncated Signature Kernel up to depth $d$ $k_d^{\oplus}: P_X \times P_X \rightarrow \mathbb{R}$:
$$k_d^{\oplus}(x,y) = \langle S(k_x), S(k_y) \rangle = \sum_{m = 0}^{d}{\int_{s_1 < ... < s_m, t_1<...<t_m} {\prod^m_{i=1}{d \kappa(s_i, t_i)}} }$$

where:
$$\kappa([s,t] \times [u,v]) = k(x(t), y(v)) - k(x(s),y(v)) - k(x(t),y(u)) + k(x(s),y(u))$$

Intuitively, the Signature Kernel computes the pairwise similarity of a collection of paths in signature transform space.

We hence propose an efficient, compact, feature engineering method that leverages the properties of the signature transform in an efficient, scalable method that generalises the notion of autocorrelation for higher-dimensional paths.

In our LOB context, at some time $t$, consider the full $60$-dimensional path of length $L$, $x_L(t)$, from times $[t-L, t]$. We may also consider the time-lagged path of length 87, $x_L(t-k)$, from times $[t-k-L, t-k]$.

We simply consider the similarity of these paths using the aforementioned inner product, i.e. $k_d^{\oplus}(x(t),x(t-k))$, corresponding to the the Kernel entries $K_{12} = K_{21}$.

For increasing $k$, we capture the "autocorrelation" on longer timespans, and hence our similarity decreases. By using an ensemble of $k$ s, we can capture short and long-term volatility. 
