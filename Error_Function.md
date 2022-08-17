# Error Function(오차함수)

- RMSE, MSE MAE 딥러닝 모델을 최적화 하는데 사용되는 오차 함수이다.

## 특징
- 모델이 학습 데이터를 입력받아 아래 테이블 내 수치들을 예측할 때 
- target은 prediction이 맞춰야 할 정답이고, epoch는 학습의 횟수를 가리킨다.
- Epoch2에서, prediction의 3번째 값인 2는 그것이 근접했어야 할 Target의 3번째 값인 7과 크게 벗어나게 예측했다는 의미에서 outlier이다. 
![image](https://user-images.githubusercontent.com/93111772/185021231-5eca26c6-1175-40c0-8bcd-f03ad57d70b0.png)

이 값을 가지고 MSE, RMSE, MAE를 계산해보면
![image](https://user-images.githubusercontent.com/93111772/185021713-5d55a38f-cf2a-4892-aede-dd23b23255b2.png)

```
import matplotlib
import numpy as np

def MSE(pred, target, epochs=len(pred)):
    losses=[]
    for i in range(epochs):
        losses.append(np.sum((pred[i]-target[i])**2)/len*(pred))
    return losses
    
    
def RMSE(pred, target, epochs=len(pred)):
    losses=[]
    for i in range(epochs):
        losses.append(np.sqrt)

        - MSE 의 특징
         1. Mean Squared Error는 예측값과 정답의 차이를 제곱하기 때문에, 이상치에 대해 민감하다. 정답에 대해 예측값이 다른 경우, 그 차이는 오차값에 상대적으로 크게 반영된다.
         2. 오차값에 제곱을 취하기 때문에 (1) 오차가 0과 1사이인 경우에, MSE에서 그 오차는 본래보다 더 작게 반영되고, (2)오차가 1보다 클때는 본래보다 더 크게 반영된다.  
         3. 모든 함수값이 미분가능하다. MSE는 이차함수이기 때문에 아래와 같이 첨점을 갖지 않는다.
          ![image](https://user-images.githubusercontent.com/93111772/185022227-65e93dc7-f6a5-4e76-9ede-904ea00bcac9.png)
        
        - RMSE 의 특징
        1. MSE에서 루트를 취하기 때문에, [1],[2] 에서 나타나는 MSE의 단점이 어느정도 해소된다.
        2. MSE는 부드러운 곡선형으로 오차함수가 그려지지만, RMSE는 루트를 취하기 때문에 미분 불가능한 지점을 갖는다.
        3. MSE 보다 이상치에 덜 민감하다. RMSE는 이상치에 대한 민감도가 MSE와 MAE 사이에 있기 때문에, 이상치를 적절히 잘 다룬다고 간주되는 경향이 있다.
        ![image](https://user-images.githubusercontent.com/93111772/185022400-77e001f0-fc50-4d0c-810d-53b030acd6bb.png)

        - MAE 의 특징
        1. 이상치에 둔감 또는 강건Robust하다. MAE는 위에 MSE, RMSE에 비해 오차값이 outlier의 영향을 상대적으로 크게 받지 않는다.
        2. 함수값에 미분 불가능한 지점이 있다. MAE를 표현한 함수의 최솟값은 첨점이기 때문에 미분이 불가능하다.
        ![image](https://user-images.githubusercontent.com/93111772/185022639-ea4d395a-aa18-4c32-b297-5dcdb0678b82.png)




## 비교


Reference : https://jysden.medium.com/%EC%96%B8%EC%A0%9C-mse-mae-rmse%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%98%EB%8A%94%EA%B0%80-c473bd831c62
