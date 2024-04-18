# Lecture 10. Optimal Control and Planning

## TOC
- what if we know the dynamics?
- open-loop planning
- stochastic optimization methods
- monte carlo tree search (MCTS)
- trajectory optimization

## 질문
- 10장은 dynamic을 알 때 행동을 결정하는 방법, 11장은 dynamic을 모를 때 이것을 학습하는 방법 
- dynamic을 알 때 세 가지 분류
  - deterministic case?
  - stochastic open-loop case?
  - stochastic closed-loop case?
- 용어
  - open-loop와 clodes-loop의 차이?
  - control과 planning 뜻은?
- stochastic optimization?
  - random shooting method
  - cross-entropy method (CEM)
  - open-loop planning과 stochastic optimization의 관계는?
  - MCTC도 stochastic optimization에 포함되는가?
- trajectory optimization이 무엇인가?
- shooting method와 collocation의 차이?
- LQR이 무엇인가? (linear quadratic regulator)
  - 최적제어(optimal control) 이론의 하나
  - 시스템의 상태방정식을 구하고, 성능 척도를 정하고, 리카티 미분방정식을 푼다.
  - LQR + 칼만 필터를 LQG (linear quadratic Gaussian)이라고 한다.
  - LQR is a well-known method that provides optimally controlled feedback gains to enable the closed-loop stable and high performance design of systems.
