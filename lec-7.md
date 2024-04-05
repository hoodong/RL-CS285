# Lecture 7. Value Function Methods

## 질문
- p6: policy iteration  
  step 1.정책 평가:
  $V_\pi(s)\leftarrow r(s,\pi(s))+\gamma E\left[V_\pi(s')\right], \quad s'\sim p(s'|s,\pi(s))$$  
  step 2.정책 개선:
  $\pi\leftarrow$ greedy policy for $A^\pi(s,a)$
- p6: Sutton 교재(4.3절)에서는 Q(s,a) 대신 V(s)를 사용했음  
  - 환경의 dynamic을 알면 V(s)에서 Q(s,a)를 계산할 수 있으므로
  
- p7: value iteration  
  1.행동가치 업데이트  
  $\quad Q(s,a)\leftarrow r(s,a)+\gamma E[V(s')]$  
  2.상태가치 업데이트  
  $\quad V(s)\leftarrow \arg_a Q(s,a)$  


