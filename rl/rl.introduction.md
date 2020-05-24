## 강화학습

## 1. 특징
- 다른 학습 방법과는 다르게 superviser가 없다
- reward 를 mixmization 하는 방법
-optimal
- 피드백(reward)이 늦어질 수 있다. 즉각적인 보상을 얻기가 힘들 수 있다.

- 스칼라 : 방향의 구별이 없고 하나의 수치로 정해지는 양
 - 온도, 길이 ,속력

- 벡터 : 수치값과 방향성이 있어야 완전하게 표시할 수 있는 양
 - 속도, 힘, 변위

3.시간이 중요하다 ( 순서가 있는 squencial data)
4.agent's action 이 그 이후에 받게되는 data에 영향을 받음

##2. 강화학습의 예시
fly stunt manoeuvres in a 
!(사진)[./img/]

##3. Reward

reward 는 scalar feedback signal  숫자 하나

agent 목적 - cumulate reward를 최대화 하는 것이 목적
reward hypothsis 축적된 reward를 극대화하는 것을 목적으로 될 수 있다


## 4.Sequential Decision Making

미래의 받을 reward를
long term 
gridy 하게 하면 안된다

## Agent & Environment

acgent - 학습할 아이
observation - action 으로 변환한 상황

## history & state

history agent가 한 것들을 쭉 적용
그 다음에 일어날 일은 history에 의해 결정
agent hsi
ev  his observation을 보내주고
state  다음에 뭘할지 결정하기 위해 쓰이는 정보들
ev observation 
state  : 다음에 쓰일 정보의 모든것

## environment state
보이지 않는 부분

## agent state
agent가 필요한 정보들

## 

어떤 state가 markov 하다 
 - 내가 결정을 할때 바로 이전 state만 의존해서 결정한다
 - the future is independent of the past given the present
 
 ## fully observable environments
 
 - MDP
 
 
 
 ## patially observable environments
 
 - POMDP
 - RNN을 사용할 수 도 있음
 - state 표현하는 방법은 여러개로 표현 할 수 있다
 
 ## Policy
 -policy value function
  - π(a|s) = P{A_t=a|S_t=s}
  - 상태 s에서 액션 a를 선택할 확률
  - 상태가 s일때 a를 선택할 확률
 
 -state value function
  -ν_π(s) = E_π{G_t|S_t=s}
  - 상태 s부터 π를 따라서 움직일 때 리턴의 기대값
  - E = 기대값
 
 - action value function
  -q_π(s,a) = E_π{G_t|S_t= s, A_t =a} 
 
 ## markov process definition
 
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
  - 어떤 상태 s에 도착했을 떄 받게 되는 보상을 의미
  - R =E[R_t |S_t =s]
  
  - 감쇠인자 (discount factor)
   - 0에서 1사이의 숫자
   - 보상의 값에 곱하여 미래의 보상을 작게 만드는 역할
   - G_t = R_t + γR_t+1 +γ**2*R_t+2+....
   
   - 감마가 필요한 이유
    - 수학적 편리성( 수가 무한대로 증가할 수 있어서)
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
   - = E{G_t|S_t =s}
   - = E{R_t+1+γ*v(s_t+1)|s_t = s}
   - = E(기대값)이 있어야 된다

- action value function
 - q_π(s,a) = E_π{R_t+1 +γ*q_π(s_t+1,A_t+1) |S_t= s, A_t =a}
 
##bellman 최적 function

- 최적의 가치 함수
 - q_* (s,a) = max*q_π(s,a) 
 - 너가 할 수 있는 정책중에 최적의 value 값
 - q_* 를 알게 된 순간 우리는 optimal 하게 행동 할 수 있다
 
 - q_* (s,a) = E_s{r + γmaxq_*(s,a) }
 
## value Function

-상황이 얼마나 좋은지 알려줌
- 현재 state가 좋은지 안좋은지 판단
확률이 ev자체도 확률성이 있을수 있다 그래서 꼭 기대값을 넣어주어야 한다

## Model

policy value model

model - 환경이 어떻게 될지 예측하는 것
 - reward를 예측
 - 그다음 state를 예측
 -
 
## RL 분류

#### value based
- value fuction 만 있는 경우

#### policy based
- policy 만 가지고 있는 경우

#### actor critic

#### Model Free
- model을 만들지 않는것 , policy or value 만 갖고

#### Model Based
- 환경을 어떻게 동작하는애다

## learning & planning

- 

## exploitation & exploration

- evironment 정보를 얻어 이해하는 과정 
- 최선의 선택을 하는 과정

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



