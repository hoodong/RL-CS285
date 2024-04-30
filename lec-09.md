# Lecture 9. Advanced Policy Gradients

## TOC
- policy gradient as policy iteration
- bounding the distribution change
- policy gradient with constraints
- natural gradient

## 질문
- p3: policy gradient vs. policy iteration
  - step 1: advatage 추정 $\hat{A}^\theta (s_t,a_t)$
  - step 2: policy 업데이트
  - policy gradient  
    $\theta \leftarrow \theta + \alpha\nabla_\theta J(\theta)$  
    $\nabla_\theta J(\theta)\approx\frac{1}{N}\sum\limits_{i=1}^{N}\sum\limits_{t=1}^{T}
    \nabla_\theta \log \pi_\theta (a_{i,t}|s_{i,t}) \hat{A}^\theta (x_t,u_t)$
  - policy iteration  
    $\pi'(a_t|s_t)=1$ if $a_t=\arg\max_{a_t}A^\pi(s_t,a_t)$  
    $\pi'(a_t|s_t)=0$ otherwise
- p4: 두 번째 등식이 성립하는 이유는?
  - $J(\theta) = E_{\tau\sim p_{\theta'}(\tau)}[V^{\pi_\theta}(s_0)]$  
  - trajectory는 new policy를 따르고, value fuction은 old function을 따른다?
- p5: policy gradient = policy iteration?  
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
- p12: 지금까지 정리하면
  - $\theta'\leftarrow \arg\max_{\theta'}\sum_t \bar{A}(\theta)$
    s.t. $|\pi_{\theta'}-\pi_\theta| \le \epsilon$
- p14: more convenient bound
  - 제한조건을 total variation distance 대신 KL-divergence를 쓰면 더 편리하다.
  - 즉 두 정책의 KL-divergence를 제한조건으로 두고 advantage를 최대화하는 policy를 찾는다.
- p18-p19: 목적함수를 근사
  - $\theta'$의 advantage를 $\theta$에서 1차 테일러 근사 (선형화)
  - $\bar{A}(\theta')\approx \nabla_\theta \bar{A}(\theta')^T (\theta'-\theta)$
  - $\bar{A}(\theta')=\bar{A}(\theta)$: policy gradient 유도와 동일
- p22: natural gradient의 learning rate? (Lagrange multiplier 이용)
  - $\max\limits_\theta'\nabla J(\theta)^T (\theta'-\theta)$
    s.t. $\frac{1}{2}(\theta'-\theta)^T\mathbf{F}(\theta'-\theta)$
  - Largangian: $L(\theta',\lambda)=J(\theta)^T (\theta'-\theta)
    \lambda\left[\frac{1}{2}(\theta'-\theta)^T\mathbf{F}(\theta'-\theta)-\epsilon\right]$  
    - $\frac{\partial L}{\partial \theta'}=J(\theta)-\lambda\mathbf{F}(\theta'-\theta)=0$
    $\rightarrow\theta'-\theta=\frac{1}{\lambda}\mathbf{F}^{-1}\nabla J(\theta)$  
    - $\frac{\partial L}{\partial \lambda}
      =\frac{1}{2}(\theta'-\theta)^T\mathbf{F}(\theta'-\theta)-\epsilon=0$
    $\rightarrow\frac{1}{2\lambda^2}\nabla J(\theta)^T \mathbf{F}^{-1}\nabla J(\theta)=\epsilon$
  - learning rate $\alpha=\frac{1}{\lambda}$
    - $\theta'=\theta+\frac{1}{\lambda}\mathbf{F}^{-1}\nabla J(\theta)$
    - $\alpha=\sqrt{\frac{2\epsilon}{\nabla J(\theta)^T \mathbf{F}^{-1}\nabla J(\theta)}}$
      
    
    
    
    
