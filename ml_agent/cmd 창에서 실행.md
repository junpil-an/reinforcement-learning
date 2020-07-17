
#### anaconda prompt 창에서 실행

- mlagent-learn --train --slow trainer_config.yaml

- mlagent-learn --train --run-id="저장 이름" trainer_config.yaml

#### 이전 학습 이어서 실행

- mlagent-learn --train --run-id="저장 이름" trainer_config.yaml --load

#### 텐서보드 창 열고 훈련 정보 확인

- tensorboard --logdir=results --port=6006
