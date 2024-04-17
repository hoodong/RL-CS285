# Lecture 9. Advanced Policy Gradients

## TOC
- policy gradient as policy iteration
- bounding the distribution change
- policy gradient with constraints
- natural gradient

## 질문
- p4: 두 번재 등식이 성립하는 이유는?
  - $J(\theta) = E_{\tau\sim p_{\theta'}(\tau)}[V^{\pi_\theta}(s_0)]$
- p5: 최종 식을 말로 쉽게 표현하면?
  - $J(\theta')-J(\theta)=E_{\tau\sim p_{\theta'}[\sum_t \gamma^t A^{\pi_\theta} (s_t,a_t)]$
