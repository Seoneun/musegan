# MuseGAN

기존 모델 성능 지표
악기 | #empty bar | #pitch used | #qualified | #tone distance
--- | --- | --- | --- |--- 
Drums | #1 | #2 | #3 | #4 
Piano | #1 | #2 | #3 | #4 
Guitar | #1 | #2 | #3 | #4 
Bass | #1 | #2 | #3 | #4 
Ensemble | #1 | #2 | #3 | #4 
Reed | #1 | #2 | #3 | #4 
Synth Lead | #1 | #2 | #3 | #4 
Synth Pad | #1 | #2 | #3 | #4 

# Data Augmentation


# (1) 노트를 다른 악기에 반복
랜덤하게 악기에서 나오는 마디를 다른 악기에도 연주를 하게끔 데이터를 증강함

# (2) 노트의 길이(Time stamp)를 늘림
노트의 길이를 랜덤하게 늘려 데이터를 증강함

# (3) 노트를 잘라 노트의 개수를 늘림
노트의 길이를 기준으로 노트의 개수를 늘려 데이터를 증강함

# 학습률 및 Optimizer 최적화

# (1) lr=0.0001
학습률을 기존의 20분의 1 수준으로 학습

# (2) lr=0.001
학습률을 기존의 2분의 1 수준으로 학습

# (3) Rmsprop
기존의 Adamm Optimizer에서 Rmsprop로 바꾸어 
