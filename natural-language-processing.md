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

#### Data Loader

- 데이터 로더(Data Loader)는 데이터를 배치(Batch) 단위로 모델에 밀어 넣어주는 역할을 합니다. 
- 전체 데이터 가운데 일부 인스턴스를 뽑아 배치를 구성합니다. 

#### Deep Learning

- 데이터 패턴을 스스로 익히는 인공지능의 한갈래입니다.
- 기존의 다른 구조보다 성능이 훨등히 좋습니다. 
- Deep이란 많은 은닉층(Hidden Layer)들을 사용한다는 의미입니다. 
- 이미지 분류, 음성 인식 및 합성, 자연어 처리 등 다양한 분야에서 널리 쓰이고 있습니다. 


## 토큰화 (Tokenization)

자연어 처리를 위해서는, 자연어 문장을 작은 단위인 토큰(Token)으로 분석하여야 합니다. [토큰화 (Tokenization)](https://github.com/kyopark2014/deep-learning-algorithms/blob/main/tokenization.md)에 대해 설명합니다. 


## Transfer Learning

- 트랜스퍼 러닝(Transfer Learning)은 특정 태스크를 학습한 모델을 다른 태스크 수행에 재사용하는 기법입니다. 
- 트랜스퍼 러닝을 적용하면 기존보다 모델의 학습 속도가 빨라지고 새로운 테스크를 더 잘할 수 있습니다. 

#### Upstreaming Task

- 업스트림 태스크(Upstreaming Task)는 다음 단어 맞추기, 빈칸 채우기 등 대규모 말뭉치의 문맥을 이해하는 과제입니다.
- 업스트림 태스크를 학습하는 과정을 프리 트레인(Pretrain)이라고 합니다. 
- 자연어의 풍부한 문맥(Context)을 모델에 내재화합니다. 
- 업스트림 태스크의 대표 태스크로 다음 단어 맞추기와 빈칸 단어 채우기가 있습니다. 
- GPT 계열의 모델은 다음 단어 맞히기와 같은 태스크로 Pretrain을 수행합니다.
  - 모델이 대규모 말뭉치를 가지고 다음 단어 맞추기를 반복 수행하면, 이전 문맥을 고려했을 때 어떤 단어가 그 다음에 오는것이 자연스러운지 알수 있습니다. 
  - 언어 모델(Language Model)
- BERT 곙ㄹ 모델은 빈칸 채우기와 같은 태스크로 Pretrain을 수행합니다. 
  - 모델이 많은 양의 데이터를 가지고 빈칸 채우기를 반복 학습하면, 앞뒤 문맥을 보고 빈칸에 적합한 단어를 알 수 있습니다. 
  - 마스크 언어 모델(Masked Language Model)



#### Downstreame Task

- 다운스크림 태스크(Downstreame Task)는 자연어 처리의 구체적인 과제들입니다. 
- 문서 분류, 개체명 인식등 우리가 알고자하는 자연어처리의 구체적인 문제입니다. 
- 풀어야 할 자연어 처리의 구체적인 과제들입니다.
- 다운스트림 태스크는 Pretrain을 마친 모델을 구조 변경없이 그대로 사용하거나 여기에 테스크 모듈을 덧붙인 형태로 수행합니다. 
- 자연어처리에서는 태스크의 본질은 분류(Classification)입니다. 
- 자연어를 입력받아 해당 입력이 어떤 범주에 해당하는지 확률 형태로 반환합니다. 
- 문장 생성을 제외한 대부분의 과제에서는 Pretain을 마친 마스크 언어 모델인 BERT 계열을 사용합니다. 



## 딥러닝 자연어 처리 모델 

자연어 처리 모델은 자연어를 입력받아 해당 입력이 특정 범주일 확률을 출력하고, 이 출력값을 적당히 후처리하여 자연어 형태로 가공해 반환합니다. 

### BERT 

BERT (Bidiectional Encoding Representation form Transformers)는 앞뒤 문맥으로 빈칸의 단어를 예측합니다. 

### GPT

GPT (Generative Pre-trained Transformer)는 이전 문맥을 고려하여 자연스러운 다음 단어를 예측합니다. 




## Downstram task의 학습 방식

### Fine Tuning

- 파인 튜닝(Fine Tuning)은 Pretrain을 마친 모델을 다운스트림 태스크에 맞게 업데이트하는 기법입니다. 
- 문서 분류를 수행할 경우에 Pretrain을 마친 BERT 모델 전체를 문서 분류 데이터로 업데이트합니다. 

### Prompt Tuning

- 프롬프트 튜닝(Prompt Tuning)은 다운스트림 태스크 데이터 전체를 사용합니다.
- 다운스트림 데이터에 맞게 모델 일부만 업데이트 합니다. 

### In-context Learning

- 다운스트림 태스크 데이터의 일부만 사용합니다.
- 모델을 업데이트하지 않습니다. 

#### Zero-shot Learning

- 다운스트림 태스크 데이터를 전혀 사용하지 않습니다.
- 모델이 바로 다운스트림 테스크를 수행합니다.

#### One-shot Learning

- 다운스트림 태스크 데이터를 1건만 사용합니다. 
- 모델은 1건의 데이터가 어떻게 수행되는지 참조한 뒤 다운스트림 태스크를 수행합니다. 

#### Few-shot Learning

- 다운스트림 태스크 데이터를 몇 건만 사용합니다. 
- 도델은 몇 건의 데이터가 어떻게 수행되는지 참고한 뒤 다운스트림 태스크를 수행합니다. 



## Reference 

[BERT와 GPT로 배우는 자연어 처리](https://ratsgo.github.io/nlpbook/docs/tutorial_links)

[NSME (Naver Sentiment Movie Corpus)](https://ko-nlp.github.io/Korpora/ko-docs/corpuslist/nsmc.html)

[Tranfomer - Github](https://github.com/huggingface/transformers)


