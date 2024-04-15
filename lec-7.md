# Lecture 7. Value Function Methods

- p6: policy iteration  
  1.정책 평가:
  $V_\pi(s)\leftarrow r(s,\pi(s))+\gamma E\left[V_\pi(s')\right], \quad s'\sim p(s'|s,\pi(s))$   
  2.정책 개선:
  $\pi\leftarrow$ greedy policy for $A^\pi(s,a)$  
- p6: Sutton 교재(4.3절)에서는 $Q(s,a)$ 대신 $V(s)$를 사용했음  
  - 환경의 dynamic을 알면 $V(s)$에서 $Q(s,a)$를 계산할 수 있으므로 
- p7: value iteration  
  - Bellman optimality equation을 이용: $V(s) = \max_{a}Q(s,a)$
  - 여기서 $Q(s,a)=r(s,a)+\gamma E[V(s')]$ 이므로  
  - $V(s)\leftarrow \max_{a} \left( r(s,a)+\gamma E[V(s')] \right)$, s'\sim p(s'|s,a), data: $(s,a,r)$  
  - transition dynamics $p(s'|s,a)$을 알면 $E[V(s')]$ 계산이 가능함  
- p11: Q-iteration
  - transition dynamics을 모를 때 $E[V(s')]$을 $\max_{a'} Q(s',a')$로 근사하면   
  - $Q(s,a)\leftarrow r(s,a)+\gamma\max\limits_{a'} Q(s',a')$, data: $(s,a,s',r)$
- p15: Q-iteraion이 off-policy인 이유는?
- p18: Q-learning에서 exploration을 하는 이유는?
- p18: eplilon-greedy와 Boltzmann exploration의 의미는?
- value iteration은 contraction 연산이므로 수렴이 보장됨 (Tabular case)
- Tabular case가 아닌 경우 수렴이 보장되지 않음
  


