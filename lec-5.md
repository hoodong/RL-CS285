# Lecture 4. Introduction to Reinforcement Learning

## 질문
- p4: $\sum_i$는 현재정책에서 얻은 모든 샘플에 대해 더한다는 의미!
- p6: 궤적의 발생확률에서 초기상태와 전이확률은 없어지고 정책만 남는 이유는? -> 초기상태와 전이확률은 파라미터 \theta의 함수가 아니므로, \theta에 대해 미분하면 0이 됨
- p7: REINFORCE 알고리즘 2번 라인에서 $\sum_i$가 빠져야 하지 않을까? 어쩌면 현재까지 얻어진 모든 에피소드를 더하는걸까?
- p10: ML식은 어디서 왔는가? 주어진 목적함수에 대해 파라미터를 ML 추정?
- p11: Gaussian 정책에서 f는 평균벡터이고 \Sigma는 공분산 행렬인가?
- p13: POMDP에서 policy gradient를 그대로 사용해도 될까?
- p14: policy gradient의 문제점은 무엇인가? 분산이 큰 이유는? (무엇의 분산인가?)

## 요약


