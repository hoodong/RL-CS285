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
- p4: closed-loop planning
  - 현재상태를 관찰한 후에 정책을 생성한다.
  - 앞의 예에서 모든 가능한 덧셈 문제에 대한 정답을 주는 정책을 생성할 것이다.
  - 따라서 최적 plan은 덧셈 시험에 참가하고 답을 계산하는 것이다.
- p5: model-based RL v2.0
  - 
  
