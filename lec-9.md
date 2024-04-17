# Lecture 9. Advanced Policy Gradients

## TOC
- policy gradient as policy iteration
- bounding the distribution change
- policy gradient with constraints
- natural gradient

## 질문
- p4: 두 번재 등식이 성립하는 이유는?
  - $J(\theta) = E_{\tau\sim p_{\theta'}(\tau)}[V^{\pi_\theta}(s_0)]$
  - trajectory $\tau=\{ s_0,a_0,s_1,a_1,...\} $가 $p_{\theta'}$ 분포를 따른다?
- p5: 이 식을 말로 쉽게 표현하면?  
  - $J(\theta')-J(\theta)=E_{\tau\sim p_\theta'} \left[ \sum_t \gamma^t A^{\pi_\theta} (s_t,a_t)\right]$
  - 
