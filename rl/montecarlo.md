- DP 의 한계 환경에 대한 정확한 지식을 가지고 모든 상태에 대해 동시에 계산을 진행
- 정책 이터레이션에서 정책 평가는 현재 정책을 따랐을 때 참 가치함수를 구하는 과정
  - 강화학습에서는 에측(prediction)이라고 함
- DP에서 정책 평가와 정책 발전을 합친 것을 정책 이터레이션이라고 함
  - 강화학습에서는 예측과 함께 발전시키는 것을 제어(control)이라고 부름

## 몬테카를로 근사

- 몬테카를로 - 무작위로 무언가를 해본다

- 근사 - 원래 값은 모르지만 샘플을 통해 원래값을 추정

- 몬테카를로 근사 특성 

  - 무한히 반복했을 떄 원래의 값과 동일해 진다는 점

  - 방정식을 몰라도 원래 값을 추정할 수 있다

<br>

- 가치함수 추정할 때는 에이전트가 한 번 환경에서 에피소드를 진행하는 것이 샘플링
- 몬테카를로 예측 - 샘플링을 통해 얻은 샘플의 평균으로 참 가치함수의 값을 추정

- 샘플링 + 평균 -> 가치함수 추정

- 가치함수 - 현재 상태로부터 받을 보상을 시간별로 할인해서 더한 다음 기대값을 계산

- 효율적이라도 정책 이터레이션 기대값을 계산
- 현재 정책에 따라 행동을 하면 보상을 받음

<br>

S로부터 마침 상태 T까지 에피소드

몬테카를로 예측을 하기 위해서는 각 상태의 반환값들이 많이 모여야 함

각 상태에 대해 모인 반환값들의 평균을 통해 참 가치함수의 값을 추정

- 이동평균 - 시간에 따라 평균을 업데이트 해나가는 것



- 몬테카를로 vs temporal differ
  -  value function을 평가하는 시기
    - 몬테카를로 - episode가 끝날 때 마다
    - temporal differ - time-step 마다 한 단계씩 update
  - state들의 value function을 얻는 법
    - 몬테카를로 - terminal state까지 step별로 얻은 reward를 저장 한 후 terminal state에서는 이를 바탕으로 state들의 value function을 구함

## 몬테카를로 예측

- 한 episode를 마치고 얻은 return들의 평균값, value function을 근사하고 이를 반복해서 true value를 찾자는 아이디어
- 여러 episode를 진행하며 해당 state를 지나가는 episode에서 retrun값들을 모두 구해서 산술평균을 내줌

![사진](https://t1.daumcdn.net/cfile/tistory/99409F465A4A167736)

N(s) - 총 episode 동안 state s를 방문한 횟수

G_i(s) - episode i 에서 state s 에 대한 returna 

![사진](https://t1.daumcdn.net/cfile/tistory/99CB534B5A4A1D852F)

1/n - step-size

(G_n - V_n) - 오차

- 이 업데이트 식을 통해 에피소드 동안 경험한 모든 상태에 대해 가치함수를 업데이트함

#### First-visit MC or Every visit MC

- 중복 방문에 대한 return 값을 처리하는 방식에 따라 나뉨
- first-visit MC 는 첫 번째 방문했을 때의 return값만 취함 , 두번째 이후는 고려 x
- every-visit MC 방문 할때마다 계속 return값을 바꿔줌

#### 몬테카를로 Control

policy iteration = policy evaluataion + policy improvement



value function의 model-based

local optimum



MC를 이용하는 것 model-free
