# Lecture 2. Supervised learning of behaviors

## 용어와 표기법
- 상태 state $s_t$
- 관측값 observation $o_t$
- 행동 action $a_t$
- 정책 policy $\pi_{\theta}(a_t|o_t)$, $\pi_{\theta}(a_t|s_t)$
- Markov 속성

## 모방학습 (imitation learning)
- Behavioral cloning: 전문가의 시연으로부터 배움
- 관측값과 행동이 데이터로 주어지고 지도학습을 통해 정책을 훈련시킴
- 사례: 자율주행
  - Pomerleau 1989, ALVINN: An Autonomous Land Vehicle in a Neural Network
  - Bojarski 2016, End to End Learning for Self-Driving Cars
 
## Behavioral cloning이 실패한 이유
- 데이터의 iid 가정이 성립하지 않음 (의사결정 문제에서는 현재 행동이 다음 상태에 영향을 미치기 때문)
- 따라서 작은 오류가 누적되어 데이터 분포가 달라짐 (전문가는 실수하지 않음)
- 이것을 distributional shift 문제라고 함 (학습 데이터와 테스트 데이터의 분포가 다름)
- 그러면 기존 지도학습에서는 distributional shift가 발생하지 않나요?
- 참고문헌: Ross 2011

## 해결방법
- 데이터 수집방법 개선
  - trail following as classification: Giusti 2016
  - imitation with a cheap robot: Rahmatizadeh 2017
- 모델 개선
  - 전체 히스토리 사용 (Markov 가정이 성립하지 않는 경우)
  - 하지만 데이터가 많아지면 Causal confusion 문제가 발생할 수 있음 (원인과 결과를 구분하지 못함, de Hann 2019)
  - diffusion 모델: Chi 2023
  - latent 변수: Zhao 2023
  - 트랜스포머: Brohan 2023
- 멀티태스크 학습
  - Lynch 2019, Learning Latent Plans from Play
  - Chosh 2019, Learning to Reach Goals via Iterated Supervised Learning
- 알고리즘 개선
  - DAgger: Dataset Aggregation (Ross 2011)
 
