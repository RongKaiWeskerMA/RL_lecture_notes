# Mote Carlo Learning

## Incremental Mean
- The mean $\mu_1, \mu_2,\ldots,$ of a sequence $x_1, x_2$, ... can be computed incrementally

- Update $V(s)$ incrementally after episode $S_1,  A_1, R_2,\ldots, S_T$
- For each state $S_t$ with return $G_t$

$$
N(S_t) \leftarrow N(S_t) + 1 \\
V(S_t) \leftarrow V(S_t) + \frac{1}{N(S_t)}(G_t - V(S_t))
$$


- In non-stationary problems, it can be useful to track a running mean, i.e.,, forget old episodes

$$
V(S_t) \leftarrow V(S_t) + \alpha(G_t - V(S_t))
$$

# Temporal Difference Learning

- TD methods learn directly from episodes of experience
- TD is model-free no knowledge of MPD transitions / rewards
- TD learn from incomplete episodes by bootstrapping
- TD updates a guess towards the goal

- Goal: learn $v_\pi$ online from experience under policy $\pi$
- Simplest difference learning algorithm TD(0)

$$
V(S_t) \leftarrow V(S_t) + \alpha (R_{t+1} + \gamma V(S_{t+1})-V(S_t))
$$
where $R_{t+1} + \gamma V(S_{t+1})$ is the TD target.


- Monte Carlo is an unbiased estimate of $V(S_t)$
- True TD target is also an unbiased estimate of $V(S_t)$
- TD target $R_{t+1} + \gamma V(S_{t+1})$ is a biased estimates of $V_{\pi}(S_t)$
but is lower variance.



# TD($\lambda$)





