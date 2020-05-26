import gym
#import tensorflow
from gym.envs.registration import register
import sys
import readchar
'''

env = gym.make("FrozenLake-v0")
#환경 초기화
observation= env.reset()

for _ in range(1000):
    #env.render() 화면 출력
    env.render()
    #환경에 따른 action을 설정
    action = env.action_space.sample()
    #done = gameover인지 아닌지를 알려줌
    #info = 추가정보가 있을때 추가정보를 알려줌
    observation,reward,done,info = env.step(action)
'''

LEFT =0
DOWN =1
RIGHT =2
UP =3

#코드를 입력받으면 action을 취한다
arrow_keys={
    '\x1b[A':UP,
    '\x1b[B':DOWN,
    '\x1b[C':RIGHT,
    '\x1b[D':LEFT,
}

register(
    id = "FrozenLake-v3",
    entry_point ="gym.envs.toy_text:FrozenLakeEnv",
    kwargs = {"map_name" : "4x4","is_slippery" : False}
)

env = gym.make("FrozenLake-v3")
env.render()

while True:
    key= readchar.readkey()
    print()
    #화살표가 아닌 다른 key를 누르면 출력하도록
    if key not in arrow_keys.keys():
        print("Game aborted")
        break

    action = arrow_keys[key]
    state, reward , done, info = env.step(action)
    #env.render()
    print(f"State:{state}, Action:{action},Reward: {reward},info: {info}")
    

    if done:
        print("Finished with reward", reward)
        break
