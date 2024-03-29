# Deep Learning

## Neural Network

[Neural Network](https://github.com/kyopark2014/deep-learning-algorithms/blob/main/neural-network.md)에서는 Neural Network의 특징 및 Error Back Propagation을 이용하여 최적의 Weight를 찾기 위한 방법에 대해 설명합니다. 


## Deep Learning의 특징 

Deep learning은 아래와 같이 입력층, 은닉층, 출력을 가지고 있습니다. 

- 입력층(Input Layer): 데이터를 받아들이는 층입니다.
- 은닉층(Hidden Layer): 모든 입력 노드부터 입력 값을 받아 가중합을 계산하고, 이 값을 활성 함수에 적용하여 출력층에 전달하는 층입니다.
- 출력층(Output Layer): 신경망의 최종 결과값이 포함된 층입니다. 

다수의 은닉층을 두면 다양한 비선형적 관계를 학습할 수 있는 장점이 있지만, 학습을 위한 연산량이 많아지고 기울기 소멸 문제가 발생할 수 있습니다. 이를 위해 [Dropout](https://github.com/kyopark2014/deep-learning-algorithms/blob/main/deep-learning.md#dropout), [ReLU 함수](https://github.com/kyopark2014/ML-Algorithms/blob/main/activation-function.md#relu), [배치 정규화](https://github.com/kyopark2014/deep-learning-algorithms/blob/main/deep-learning.md#batch-normalization)등을 적용합니다. 




## Deep Learning 방법

- Keras: TensorFlow2.0에서 내장 라이브러리로 사용, 사용 용이합니다.
- TensorFlow: 산업계에서 선호, 구글이 만든 ML framework (2015), GPU 사용 용이하나 사용법이 복잡합니다. (함수 python 문법에서 제한이 있어 디버깅 불편)
- CNTK: 마이크로소프트에서 개발한 방법입니다.
- theano: 학계에서 개발한 방법입니다.
- PyTorch: 함수형 Python 사용이 가능하여 디버깅 용이, 연구용으로 많이 사용됩니다.


## 기울기 소멸 문제

출력층에서 은닉층으로 전달되는 오차가 크게 줄어들어 학습이 되지 않는 현상입니다. 은닉층이 많은 신경망에서 기울기 소멸문제가 발생하기 쉽습니다. 

기울기 소멸문제는 [시그모이드](https://github.com/kyopark2014/ML-Algorithms/blob/main/activation-function.md#sigmoid)나 [하이퍼볼릭 탄젠트](https://github.com/kyopark2014/ML-Algorithms/blob/main/activation-function.md#tanh) 대신 [렐루](https://github.com/kyopark2014/ML-Algorithms/blob/main/activation-function.md#relu) 활성화 함수를 사용하면 해결할 수 있습니다. 

## 경사 하강법의 성능이 나빠지는 문제

경사 하강법은 [손실 함수](https://github.com/kyopark2014/deep-learning-algorithms/blob/main/loss-function.md)의 비용이 최소가 되는 지점을 찾을 때까지 기울기가 낮은 쪽으로 계속 이동하는데, 오히려 성능이 나빠지는 문제가 있습니다.

### Batch Gradient Descent

배치 경사 하강법 (Batch Gradient Descent: BGD)은 전체 데이터셋에 대한 오류를 구한 후 기울기를 한번만 계산하여 모델의 파라미터를 업데이트 하는 방법입니다. 즉, 전체 훈련 데이터셋에 대해 가중치를 편미분하는 방법입니다. 

한 스텝에 모든 훈련 데이터셋을 사용하므로 학습이 오래걸리는 단점이 있습니다.

### Stocastic Gradient Descent

[학률적 경사 하강법(Stocastic Gradient Descent: SGD)](https://github.com/kyopark2014/deep-learning-algorithms/blob/main/stochastic-gradient-descent.md)은 임의로 선택한 데이터에 대해 기울기를 계산하는 방법으로 적은 데이터를 사용하므로 빠른 계산이 가능합니다. 

### Mini-batch Gradient Descent

미니 배치 경사 하강법 (Mini-batch Gradient Descent)은 전체 데이터셋을 미니 배치로 여러개를 나누고, 미니 배치 한개마다 기울기를 구한 후 그것의 평균 기울기를 이용하여 모델을 업데이트해서 학습하는 방법입니다. 전체 데이터를 학습하는것보다 빠르며, 확률적 경사 하강법보다 안정적이라는 장점이 있습니다. 



## Deep Learning 용어 

### Weight

가중치(Weight)는 입력값이 연산 결과에 미치는 영향력을 조절하는 요소입니다. 

### Transfer Function

전달함수(Transfer Function)은 가중합을 의미합니다. 각 노드에 들어오는 신호에 가중치를 곱하여 다음 노드로 전달되는데, 이 값들을 모두 더한 합계를 가중합이라고 합니다. 노드의 가중합이 계산되면 가중합을 활성화 함수로 보내기 때문에 전달함수라고도 합니다. 

### Activation Function 

활성화 함수(Activation Function)은 전달 함수에서 전달받은 값을 출력할 때, 일정 기준에 따라 출력 값을 변화시키는 비선형 함수입니다. [활성화 함수](https://github.com/kyopark2014/ML-Algorithms/blob/main/activation-function.md)에서 상세히 설명합니다. 

### Loss Function 

[손실함수](https://github.com/kyopark2014/deep-learning-algorithms/blob/main/loss-function.md)에서 상세하게 설명합니다.

### Activation Function

신경망에 비선형성을 주기 위하여 dense에 Sigmoid, Relu와 같은 [activation function](https://github.com/kyopark2014/ML-Algorithms/blob/main/activation-function.md)을 지정할 때 지정할 수 있습니다. 신경망에서 미분시 계단함수를 쓸 수 없으므로, signoid를 사용하는데, 이것은 신경망의 층이 깊어지면 signoid의 미분값이 계속 작아져서 ReLU를 사용하기도 합니다. 

```python
model = keras.Sequential(name='fashion')
model.add(keras.layers.Flatten(input_shape=(28, 28), name='flatten'))
model.add(keras.layers.Dense(100, activation='relu', name='hidden'))
model.add(keras.layers.Dense(10, activation='softmax', name='output'))

model.summary()
```

### Optimizer 

확률적 경사 하강법의 파라미터 변경 폭이 불안정한 문제를 해결하기 위해, 학습속도와 운동량을 조정하는 옵티마이저를 사용합니다.  

[Gradient Descent](https://github.com/kyopark2014/ML-Algorithms/blob/main/stochastic-gradient-descent.md#gradient-descent)는 모든 데이터를 가지고 에러값을 찾은 후에 기울기를 구해서 Weight를 업데이트 합니다. [Stochastic Gradient Descent](https://github.com/kyopark2014/deep-learning-algorithms/blob/main/stochastic-gradient-descent.md)는 확율을 이용해서 속도를 개선합니다. Adam은 Momentum과 Step size를 모두 고려하여 가장 많이 사용되고 있습니다.

![image](https://user-images.githubusercontent.com/52392004/187076472-21b31bbd-3bbb-4f89-8e0a-b457bf11cc49.png)

기본값인 RMSprop을 아래처럼 adom으로 변경 할 수 있습니다. 

```python
model.compile(optimizer='adam', loss='sparse_categorical_crossentropy', metrics='accuracy')

model.fit(train_scaled, train_target, epochs=5, batch_size=32, verbose=1) 
```

optimizer를 최적화할때는 accuracy가 최적인 상태로 수렴하는 시간과 최대 accuracy을 기준으로 합니다. 



### Dropout

Neural Network에서 불필요한 일부 Node를 랜덤하게 제외함으로써 과적합(Overfitting) 문제를 해결할 수 있습니다. 

![image](https://user-images.githubusercontent.com/52392004/187076792-5a5db38e-8f53-48f4-b4d4-e3886b6edf3f.png)

- Dropout을 통해 보통 성능이 좋아지지만, 데이터 적으면 오히려 나빠질수도 있습니다. 
- 학습속도는 2-3배 느려집니다.
- 테이터가 매우 클 경우에는 이미 과적합이 없으므로 성능개선이 미미합니다. 
- 40~60% 정도 dropout이 좋음

![image](https://user-images.githubusercontent.com/52392004/187076917-472b0c3b-83d9-4293-9862-4454eb54192a.png)

```python
model = model_fn(keras.layers.Dropout(0.3))

model.summary()
```

### Batch Normalization

Internal Covariate Shift (내부공변량 변화)는 [z-fold cross validation](https://github.com/kyopark2014/ML-Algorithms/blob/main/preprocessing.md#k-fold-cross-validation%EB%A5%BC-%EC%9D%B4%EC%9A%A9%ED%95%9C-%EA%B5%90%EC%B0%A8%EA%B2%80%EC%A6%9D)처럼 입력 데이터(mini batch)의 분포가 바뀌는 현상을 말합니다. 즉, 노드의 가중치가 바뀌면 입력의 분포가 바뀌게 되는 현상인데, 바뀌게 되는 분포가 레이어를 타고 전파되는 문제를 가지고 있어서, 학습시 분포가 계속 바뀌어서 정상적인 학습이 되지 않습니다. 

아래는 내부 공변량의 변화를 보여줍니다. 

![image](https://user-images.githubusercontent.com/52392004/187076987-35763aa5-494f-4e74-9e22-f958a317352b.png)



이 경우에 아래와 같이 입력을 정규분포로 변환하는 Layer를 추가(z-transform)하는 방법으로 해결 할 수 있습니다. 에러 그래프가 수렴하지 않고 계속 튀는 경우에 Batch normalization을 고려할 수 있습니다. 

![image](https://user-images.githubusercontent.com/52392004/187077375-02d10cd7-e932-4931-963d-47055e302339.png)


Batch Normalization에서는 각 layer에 들어가는 input을 normalize 시킴으로써 layer의 학습을 가속하는데, 이 때 whitening 등의 방법을 쓰는 대신 각 mini-batch의 mean과 variance를 구하여 normalize한다. 실제로 이 Batch Normalization을 네트워크에 적용시킬 때는, 특정 Hidden Layer에 들어가기 전에 Batch Normalization Layer를 더해주어 input을 modify해준 뒤 새로운 값을 activation function으로 넣어주는 방식으로 사용한다. 

아래와 같이 은닉층 다음에서 아래와 같이 사용합니다. 

```python
model.add(keras.layers.BatchNormalization()
```

아래는 [deep CNN의 한 예](https://buomsoo-kim.github.io/keras/2018/05/05/Easy-deep-learning-with-Keras-11.md/)입니다.

```python
model.add(Conv2D(filters = 50, kernel_size=(3,3), strides=(1,1), padding='same', kernel_initializer='he_normal'))
model.add(BatchNormalization())
model.add(Activation('relu'))
model.add(MaxPooling2D(pool_size=(2,2)))
model.add(Conv2D(filters = 50, kernel_size=(3,3), strides=(1,1), padding= same', kernel_initializer='he_normal'))
model.add(BatchNormalization())
model.add(Activation('relu'))
model.add(Conv2D(filters = 50, kernel_size=(3,3), strides=(1,1), padding='same', kernel_initializer='he_normal'))
model.add(BatchNormalization())
model.add(Activation('relu'))
model.add(MaxPooling2D(pool_size=(2,2)))
```
### Flatten 

아래처럼 Flatten()을 이용하여, 입력을 모두 1차원 배열로 변환합니다. 

```python
model = keras.Sequential(name='fashion')
model.add(keras.layers.Flatten(input_shape=(28, 28), name='flatten'))
model.add(keras.layers.Dense(100, activation='relu', name='hidden'))
model.add(keras.layers.Dense(10, activation='softmax', name='output'))

model.summary()
```


### GPU 상태 확인 

아래처럼 console에서 nvidia-smi라는 명령어로 GPU 상태를 확인할 수 있습니다. 

```c
sh-4.2$ nvidia-smi
NVIDIA-SMI has failed because it couldn't communicate with the NVIDIA driver. Make sure that the latest NVIDIA driver is installed and running.
```



### Classification 예제

[deep_learnig.ipynb](https://github.com/kyopark2014/deep-learning-algorithms/blob/main/src/deep_learnig.ipynb)는 Fashion MNIST를 가지고 classification을 하는 deep learning 예제를 보여줍니다. 

1) Fassion MNIST 데이터를 로딩합니다. 

```python
import tensorflow as tf

tf.keras.utils.set_random_seed(42)
tf.config.experimental.enable_op_determinism()

from tensorflow import keras

(train_input, train_target), (test_input, test_target) = keras.datasets.fashion_mnist.load_data()
```

이때 로드된 데이터의 예는 아래와 같습니다. 

![image](https://user-images.githubusercontent.com/52392004/193933326-366d1a09-51d8-48ea-ae78-144b1b9c2408.png)

2) dataset을 준비합니다. 

```python
train_scaled = train_input / 255.0
test_scaled = test_input / 255.0

from sklearn.model_selection import train_test_split
train_scaled, val_scaled, train_target, val_target = train_test_split(
    train_scaled, train_target, test_size=0.2, random_state=42)
```

3) Model을 생성합니다. 

```
def model_fn(a_layer=None):
    model = keras.Sequential(name='fashion')
    model.add(keras.layers.Flatten(input_shape=(28, 28), name='flatten'))   ## Batch Normalization
    model.add(keras.layers.Dense(100, activation='relu', name='hidden'))    ## Activation Function
    if a_layer:
        model.add(a_layer)
    model.add(keras.layers.Dense(10, activation='softmax', name='output'))
    return model

model = model_fn(keras.layers.Dropout(0.3))    ## Dropout
```

4) optimizer, loss function, metric을 정의 합니다. 

```python
model.compile(optimizer='adam', loss='sparse_categorical_crossentropy', metrics='accuracy')   # Optimizer, Loss Function
```

5) 결과가 이전보다 좋으면 저장합니다. 

```python
checkpoint_cb = keras.callbacks.ModelCheckpoint('best-model.h5', save_best_only=True)   # Callback to save the best
```

6) 학습을 시작합니다. 

```python
history = model.fit(train_scaled, train_target, 
                    epochs=20, 
                    batch_size=32, 
                    verbose=1, 
                    validation_data=(val_scaled, val_target),
                    callbacks=[checkpoint_cb])      # epoch, batch_size
```

7) 최적의 모델을 로드 합니다. 

```python
model = keras.models.load_model('best-model.h5')
```

8) validation dataset으로 평가를 수행합니다. 

```python
model.evaluate(val_scaled, val_target)
```

이때의 결과는 아래와 같습니다. 

```python
375/375 [==============================] - 0s 873us/step - loss: 0.3125 - accuracy: 0.8909
[0.3125297725200653, 0.890916645526886]
```

9) test dataset으로 평가를 합니다. 

```python
model.evaluate(test_scaled, test_target)
```

Test dataset에 대한 결과는 아래와 같습니다. 

```python
313/313 [==============================] - 0s 1ms/step - loss: 0.3394 - accuracy: 0.8841
[0.33944830298423767, 0.8841000199317932]
```

10) 이때의 history graph는 아래와 같습니다. 

![image](https://user-images.githubusercontent.com/52392004/187084827-f0cf2722-13bf-46c7-ba2d-fd0778e57d8c.png)




## Deep Learning 실습

[Deep Learning 실습](https://github.com/kyopark2014/deep-learning-algorithms/blob/main/deep-learning-keras.md)에서는 Fashion MNIST 데이터를 이용하여 Keras 실습에 대해 설명합니다. 


## Reference 

[혼자 공부하는 머신러닝+딥러닝](https://github.com/rickiepark/hg-mldl)

[심층 인공 신경망 모델 (배치 정규화)](https://wikidocs.net/84506)

[BatchNormalization layer](https://keras.io/api/layers/normalization_layers/batch_normalization/)

