# Lecture 6. Actor-Critic Algorithms

## 질문
- p5: 가치함수 정의
  - state-action value function (Q function)    
    $Q^{\pi}(s_t,a_t)=\sum\limits_{t'=t}^{T}E_{\pi_{\theta}}\left[r(s_t',a_t'|s_t,a_t)\right]$ : total reward from taking $a_t$ in $s_t$      
  - state value function   
    $V^{\pi}(s_t)=\sum\limits_{t'=t}^{T}E_{\pi_{\theta}}\left[r(s_t',a_t'|s_t)\right]$ 
    $=E_{a_t\sim\pi_{\theta}(a_t|s_t)}\left[Q^{\pi}(s_t,a_t)\right]$ : total reward from  $s_t$   
- p6: Q 함수의 근사
  - $Q^{\pi}(s_t,a_t)$  
    $= r(s_t,a_t)+E\left[V^{\pi}(s_{t+1})\right], \quad s_{t+1}\sim p(s_{t+1}|s_t,a_t)$    
    $\approx r(s_t,a_t) + V^{\pi}(s_{t+1})$, $\quad s_{t+1}$ 는 현재 궤적에서 얻어짐
- p15: policy gradient에 discound factor를 적용할 때 option 1과 option 2의 차이?
- p15: 실제로는 option 1을 사용하는 이유는?
- p20: on-policy 가정을 제거해서 off-policy로 동작시키려는 이유는? (on-policy actor critic의 단점?)
- p21: off-policy actor-critic을 위해 기존 알고리즘에서 바꿔야 하는 두 군데는?
  - replay buffer에서 가져온 transition $(s_i,a_i,r_i,s_i^{'})$는 old actor에서 얻어진 것  
  - $a_i$ did not come from latest ${\pi}_{\theta}$
- p22: (알고리즘 3라인 가치망 업데이트) $\hat{Q}_{\phi}^{\pi}(s_i^{'},a_i^{'})$을 쓸 때
  왜 $a_i^{'}$를 현재정책에서 정하는지?
  - $Q^\pi(s,a)=r(s,a)+\gamma V^\pi(s')$  (?)  
    $\qquad\qquad=r(s,a)+\gamma E\left[Q^\pi(s',a')\right], a'\sim \pi(a'|s')$
- p23: (알고리즘 5라인 gradient 계산) 행동을 현재정책에서 샘플링하는 이유는?
  - $\nabla_\theta J(\theta)\approx$
    $\frac{1}{N}\sum_i\nabla_\theta\log\pi_\theta(a_i^\pi)\hat{A}^\pi(s_i,a_i^\pi)$,
    $\quad a_i^\pi\sim \pi_\theta(a|s_i)$
  - critic (1~3 라인): 리플레이 버퍼에서 가져온 샘플로 Q 함수를 업데이트
  - actor (4~5 라인): 
   

