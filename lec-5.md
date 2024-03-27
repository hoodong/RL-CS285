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
$$ J(\theta') \approx J(\theta') + (\theta'-\theta)^T \nabla_{\theta}J(\theta) $$

  $$J(\theta')=E_{\tau\sim p_{\theta'}(\tau)}\left[ r(\tau) \right]
  = E_{\tau\sim p_{\theta}(\tau)}\left[ \frac{p_{\theta'}(\tau)}{p_{\theta}(\tau)} r(\tau) \right] $$

  $ J(\theta') \approx J(\theta') + (\theta'-\theta)^T \nabla_{\theta}J(\theta) $

- p35: 그림에서 Vanilla policy gradient의 문제점?  
- p35: constrained optimization 문제 유도과정?  
  1st order Taylor expansion 
  $$ J(\theta') \approx J(\theta') + (\theta'-\theta)^T \nabla_{\theta}J(\theta) $$
  
- p36: natural policy gradient 이해?
$ J(\theta') \approx J(\theta') $
$ J(\theta') \approx J(\theta') + (\theta'-\theta)^T \nabla_{\theta}J(\theta) $ 
  



