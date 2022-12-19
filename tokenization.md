# Tokenization

토큰화 (Tokenization)는 문장을 토큰 시퀀스(Token Sequence)로 나누는 과정입니다. 

## Token

- 토큰(Token)은 자연어 처리 모델의 입력을 의미 합니다. 
- 토큰은 문장(Sentence)보다 작은 단위입니다. 
- 한 문장은 여러 개의 토큰으로 구성됩니다.
- 토큰 분리 기준은 상황에 따라 다를 수 있습니다. 
- 문장을 띄어쓰기만으로 나눌수도 있고, 의미의 최소 단위인 형태소(Morpheme) 단위로 나눌 수도 있습니다. 

## Tokenizer 

- 토크나이저 (Tokenizer)는 토큰화를 수행하는 프로그램입니다. 
- BPE (Byte Pair Encoding), 워드피스(ㅈWorkpiece) 등이 있습니다. 
- 대표적인 한국어 토크나이저로는 은전한닢(mecab), 꼬꼬마(kkma)등이 있습니다. 
  - 언어 전문가들이 토큰화해 놓은 데이터를 학습에 최대한 전문적인 분석 결과와 비슷하게 토큰화를 수행합니다. 
  - 토큰화뿐 아니라 품사부착(Part-Of-Speech tagging)까지 수행할 수 있습니다. 

### BPE

- BPE(Byte-Pair Encoding)은 원래 정보를 압축하는 알고리즘으로 제안되었는데, 자연어 처리 모델에도 널리 쓰이는 토큰화 기법입니다. 
- GPT 모델은 BPE 기법으로 토큰화를 수행합니다. 


### Wordpiece

- BERT 모델은 BPE와 유사한 워드피스(Wordpiece)를 토크나이저로 사용합니다. 

