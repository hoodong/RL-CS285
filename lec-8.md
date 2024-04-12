# Lecture 8. Deep RL with Q-Functions
- p3: online Q-iteration algorithm에서 3 라인이 gradient descent가 맞는지?
  -  $L=\frac{1}{2}(Q_\phi-y)^2$
  -  $\frac{\partial L}{\partial \phi} =$
     $(Q_\phi-y)(\frac{\partial Q_\phi}{\partial \phi}-\frac{\partial y}{\partial \phi})$
  -  슬라이드에는 $\frac{\partial y}{\partial \phi}$ 항이 빠져있는 이유는?
  -  semi-gradient descent?
- p3: "no gradient through target value"가 무슨 뜻인지?
  -  $\frac{\partial y}{\partial \phi}$ 항이 없음
- p4: online Q-learning의 2가지 문제점
  - 샘플의 상관도가 높다.
  - 타겟값이 계속 변한다.
- p4: correlated samples이 왜 문제가 되는지? 학습에 어떤 영향을 주는지?
- p11: target network를 가지는 Q-learning에서 N과 K의 차이는?
  - N: 데이터 수집 및 리플레이 버퍼에 저장하는 횟수
  - K: 리플레이 버퍼에서 샘플링 및 파라미터 업데이트 횟수
  - 여기서 데이터는 (s,a,s',r)
- p12: 두 알고리즘의 차이? 단지 DQN은 K=1?
  - 위 1 = 아래 5
  - 위 2 = 아래 1
  - 위 3,4 = 아래 2,3,4
- p13: Polyak averaging과 같은 altenative target network을 쓰는 이유는?
- p16: general Q-learning 관점
  - process 1: data collection
  - process 2: target update
  - process 3: Q-function regression
- p17: general Q-learning 관점에서 다음 3가지 방식의 차이점은?
  - online Q-learning
  - DQN
  - fitted Q-iteration
- p22: double Q-learning의 원리를 쉽게 설명하면?
- p27: Q-learning에서 continuous actions?
  - option 1: stochastic optimization?
  - option 2: normalized advantage function (ANF, GU 2016)
  - option 3: deep deterministic policy gradient (DDPG, Lillicrap 2016)

     
