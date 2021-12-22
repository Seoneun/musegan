# 2021-2 데이터캡스톤디자인
# 주제: MuseGAN 모델 성능 향상

# MuseGAN
 - 다성악을 만드는 GAN 모델, 다성악을 만드는 여타 다른 작곡 AI와는 다르게 시계열 데이터를 사용하여 작곡하는 것이 아닌 악기 간의 조화를 중시하며 곡을 작곡하는 AI 모델입니다.
 - 이번 모델에서 사용한 악기
 - Drums, Piano, Guitar, Bass, Ensemble, Reed, Synth Lead, Synth Pad
 - 논문에서 제시한 모델: Jamming Model, Composer Model, Hybrid Model
 - Jamming Model: 즉흥으로 곡을 생성하는 방식에서 고안된 모델입니다. 각 악기마다 각자의 잠재벡터를 가지고 곡을 생성하는 모델입니다.
 - Composer Model: 작곡가가 곡을 생성하는 방식에서 고안된 모델입니다. 각 악기마다 작곡가가 전담별로 따로 있어 곡을 생성하는 것이 아닌 한 작곡가가 모든 악기의 음을 작곡합니다. 이를 바탕으로 모든 악기의 공통된 잠재벡터를 가지고 곡을 생성하는 모델입니다.
 - Hybrid Model: Jamming Model, Composer Model을 융합한 모델입니다.. 각 악기마다 각자의 잠재벡터를 가지고 추가로 공통된 잠재벡터를 가져 곡을 생성하는 모델입니다.
 - 이번 프로젝트에서는 Hybrid Model을 선택하여 진행했습니다.

# 성능지표
논문에서 제시한 성능 지표 중 이번 캡스톤 주제에서 주된 성능 향상 지표로 선택한 성능 지표입니다.
 - Empty bar: 오선보 악보에서 빈 마디의 비율을 의미합니다. 0~1까지의 값을 가지며 작을 수록 성능이 향상됩니다.
 - Pitch used: 마디 별로 사용된 음의 수를 의미합니다.
 - Qualified Note: Qualified Note의 비율을 의미합니다. Qualified Note란 time stamp가 3보다 작지 않은 노트를 의미합니다. 높을 수록 곡이 단조롭지 않고 성능이 향상됩니다.
 - Tone distance: 음계 간 거리입니다. Piano와 Guitar의 음계 간 거리를 기준으로 잡았습니다. 작을 수록 음계 거리가 가까움을 의미하고 조화를 이룹니다. 작을 수록 성능이 향상됩니다.

# GOAL
 - 이번 프로젝트의 목표는 MuseGAN 모델의 성능 지표 중 Empty bar, Tone distance는 낮추고 Qualified Note를 높이는 것입니다. 이를 위하여 Data Augmentation, 학습률 조정, Optimizer 변경을 시도했습니다.

# DATASET
 - lastfm_alternative_8b_phrase.npy: 2074개 곡에서 추출한 13,746개의 4마디 악절로 이루어진 데이터 셋입니다. Drums, Piano, Guitar, Bass, Ensemble, Reed, Synth Lead, Synth Pad 총 8개의 트랙을 가지며 락 스타일의 곡들입니다.

기존 모델 성능 지표
악기 | Empty bar | Pitch used | Qualified note | Tone distance
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
악기 | Empty bar | Pitch used | Qualified note | Tone distance
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
악기 | Empty bar | Pitch used | Qualified note | Tone distance
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
악기 | Empty bar | Pitch used | Qualified note | Tone distance
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
악기 | Empty bar | Pitch used | Qualified note | Tone distance
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
악기 | Empty bar | Pitch used | Qualified note | Tone distance
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
악기 | Empty bar | Pitch used | Qualified note | Tone distance
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
악기 | Empty bar | Pitch used | Qualified note | Tone distance
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
악기 | Empty bar | Pitch used | Qualified note | Tone distance
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
악기 | Empty bar | Pitch used | Qualified note | Tone distance
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
악기 | Empty bar | Pitch used | Qualified note | Tone distance
--- | --- | --- | --- |--- 
Drums | 0.0000 | 5.9688 | None | None
Piano | 0.1953 | 6.6408 | 0.5477 | 1.36086
Guitar | 0.0391 | 11.0732 | 0.5455 | 1.36086
Bass | 0.0000 | 4.9453 | 0.6305 | None
Ensemble | 0.1016 | 7.5043 | 0.4146 | None
Reed | 0.5625 | 2.1071 | 0.5060 | None
Synth Lead | 0.8594 | 4.0556 | 0.6659 | None
Synth Pad | 0.8516 | 8.1579 | 0.5130 | None

# (3-1) Rmsprop, 노트 늘리기
기존의 Adamm Optimizer에서 Rmsprop로 바꾸어 학습

모델 성능 지표
악기 | Empty bar | Pitch used | Qualified note | Tone distance
--- | --- | --- | --- |--- 
Drums | 0.0312 | 8.4355 | None | None
Piano | 0.2969 | 6.6000 | 0.6259 | 1.26037
Guitar | 0.2500 | 9.8021 | 0.6584 | 1.26037
Bass | 0.1953 | 4.2718 | 0.5800 | None
Ensemble | 0.4141 | 9.0667 | 0.4911 | None
Reed | 0.6250 | 4.7292 | 0.6427 | None
Synth Lead | 0.8516 | 10.0526 | 0.6161 | None
Synth Pad | 0.8203 | 10.6957 | 0.6508 | None

# (3-2) Rmsprop, 노트 옮기기
기존의 Adamm Optimizer에서 Rmsprop로 바꾸어 학습

모델 성능 지표
악기 | Empty bar | Pitch used | Qualified note | Tone distance
--- | --- | --- | --- |--- 
Drums | 0.0000 | 11.8906 | None | None
Piano | 0.2734 | 12.2796 | 0.6898 | 0.82052
Guitar | 0.2743 | 11.7742 | 0.5619 | 0.82052
Bass | 0.0000 | 5.1406 | 0.5899 | None
Ensemble | 0.3281 | 11.1977 | 0.6086 | None
Reed | 0.6328 | 6.5745 | 0.6563 | None
Synth Lead | 0.7109 | 10.0000 | 0.6299 | None
Synth Pad | 0.4609 | 5.5652 | 0.6474 | None

# (3-3) Rmsprop, 노트분리
기존의 Adamm Optimizer에서 Rmsprop로 바꾸어 학습

모델 성능 지표
악기 | Empty bar | Pitch used | Qualified note | Tone distance
--- | --- | --- | --- |--- 
Drums | 0.0469 | 68.5820 | None | None
Piano | 0.3594 | 53.0854 | 0.8706 | 0.20802
Guitar | 0.1719 | 57.3774 | 0.7735 | 0.20802
Bass | 0.0938 | 73.9828 | 0.8082 | None
Ensemble | 0.5078 | 54.5079 | 0.9101 | None
Reed | 0.6016 | 36.8824 | 0.8581 | None
Synth Lead | 0.7656 | 54.9333 | 0.4400 | None
Synth Pad | 0.7812 | 44.9286 | 0.5756 | None

# 최종 성능 비교
시도한 모델에서 가장 성능이 좋았던 모델은 Optimizer를 Rmsprop를 사용하고 노트 분리 데이터 증강기법을 사용한 모델입니다. Empty bar의 경우 성능 향상이 이루어졌다 말하기는 힘들겠으나 Qualified note의 경우 Synth Lead, Synth Pad를 제외한 모든 악기들의 성능이 크게 향상되었고 Tone distance의 경우 마찬가지로 성능이 향상되었습니다.

# Papers
MuseGAN: Multi-track Sequential Generative Adversarial Networks for Symbolic Music Generation and Accompaniment
Hao-Wen Dong,* Wen-Yi Hsiao,* Li-Chia Yang and Yi-Hsuan Yang, (*equal contribution)
in Proceedings of the 32nd AAAI Conference on Artificial Intelligence (AAAI), 2018.
<a href=https://arxiv.org/abs/1709.06298>[arxiv]</a>
