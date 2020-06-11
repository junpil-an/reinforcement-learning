## sarsa

- 흐름도 상 policy iteration 과 value iteration이 sarsa로 발전함

- GPI(generalized policy iteration) : 정책 평과 가정에서 참 가치함수에 수렴할 때 까지 정책발전과 번갈아 가면서 실행하는 것
  - 주어진 가치함수에 대해 새로운 정책을 얻는 과정
- 시간차 방법, 타임스텝마다 가치함수를 업데이트함
- 가치 이터레이션에서는 정책 이터레이션과는 달리 별도의 policy없이 단지 가치함수에 대해 탐욕적으로 움직임
  - 시간차 예측 + 탐욕 정책 - 시간차 제어(temporal-difference control)
  - 시간차 제어에서는 [S_t,A_t,R_t+1,S_t+1,A_t+1]을 샘플로 사용
  - `S_t`에서 탐욕 정책에 따라 `A_t`를 하고 환경은 `R_t+1`을 주고 다음 상태 `S_t+1`을 알려줌
  - agent는 탐욕 정책에 따라 `A_t+1` 하고 하나의 샘플이 완성되면 큐 함수를 업데이트
- 초기 탐욕 정책은 잘못된 학습으로 가게 할 가능성이 큼 , 따라서 충분히 다양한 경험을 하게 만들어야 함
- epsilon 만큼 탐욕적이지 않은 정책을 실시(가장 큰 큐함수를 가지는 행동을 선택)
  - epsilon 탐욕 정책은 에이전트가 지속적으로 탐험하게 함

<br>

- 살사 정리
  - epsilon greedy policy sample[S_t,A_t,R_t+1,S_t+1,A_t+1]
  - 획득한 샘플로 다음 식을 통해 큐함수 업데이트
- 살사 한계  - onpolicy temporal-difference control,
  - 자신이 행동하는대로 학습하는 시간차 제어
  - 탐험을 위해 선택한 e - 탐욕정책 때문에 agent는 최적 정책을 학습하지 못하고 잘못된 정책을 학습
  - 이 것을 해결하기 위해 사용 - `offpolicy temporal difference control(Q-learning)`을 사용

