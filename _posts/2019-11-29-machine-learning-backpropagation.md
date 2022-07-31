---
layout: post
title: 신경망이 학습 하는 원리? 역전파(backpropagation)에 대해 알아보자. 
date: 2019-11-29 09:00:00 +0300
category : MachineLearning
---

흔히들 역전파, 영어로 하면 backpropagation이라고 하는 용어를 한번쯤은 들어보셨을 거라 생각합니다. 인공지능은 어떻게 학습하는 것인지, 역전파는(backpropagation)가 무엇인지 알아보도록 하겠습니다.  

## 역전파 (backpropagation)

역전파는 말이 어려워보이는 것 뿐이지, 생각보다 어려운 개념은 아닙니다. 역전파를 이야기 할때는 순전파라는 개념을 알아야 되기 때문에 함께 이야기 하겠습니다.우선 개념 이해를 위해 쉬운 예를 들어보도록 하겠습니다.  

우리는 중간고사와 기말고사등과 같은 시험을 잘 보기위해 학교에서나 학원에서 수업을 듣고는 합니다. 이렇게 공부를 하고 우리는 시험을 보게 되는데, 이러한 과정을 **순전파(forwardpropagation)**라고 합니다. 반대로 역전파는 이러한 우리가 다음 시험을 더 잘보기 위해 오답노트를 작성하여 공부를 다시 하고는 하는데 이 과정을 **역전파(backpropagation)**라고 합니다.    

그렇다면 실제로 인공지능이 학습하는 부분은 순전파일까요? 역전파일까요?  
인공지능이 실제로 학습하는 부분은 역전파 부분입니다. 그래서 역전파 부분이 중요하답니다.   

저번 포스팅때 이야기 했던 수치미분! 다들 기억 하시나요 ? 수치 미분을 기울기를 구하여 좋은 학습 결과를 뽑아낼 수 있지만, 매번 다시 계산하면서 기울기를 다시 구하는 방법은 비효울적이고 성능이 느립니다. 그래서 신경망에서 학습 처리할때, 최소화 되는 함수의 경사를 효율적으로 계산하기 위한 방법이 역전파랍니다.  
 
역전파라는 개념이 없을 경우 아래 그림과 같이 순전파 라는 개념만 있게 됩니다.  

![ml8](/public/img/ml8.png){: width="70%" height="70%" }{: .center}

이렇게 되면 무엇이 문제가 되냐면, 만약 output의 결과가 이상하다면, 다시 처음부터 학습을 해야 합니다. 그렇게 되면 학습시간이나, 컴퓨터 성능이 느리고 비효율적이게 되죠. 그렇기 때문에 역전파라는 개념이 생기게 된거랍니다. output층부터 차례대로 역방향으로 따라 올라가서 각 층에 있는 노드의 오차를 계산하는 겁니다. 

![ml9](/public/img/ml9.png){: width="70%" height="70%" }{: .center}

그렇게 각 노드이 오차만 계산하고 그 오차를 사용해서 함수의 기울기를 계산하는 방식으로 학습 결과에 영향을 주는거죠. 
즉, 전파된 오차만을 다시 계산해서 가중치를 조정하는 것이 역전파라고 할 수 있습니다.   

## 간단한 신경망 구현하기.

우선 행렬을 입력받아서 결과를 출력하는 forward 함수를 만들어 보겠습니다.
 
 ```python
import numpy as np

x = np.array([1,2]) # 입력값 
w = np.array([[1,3,5],[2,4,6]]) # 가중치
b = np.array([1,1,1]) # 바이어스

def forward(x,w,b):
  out = np.dot(x,w)+b
  return out
```

print를 찍으면 [6 12 18]이 나오는 것을 알 수 있습니다. 이번에는 역전파 함수를 backward라는이름으로 생성해볼까요?  


```python 
x = np.array([[1,2],[3,4]])
w = np.array([[1,3,5],[2,4,6]]) # 가중치
dy = np.array([[1,1,1],[2,2,2]]) # 역전파로 들어오는 값

def backward(x,w,dy):
  dx = np.dot(dy,w.T) # x의 역전파
  dw = np.dot(x.T, dy) # w(가중치)의 역전파
  db = np.sum(dy,axis = 0) # bias의 역전파 (역전파로 들어온 값의 합)
                          # axis = 0 열을 더한다.
  return dx,dw,db
```


그럼 이번엔 조금 더 나아가서 위에서 만든 forward 함수와 backward 함수를 묶어서 class 로 생성해보겠습니다. 저는 class이름을 Affine 이라고 하겠습니다.  


```python
class Affine:
  def __init__(self, w,b):
    self.w = w
    self.b = b

  def forward(self,x):
    out = np.dot(x, self.w)+self.b
    return out

  def backward(self, x, dy):
    dx = np.dot(dy, self.w.T)
    dw = np.dot(x.T, dy)
    db = np.sum(dy,axis=0)
    return dx,dw,db
```

이제 이렇게 클레스를 만들었으니 affine 클래스를 사용해서 2층짜리 신경망을 구현해보도록 하겠습니다. 입력값과 w,b가 아래와 같을때, 순전파 결과 행렬을 출력해보도록 하겠습니다.   


```python
x=np.array([[1,2]]) # x.shape : (1,2)
w1=np.array([[1,3,5],[2,4,6]]) # w1.shape : (2,3)
w2=np.array([[1,4],[2,5],[3,6]])
b1=np.array([1,2,3])
b2=np.array([1,2])
```

클래스는 이미 만들었으니, 출력해보겠습니다.

```python
affine1=Affine(w1,b1)
affine2=Affine(w2,b2)
y1=affine1.forward(x)
y2=affine2.forward(y1)

print('출력 행렬:\n',y2)
```  

출력하면 [93 211]이 나오는 것을 확인 할 수 있습니다. 이번엔 역전파를 구현해보도록 하겠습니다.   

```python
dy=y2

affine1=Affine(w1,b1)
affine2=Affine(w2,b2)
y1=affine1.forward(x)
y2=affine2.forward(y1)

dx1,dw1,db1=affine2.backward(y1,dy)
dx,dw,db=affine1.backward(x,dx1)

print('dx:\n',dx)
print('dw:\n',dw)
print('db:\n',db)
```

![ml10](/public/img/ml10.png){: width="20%" height="10%" }{: .center}

생각보다 어렵지 않네요. 여기서 나중에 활성화 함수나, loss 함수 등 여러가지 추가하면 신경망이 되는데, 그 부분은 담 포스팅에서 다루겠습니다.

