# Lecture 12. Model-based Policy Learning

## keywords
- model-free learning with a model
- Syna-style algorithm
- multi-step models & successor representations


## 질문 및 요약
- p2: 지난 강의에서는 model-based RL ver 1.5을 다루었다.
  - 모델 오류를 보정하기 위해 매 시간 스텝마다 replanning을 수행한다.(MPC)
  - 하지만 open-loop planning을 쓰면 큰 단점이 발생한다.
- p3: open-loop contol은 최적이 아니다.
  - 예를 들어 간단한 한자리 덧셈 시험을 생각해 보자.
  - 두 가지 연속된 행동을 정해야 한다. 1.시험 참가여부, 2.답안 제출(덧셈 계산)
  - 보상은 답을 맞추면 2000달러, 답을 틀리면 -1000달러, 시험을 안보면 0이다.
  - open-loop contol에서는 시험 문제를 보지도 않고 답을 정해야 한다.
  - 따라서 최적 plan은 시험에 참가하지 않는 것이다. (문제를 보지 않고 답을 맞출 확률이 매우 낮기 때문에)
  - MPC를 쓰더라도 이 문제는 해결할 수 없다. (시험에 참가하지 않을 것이므로)
  - 이 문제를 해결하려면 closed-loop control을 써야 한다.
- p4: closed-loop control
  - 현재상태를 관찰한 후에 정책을 생성한다.
  - 앞의 예에서 모든 가능한 덧셈 문제에 대한 정답을 주는 정책을 생성할 것이다.
  - 따라서 최적 plan은 덧셈 시험에 참가하고 답을 계산하는 것이다.
  - 그러면 어떤 형태의 정책을 써야 할까? global vs local
  - LQR은 open-loop plan 근처에서만 유효한 local 정책이다.
  - 신경망은 모든 상태에 대한 행동을 생성하는 global 정책이다.
- p5: model-based RL v2.0  
  - 학습된 모델이 있을 때 총 보상을 최대화하도록 정책을 학습시켜야 한다.
  - 계산 그래프는 3개의 함수로 구성된다: policy $\pi$, dynamics $f$, reward $r$
  - $r$은 안다고 가정, $\pi$ 와 $r$은 학습할 신경망, 손실함수는 $-\sum_t r_t$이다.
  - 각 보상 노드에서 역전파를 수행해 총 보상에 대한 정책 파라미터의 그래디언트를 계산할 수 있다.
  - ver 1.5와 비교해보면 planning이 정책 학습으로 바뀌었다.
  - model-free policy gradient와 달리 dynamics가 gradient 계산에 포함된다.(model-based policy gradient)
- p6: 이 방식의 문제점
  - 먼저 수행된 행동이 늦게 수행된 행동보다 보상에 더 큰 영향을 준다. (최종 행동은 최종 보상에만 영향을 주지만, 첫 행동은 모든 보상에 영향을 준다.)
  - 즉, 처음 행동들은 그래디언트가 크고, 마지막 행동들은 그래디언트가 작다. 파라미터 민감도가 다르다 (ill-conditioned problem)
  - 하지만 여기서는 LQR과 같은 2차 방법을 사용할 수 없다.  왜냐하면 정책 파라미터는 모든 시간 스텝이 결합되어 있기 때문에 동적 프로그래밍을 사용할 수 없다.(?)
  - 딥러닝 관점에서는 RNN 학습시키는 문제와 비슷하다. (LSTM, transformer)  
  
