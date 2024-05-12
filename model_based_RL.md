# Model Learning 

- Goal: estimate model $\mathcal{M}_{\eta}$ from experience $\{S_1, A_1, R_2,\ldots, S_t\}$

- This is a supervised learning problem 


$$
S_1,A_1 \rightarrow R_2, S_2\\
S_2,A_2 \rightarrow R_3, S_3\\
S_{T-1}, A_{T-1} \rightarrow R_T,S_T
$$

- Am model $\mathcal{M}$ is a representation of an MDP $<S,A,P,R>$ parameterized by $\eta$


## Sample-Based Planning

- A simple but powerful approach to planning

- Use the model only to generate samples 

- Sample experience from model 


## Integrated Architectures




