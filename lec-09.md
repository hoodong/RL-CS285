# Lecture 9. Advanced Policy Gradients

## TOC
- policy gradient as policy iteration
- bounding the distribution change
- policy gradient with constraints
- natural gradient

## 질문
- p3: (review) policy gradient vs. policy iteration
  - policy gradient  
    $\theta \leftarrow \theta + \alpha\nabla_\theta J(\theta)$  
    $\nabla_\theta J(\theta)\approx\frac{1}{N}\sum\limits_{i=1}^{N}\sum\limits_{t=1}^{T}
    \nabla_\theta \log \pi_\theta (a_{i,t}|s_{i,t}) \hat{A}^\theta (x_t,u_t)$
  - policy iteration  
    $\pi'(a_t|s_t)=1$ if $a_t=\arg\max_{a_t}A^\pi(s_t,a_t)$  
    $\pi'(a_t|s_t)=0$ otherwise
- p4: 아래 식이 성립하는 이유는?
  - $E_{s_0\sim p(s_0)}[V^{\pi_\theta}(s_0)] = E_{\tau\sim p_{\theta'}(\tau)}[V^{\pi_\theta}(s_0)]$  
  - trajectory는 new policy를 따르고, value fuction은 old function을 따른다?
  - 왜냐하면 $V^{\pi_\theta}(s_0)$에서 random한 부분은 $s_0$ 뿐이므로 $a_t$가 어떤 정책이든 기대값 계산에 영향을 주지 않는다.  
    즉, $a_t$의 정책에 상관없이 $E_{s_0}[V^{\pi_\theta}(s_0)]=E_{s_0,a_0,s_1,...}[V^{\pi_\theta}(s_0)]$이 성립한다.   
    강의자료에서는 수식 전개를 위해 $a_t$가 new policy를 따른다고 가정했다.
- p5: 기대값은 새 정책, advantage는 이전 정책? 
  - $J(\theta')-J(\theta)=E_{\tau\sim p_\theta'} \left[ \sum_t \gamma^t A^{\pi_\theta} (s_t,a_t)\right]$
  - advantage는 old policy를 따르고, trajectory는 new policy를 따른다는 것이 무슨 뜻인지?
  - advatage $A_\pi (s_t,a_t)$는 행동가치 $Q_\pi(s_t,a_t)$와 상태가치 $V_\pi(s_t)$의 차이로 정의된다.
    즉 상태 $s_t$에서 행동 $a_t$를 하고 이후에는 정책 $\pi$에 따라 행동할 때,
    행동 $a_t$으로 인한 가치 증가를 의미한다.
  - 주어진 식을 풀어 써보면 $J(\theta')-J(\theta)=$
    $E_{\pi'}[A_\pi(s_0,a_0)+\gamma A_\pi(s_1,a_1)+\gamma^2 A_\pi(s_2,a_2)+...]$  
    따라서 $A_\pi(s_t,a_t)$ 계산에서 $a_t$는 새 정책 $\pi'$, $a_{t+1},a_{t+2},...$는 이전 정책 $\pi$을 따른다.
  - 요약하면 기대값은 new policy, advantage는 old policy를 따른다!
- p6: distribution mismatch
  - 근사: $J(\theta')-J(\theta)\approx\bar{A}(\theta')$ : state prob에 새 정책 대신 기존 정책을 사용해서 계산
  - 가정: $\pi_{\theta'}\approx\pi_{\theta} \rightarrow p_{\theta'}(s_t)\approx p_{\theta}(s_t)$
    정책이 비슷하면 분포도 비슷하다!
- p11: bounding distributional mismatch
  - 정책의 차이가 $\epsilon$ 이하이면, 분포의 차이는 $2\epsilon t$ 이하이다.   
  - $|\pi_{\theta'}-\pi_{\theta}|\le\epsilon \rightarrow |p_{\theta'}-p_{\theta}|\le 2\epsilon t$
  - 여기서 두 분포의 절대값은 total variation distance (TV-distance)를 의미한다.
- p12: 지금까지 정리하면
  - $\theta'\leftarrow \arg\max_{\theta'}\sum_t \bar{A}(\theta)$
    s.t. $|\pi_{\theta'}-\pi_\theta| \le \epsilon$
- p14: more convenient bound
  - 제한조건을 TV-distance 대신 KL-divergence를 쓰면 더 편리하다.
  - 참고: $d_{TV}(p,q) \le \sqrt{\frac{1}{2}D_{KL}(p||q)}$
  - 즉 두 정책의 KL-divergence를 제한조건으로 두고 advantage를 최대화하는 policy를 찾는다.
- p18-p19: 목적함수를 근사
  - $\theta'$의 advantage를 $\theta$에서 1차 테일러 근사 (선형화)
  - $\bar{A}(\theta')\approx \nabla_\theta \bar{A}(\theta')^T (\theta'-\theta)$
  - $\nabla_\theta\bar{A}(\theta')=\nabla_\theta J(\theta)$: policy gradient와  동일 (lec-6, p5)
  - 여기서 $J(\theta)$의 정의는?
- p22: natural gradient의 learning rate? (Lagrange multiplier 이용)
  - $\max\limits_\theta'\nabla J(\theta)^T (\theta'-\theta)$
    s.t. $\frac{1}{2}(\theta'-\theta)^T\mathbf{F}(\theta'-\theta)$
  - Largangian $L(\theta',\lambda)=J(\theta)^T (\theta'-\theta)
    \lambda\left[\frac{1}{2}(\theta'-\theta)^T\mathbf{F}(\theta'-\theta)-\epsilon\right]$  
    - $\frac{\partial L}{\partial \theta'}=J(\theta)-\lambda\mathbf{F}(\theta'-\theta)=0$
    $\rightarrow\theta'-\theta=\frac{1}{\lambda}\mathbf{F}^{-1}\nabla J(\theta)$  
    - $\frac{\partial L}{\partial \lambda}
      =\frac{1}{2}(\theta'-\theta)^T\mathbf{F}(\theta'-\theta)-\epsilon=0$
    $\rightarrow\frac{1}{2\lambda^2}\nabla J(\theta)^T \mathbf{F}^{-1}\nabla J(\theta)=\epsilon$
  - learning rate $\alpha=\frac{1}{\lambda}$
    - $\theta'=\theta+\alpha\mathbf{F}^{-1}\nabla J(\theta)$
    - $\alpha=\sqrt{\frac{2\epsilon}{\nabla J(\theta)^T \mathbf{F}^{-1}\nabla J(\theta)}}$
      
    
    
    
    
