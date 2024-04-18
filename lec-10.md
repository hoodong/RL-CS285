# Lecture 10. Optimal Control and Planning

## TOC
- what if we know the dynamics?
- open-loop planning
- stochastic optimization methods
- monte carlo tree search (MCTS)
- trajectory optimization

## 질문
- 10장은 dynamic을 알 때 행동을 결정하는 방법에 대해  
  11장은 dynamic을 모를 때 이것을 학습하는 방법에 대해
- dynamic을 알 때 세 가지 분류
  - deterministic case?
  - stochastic open-loop case?
  - stochastic closed-loop case?
- prediction은 주어진 정책의 가치함수를 찾는 것(정책 평가), control은 최적의 정책을 찾은 것
- planning의 뜻?
  - (Sutton 8.1) any computational process that takes a model as input and produces or improves a policy for interacting with the modeled environment
- control과 planning의 차이?
- open-loop와 clodes-loop의 차이?
- open loop methods
  - random shooting
  - cross-entropy method (CEM)
  - Monte Carlo tree search (MCTS)
  - linear quadratic regulator (LQR)
- trajectory optimization이 무엇인가?
- shooting method와 collocation의 차이?
- LQR은 무엇인가?
  - 최적제어 문제: 물리적인 제약조건을 만족하면서 성능지표 또는 목적함수를 최적화하도록 동적 시스템(dynamic system)의 제어변수을 결정하는 문제
  - linear: 시스템이 선형, quadratic: 목적함수가 2차함수, regulator: 시스템 상태를 0으로 만드는 제어기
  - (chatgpt3.5) LQR은 시스템의 상태를 조절하여 원하는 목표를 달성하는 제어기를 설계하는 방법 중 하나로서, 시스템 모델링/성능 지표 정의/최적제어 입력 계산/피드백 제어기 설계 의 단계를 거침
- CEM은 무엇인가? (wikipedia)
  - a Monte Carlo method for importance sampling and optimization
  - 알고리즘
    - step 1: obtain N samples from current sampling distribution
    - step 2: evaluate objective function at sampled points
    - step 3: sort X by objective function values in descending order
    - step 4: update parameters of sampling distribution via elite samples
    - repeat step 1 to step 4 until stopping criterion
  - 이 방법이 어떻게 cross-entropy를 최소화 할까?
  - importance sampling이 어디서 사용되는 걸까? 
