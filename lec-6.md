# Lecture 6. Policy Gradients

## 질문
- p5: 가치함수 정의
  - state-action value function (Q function)    
    $Q^{\pi}(s_t,a_t)=\sum\limits_{t'=t}^{T}E_{\pi_{\theta}}\left[r(s_t',a_t'|s_t,a_t)\right]$ : total reward from taking $a_t$ in $s_t$      
  - state value function   
    $V^{\pi}(s_t)=E_{a_t\sim\pi_{\theta}(a_t|s_t)}\left[Q^{\pi}(s_t,a_t)\right]$ : total reward from  $s_t$   
- p6: Q 함수의 근사
  - $Q^{\pi}(s_t,a_t)=r(s_t,a_t)+\sum\limits_{t'=t+1}^{T}E_{\pi_{\theta}}\left[r(s_t',a_t'|s_t,a_t)\right]$  
    $= r(s_t,a_t)+E_{s_{t+1}\sim p(s_{t+1}|s_t,a_t)}\left[V^{\pi}(s_{t+1})\right]$  
    $\approx r(s_t,a_t) + V^{\pi}(s_{t+1})$
    $Q^{\pi}(s_t,a_t)&=r(s_t,a_t)+\sum\limits_{t'=t+1}^{T}E_{\pi_{\theta}}\left[r(s_t',a_t'|s_t,a_t)\right]
    &= r(s_t,a_t)+E_{s_{t+1}\sim p(s_{t+1}|s_t,a_t)}\left[V^{\pi}(s_{t+1})\right]  
    &\approx r(s_t,a_t) + V^{\pi}(s_{t+1})
    $  
