## 강화학습

##1. 특징
superviser가 없다

reward 를 mixmization 하는 방법

optimal
2.피드백이 늦어질 수 있다.
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
 
 - agent의 행동을 규정
 - state 를 넣어주면 action을 넣어주는 mapping 역할
 - 보통 파이로 표시 - 
 - Deterministic policy -   s하나를 넣어주면 action 하나가 결졍적으로 정해짐
 
 - Stochastic policy -  하나를 던져주면 여러 action이 가능한데 확률에 따라 픽해서 action 하나가 선택됨
    
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

- exploitation - go to your favourite restaurant
- exploration - Try a new restaurant

##prediction and control

- prediction - 평가하는것
 - value fuction 을 잘 학습시킨다
 
 -control - 미래를 최적화한다
  -best policy를 찾는다



