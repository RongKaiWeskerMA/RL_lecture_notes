# Introduction

* Represent value functoin by a lookup table
    - Every state s has an entry $V(s)$ 
    - Or every state-action pair $s,a$ has an entry $Q(s,a)$


* Function approximation
    - $\hat{v}(s, w) \approx v_\pi(s)$ or
    - $\hat{q}(s,a,w) \approx q_\pi(s, a) $

* Differential function approximators
    - Linear comninations of feautres
    - Neural netowrk
    - Decision tree
    - Nearest neighbors
    - Fourier wavelet

- Incremental Methods
    - For TD(0), the target is the TD target $R_{t+1} + \gamma\hat{v}(S_{t+1},w)$ 

    $\Delta w = \alpha(R_{t+1} +  v(S_{t+1},w) - v(S_{t},w))\nabla_wv(S_t,w)$

# Policy-Based Reinforcement Learning

- Directly parameterize the policy 

    $\pi_{\theta}(s,a)=\mathbb{P}[a|s,\theta]$

- focus on model-free reinforcement learning.

- Value Based
    - Learnt Value Function
    - Implicit policy

- Policy Based
    - No value Function
    - Learnt Policy

- Actor-Critic
    - Learnt Value Function
    - Learnt Policy



## Policy Objective Functions

- In episodic environments we can use the *start value*

    $J_1(\theta) = V^{\pi_\theta}(s_1) = \mathbb{E}_{\pi_\theta}[v_1]$

- In continuous environments we can use the average value:

    $J_{avV}(\theta) = \sum_sd^{\pi_\theta}(s) V^{\pi_\theta}(s)$


# Policy Gradient 

## Computing Gradients By Finite Differences

- Score Function 

- Softmax Policy

    - We will use a softmax policy as a running example

    - Weights actions using linear combination of features $\phi(s, a)^\top\theta$

    - Probablity of action is propotional to exponentiated weight:

        $\pi_{\theta}(s,a)\propto \exp^{\phi(s,a)^\top\theta}$

    - The score function is:
    
    $$
    \begin{equation}

        \nabla_{\theta}\log\pi_\theta(s,a) = \phi(s,a) - \mathbb{E}_{\pi_\theta}[\phi(s,.)]
    \end{equation}
    $$


    ## Action-Value Actor-Critic

    - Simple actor-crtic algorithm based on action-value critic
    - Using linear value function approximator: $Q_w(s,a) = \phi(s,a)^\top w$

        - Critic Update w by linear TD(0)

        - Actor Update $\theta$ by policy gradient



## Reducing Variance Using a Baseline



- We subtract a baseline function $B(s)$ from the policy gradient 
- This can reduce variance, without changing expectation

$$
\begin{align*}
\mathbb{E}[\nabla\log_{\pi_\theta}(s,a)B(s)] = \sum_{s\in S}d^{\pi_{\theta}}(s)\sum_a\nabla_\theta\pi_\theta(s,a)B(s) \\
= \sum_{s\in S}d^\pi_\theta B(s) \nabla_\theta\sum_{a\in A}\pi_\theta(s,a)
\\
=0
\end{align*}
$$


- A good baseline is the state value function $B(s) = V^{\pi_\theta}(s)$
-So we can rewrite the policy gradient using the advantage function $A^{\pi_\theta}(s,a)$

$$
A^{\pi_\theta}(s,a) = Q^{\pi_\theta}(s,a) - V^{\pi_\theta}(s)
$$




