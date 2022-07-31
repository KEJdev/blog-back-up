---
layout: post
title: 파이썬 for-else 사용하기
date: 2022-07-12 09:00:00 +0300
category : Python
---


`if`문에 `else`문이 있는데, `else`는 `for`문에도 있다.  
친숙하지 않겠지만, 사용법을 이해하면 유용하게 사용할 수 있다.  

## for-else
보통 for문은 아래와 같이 사용한다.   

```python
for n in range(2, 10):
    for x in range(2, n):
        if n % x == 0:
            print(n, 'equals', x, '*', n//x)
            break           
```

위 코드는 공식 문서에서 가져온 간단한 예시고, 소수를 찾는 코드이다.   
여기서 `else`를 사용하면 아래와 같이 출력이 해볼 수 있다.


```python
for n in range(2, 10):
    for x in range(2, n):
        if n % x == 0:
            print(n, 'equals', x, '*', n//x)
            break
    else:
        print(n, 'is a prime number')
```

`else`는 루프가 정상적으로 완료되면 실행되며, 이것은 어떠한 break문도 만나지 않았다는 것을 말한다. 루프를 실행하고 각 아이템을 검색하는 것이 일반적인 구조인데, 루프를 종료시키는 시나리오에는 두가지가 있다.   
첫번째는 아이템을 발견하고 break를 만나 루프를 빠져나오거나, 두번째는 루프를 끝까지 도는 것이다. 이때 어떤 것이 루프를 종료시키는 원인인지 궁금할 때, 위 코드처럼 루프가 끝나면 플래스를 확인하는 방법으로 사용할 수있다.  
