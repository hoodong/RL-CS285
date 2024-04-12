# Lecture 8. Deep RL with Q-Functions
- p3. online Q-iteration algorithm에서 3 라인이 gradient descent가 맞는지?
  -  $L=\frac{1}{2}(Q_\phi-y)^2$
  -  $\frac{\partial L}{\partial \phi} =$
     $(Q_\phi-y)(\frac{\partial Q_\phi}{\partial \phi}-\frac{\partial y}{\partial \phi})$
  -  슬라이드에 $\frac{\partial y}{\partial \phi}$ 항이 빠져있음


     
