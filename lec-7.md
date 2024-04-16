# Lecture 7. Value Function Methods

- $V(s)$와 $Q(s,a)$의 관계 (lec-6, p6)
  - $V(s) = E_a[Q(s,a)],\quad a\sim \pi(a|s)$
  - $Q(s,a) = r(s,a) + \gamma E_{s'}[V(s')],\quad s'\sim p(s'|s,a)$
- p6: policy iteration  
  - 정책 평가:
  $V_\pi(s)\leftarrow r(s,\pi(s))+\gamma E\left[V_\pi(s')\right], \quad s'\sim p(s'|s,\pi(s))$   
  - 정책 개선:
  $\pi\leftarrow$ greedy policy for $A^\pi(s,a)=Q^\pi(s,a)-V^\pi(s)$
  - p6: Sutton 교재(4.3절)에서는 $Q(s,a)$ 대신 $V(s)$를 사용했음  
    - 환경의 dynamic을 알면 $V(s)$에서 $Q(s,a)$를 계산할 수 있으므로 
- p7: value iteration
  - $V(s) = \max_{a}Q(s,a)$ (Bellman optimality equation)
  - $Q(s,a)=r(s,a)+\gamma E[V(s')]$
  - 위 두식을 합치면
    - $V(s)\leftarrow \max_{a} \left( r(s,a)+\gamma E[V(s')] \right),\quad s'\sim p(s'|s,a)$    
    - $p(s'|s,a)$를 알면 $E[V(s')]$ 계산 가능
    - $p(s'|s,a)$를 모르면? Q-iteration
- p11: Q-iteration
  - value iteration에서 $E[V(s')]$을 $\max_{a'} Q(s',a')$로 근사하면   
  - $Q(s,a)\leftarrow r(s,a)+\gamma\max\limits_{a'} Q(s',a')$
  - value iteration에서는 data가 $(s,a,r)$, Q-iteration에서는 data가 $(s,a,s',r)$
- p15: Q-iteraion이 off-policy인 이유는?
- p18: Q-learning에서 exploration을 하는 이유는?
- p18: eplilon-greedy와 Boltzmann exploration의 의미는?
- value iteration은 contraction 연산이므로 수렴이 보장됨 (Tabular case)
- Tabular case가 아닌 경우 수렴이 보장되지 않음
  


