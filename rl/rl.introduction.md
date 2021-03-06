## 강화학습

## 1. 특징
- 다른 학습 방법과는 다르게 superviser가 없다
- reward 를 mixmization 하는 방법
- optimal해에 도달하려고 한다
- 피드백(reward)이 늦어질 수 있다. 즉각적인 보상을 얻기가 힘들 수 있다.

3.시간이 중요하다 ( 순서가 있는 squencial data)
4.agent's action 이 그 이후에 받게되는 data에 영향을 받음
 
## 2.강화학습의 예시
atari 게임 만들기

## 3.Reward(R_t)

reward 는 scalar(숫자 하나)

agent 목적 - cumulate reward를 최대화 하는 것이 목적 
reward hypothsis 축적된 reward를 극대화하는 것을 목적으로 될 수 있다


## 4.Sequential Decision Making

- 미래의 받을 reward의 총합을 극대화 하는게 목적
- 한번 action을 했는데 결과가 즉각적으로 안 올 수 있다(long term이 발생할 수 있음) 
 - ex) chess 퀸을 잡기 위해 졸을 하나를 포기한다(더 나중 미래를 위해 길게봐야함) 

## Agent & Environment

agent(A_t) - 학습할 개체
observation(O_t) - action 으로 인한 변환된 상황

-`agent` 가 `action(A_t)`을 하면 `environment`가 `reward(R_t)`와 `observation(O_t)`을 주고
`agent`는 `R_t`와 `O_t` 를 받고 다음 `A_t`을 한다
-time_step 
- `agent`는 `A_t`하고 `O_t`받고 `R_t` 받고 `environment`는 각 time step마다 `A_t` 받아서 `O_t`를 뱉어준다

## history & state
 
- H[]= O_t,R_t,A_t
- history agent가 한 것들을 쭉 적용
- 그 다음에 일어날 일은 history에 의해 결정
- agent 는 history를 보고 action을 하고
- environment는 action을 받고 observation을 방출해 주고  
- state(S_t) - 다음에 뭘할지 결정하기 위해 쓰이는 정보들(history의 function) 
 - state : 다음에 쓰일 정보의 모든것

## environment state
- environment state - Se_t : 
보이지 않는 부분


## agent state
agent - 내가 다음 action을 하는데 필요한 정보들

## Marcov state 

- P[S_t+1|S_t] = P[S_t+1|S_1....S_t]
- `S_t`가 `S_t+1`로 될 확률이 `S_1+...S_t`가 `S_t+1`될 확률이면 state는 marcov하다
- 오직 현재 state만 미래에 영향을 준다 

 ## fully observable environments
 - environmet를 볼수 있을 상황일때
 - MDP(marcov decision process)
 
 
 
 ## patially observable environments
 - 현재 agent state != environment state
 - POMDP(patially observable MDP)
 - agent는 state 표현형을 구축해야 한다?
  - RNN을 사용할 수 도 있음
  - state 표현하는 방법은 여러개로 표현 할 수 있다
 
 ## Policy
 
 - agent의 행동을 규정ㅋ
 - state를 넣어주면 action을 보냄
 - Deterministic policy :a= π(s)
  - S를 넣어주면 Action 하나를 결정적으로 정해줌
 - Stochastic policy π(a|s) = P[A_t=a|S_t=s]
  - S를 넣어주면 여러 Action들중 확률로 하나를 정해줌
 
 -policy value function
  - π(a|s) = P[A_t=a|S_t=s]
  - 상태 s에서 액션 a를 선택할 확률
  - 상태가 s일때 a를 선택할 확률
 
 -state value function
  -ν_π(s) = E_π[G_t|S_t=s]
  - 상태 s부터 π를 따라서 움직일 때 리턴의 기대값
  - E = 기대값
 
 - action value function
  - q_π(s,a) = E_π{G_t|S_t= s, A_t =a} 
 
 ## markov definition process 
 
 - 상태의 집합 S
  - 가능한 상태 들을 모두 모아놓은 집합
  - MP=(S,P) 
  
  - 전이확률 정렬 P
  P_ss' 상태 s에서 다음상태가 s'가 될 확률
  
 - P[S_t+1|S_t] = P[S_t+1|S_1,S_2....S_t]
 
 ## MRP
 
 - 상태의 집합 S
 - 전이확률 정렬 P
 - 보상 함수 R
  - 어떤 상태 s에 도착했을 때 받게 되는 보상을 의미
  - R =E[R_t |S_t =s]
  
 - 감쇠인자 (discount factor)
   - 0에서 1사이의 숫자
   - 보상의 값에 곱하여 미래의 보상을 작게 만드는 역할
   - G_t = R_t + γR_t+1 +γ**2*R_t+2+....
   
   - 감마가 필요한 이유
    - 수학적 편리성( 수가 무한대로 증가할 수 있어서)
     - time-step 마다 agent는 0.1 reward를 받아도 1 reward를 받아도 무한대이면 계속 무한대임
     - episode의 처음과 끝의 reward가 같으면 두 상황 중 어떤 경우가 더 나은지 판단하기 힘듦
    - 사람의 선호 반영
    - 미래에 대한 불확실성 반영
    - 실제 시스템이 그러한 경우가 있음 ex) 이자
    
 - MRP의 가치함수(value function)
  - 상태 s로 부터 시작하여 에피소드가 끝날 때 까지 얻는 리턴(감쇠된 누적보상)의 기댓값
 
 - agent의 행동을 규정
 - state 를 넣어주면 action을 넣어주는 mapping 역할
 - 보통 파이로 표시 - 
 - Deterministic policy -   s하나를 넣어주면 action 하나가 결졍적으로 정해짐
 
 - Stochastic policy -  하나를 던져주면 여러 action이 가능한데 확률에 따라 픽해서 action 하나가 선택됨
    
## MDP
- MDP Ξ(S,A,P,R,γ)

- 상태의 집합 S
- 전이 확률 행렬 P
 -Pa_ss' - a : 액션 a를 선택했을 때 상태 s에서 다음 상태가 s'이 될 확률

- 액션의 집합 A
- 보상함수 R
 - Ra_s = E[R_t+1|S_t=s , A_t =a]

## bellman function
- 가치 함수는 두 파트로 나눠 생각할 수 있다
 - 즉각적인 보상 R_t+1
 - 다음 상태의 가치 γ*ν_π(s_t+1)

 - MDP를 풀때 사용하는 방정식
 <br>
 - state value function
  - v(s) 
   - = E[G_t|S_t =s]
   - = E[R_t+1+γ*v(s_t+1)|s_t = s]
   - = E(기대값)이 있어야 된다

- action value function
 - q_π(s,a) = E_π{R_t+1 +γ*q_π(s_t+1,A_t+1) |S_t= s, A_t =a}
 
##bellman 최적 function

- 최적의 가치 함수
 - q_* (s,a) = max*q_π(s,a) 
 - 너가 할 수 있는 정책중에 최적의 value 값
 - q_* 를 알게 된 순간 우리는 optimal 하게 행동 할 수 있다
 
 - q_* (s,a) = E_s[r + γmaxq_*(s,a) ]
 
## value Function

- 상황이 얼마나 좋은지 알려줌(총 받을 미래 reward를 기대값
- 현재 state가 좋은지 안좋은지 판단
확률이 ev자체도 확률성이 있을수 있다 그래서 꼭 기대값을 넣어주어야 한다

## Model

- model - environment가 어떻게 될지 prediction 하는 것
 - reward를 예측
 - 그다음 state를 예측
- P_ss'=P[S_t+1 = s'|S_t s,A_t=a]

- model based(model을 사용할때)
- model free(model을 사용하지 않을때)
  
 
## 몬테 카를로 방법론
 - MC 는 경험으로부터 직접 배우는 방법론
 - MC 는 mdeol -free 방법론
  - MDP의 상태 전이나 보상 함수에 관한 지식이 전혀 필요없음
  
 - MC 는 완전한 에피소드로부터 배움
- 정책 π를 이용해 얻은 에피소드들로 부터 가치 함수 v_π학습하기
 - S1,A1,R2 .... ~π
- 리턴이 누적된 보상의 합임을 기억
 - G_t = R_t + γR_t+1 +γ**2*R_t+2+....
- 가치 함수는 미래에 얻을 보상의 기대값
 - ν_π(s) = E_π[G_t|S_t=s]
 
## every-visit 몬테카를로 가치 평가법
- 상태 s의 가치를 평가하기 위해서 에피소드 안에서 상태 s를 방문할 때 마다
- 카운터를 증가시키고   N(s) <- N(s)+1
- 총 리턴값도 증가시키고 S(s) < - S(s) + G_t
- 가치는 그 평균으로 계산함 V(s) = S(s)/N(s)  
- N(s) -> ∞이면 V(s) -> v_π(s)
 
## 각 방법론의 특징
- TD 는 최종 결과를 알기 전에 학습할 수 있다
 - TD는 매 스탭마다 온라인ㄴ으로 학습할 수 있음
 - 반면 MC는 에피소드가 끝나서 리턴을 알게 될 때 까지 기다려야 함

- MC : Vπ(s_t) = E[G_t]
- TD : Vπ(s_t) = E[r_t+1 + γVπ(s_t+1]

- Bias
 - 리턴 G_t 는 가치함수 
 
- Variance
 - TD 타겟은 리턴보다 variance가 훨씬 작음
 - 리턴은 수많은 액션,트랜지션,보상과 관련이 되지만 TD 타켓은 한 개의 액션,트랜지션,보상과 관련이 있기 때문


## RL 분류

#### value based
- value fuction 만 있는 경우

#### policy based
- policy 만 가지고 있는 경우

#### actor critic
-value와 policy를 둘다 학습한 경우

#### Model Free
- model을 만들지 않는것 , policy or value 만 갖고

#### Model Based
- 환경을 어떻게 동작하는애다

## learning & planning

- 

## exploitation & exploration

- exploitation 
 - go to your favourite restaurant
 - 아는 것을 바탕으로 최선을 다 하는 것
- exploration 
 - Try a new restaurant
 - 정보를 더 얻고자 새로운 모험을 하는 것

##prediction and control

- prediction - 평가하는것
 - value fuction 을 잘 학습시킨다
 
 -control - 미래를 최적화한다
  -best policy를 찾는다
  
## 추가 모르는 개념

- 스칼라 : 방향의 구별이 없고 하나의 수치로 정해지는 양
 - 온도, 길이 ,속력

- 벡터 : 수치값과 방향성이 있어야 완전하게 표시할 수 있는 양
 - 속도, 힘, 변위




