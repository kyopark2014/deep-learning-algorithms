# 손실함수 (Loss Function)

손실함수(Loss Function)는 예측값과 실제 정답간의 차이를 표현하는 함수입니다. 0에 가까울수록 완벽하게 추정할 수 있다는 의미입니다. 

 
- Regression: MSE(Mean Squared Error,평균제곱오차)
   
- Logistic Regression: Logistic loss function (Binary cross entropy loss function)
   
- MulticlassClassification: Cross entropy loss function

대표적인 손실함수에는 평균제곱오차(MSE)와 Cross Entropy Error가 있습니다.

## Mean Squared Error

평균제곱오차(Mean Squared Error: MSE)는 실제값과 예측값의 차이(error)를 제곱하여 평균을 낸것입니다. 실제값과 예측값의 차이가 클수록 평균 제곱 오차의 값도 커집니다. 회귀에서 손실함수로 평균제곱오차를 주로 사용합니다. 

## Cross Entropy Error

크로스 엔트로피 오차(Cross Entropy Error: CEE)는 분류(Classification) 문제에서 one-hot encoding을 했을때만 사용하는 오차 계산법입니다. 분류에서 주로 사용하는 sigmoid 함수는 자연 상수 e때문에 평균 제곱 오차를 적용하면 매끄럽지 못한 그래프가 출력되어서 지역 최소점(Local minimum)에서 더이상 학습을 하지 못할 수 있습니다. 따라서 e에 반대되는 자연 로그를 출력값에 취합합니다. 

### 분류에서 손실함수 

이진분류의 경우에는 binary_crossentropy를, 다중분류의 경우에는 categorical_crossentropy을 사용합니다. 또한, 만약 티셔츠를 (1,0,0,0,0,0,0,0,0,0)와 같이
[one hot encoding](https://github.com/kyopark2014/deep-learning-algorithms/blob/main/embedding.md#one-hot-encoding)으로 표현된다면 아래와 같이 티셔츠는 -log(a1)으로 표현됩니다. 여기서는 Keras이 [손실함수 (Loss Function)](https://github.com/kyopark2014/deep-learning-algorithms/blob/main/loss-function.md)로 "sparse_categorical_crossentropy"을 사용합니다. "sparse"를 붙이면 one hot encoding을 처리하여 줍니다. 

![image](https://user-images.githubusercontent.com/52392004/187072798-c115d22c-18d5-4c89-81a9-d51ee5849269.png)

아래처럼 Artifical Neural Network를 정의할 수 있습니다. 모델 훈련은 fit()으로 진행하는데, batch_size의 기본값은 32입니다. 만약 train_scaled가 4800개라면, epoch가 5개이고, batch_size가 32일때 한번의 epoch가 1500개씩 사용하게 됩니다. batch_size가 너무 크면 GPU에 올라갈수 없는 경우도 있으므로 중요한 옵션입니다. 

```python
import tensorflow as tf
from tensorflow import keras

from sklearn.model_selection import train_test_split

train_scaled, val_scaled, train_target, val_target = train_test_split(
    train_scaled, train_target, test_size=0.2, random_state=42)

dense = keras.layers.Dense(10, activation='softmax', input_shape=(784,))   # Output
model = keras.Sequential(dense)

model.compile(loss='sparse_categorical_crossentropy', metrics='accuracy')
model.fit(train_scaled, train_target, epochs=5, batch_size=32, verbose=1) 
```
