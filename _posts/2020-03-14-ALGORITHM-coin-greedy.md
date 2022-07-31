---
layout: post
title: 파이썬으로 탐욕 알고리즘 구현하기(동전)
date: 2020-03-14 14:00:00 +0300
category : Algorithm
use_math : true
---  

탐욕 알고리즘은 당장 눈앞의 이익만 추구하는 것을 이야기 하며, 먼 미래를 내다 보지 않고 지금 당장의 최선이 무엇인가를 판단하는 알고리즘입니다. 

그럼 탐욕 알고리즘을 이용하여 금액과 화폐가 주어졌을 때 가장 적은 화폐로 지불하는 것을 구현해도록 하겠습니다. 

예를 들어 액수를 362 라고 입력하고 화폐단위를 1,50,100 이라고 입력했을 때 결과 값이 100원 3개, 50원 1개, 1원 12개의 값이 나와야 합니다. 

```python
def coinGreedy(): 
    money = int(input('액수입력 : '))
    cash_type = [int(x) for x in input('화폐단위를 입력하세요 : ').split(' ')]
    cash_type=sorted(cash_type, reverse=True)
    coin={}
    for i in cash_type:
        cnt=0
        while money >= i:
            money=money-i
            cnt += 1
        coin[i]=cnt

    for key in coin:
        print('{0}원 : {1}개'.format(key,coin[key]))
    
coinGreedy()
```
 
구현하면 위와 같이 구현할 수 있고 탐욕스럽게 잘 나오고 있는 것을 알 수 있습니다. 






