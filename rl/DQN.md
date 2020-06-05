## DQN
#### Neural Network

- 학습과정 : 뉴럴 넷을 수정해 주는 과정
- 의도한 값 보다 뉴럴넷 아웃풋이 작으면 -> 아웃풋이 커지도록
- 의도한 값 보다 뉴럴넷 아웃풋이 크면 -> 아웃풋이 작아지도록


- 어떻게?
  - gradient descent(경사하강법)
- 결국 뉴럴넷에 정답을 새겨 넣는 것, 마치 테이블과 비슷
- TD 러닝

- 벨만 최적 방정식
 - action-value function 이 environment의 model을 몰라도 되므로 사용이 많이 됨
 - 현재 state의 value function은 다음 state의 discounted value function에 어떤 행동을 해서 받는 reward를 합한 것
 - expectation 이 붙은 것 , reward도 어떤 action을 취하는 지에 따라 다르고 도착하는 state 또한 달라짐


-리플레이 버퍼

-타겟 네트워크


DQN(Deep Q - Networks)
- Q-function 을 approximate 하는 dnn 

- 그 전에 agent는 env를 MDP르 통해 이해를 하는데 학습을 하려면 필요한 모든 state에 대한 action-value function 값을 저장하고
update 시켜나가야 하는데, 학습이 상당히 느려짐
따라서 approximation을 하고 그 방법 중 하나가 dnn이다

강화학습의 목표 - optimal policy를 구하는 것 , 
각 state에서 optimal한 action value function을 알고 있으면 q값이 큰 action을 취하면 되는 것,

