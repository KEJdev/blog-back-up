---
layout: post
title:  파이썬으로 원주율 구하기(몬테카를로)
date: 2020-03-20 12:00:00 +0300
category : Python
use_math : true
---     

오늘은 몬테카를로 알고리즘으로 파이썬 원주율을 구해보려고 합니다. 

## 원주율  

가로 길이가 2인 사각형에 내접하는 반지름 길이가 1인 원의 넓이를 몬테카를로 알고리즘으로 구해보겠습니다.

![cir2](/public/img/cir2.png){: width="50%" height="50%" }{: .center}

원에 무작위로 점을 찍어서 원 안에 들어가는 점의 개수와 사각형 안에 찍히는 전체 점의 개수를 비교합니다. 예를 들면 10개의 점을 무작위로 찍었을 때, 원 안에 찍히는 점의 개수가 7개 라면? 이런식으로 비교하는 거죠. 

그래서 100개의 점을 무작위로 찍었을 때, 1000, 10000, ... 1억개의 점을 무작위로 찍었을 때, 찍는 점의 수가 많아 질수록 실제 원의 넓이에 가까워 집니다.  

![cir3](/public/img/cir3.png){: width="100%" height="100%" }{: .center}

만약에 100개의 점을 찍었을 때, 이 중 80개의 점이 부채꼴의 내부에 찍혔다면, 아래와 같이 계산 할 수 있습니다. 

![cir4](/public/img/cir4.png){: width="100%" height="100%" }{: .center}

코드로 구현하면 아래와 같이 구현 할 수 있습니다.

```python
num=int(input('랜덤을 반복할 횟수는 ? '))

cnt=0
for i in range(num):
    x=random.uniform(0,1)
    y=random.uniform(0,1)
    if x*x + y*y <= 1:
        cnt+=1
print((cnt/num)*4)
```

몬테카를로 원주율을 구하기 위해선 랜덤으로 점을 찍어야 하기 때문에 랜덤으로 점을 막 찍고 부채꼴 안에 있는 점의 갯수가 몇개인지 count만 하면 되기 때문에 코드가 간단합니다. 

![cir](/public/img/cir.png){: width="50%" height="50%" }{: .center}

