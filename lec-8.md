# Lecture 8. Deep RL with Q-Functions
- p3: online Q-iteration algorithm에서 3 라인이 gradient descent가 맞는지?
  -  $L=\frac{1}{2}(Q_\phi-y)^2$
  -  $\frac{\partial L}{\partial \phi} =$
     $(Q_\phi-y)(\frac{\partial Q_\phi}{\partial \phi}-\frac{\partial y}{\partial \phi})$
  -  슬라이드에는 $\frac{\partial y}{\partial \phi}$ 항이 빠져있음 (semi-gradient method?)
- p3: "no gradient through target value"가 무슨 뜻인지?
- p4: correlated samples이 왜 문제가 되는지? 학습에 어떤 영향을 주는지?
- p11: target network를 가지는 Q-learning에서 N과 K의 차이는?
  - N은 데이터 수집하고 리플레이 버퍼에 저장하는 횟수
  - K는 리플레이 버퍼에서 데이터 샘플링하는 횟수


     
