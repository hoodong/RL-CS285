# Lecture 4. Introduction to Reinforcement Learning

## 용어와 표기법
- 상태 state $s_t$
- 관측값 observation $o_t$
- 행동 action $a_t$
- 정책 policy $\pi_{\theta}(a_t|o_t)$, $\pi_{\theta}(a_t|s_t)$
- Markov 속성

## 정의
- Markov chain: $\mathcal{M=\lbrace S,T \rbrace}$
  - $\mathcal{S}$: state space
  - $\mathcal{T}$: transition operator
  - 상태확률 $\mu_{t,i}=P(s_t=i)$과 천이확률 $\mathcal{T}\_{i,j}=P(s_{t+1}=i|s_t=j)$에 대해 $\mu_{t+1,i}=\sum_j \mathcal{T}\_{i,j}\cdot \mu_{t,i}$이 성립
  - 행렬식으로 나타내면 $\mu_{t+1}=\mathcal{T}\mu_{t}$
- Markov decision process: $\mathcal{M=\lbrace S,A,T,r \rbrace}$
  - $\mathcal{A}$: action space
  - $r$: reward function
- patially observed Markov decision process: $\mathcal{M=\lbrace S,A,O,T,E,r \rbrace}$
  - $\mathcal{O}$: observation space
  - $\mathcal{E}$: emission space

## 강화학습의 목표

## 
- finite horizon 경우
- infinite horizon 경우

## 강화학습 알고리즘
- 1.샘플생성(정책수행) -> 2.모델접합/리턴추정 -> 3.정책개선: 1,2,3을 반복
