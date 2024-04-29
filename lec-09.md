# Lecture 9. Advanced Policy Gradients

## TOC
- policy gradient as policy iteration
- bounding the distribution change
- policy gradient with constraints
- natural gradient

## 질문
- p4: 두 번째 등식이 성립하는 이유는?
  - $J(\theta) = E_{\tau\sim p_{\theta'}(\tau)}[V^{\pi_\theta}(s_0)]$  
  - trajectory $\tau$의 분포에는 초기상태 $p(s_0)$, 정책 $\pi(a|s)$, 전이확률 $p(s'|s,a)$이 모두 포함되어 있음
  - trajectory는 new policy를 따르고, value fuction은 old function을 따른다는 것은 서로 모순되는 것 같음!
- p5: 아래 식을 쉽게 설명하면?  
  - $J(\theta')-J(\theta)=E_{\tau\sim p_\theta'} \left[ \sum_t \gamma^t A^{\pi_\theta} (s_t,a_t)\right]$
  - p4 질문과 마찬가지로 advantage는 new policy를 따르고, trajectory는 old policy를 따른다는 것이 무슨 뜻인지?
    혹시 importance sampling 개념?
  - 즉, old policy로 얻은 샘플을 이용해 new policy의 기대값을 계산한다는 의미? 
- p6: distribution mismatch
  - 근사: $J(\theta')-J(\theta)\approx\bar{A}(\theta')$ : old policy의 샘플로 계산한 new policy의 advantage
  - 가정: $\pi_{\theta'}\approx\pi_{\theta} \rightarrow p_{\theta'}(s_t)\approx p_{\theta}(s_t)$
- p11: bounding distributional mismatch
  - 정책의 차이가 $\epsilon$ 이하이면, 분포의 차이는 $2\epsilon t$ 이하이다.   
  - $|\pi_{\theta'}-\pi_{\theta}|\le\epsilon \rightarrow |p_{\theta'}-p_{\theta}|\le 2\epsilon t$
  - 여기서 두 분포의 절대값은 total variation distance를 의미한다. 
- p14: more convenient bound
  - 제한조건을 total variation distance 대신 KL-divergence를 쓰면 더 편리하다.
  - 즉 두 정책의 KL-divergence를 제한조건으로 두고 advantage를 최대화하는 policy를 찾는다.
- p18: 목적함수를 근사
  - $\theta'$의 advantage를 $\theta$에서 1차 테일러 근사 (선형화)
  - $\bar{A}(\theta')\approx \del_\theta \bar{A}(\theta')^T (\theta'-\theta)$
    
    
