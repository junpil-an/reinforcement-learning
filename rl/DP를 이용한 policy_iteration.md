## dynamic 프로그래밍

DP로 벨만 기대 방정식을 푸는 것이 policy iteration , 벨만 최적 방정식을 푸는 것이 가치 iteration

- policy iteratin
  - 벨만 기대 방정식 사용 

- value iteration
  - 벨만 최적 방정식 사용
- policy evaluation
  - true value 를 구하기 어려우니 iteration을 반복하며 점점 true value값에 도달하는 것



강화학습은 순차적으로 행동을 결정해야 하는 문제를 푸는 방법 중 하나

- 순차적 행동 문제를 MDP로 전환한다
- 가치함수를 벨만 방정식으로 반복적으로 계산한다
  - ![사진](https://raw.githubusercontent.com/zoomKoding/zoomKoding.github.io/source/assets/_posts/RL1-16.png)
- 최적 가치함수 & 최적 정책을 찾는다



DP 는 큰 문제 안에 작은 문제들이 중첩된 경우 , 전체 큰 문제를 작은 문제로 쪼개서 풀겠다

이 계산은 모든 상태에 대해 하며 한 번 계산이 끝나면 모든 상태의 가치함수를 업데이트 함



## policy iteration

- policy iteration 과 value iteration 은 후에 살사로, 살사는 off-policy로 변형되어 q-learning으로 이어짐

- policy는 모든 state에서 어떻게 action할 지에 대한 정보
- 우리가 얻고자 하는 policy는 random이 아님, 현재 policy를 평가하고 발전시켜야 함
  - policy evaluation
  - policy imporvement

<br>

- 정책 평가들을 기준으로 더 나은 정책으로 점점 더 발전시킴
- policy에 대한 평가는 value function으로 판단할 수 있음
  - ![가치함수](https://raw.githubusercontent.com/zoomKoding/zoomKoding.github.io/source/assets/_posts/RL1-13.png)

- 현재 정책에 따라 평가

- 핵심 주변 상태의 value fuction과 한 time step의 reward만 고려해서 현 state의 다음 value function을 계산 하겠다

<br>

- DP에서 agent는 evironment의 모든 정보를 알고 있음, 이 정보를 통해 최적 정책을 찾는  계산

- policy evaluation은 여러 번에 걸쳐서 해야 정확한 value function을 얻을 수 있다
