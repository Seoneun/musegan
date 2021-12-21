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
Drums | 0.1484 | 6.8991 | None | None
Piano | 0.6562 | 15.1136 | 0.5922 | 0.81706
Guitar | 0.3828 | 10.0253 | 0.5619 | 0.81706
Bass | 0.3359 | 4.1647 | 0.6699 | None
Ensemble | 0.5859 | 11.3774 | 0.5057 | None
Reed | 0.7656 | 8.6333 | 0.7444 | None
Synth Lead | 0.8047 | 8.3600 | 0.6257 | None
Synth Pad | 0.0000 | 1.8906 | 0.5135 | None

# (3) 노트를 잘라 노트의 개수를 늘림
노트의 길이를 기준으로 노트의 개수를 늘려 데이터를 증강함

모델 성능 지표
악기 | Empty bar | Pitch used | Qualified | Tone distance
--- | --- | --- | --- |--- 
Drums | 0.0625 | 71.0000 | None | None
Piano | 0.4141 | 52.7333 | 0.8744 | 0.35740
Guitar | 0.0312 | 52.3629 | 0.7626 | 0.35740
Bass | 0.1406 | 72.0182 | 0.8690 | None
Ensemble | 0.4453 | 55.8169 | 0.9080 | None
Reed | 0.3672 | 21.7778 | 0.6472 | None
Synth Lead | 0.6875 | 53.0250 | 0.5690 | None
Synth Pad | 0.7266 | 50.1429 | 0.4775 | None

# 학습률 및 Optimizer 최적화

# (1) lr=0.0001
학습률을 기존의 20분의 1 수준으로 학습

모델 성능 지표
악기 | Empty bar | Pitch used | Qualified | Tone distance
--- | --- | --- | --- |--- 
Drums | 0.0156 | 3.2222 | None | None
Piano | 0.5312 | 7.7333 | 0.4642 | 0.96167
Guitar | 0.0000 | 6.1406 | 0.5615 | 0.96167
Bass | 0.0312 | 3.0000 | 0.5365 | None
Ensemble | 0.3594 | 3.9268 | 0.5693 | None
Reed | 0.9062 | 3.5000 | 0.2400 | None
Synth Lead | 0.7500 | 1.8125 | 0.3498 | None
Synth Pad | 0.7344 | 5.6471 | 0.4872 | None

# (1-1) lr=0.0001, 노트반복
학습률을 기존의 20분의 1 수준으로 학습

모델 성능 지표
악기 | Empty bar | Pitch used | Qualified | Tone distance
--- | --- | --- | --- |--- 
Drums | 0.0312 | 2.6290 | None | None
Piano | 0.4375 | 4.6389 | 0.4450 | 1.26469
Guitar | 0.0938 | 6.5000 | 0.4448 | 1.26469
Bass | 0.0625 | 2.0000 | 0.3765 | None
Ensemble | 0.3906 | 4.9231 | 0.5354 | None
Reed | 0.6406 | 2.3478 | 0.5652 | None
Synth Lead | 0.7188 | 3.8333 | 0.2534 | None
Synth Pad | 0.7812 | 4.3571 | 0.4245 | None


# (1-2) lr=0.0001, 노트 늘리기
학습률을 기존의 20분의 1 수준으로 학습

모델 성능 지표
악기 | Empty bar | Pitch used | Qualified | Tone distance
--- | --- | --- | --- |--- 
Drums | 0.0000 | 6.7031 | None | None
Piano | 0.3125 | 14.4091 | 0.5014 | 1.17671
Guitar | 0.0625 | 4.3333 | 0.5066 | 1.17671
Bass | 0.0312 | 5.9194 | 0.4038 | None
Ensemble | 0.5165 | 4.9355 | 0.5455 | None
Reed | 0.5000 | 4.3125 | 0.5952 | None
Synth Lead | 0.7188 | 10.1667 | 0.4929 | None
Synth Pad | 0.6406 | 3.3043 | 0.4685 | None

# (2) lr=0.001
학습률을 기존의 2분의 1 수준으로 학습

모델 성능 지표
악기 | Empty bar | Pitch used | Qualified | Tone distance
--- | --- | --- | --- |--- 
Drums | 0.0625 | 4.8833 | None | None
Piano | 0.7188 | 13.1667 | 0.5847 | 1.03577
Guitar | 0.3281 | 7.8837 | 0.5338 | 1.03577
Bass | 0.0312 | 2.9032 | 0.4518 | None
Ensemble | 0.5156 | 5.6774 | 0.3490 | None
Reed | 0.4688 | 2.4706 | 0.7331 | None
Synth Lead | 0.9219 | 6.8000 | 0.7754 | None
Synth Pad | 0.7500 | 7.1250 | 0.5637 | None

# (2-1) lr=0.001, 노트 반복
학습률을 기존의 2분의 1 수준으로 학습

모델 성능 지표
악기 | Empty bar | Pitch used | Qualified | Tone distance
--- | --- | --- | --- |--- 
Drums | 0.0000 | 7.9688 | None | None
Piano | 0.6719 | 10.3810 | 0.6317 | 1.14072
Guitar | 0.4219 | 7.1351 | 0.4959 | 1.14072
Bass | 0.0156 | 2.0159 | 0.6477 | None
Ensemble | 0.5312 | 7.4667 | 0.4331 | None
Reed | 0.6875 | 4.5000 | 0.6324 | None
Synth Lead | 0.7031 | 3.0526 | 0.6670 | None
Synth Pad | 0.7500 | 6.0625 | 0.7254 | None

# (2-2) lr=0.001, 노트 늘리기
학습률을 기존의 2분의 1 수준으로 학습

모델 성능 지표
악기 | Empty bar | Pitch used | Qualified | Tone distance
--- | --- | --- | --- |--- 
Drums | 0.0625 | 7.7833 | None | None
Piano | 0.5938 | 11.5769 | 0.6634 | 0.74388
Guitar | 0.0156 | 8.6508 | 0.4675 | 0.74388
Bass | 0.0781 | 3.6949 | 0.6204 | None
Ensemble | 0.6094 | 11.0000 | 0.5925 | None
Reed | 0.8750 | 9.6250 | 0.7401 | None
Synth Lead | 0.4688 | 3.6765 | 0.5178 | None
Synth Pad | 0.8594 | 13.3333 | 0.6763 | None

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
