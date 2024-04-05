# Lecture 7. Value Function Methods

## 질문
- p6: policy iteration  
  1.정책 평가  
  $V_\pi(s)\leftarrow r(s,\pi(s))+\gamma E\left[V_\pi(s')\right], \quad s'\sim p(s'|s,\pi(s))$  
  2.정책 개선  
  $\pi\leftarrow \pi'$ where $\pi'$ is the greedy policy for the current action value
  
- p7: value iteration
  1.행동가치 업데이트  
  $Q(s,a)\leftarrow r(s,a)+\gamma E[V(s')]$
  2.상태가치 업데이트
  $V(s)\leftarrow \arg_a Q(s,a)$


