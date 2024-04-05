# Lecture 7. Value Function Methods

## 질문
- p6: policy iteration  
  1.
  $V_\pi(s)\leftarrow r(s,\pi(s))+\gamma E\left[V_\pi(s')\right], \quad s'\sim p(s'|s,\pi(s))$  
  2.
  $\pi\leftarrow \pi'$
  $\pi'(a_t|s_t)=1 if a_t=\argmax_{a_t} A^\pi(s_t,a_t), otherwise \pi'(a_t|s_t)=0$
- p7: value iteration
  $$


