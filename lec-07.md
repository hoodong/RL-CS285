# Lecture 7. Value Function Methods

- $V(s)$와 $Q(s,a)$의 관계 (lec-6, p6)
  - $V(s) = E_{a}[Q(s,a)],\quad a\sim \pi(a|s)$
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
  - $Q(s,a)=r(s,a)+\gamma E[V(s')]$ (relation b/w Q and V)
  - 위 두식을 합치면
    - $V(s)\leftarrow \max_{a} \left( r(s,a)+\gamma E[V(s')] \right),\quad s'\sim p(s'|s,a)$    
    - $p(s'|s,a)$를 알면 $E[V(s')]$ 계산 가능
    - $p(s'|s,a)$를 모르면? Q-iteration
- p11: Q-iteration
  - $E[V(s')]\approx \max_{a'} Q(s',a')$
  - $Q(s,a)\leftarrow r(s,a)+\gamma\max\limits_{a'} Q(s',a')$
  - value iteration에서 data는 $(s,a,r)$, Q-iteration에서 data는 $(s,a,s',r)$
- p15: Q-iteraion이 off-policy인 이유는?
- p18: Q-learning에서 exploration이 필요한 이유를 쉽게 설명하면?
- p18: eplilon-greedy와 Boltzmann exploration의 의미는?
- p22: value iteration은 contraction 연산이므로 수렴이 보장됨 (Tabular case)
- p23: fitted value iteration은 수렴이 보장되지 않음 (non-tabular case)
  - value iteration & fitting은 contraction 연산이 아님
  


