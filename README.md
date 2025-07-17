# Background

Let $P_X$ be a set of paths in a topological space $X$. We define the truncated Signature Kernel up to depth $d$ $k_d^{\oplus}: P_X \times P_X \rightarrow \mathbb{R}$:
$$k_d^{\oplus}(x,y) = \langle S(k_x), S(k_y) \rangle = \sum_{m = 0}^{d}{\int_{s_1 < ... < s_m, t_1<...<t_m} {\prod^m_{i=1}{d \kappa(s_i, t_i)}} }$$

where:
$$\kappa([s,t] \times [u,v]) = k(x(t), y(v)) - k(x(s),y(v)) - k(x(t),y(u)) + k(x(s),y(u))$$

Intuitively, the Signature Kernel computes the pairwise similarity of a collection of paths in signature transform space.

We hence propose an efficient, compact, feature engineering method that leverages the properties of the signature transform in an efficient, scalable method that generalises the notion of autocorrelation for higher-dimensional paths.

In our LOB context, at some time $t$, consider the full $60$-dimensional path of length $L$, $x_L(t)$, from times $[t-L, t]$. We may also consider the time-lagged path of length 87, $x_L(t-k)$, from times $[t-k-L, t-k]$.

We simply consider the similarity of these paths using the aforementioned inner product, i.e. $k_d^{\oplus}(x(t),x(t-k))$, corresponding to the the Kernel entries $K_{12} = K_{21}$.

For increasing $k$, we capture the "autocorrelation" on longer timespans, and hence our similarity decreases. By using an ensemble of $k$ s, we can capture short and long-term volatility. 

# Conclusions

We tested a variety of feature engineering and Machine Learning methods to improve long-term predictive performance on LOB data. We found the most success using a blend of two groups of LightGBM models; one augmented by signature kernels, and the other trained on signature transforms. The most important development was the "autocorrelation"-like statistic derived from Signature Kernels - we demonstrated in our previous submission that it demonstrably boosts the performance of a control LightGBM model by a significant degree.

We hypothesise that this statistic captures temporal fluctuations and nonlinear interactions within the data in a compact manner for use in our models. This makes it a preferable choice over the high-dimensional and computationally expensive signature transform, which we had to truncate earlier due to computational bottlenecks. Furthermore, our proposed statistic acts as a effective measure of "autocorrelation" for high-dimensional rough paths, and is low-dimensional enough to be fit alongside other data.

However, it is important to contextualise signature-based methods in both the ML pipeline and data setting. Our results suggest that their utility is maximized when placed alongisde and even composed with traditional financial features. By incorporating windowing in kernels and blending lagged models, we were overall able to capture the multiscale time dynamics to a high degree.

We also explored a variety of blending and stacking methods to effectively minimize overfitting and create a more robust and powerful model.

Overall, our findings highlight the power of signature kernels in feature engineering. Future work could further explore computing statistics of larger kernels, using familes of lagged time series, and refining windowing strategies.
