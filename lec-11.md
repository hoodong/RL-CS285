# Lecture 11. Model-based RL

## keywords
- naive approach
- distributional shift
- uncertainty
- complex objervations

## 질문
- p3: version 0.5
  - 1.run base policy to collect dataset
  - 2.learn dynamic model to minimize mse loss
  - 3.plan through model to choose actions
- p5: distribution mismatch problem
  - 모델학습에 사용된 상태 분포와 planning에 사용된 상태 분포가 다르다.
- p6: version 1.0 (+DAgger)
  - 1.run base policy to collect dataset
  - 2.learn dynamic model to minimize mse loss
  - 3.plan through model to choose actions
  - 4.execute those actions and add the resulting data to dataset
  - repeat step 2~4
 - p8: version 1.5 (+MPC)
  - 1.run base policy to collect dataset {(s,a,s')}
  - 2.learn dynamic model f(s,a) to minimize mse loss
  - 3.plan through f(s,a) to choose actions
  - 4.execute the first planned action, observe resulting state s'
  - 5.append (s,a,s') to dataset
