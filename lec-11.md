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
- p6: version 1.0 (+DAgger: data aggregation)
  - 1.run base policy to collect dataset
  - 2.learn dynamic model to minimize mse loss
  - 3.plan through model to choose actions
  - 4.execute those actions and add the resulting data to dataset
  - repeat step 2 - 4
- p8: version 1.5 (+MPC: replan)
  - 1.run base policy to collect dataset {(s,a,s')}
  - 2.learn dynamic model f(s,a) to minimize mse loss
    - 3.plan through f(s,a) to choose actions
    - 4.execute the first planned action, observe resulting state s' (MPC)
    - 5.append (s,a,s') to dataset
    - repeat step 3~5 (replan)
  - repeat step 2~5 (learn dynamics)
- p9: version 1.0과 version 1.5의 차이?
  - step 3-5를 보면 replan 과정에서 dynamics f(s,a)가 변하지 않는다. 그러면 version 1.0과 차이가 무엇일까?
  - f(s,a)가 변하지 않으면 replan 결과가 동일하지 않을까? 달라진다!
  - 왜냐하면 version 1.0은 모델에서 얻은 s'로 planning 하지만, vesion 1.5는 환경에서 얻은 s'로 planning 한다.
- MPC (https://www.mathworks.com/help/mpc/gs/what-is-mpc.html)
  - Model predictive control (MPC) is an optimal control technique in which the calculated control actions minimize a cost function for a constrained dynamical system over a finite, receding, horizon.
  - At each time step, an MPC controller receives or estimates the current state of the plant.
  - It then calculates the sequence of control actions that minimizes the cost over the horizon by solving a constrained optimization problem that relies on an internal plant model and depends on the current system state.
  - The controller then applies to the plant only the first computed control action, disregarding the following ones.
  - In the following time step the process repeats.
- p11: performance gap (MuJoCo cheetah)
  - model-based(Mb) vs. model-free(Mf) vs. Mb-Mf
  - cumulative reward 그래프를 해석하는 방법 (클수록 좋은지?)
  - Mb와 Mf의 y축 시작지점이 다른 이유는?
  - Mb로만 계속 학습하면? 그래프에서는 Mb로 시작해서 중간에 Mf로 바꿈
  - Mb+Mf와 Mf를 비교할 때 x축 시작지점이 동일해야 하지 않을까? 

 
