---
layout: post
title: 머신러닝에서 단층/다층퍼셉트론(And, XOR Perceptron) 구현하기
date: 2019-11-07 09:00:00 +0300
category : MachineLearning
use_math : true
---

저번 포스팅에 이어 이번에는 퍼셉트론에 대해 좀더 자세히 다뤄보겠습니다.   
또한 직접 PYTHON으로 구현해보겠습니다. 

## 단층 퍼셉트론  

우선 AND Perceptron에 대해 알아보겠습니다. 

![eandtc_img](/public/img/and.png){: width="70%" height="70%" }{: .center}
![ml1](/public/img/ml1.png){: width="70%" height="70%" }{: .center}

그림의 원을 뉴런 혹은 노드라고 부릅니다.  
입력 신호가 뉴런에 보내질 때는 각각의 고유한 가중치가 곱해집니다. (x0,x1,x2,w0,w1,w2)   
뉴런에서 보내온 신호의 총 합이 정해진 한계를 넘어설 때만 1을 출력합니다.  

그렇다면 퍼셉트론의 동작원리를 잠시 수식으로 보겠습니다.

![ml2](/public/img/ml2.png){: width="30%" height="30%" }{: .center}


퍼셉트론 동작원리는 수식으로 나타내면 위와 같습니다. 퍼셉트론은 복수의 입력 신호 각각에 고유한 가중치를 부여합니다. 가중치는 각 신호가 결과에 주는 영향력을 조절하는 요소로 적용됩니다.  

AND게이트는 아래의 표와 같습니다.  

|<center>입력(and)</center> |  <center> x1 </center> | <center> x2 </center> | <center> t (타겟)</center> | 
|:--------:|:--------:|:--------:|:--------:|
|**i1**|0|0|0|
|**i2**|0|1|0|
|**i3**|1|0|0|
|**i4**|1|1|1|

그러면 이제 AND Perceptron 구현해보겠습니다.

```python
def AND_Perceptron(x1,x2):
	w = np.array([0.5,0.5])
	b = -0.7
	theta = 0

	x = np.array([x1,x2])
	tmp = np.sum(w*x)+b

	if tmp > theta:
		return 1
	elif tmp <= theta:
		return 0

inputData = np.array([[0, 0], [0, 1], [1, 0], [1, 1]])
print("＊ ＊ ＊ ＊ AND Perceptron ＊ ＊ ＊ ＊ ")

for xs1 in inputData:
    print(str(xs1) + " ==> " + str(AND_Perceptron(xs1[0], xs1[1])))
```

w는 가중치고, b는 bias라고 합니다. bias란 뉴런이 얼마나 활성화 하느냐를 조정하는 매개변수입니다. 
그렇다면 이번엔 OR Perceptron을 구현해보겠습니다.  

![or](/public/img/or.png){: width="70%" height="70%" }{: .center}

```python
def OR_Perceptron(x1, x2):
    w = np.array([0.5, 0.5])
    b = 0
    theta = 0

    x = np.array([x1, x2])

    tmp = np.sum(w * x) + b

    if tmp > theta:
        return 1
    elif tmp <= theta:
        return 0

inputData = np.array([[0, 0], [0, 1], [1, 0], [1, 1]])
print("＊ ＊ ＊ ＊ OR Perceptron ＊ ＊ ＊ ＊ ")

for xs1 in inputData:
    print(str(xs1) + " ==> " + str(OR_Perceptron(xs1[0], xs1[1])))
```

OR Perceptron의 결과는 아래의 표와 같습니다.  

|<center>입력(or)</center> |  <center> x1 </center> | <center> x2 </center> | <center> t (타겟)</center> | 
|:--------:|:--------:|:--------:|:--------:|
|**i1**|0|0|0|
|**i2**|0|1|1|
|**i3**|1|0|1|
|**i4**|1|1|1|

마지막으로 Not And Perceptron도 구현해보겠습니다.  

```python
import numpy as np

def NotAnd_Perceptron(x1, x2):
    w = np.array([0.5, 0.5])
    b = 0
    theta = 0

    x = np.array([x1, x2])

    tmp = np.sum(w * x) + b

    if tmp > theta:
        return 1
    elif tmp <= theta:
        return 0
    
inputData = np.array([[0, 0], [0, 1], [1, 0], [1, 1]])
print("＊ ＊ ＊ ＊ Not And Perceptron ＊ ＊ ＊ ＊ ")

for xs1 in inputData:
    print(str(xs1) + " ==> " + str(NotAnd_Perceptron(xs1[0], xs1[1])))
```

Not And Perceptron은 위와 같으며 결과는 아래와 같습니다.  

|<center>입력(Not And)</center> |  <center> x1 </center> | <center> x2 </center> | <center> t (타겟)</center> | 
|:--------:|:--------:|:--------:|:--------:|
|**i1**|0|0|1|
|**i2**|0|1|1|
|**i3**|1|0|1|
|**i4**|1|1|0|

## 다층 퍼셉트론  

다층 퍼셉트론은 단층퍼셉트론 연산에 중간층을 끼어넣은 것을 말합니다. 함수로 생성해보겠습니다. 

```python
def xor(x1, x2): # 입력값 : 0층
    s1=OR_Perceptron(x1,x2) # 1층
    s2=NotAnd_Perceptron(x1,x2) # 1층
    s3=AND_Perceptron(s1,s2) # 2층
    return s3

inputData = np.array([[0,0],[0,1],[1,0],[1,1]])

print("--Xor Perceptron---")
for xs1 in inputData:
    print(str(xs1) + " ==> " + str(xorPerceptron(xs1[0], xs1[1])))

```

이렇게 중간층이 있으므로 다층 퍼셉트론이라고 합니다.  

## 단층 신경망 ? 다층 신경망 ?  

그렇다면 단층 신경망과 다층 신경망의 차이점이 무엇을까요 ?  

|  <center>단층 신경망</center> |  <center> 다층신경망 </center> |
|:--------:|:--------:|
|입력층->출력층|얕은 신경망 ( 입력층 - 은닉층 - 출력층 )|
||심층 신경망 ( 입력층 - 은닉층들 - 출력층 )|



그렇다면 퍼셉트론과 신경망의 차이점은 무엇일까요?  

## 퍼셉트론 ? 신경망 ? 

- 퍼셉트론은 원하는 결과를 출력하도록 사람이 직접 가중치를 정해줘야 합니다.  
- 신경망은 가중치 매개변수의 적잘한 값을 기계가 데이터로부터 학습해서 자동으로 알아냅니다.  
