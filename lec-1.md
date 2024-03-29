# Lecture 1. Introduction and cource overview

## 배울 내용
- 지도학습 vs 강화학습
- model-free 알고리즘: Q-learning, policy gradient, actor-critic
- model-based 알고리즘: planning, sequence modeling
- 탐색
- offline RL
- inverse RL
- 고급 연구주제

## 강화학습이란 무엇인가?
- 지도학습과 어떻게 다른가?
- 강화학습의 수학적 틀: 에이전트, 환경, 상태, 행동, 보상, 정책

## 응용사례
- 거대 언어모형: Illustrating reinfocement learning from human feedback, Huggingface 2022
- 생성모형: Training diffusion models with reinforcement learning, Black 2023
- 칩 설계: Chip design with deep reinforcement learning, Google 2020

## 왜 심층 강화학습을 공부해야 하는가?
- The bitter lesson, Sutton 2019 
- AI 연구에서 인간지식을 컴퓨터에 넣는 것은 근원적인 해결책이 아님
- 계산량 증대를 통해서만 획기적인 성능개선 가능 (예: 체스게임, 컴퓨터비전, 바둑)
- 대규모 계산을 활용하는 중요한 두가지 방법: 학습, 탐색
- 학습은 데이터에서 패턴을 추출하는 것, 탐색은 계산을 이용해 최적의 결정을 내리는 것
- 최적화 없이 데이터만 있으면 새로운 문제를 풀 수 없고, 데이터 없이 최적화만 있으면 실세계에 적용하기 어려움

## 기계학습이 필요한 이유
- The real reason for brains, Wolpert 2011 (TED)
- 두뇌가 있는 이유는 움직임을 생성하기 위해서임 (움직임은 주변세계에 영향을 미치는 유일한 방법) 
- 기계학습이 필요한 이유는 결정을 내리기 위해서임 (예: 물체분류, 자율주행)

## 추가 연구주제
- 보상함수의 학습 (inverse RL)
- 도메인 사이의 지식 전이 (전이학습, 메타학습)
- 실세계에서 순차적 의사결정 문제는 아직 쉽지 않음 

## 지능을 가진 기계를 만들려면 어떻게 해야할까?
- 어디서 시작해야 하나?
- 단일 알고리즘이어야 할까? (예: 인간의 뇌)
- 심층 강화학습으로 해야하지 않을까?

## 여전히 해결해야 할 문제
- deep RL은 배우는 속도가 느림 (인간은 빨리 배움)
- 전이학습에 대한 연구가 필요 (인간은 과거 경험에서 배움)
