---
layout: post
title: 파이썬으로 버블정렬 알고리즘 구현하기
date: 2020-03-14 11:00:00 +0300
category : Algorithm
use_math : true
---  

버블정렬은 두 인접한 원소를 검사하여 정렬하는 방법입니다. 

![bubble](/public/img/bubble.png){: width="40%" height="40%" }{: .center}

파이썬으로 구현하자면 아래와 같이 구현할 수 있습니다.


```python
def bubble_search(data):
    for i in range(len(data)):
        for j in range(len(data)-1):
            if data[j] > data[j+1]:
                (data[j],data[j+1]) = (data[j+1],data[j])
            print('i=',i,'j=',j,data) 
    print(data)

data = [5,4,3,2,1,8,7,10]
bubble_search(data)
```


여기서 버블 정렬을 재귀 함수로 구현한다면 아래와 같이 구현할 수 있습니다.

```python
def bubble_search(data):
    for i in range(len(data)-1):
        if data[i] > data[i+1]:
            a = data[i]
            data[i] = data[i+1]
            data[i+1] = a            
            bubble_search(data)
            
    return data

data = [5,4,3,2,1,8,7,10]
print(data)
print(bubble_search(data))
```




