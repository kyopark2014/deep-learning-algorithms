# 자연어 처리

여기서는 Deep-learning 기반 자연어처리 모델에 대해 설명합니다. 

## 용어

#### Model
- 입력을 받아 어떤 처리를 수행하는 함수(Function)입니다. 
- 어떤 입력을 받아서 해당 입력이 특정 범주일 확률을 반환하는 확률함수입니다. 
  - 모델의 출력은 확률입니다. 
  - 자연어 처리 모델의 입력은 사람 말 (자연어)입니다.

#### Training

- 학습(Training)이란 출력이 정답에 가까워지도록 모델을 업데이트하는 과정입니다. 

#### Deep Learning

- 데이터 패턴을 스스로 익히는 인공지능의 한갈래입니다.
- 기존의 다른 구조보다 성능이 훨등히 좋습니다. 
- Deep이란 많은 은닉층(Hidden Layer)들을 사용한다는 의미입니다. 
- 이미지 분류, 음성 인식 및 합성, 자연어 처리 등 다양한 분야에서 널리 쓰이고 있습니다. 

#### Transfer Learning

- 트랜스퍼 러닝(Transfer Learning)은 특정 태스크를 학습한 모델을 다른 태스크 수행에 재사용하는 기법입니다. 
- 트랜스퍼 러닝을 적용하면 기존보다 모델의 학습 속도가 빨라지고 새로운 테스크를 더 잘할 수 있습니다. 

##### Upstreaming Task

###### 업스르리밍 테스크(Upstreame Task): 다음 단어 맞추기, 빈칸 채우기 등 대규모 말뭉치의 문맥을 이해하는 과제입니다.
- 다운스크림 테스크(Downstreame Task): 문서 ㅂㄴ류, 개체명 인식등 우리가 알고자하는 자연어처리의 구체적인 문제입니다. 

## 딥러닝 자연어 처리 모델 

자연어 처리 모델은 자연어를 입력받아 해당 입력이 특정 범주일 확률을 출력하고, 이 출력값을 적당히 후처리하여 자연어 형태로 가공해 반환합니다. 

### BERT 

BERT (Bidiectional Encoding Representation form Transformers)는 앞뒤 문맥으로 빈칸의 단어를 예측합니다. 

### GPT

GPT (Generative Pre-trained Transformer)는 이전 문맥을 고려하여 자연스러운 다음 단어를 예측합니다. 



## Reference 

[BERT와 GPT로 배우는 자연어 처리](https://ratsgo.github.io/nlpbook/docs/tutorial_links)
