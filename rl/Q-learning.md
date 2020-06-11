## Q-learning

- offpolicy - 현재 행동하는 policy와 독립적으로 학습한다, 행동하는 정책과 학습하는 정책을 따로 분리한다

![사진](https://wikimedia.org/api/rest_v1/media/math/render/svg/8158847df27c65c1ecb2fde471c62f197f3d6738)

- 실제 다음 상태 s_t+1에서 다음 행동을 해보는 것이 아니라 , 다음 상태 s_t+1에서 가장 큰 Q함수를 가지고 업데이트를 하는 것

- 벨만 최적 방정식을 사용

- 실제 환경에서 행동하는 정책과 Q함수를 업데이트할 때 사용하는 정책이 다름
  - 행동 선택 - e- 탐욕정책
  - 업데이트 - 벨만 최적 방정식

- 살사와 Q-learning의 차이
  - onpolicy, offpolicy의 차이, onpolicy는 지속적인 탐험 때문에 구석에 갇힐 수가 있음
  - offpolicy는 큐함수의 max값으로 업데이트하기 때문에 갇히지 않고 벗어나는 정책을 학습