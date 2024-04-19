# Lecture 9. Advanced Policy Gradients

## TOC
- policy gradient as policy iteration
- bounding the distribution change
- policy gradient with constraints
- natural gradient

## 질문
- p4: 두 번째 등식이 성립하는 이유는?
  - $J(\theta) = E_{\tau\sim p_{\theta'}(\tau)}[V^{\pi_\theta}(s_0)]$
  - $\tau=s_0,a_0,s_1,a_1,...$가 $p_{\theta'}$ 분포를 따른다는 것이 무슨 뜻인지?  
  - trajectory $\tau$의 분포에는 초기상태 $p(s_0)$, 정책 $\pi(a|s)$, 전이확률 $p(s'|s,a)$이 모두 포함되어 있음
  - trajectory는 new policy를 따르고, value fuction은 old function을 따른다는 것은 서로 모순되는 것 같음!
- p5: 아래 식을 쉽게 설명하면?  
  - $J(\theta')-J(\theta)=E_{\tau\sim p_\theta'} \left[ \sum_t \gamma^t A^{\pi_\theta} (s_t,a_t)\right]$
  - p4 질문과 마찬가지로 advantage는 new policy를 따르고, trajectory는 old policy를 따른다는 것이 무슨 뜻인지?
    혹시 importance sampling 개념?
  - 즉, old policy의 advantage를 new policy의 advantage로 환산?
- p6: distribution mismatch
  - 근사: $J(\theta')-J(\theta)\approx\bar{A}(\theta')$
  - 가정: $\pi_{\theta'}\approx\pi_{\theta} \rightarrow p_{\theta'}(s_t)\approx p_{\theta}(s_t)$
    
    