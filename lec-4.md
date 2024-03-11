# Lecture 4. Introduction to Reinforcement Learning

## 용어와 표기법
- 상태 state $s_t$
- 관측값 observation $o_t$
- 행동 action $a_t$
- 정책 policy $\pi_{\theta}(a_t|o_t)$, $\pi_{\theta}(a_t|s_t)$
- Markov 속성

## 정의
- Markov chain
  - $\mathcal{M=\lbrace S,T \rbrace}$
  - $\mathcal{S}$: state space
  - $\mathcal{T}$: transition operator
  - 상태확률 $\mu_{t,i}=P(s_t=i)$과 천이확률 $\mathcal{T}\_{i,j}=p(s_{t+1}=i|s_t=j)$에 대해 $\mu_{t+1,i}=\sum_j \mathcal{T}\_{i,j}\cdot \mu_{t,i}$이 성립
  - 행렬식으로 나타내면 $\mu_{t+1}=\mathcal{T}\mu_{t}$
- Markov decision process (MDP)
  - $\mathcal{M=\lbrace S,A,T,r \rbrace}$
  - $\mathcal{A}$: action space
  - $r$: reward function
- patially observed Markov decision process (POMDP)
  - $\mathcal{M=\lbrace S,A,O,T,E,r \rbrace}$
  - $\mathcal{O}$: observation space
  - $\mathcal{E}$: emission probability $p(o_t|s_t)$

## 강화학습의 목표
- 궤적(trajectory): $\tau=s_1,a_1,s_2,s_2,...,s_T,a_T$
- 어떤 궤적이 일어날 확률은 초기상태 확률 $p(s_1)$, 에이전트의 정책 $\pi_\theta(a|s)$, 환경의 천이확률 $p(s'|s,a)$로 주어짐
- $p_\theta(\tau)=p_\theta(s_1,a_1,s_2,s_2,...,s_T,a_T)$  
  $= p(s_1)p(a_1|s_1)p(s_2|s_1,a_1)p(a_2|s_1,a_1,s_2)p(s_3|s_1,a_1,s_2,a_2)...$ (연쇄율)  
  $= p(s_1)\prod\limits_{t=1}^{T}\pi_\theta(a_t|s_t)p(s_{t+1}|s_t,a_t)$ (Markov 성질)
- 강화학습의 목표는 (궤적에서 얻어지는) 누적 보상의 기대값을 최대화하는 정책을 찾는 것 (즉, 정책의 파라미터 $\theta$)
  $\theta^\star=\text{arg}\max\limits_{\theta} E_{\tau\sim p_\theta(\tau)}\left[ \sum\limits_t r(s_t,a_t) \right]$
- finite horizon 경우  
  $\theta^\star=\text{arg}\max\limits_{\theta} \sum\limits_t E_{(s_t,a_t)\sim p_\theta (s_t,a_t)} r(s_t,a_t)$
- infinite horizon 경우

## 강화학습 알고리즘
- 기본구조: 1.샘플생성(정책수행) -> 2.모델접합/리턴추정 -> 3.정책개선 (1,2,3을 반복)
- 계산량이 가장 많은 부분은? 2번

## 가치함수
- 보상함수의 기대값
- Q 함수: $Q^\pi(s_t,a_t)$, 상태 $s_t$에서 행동 $a_t$로부터 얻어지는 보상의 기대값 (행동 가치함수)
- value 함수: $V^\pi(s_t)$, 상태 $s_t$에서 얻어지는 보상의 기대값 (상태 가치함수)
- 두 가지 중요한 개념 (?)
  - 1. 정책이 주어지면 Q 함수를 알 수 있고, 따라서 정책을 개선할 수 있음
  - 2. 좋은 행동을 선택하는 확률을 증가시키도록 그래디언트를 계산 (행동가치가 상태가치보다 크다면 그 정책의 확률을 증가시킴)

## 알고리즘 종류
- policy gradient
- 가치 기반: 가치함수를 추정해서 최적정책을 찾는다
- actor-critic
- 모델 기반

