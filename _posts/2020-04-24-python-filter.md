---
layout: post
title: Python 정수 리스트에서 소수만 걸러내기(filter)
date: 2020-04-24 09:00:00 +0300
category : Python
use_math : true
---     

파이썬에서 간혹 리스트에 소수만을 걸러 내고 싶을때, 사용되는 filter 함수입니다. 
이름에서부터 느껴지듯 뭔가 걸러내기 위해 사용되는 함수라는 것을 알 수 있습니다. 

## filter

기본적으로 내장되어 있는 모듈이기 때문에 따로 불러 올 필요는 없습니다. filter를 이용하면 소수를 걸러낼 수 있다고 했는데, 소수는 두개의 수로 못나눈 것을 이야기합니다. 대표적으로 7이 소수가 될 수 있습니다. 소수의 반대는 합성수라고 이야기 할 수 있는데, 합성수의 예로는 6이 있습니다. (2*3=6)

```python 
def getPrime(x):
    for i in range(2, x-1):
        if x%i == 0:
            break
    else:
        return x

listdata = [117, 119, 1113, 11113, 11119]
ret = filter(getPrime, listdata)
print(list(ret))            # [11113, 11119] 가 출력됨
```

