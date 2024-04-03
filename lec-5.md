# Lecture 5. Policy Gradients

## 질문
- p4: $\sum_i$는 현재정책에서 얻은 모든 샘플에 대해 더한다는 의미!
- p6: 궤적의 발생확률에서 초기상태와 전이확률은 없어지고 정책만 남는 이유는?  
  -> 초기상태와 전이확률은 파라미터 $\theta$의 함수가 아니므로, $\theta$에 대해 미분하면 0이 됨
- p10: ML식은 어디서 왔는가? 주어진 목적함수에 대해 파라미터를 ML 추정?
- p11: Gaussian 정책에서 $f$는 평균벡터이고 $\Sigma$는 공분산 행렬인가?
- p13: POMDP에서 policy gradient를 그대로 사용해도 될까?
- p14: policy gradient의 문제점은 무엇인가? 분산이 큰 이유는? (무엇의 분산인가?)
- p24: off-policy policy gradient  
  $$J(\theta')=E_{\tau\sim p_{\theta'}(\tau)}\left[ r(\tau) \right]
  = E_{\tau\sim p_{\theta}(\tau)}\left[ \frac{p_{\theta'}(\tau)}{p_{\theta}(\tau)} r(\tau) \right] $$
- p25: off-policy gradient 유도 과정
  - $\prod _{t'=1}^{t}$에서 future actions don't affect current weight 의미?
  - $\prod _{t''=t}^{t'}$ 부분을 무시하면 policy iteration algorithm이 되는 이유?
- p26: off-policy gradient 유도 과정
- p35: 그림에서 Vanilla policy gradient의 문제점?
  - 파라미터 간의 민감도가 다르다!
  - 파라미터 1 방향은 빨리 변하고, 파라미터 2 방향은 천천히 변함 
- p35: constrained optimization 문제 유도과정?  
  - 1st order Taylor expansion  
    $J({\theta}') \approx J(\theta) + (\theta'-\theta)^T \nabla_{\theta}J(\theta) $
- p36: natural policy gradient 이해?  
  - vanilla policy gradient
    $\max\limits_{\theta'}J(\theta')\quad s.t. ||\theta'-\theta||^2 \le \epsilon$
  - natural policy gradient
    $\max\limits_{\theta'}J(\theta')\quad s.t. D(\pi_\theta'-\pi_\theta) \le \epsilon$
- p36: 주어진 constraint optimization 문제에서 natural policy gradient의 해를 구하는 방법?
  - Lagrange multiplier 이용!
  - 유도과정이 잘 설명된 논문
    - van Heeswijk 2022, Natural Policy Gradients In Reinforcement Learning Explained
- p36: Fish information matrix의 의미와 KL-divergence와의 관계?
  - 참고: Natural Policy Gradient 논문 리뷰 https://rlwithme.tistory.com/5 
  - 피셔 정보 행렬을 scroe 함수의 공분산으로 정의
  - 즉 음의 log-likelihood의 Hessian의 기댓값이므로 곡률 행렬로 해석이 가능함 (?)
  - Fish information matrix = Hessian of KL-divergence (?)
    
    
   
  



