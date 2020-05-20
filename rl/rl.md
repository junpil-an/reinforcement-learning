## 강화학습

- 어떤 환경(Environment) 안에서 에이전트(Agent)가 현재의 상태(State)를 인식하여

보상(Reward)을 최대화하는 동작(Action)을 선택하는 방법


- 상태(state) : 현재 시점에서 상황이 어떤지 나타내는 값의 집합
	- state space : 가능한 모든 상태의 집합(S)
	- 특정 시각 t 에서의 상태값 s_t

- 행동(action) : 우리가 취할 수 있는 선택지
	- action space : 가능한 모든 행동의 집합(A)
	- 특정 시각 t 에서 상태 s_t를 본 뒤 취했던 행동은 a_t로 

- 보상(reward) : Agent가 어떤 행동을 했을 때 따라오는 이득
	- 보상값에 -1을 곱해서 비용(Cost)
	- -1을 곱하면 값이 낮을 수록 좋다

- 에이전트(Agent) : 주어진 문제 상황에서 행동하는 주체

- 정책(policy) : 에이전트가 판단하는 방식
	- 정책을 수학적으로 상태에 따른 행동의 조건부 확률 **P(actionalstate)**
	- 정책 중 가장 좋은 것을 optimal policy

- 환경(environment) : 문제 세팅 그 자체
	- Agent 가 취할 수 있는 행동
	- 그에 따른 게임 자체의 모든 규칙을 환경이라 함

- 강화학습의 환경이 Markov proporty 를 가짐

- s_t+1 과 r_t 는 s_t,a_t만의 함수, 
- 과거에 얻을 수 있는 필요한 정보는 이미 s_t에 담겨있음
- Deep Reinforvement learning 에서는 RNN 등을 추가해 과거 상태를 요약하는 벡터를 만들어
근사적으로 해결, RNN의 internal context vector 가 state space에 추가


## ex 

- 게임 상태 스크린샷 저장 시 
모든 정보가 현재 화면 스크린샷에 담겨 있기 때문에 Markov property를 만족하는 환경
- 배그같은 경우는 뒤쪽환경을 알 수 없기 때문에 Markov property를 만족하지 못함
<br>

- 초기상태(initial state) : Agent가 처음으로 환경과 상호작용할 때의 상태,시작화면

- 종료상태(terminal state) : 더 이상의 행동이 불가능한 상태

- 에피소드(episode) : 초기부터 종료까지 Agent가 거친 (상태,행동,보상)의 sequence



<br>
## 주의점

- 보상이 현재 상태,행동에 대한 즉각적인 값
- 누적 보상이 제일 높은 행동을 골라야 함 -> 가치함수
<br>

- 같은 알고리즘이라 할 지라도 보상 함수를 어떻게 정의하느냐에 따라 성능이 달라질 수 있음
- reward shaping : 어떻게 할당할 지 결정하는 것 

## 최종 정리

- 상태 s_t에서 행동 a_t를 취해 상태가 s_t+1로 바뀌면서 얻은 보상을 r_t라 함
- **`R : S x A x S -> R`**



## 강화학습 분야에서 자주 쓰이는 용어 & 개념

- 가치 함수

각 행동이 얼마나 가치 있는지 판단하기 위해 누적 보상 값을 예측할 수 있어야 함


















- 문제 정의 환경 / 문제 풀이 에이전트

## Gym 에서 제공하는 환경

- Classic control
- Algorithmic
- Atari
- Board games
- Box2D
- Toy Text
- Doom


OpenAI Gym 사용법

gym.Env를 상속받고

_reset , _step , _render 를 구현한다

## Agent method

- 에이전트는 아래와 같은 환경 method를 호출해 학습
- reset
- step
- render

## 틱택토(TicTacToe)

- 대전 보드 게임 ,두 에이전트
- 단순해 보이지만 개념을 잡는데 도움

- HumanAgent
- 사람이 렌더링 결과를 보고 숫자를 입력해 플레이
- 문제를 풀기 전 환경 파악
- 강화학습 에이전트 학습 후 검증에도 사용




- Gym형식을 따라 구현

- 참고 - 클래식 AI에서 틱택토
