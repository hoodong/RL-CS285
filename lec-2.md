# Lecture 2. Supervised learning of behaviors

## 용어와 표기법
- 상태 state $s_t$
- 관측값 observation $o_t$
- 행동 action $a_t$
- 정책 policy $\pi_{\theta}(a_t|o_t)$, $\pi_{\theta}(a_t|s_t)$
- Markov 속성

## 모방학습 (imitation learning)
- Behavioral cloning: 관측값과 행동이 데이터로 주어지고 지도학습을 통해 정책을 훈련시킴
- 사례: 자율주행
  - Pomerleau 1989, ALVINN: An Autonomous Land Vehicle in a Neural Network
  - Bojarski 2016, End to End Learning for Self-Driving Cars
 
## Behavioral cloning이 실패한 이유
- 데이터의 iid 가정이 성립하지 않음
- distributional shift 문제

## 해결방법
- 데이터 수집방법 개선
  - trail following as classification: Giusti 2016
  - imitation with a cheap robot: Rahmatizadeh 2017
- 모델 개선
  - 전체 히스토리 사용 (Markov 가정이 성립하지 않으므로)
  - Causal confusion 문제: de Hann 2019
  - diffusion 모델: Chi 2023
  - latent 변수: Zhao 2023
  - 트랜스포머: Brohan 2023
- 멀티태스크 학습
  - Lynch 2019, Learning Latent Plans from Play
  - Chosh 2019, Learning to Reach Goals via Iterated Supervised Learning
- 알고리즘 개선
  - DAgger: Dataset Aggregation (Ross 2011)
 
