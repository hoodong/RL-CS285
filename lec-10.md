# Lecture 10. Optimal Control and Planning

## TOC
- model-based RL
- open-loop planning
- stochastic optimization methods
- monte carlo tree search (MCTS)
- trajectory optimization

## 질문
- 용어
  - planning?
    - (Sutton 8.1) any computational process that takes a model as input and produces or improves a policy for interacting with the modeled environment
  - control과 planning의 차이?
  - prediction과 control의 차이?
  - open-loop와 closes-loop의 차이?  
- 환경의 transition dynamic을 아는 경우
  - deterministic case?  
  - stochastic open-loop case?
  - stochastic closed-loop case?
- stochastic 인 경우에 환경/정책 중에 어떤 것이 random? 둘 다?
- deterministic인 경우는 왜 open-loop와 closed-loop로 나누지 않는지? 
- open loop methods
  - random shooting
  - cross-entropy method (CEM)
  - Monte Carlo tree search (MCTS)
  - linear quadratic regulator (LQR)

- p15: CEM
  - a Monte Carlo method for importance sampling and optimization
  - 알고리즘 (wikipedia)
    - step 1: obtain N samples from current sampling distribution
    - step 2: evaluate objective function at sampled points
    - step 3: sort X by objective function values in descending order
    - step 4: update parameters of sampling distribution via elite samples
    - repeat step 1 to step 4 until stopping criterion
  - 이 방법이 어떻게 cross-entropy를 최소화 할까?
  - importance sampling이 어디서 사용되는 걸까?
- p20: MCTS
  - 모든 tree를 탐색할 수 없으니 어디부터 탐색할지 정해야 한다.
  - 보상이 크고 방문 횟수가 적은 노드부터 탐색하자. 
  - 알고리즘 ($s_1$: root node, $s_l$: leaf node)
    - step 1: TreePolicy($s_1$)를 이용해 $s_l$를 찾는다.
    - step 2: DefaultPolicy($s_l$)를 이용해 $s_l$의 가치를 평가한다.
    - step 3: $s_1$과 $s_l$ 사이의 모든 가치를 업데이트 한다.(backup)
    - step 1 - step 3를 반복한다.
    - $s_1$에서 최선의 행동의 취한다.
  - step 2가 왜 필요한지? (leaf node의 가치 계산)
  - TreePolicy는 UCT (upper confidence bounding tree)를 이용한다.
  - UCT는 confidence interval의 upper bound를 계산한다. (Hoeffding's inequality에서 유도)
- p23: trajectory optimization with derivative
  - 앞에서는 목적함수의 구조를 모르는 상황이었지만(black optimization), 이제 목적함수의 미분을 알 수 있다면?
- p25: shooting method와 collocation method의 차이?
- p26: LQR (linear quadratic regulator)  
  - 최적제어: 물리적인 제약조건을 만족하면서 성능지표 또는 목적함수를 최적화하도록 동적 시스템(dynamic system)의 제어변수을 결정하는 문제
  - linear-quadratic system: 시스템이 선형, 목적함수가 2차함수인 시스템  
  - (chatgpt3.5) LQR은 시스템의 상태를 조절하여 원하는 목표를 달성하는 제어기를 설계하는 방법 중 하나로서, 시스템 모델링/성능 지표 정의/최적제어 입력 계산/피드백 제어기 설계로 구성된다.
- p27: linear인 경우에 LQR
  - $c(x_t,u_t)$와 $f(x_t,u_t)$를 각각 2차와 1차로 근사할 때 행렬 $C_t,F_t$과 벡터 $c_t,f_t$의 의미는?
  - 행렬 $C_t,F_t$는 Hessian, 벡터 $c_t,f_t$는 gradient인가?
  - $t=T$에서 Q 함수가 비용+상수로 주어지는 이유: $Q(x_T,u_T)=\text{const}+c(x_T,u_T)$
- p34: stochastic인 경우에 LQR
- p36: nonlinear인 경우에 LQR
  - nonlinear system을 linear-quadratic system으로 근사한다.
  - iterative LQR (iLQR)
  - p39: iLQR는 Newton's method의 근사
  - p40: differential dynamic programming (DDP)는 시스템을 2차로 근사
    
