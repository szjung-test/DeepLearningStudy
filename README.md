# shu's deeplearning study

# CNN Model timeline
- CNN 이란 Convolution layer + Pooling layer 조합으로 만들어진 모델들을 CNN 모델이라고 한다.

    - 1988 : LeNet 
    - 2012 : AlexNet
    - 2013 : Network in Network
    - 2014 : GoogLeNet (2014 ImageNet 우승)
    - 2014 : VGGNet (2014 ImageNet 준우승)
    - 2015 : ResNet
    - 2017 : DenseNet


# feature extraction(특징 추출)
- 1. convolution layer
- 특징 추출기 역할을 한다
- 컨볼루션 연산
- stride
- (zero) padding
- activation function
- 합성곱 층(convolution layer = 합성곱 연산 + 활성화 함수) 이후 풀링층을 추가
- 특징 : 이미지의 특징을 판단한다. 컴퓨터는 이미지에서 물체를 판별할 때, 다른 위치에 있는 같은 물체를 다른 물체라고 판다.
- 문제해결 방법 : convolution layer , 이미지 크기보다 작은 filter(=kernel) 사용, filter 로 특징을 판별한다
- image와 filter 의 convolution연산(dot product)결과는 Feature map(=Activation map) 추출
- filter 하나당 하나의 특징을 찾는다.
- convolution filter 수 = output feature map 채널수 
    
    - Convolution layer 의 Activation Function
        - 1.1 딥러닝 네트워크에서 노드에 들어오는 값들에 대해 곧바로 다음 레이어로 전달하지 않고
        주로 비선형 함수를 통화 후 전달. 이때, 비선형 함수를 활성화 함수(Activation function)라 한다.
        - Ex) ReLu, ReLU6

- 2. Pooling layer
- 특성 맵을 다운 샘플링하여 크기를 줄임
- 특징 : feature 특징을 강화한다.
- 특정 값만 유지하고 나머지 값은 버린다. 
    - max pooling
        - 1. 계산 감소
        - 2. 사이즈를 줄이는 것이기 때문에 필연적으로 오차가 발생하고 오버피팅 줄어듦

    - average pooling
        - 1. 거의 안씀
        - 2. 0,0,0,1 이면 1에 특징 값을 강조해야 하는데, 평균을 내면 특징 값을 강조할 수 없음
        - 3. 경우에 따라 평균 풀링이 좋은 경우가 있음

    - Overlap Pooling
        - 1. 가끔 논문에 나오는 풀링 방법

# hyper parameter
- pooling, stride, padding 은 하이퍼파라미터로 계산X

# Fully connected layer의 patameter 갯수
- CNN 두 종류의 FC layer 존재
    - 마지막 Conv layer 바로 뒤에 붙는 FC layer
    - 다른 FC layer 에 연결되는 FC layer

# Classification (특징 추출 이후에 이어지는 결과 도출)
- fully-connected layer

# Transfer learning
- 전이 학습은 한 문제를 해결하고 다른 관련 문제에 적용하면서 얻은 지식을 저장하는 데 중점을 둔 기계 학습의 연구 문제
ex) 자동차를 인식하는법을 배우는 동안 얻은 지식은 트럭을 인식하려고 할 때 적용 가능


# Network in Network(2013)
- Convolution layer가 local receptive field 에서 Feature 추출할 때 filter로 계산하여 Linear 한 문제 해결하려고함
- 기존에는 Feature map을 늘려서 이러한 문제를 극복하려고 했지만 Filter가 늘어남에 따라 연산량이 늘어나는 문제 발생
- Convolution 을 할 때 Filter 대신에 MLP(Multi layer perceptron)를 사용하여 Feature 추출 방법 고안

# GoogLeNet(2014)
- 22층을 가진 deep neural network
- 깊이와 넓이가 증가할 수록 높은 정확도를 얻을 수 있다.
- but 두 가지 단점
- 1. 기하급수적으로 parameter 증가 -> network의 깊이와 크기를 증가 제한
- 2. 

# VGG(2014)
- 3*3 convolution filter 사용하여 convolution layer 깊이를 증가시킨 모델


# ResNet(2015)
- residual representation 함수를 학습함으로써 신경망이 152 layer 까지 가질 수 있다.
- ResNet 은 이전 layer의 입력을 다음 layer로 전달하기 위해 skip connection(또는 shortcut connection)
- skip connection 은 깊은 신경망이 가능하게 한다.
