# MuseGAN

기존 모델 성능 지표
악기 | Empty bar | Pitch used | Qualified | Tone distance
--- | --- | --- | --- |--- 
Drums | 0.0000 | 7.1406 | None | None
Piano | 0.0156 | 8.5635 | 0.3076 | 1.12761
Guitar | 0.4141 | 7.6133 | 0.5699 | 1.12761
Bass | 0.0234 | 4.4560 | 0.5812 | None
Ensemble | 0.0000 | 5.8438 | 0.5090 | None
Reed | 0.6953 | 3.6923 | 0.5962 | None
Synth Lead | 0.7734 | 5.0000 | 0.5748 | None
Synth Pad | 0.9141 | 6.3636 | 0.6739 | None

# Data Augmentation

# (1) 노트를 다른 악기에 반복
랜덤하게 악기에서 나오는 마디를 다른 악기에도 연주를 하게끔 데이터를 증강함

모델 성능 지표
악기 | Empty bar | Pitch used | Qualified | Tone distance
--- | --- | --- | --- |--- 
Drums | 0.0312 | 11.0242 | None | None
Piano | 0.0156 | 9.9603 | 0.4843 | 0.57163
Guitar | 0.0156 | 10.0317 | 0.5166 | 0.57163
Bass | 0.0156 | 11.1587 | 0.5359 | None
Ensemble | 0.0156 | 11.6508 | 0.5461 | None
Reed | 0.0000 | 11.0312 | 0.5287 | None
Synth Lead | 0.0156 | 11.4603 | 0.5204 | None
Synth Pad | 0.0156 | 11.8571 | 0.4731 | None

# (2) 노트의 길이(Time stamp)를 늘림
노트의 길이를 랜덤하게 늘려 데이터를 증강함

모델 성능 지표
악기 | Empty bar | Pitch used | Qualified | Tone distance
--- | --- | --- | --- |--- 
Drums | 0.0000 | 7.1406 | None | None
Piano | 0.0156 | 8.5635 | 0.3076 | 1.12761
Guitar | 0.4141 | 7.6133 | 0.5699 | 1.12761
Bass | 0.0234 | 4.4560 | 0.5812 | None
Ensemble | 0.0000 | 5.8438 | 0.5090 | None
Reed | 0.6953 | 3.6923 | 0.5962 | None
Synth Lead | 0.7734 | 5.0000 | 0.5748 | None
Synth Pad | 0.9141 | 6.3636 | 0.6739 | None

# (3) 노트를 잘라 노트의 개수를 늘림
노트의 길이를 기준으로 노트의 개수를 늘려 데이터를 증강함

모델 성능 지표
악기 | Empty bar | Pitch used | Qualified | Tone distance
--- | --- | --- | --- |--- 
Drums | 0.0000 | 7.1406 | None | None
Piano | 0.0156 | 8.5635 | 0.3076 | 1.12761
Guitar | 0.4141 | 7.6133 | 0.5699 | 1.12761
Bass | 0.0234 | 4.4560 | 0.5812 | None
Ensemble | 0.0000 | 5.8438 | 0.5090 | None
Reed | 0.6953 | 3.6923 | 0.5962 | None
Synth Lead | 0.7734 | 5.0000 | 0.5748 | None
Synth Pad | 0.9141 | 6.3636 | 0.6739 | None

# 학습률 및 Optimizer 최적화

# (1) lr=0.0001
학습률을 기존의 20분의 1 수준으로 학습

모델 성능 지표
악기 | Empty bar | Pitch used | Qualified | Tone distance
--- | --- | --- | --- |--- 
Drums | 0.0000 | 7.1406 | None | None
Piano | 0.0156 | 8.5635 | 0.3076 | 1.12761
Guitar | 0.4141 | 7.6133 | 0.5699 | 1.12761
Bass | 0.0234 | 4.4560 | 0.5812 | None
Ensemble | 0.0000 | 5.8438 | 0.5090 | None
Reed | 0.6953 | 3.6923 | 0.5962 | None
Synth Lead | 0.7734 | 5.0000 | 0.5748 | None
Synth Pad | 0.9141 | 6.3636 | 0.6739 | None

# (1-1) lr=0.0001, 노트반복
학습률을 기존의 20분의 1 수준으로 학습

모델 성능 지표
악기 | Empty bar | Pitch used | Qualified | Tone distance
--- | --- | --- | --- |--- 
Drums | 0.0000 | 7.1406 | None | None
Piano | 0.0156 | 8.5635 | 0.3076 | 1.12761
Guitar | 0.4141 | 7.6133 | 0.5699 | 1.12761
Bass | 0.0234 | 4.4560 | 0.5812 | None
Ensemble | 0.0000 | 5.8438 | 0.5090 | None
Reed | 0.6953 | 3.6923 | 0.5962 | None
Synth Lead | 0.7734 | 5.0000 | 0.5748 | None
Synth Pad | 0.9141 | 6.3636 | 0.6739 | None


# (1-2) lr=0.0001, 노트 늘리기
학습률을 기존의 20분의 1 수준으로 학습

모델 성능 지표
악기 | Empty bar | Pitch used | Qualified | Tone distance
--- | --- | --- | --- |--- 
Drums | 0.0000 | 7.1406 | None | None
Piano | 0.0156 | 8.5635 | 0.3076 | 1.12761
Guitar | 0.4141 | 7.6133 | 0.5699 | 1.12761
Bass | 0.0234 | 4.4560 | 0.5812 | None
Ensemble | 0.0000 | 5.8438 | 0.5090 | None
Reed | 0.6953 | 3.6923 | 0.5962 | None
Synth Lead | 0.7734 | 5.0000 | 0.5748 | None
Synth Pad | 0.9141 | 6.3636 | 0.6739 | None

# (2) lr=0.001
학습률을 기존의 2분의 1 수준으로 학습

모델 성능 지표
악기 | Empty bar | Pitch used | Qualified | Tone distance
--- | --- | --- | --- |--- 
Drums | 0.0000 | 7.1406 | None | None
Piano | 0.0156 | 8.5635 | 0.3076 | 1.12761
Guitar | 0.4141 | 7.6133 | 0.5699 | 1.12761
Bass | 0.0234 | 4.4560 | 0.5812 | None
Ensemble | 0.0000 | 5.8438 | 0.5090 | None
Reed | 0.6953 | 3.6923 | 0.5962 | None
Synth Lead | 0.7734 | 5.0000 | 0.5748 | None
Synth Pad | 0.9141 | 6.3636 | 0.6739 | None

# (2-1) lr=0.001, 노트 반복
학습률을 기존의 2분의 1 수준으로 학습

모델 성능 지표
악기 | Empty bar | Pitch used | Qualified | Tone distance
--- | --- | --- | --- |--- 
Drums | 0.0000 | 7.1406 | None | None
Piano | 0.0156 | 8.5635 | 0.3076 | 1.12761
Guitar | 0.4141 | 7.6133 | 0.5699 | 1.12761
Bass | 0.0234 | 4.4560 | 0.5812 | None
Ensemble | 0.0000 | 5.8438 | 0.5090 | None
Reed | 0.6953 | 3.6923 | 0.5962 | None
Synth Lead | 0.7734 | 5.0000 | 0.5748 | None
Synth Pad | 0.9141 | 6.3636 | 0.6739 | None

# (2-2) lr=0.001, 노트 늘리기
학습률을 기존의 2분의 1 수준으로 학습

모델 성능 지표
악기 | Empty bar | Pitch used | Qualified | Tone distance
--- | --- | --- | --- |--- 
Drums | 0.0000 | 7.1406 | None | None
Piano | 0.0156 | 8.5635 | 0.3076 | 1.12761
Guitar | 0.4141 | 7.6133 | 0.5699 | 1.12761
Bass | 0.0234 | 4.4560 | 0.5812 | None
Ensemble | 0.0000 | 5.8438 | 0.5090 | None
Reed | 0.6953 | 3.6923 | 0.5962 | None
Synth Lead | 0.7734 | 5.0000 | 0.5748 | None
Synth Pad | 0.9141 | 6.3636 | 0.6739 | None

# (3) Rmsprop
기존의 Adamm Optimizer에서 Rmsprop로 바꾸어 학습

모델 성능 지표
악기 | Empty bar | Pitch used | Qualified | Tone distance
--- | --- | --- | --- |--- 
Drums | 0.0000 | 7.1406 | None | None
Piano | 0.0156 | 8.5635 | 0.3076 | 1.12761
Guitar | 0.4141 | 7.6133 | 0.5699 | 1.12761
Bass | 0.0234 | 4.4560 | 0.5812 | None
Ensemble | 0.0000 | 5.8438 | 0.5090 | None
Reed | 0.6953 | 3.6923 | 0.5962 | None
Synth Lead | 0.7734 | 5.0000 | 0.5748 | None
Synth Pad | 0.9141 | 6.3636 | 0.6739 | None

# (3-1) Rmsprop, 노트 늘리기
기존의 Adamm Optimizer에서 Rmsprop로 바꾸어 학습

모델 성능 지표
악기 | Empty bar | Pitch used | Qualified | Tone distance
--- | --- | --- | --- |--- 
Drums | 0.0000 | 7.1406 | None | None
Piano | 0.0156 | 8.5635 | 0.3076 | 1.12761
Guitar | 0.4141 | 7.6133 | 0.5699 | 1.12761
Bass | 0.0234 | 4.4560 | 0.5812 | None
Ensemble | 0.0000 | 5.8438 | 0.5090 | None
Reed | 0.6953 | 3.6923 | 0.5962 | None
Synth Lead | 0.7734 | 5.0000 | 0.5748 | None
Synth Pad | 0.9141 | 6.3636 | 0.6739 | None

# (3-2) Rmsprop, 노트 옮기기
기존의 Adamm Optimizer에서 Rmsprop로 바꾸어 학습

모델 성능 지표
악기 | Empty bar | Pitch used | Qualified | Tone distance
--- | --- | --- | --- |--- 
Drums | 0.0000 | 7.1406 | None | None
Piano | 0.0156 | 8.5635 | 0.3076 | 1.12761
Guitar | 0.4141 | 7.6133 | 0.5699 | 1.12761
Bass | 0.0234 | 4.4560 | 0.5812 | None
Ensemble | 0.0000 | 5.8438 | 0.5090 | None
Reed | 0.6953 | 3.6923 | 0.5962 | None
Synth Lead | 0.7734 | 5.0000 | 0.5748 | None
Synth Pad | 0.9141 | 6.3636 | 0.6739 | None

# (3-3) Rmsprop, 노트 
기존의 Adamm Optimizer에서 Rmsprop로 바꾸어 학습

모델 성능 지표
악기 | Empty bar | Pitch used | Qualified | Tone distance
--- | --- | --- | --- |--- 
Drums | 0.0000 | 7.1406 | None | None
Piano | 0.0156 | 8.5635 | 0.3076 | 1.12761
Guitar | 0.4141 | 7.6133 | 0.5699 | 1.12761
Bass | 0.0234 | 4.4560 | 0.5812 | None
Ensemble | 0.0000 | 5.8438 | 0.5090 | None
Reed | 0.6953 | 3.6923 | 0.5962 | None
Synth Lead | 0.7734 | 5.0000 | 0.5748 | None
Synth Pad | 0.9141 | 6.3636 | 0.6739 | None
