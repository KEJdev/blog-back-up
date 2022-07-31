---
layout: post
title: 재귀 알고리즘으로 팩토리얼과 최대공약수 구하기 (Python)
date: 2019-12-03 09:00:00 +0300
category : Algorithm
---

계속해서 재귀 알고리즘에 익숙해지기 위해 알고리즘 단골 문제인 팩토리얼과 최대공약수를 풀어보겠습니다. 재귀 함수가 무엇인지는 저번 포스팅에서 설명했으므로 이번에는 자세한 이야기는 생략하겠습니다. 

## factorial  

10!을 구할껀데, 10!을 풀어서 이야기하면 10 * 9 * 8 * 7 * 6 * 5 * 4 * 3 * 2 * 1 이고 , 계산하면 3,628,800 입니다. 구현하면 아래와 같습니다.

```python
def factorial2(count):
    if count > 0:
        return count * factorial2(count-1)
    elif count==0:
        return 1
    
factorial2(10)
```

코드 설명을 조금 하자면, 아래와 같습니다.  

    fact(10) 
        10 * fact(9)
            9 * fact(8)
                8 * fact(7)
                    7 * fact(6) .... 
 


그렇다면 이번에 최대 공약수를 출력해보는 재귀함수를 만들어 보겠습니다.  
사람마다 알고리즘 짜는 방식이 조금 다르니, 그 점을 유의 해주시고 저는 함수 두개를 만들어 구현해보겠습니다.  

```python 
def find_gcd_1(a,b):
    return a if b == 0 else find_gcd__1(b,int(a%b))

def find_gcd_2(a,b):
    return find_gcd_1(a,b) if a > b else find_gcd_1(b,a)

print(find_gcd(16,20))
```

흐음... 만약에 함수로 한다고 하면 아래와 같이 만들 수 있습니다. 


```python
def find_gcd(num1,num2):
    if num1<num2:
        (num1,num2)=(num2,num1)    
    if num1>num2:
        num1=num1-num2
        return find_gcd(num1,num2)
    else:
        return num1

# 또는

def find_gcd(a,b):
    return a if b == 0 else find_gcd(b,int(a%b)) # 두 수의 나머지와의 공약수

print(find_gcd(20,16))
```

이렇게 보니 재귀가 쉬운것 같으면서도 어렵네요... 

