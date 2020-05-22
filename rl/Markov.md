## Markov Processed

RL 에서 환경을 표현
environment
현재 state가 완전히 표현하는 것
모든 rl 은 mdp 형태로 만들 수 있음
상태들이 n 개 계속 state를 옮겨 가는 것 

## Markov Property

state가 아는 순간 history를 던질 수 있다 

## 

episode - 한번 어느 state 에서 시작해서 final terminal 까지 가는 것


## markov reward process

S,P,R,
S - state
P - state trasition matrix
R - reward function 정의를 내림
γ - 

##return

return 을 mixmizer 해야함

## why discount

수학적으로 편리 - 수렴성이 증명이 된다??

문제에 따라 discount 가 필요한 이유도 있고 아닌 경우도 있고

## value function

return 의 기대값

## bellman equation
- 시간복잡도 O(n**3)
- dynamic programming
- monte-carlo evaluation
- Temporal-Difference learning

선형대수학을 잘 해야한다

## MDP
(S,A,P,R,γ)

policy - state st에 있을 때 a 할 확률
MDP 

## value function 

- The state-value function V(s) of an MDP is the expected return starting from state s,
 - input state 하나만

- action-value function 
 - input state , action 두개
 

## Optimal value function

Optimal - 어떤 policy를 따를 때 그 중 제일 나은 것


## Optimal Policy

## solving
- bellman optimality equation is non-linear
- value iteration
- policy iteration
- q-learning
- sarsa


 
