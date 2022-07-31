---
layout: post
title: 파이썬 while loop문을 사용하여 log함수 구현하기
date: 2019-12-06 09:00:00 +0300
category : Python
---

for문과 if문은 가장 흔하고 많이 쓰이는 문법이지만, while문도 자주 쓰이는 문법 중 하나입니다. 문법도 어렵지 않아서 금방 익힐 수 있습니다. while문이 가장 쓰기 편한 문법 중 하나인데, 그 이유는 조건이 참일 때, 실행시킨다던가, 아니면 무한루프로 계속 돌리다가 어느 순간에 멈추는 등 편리하기 때문입니다. 

## while   

while문 구조는 아래와 같습니다.  

![python_a5](/public/img/python_a5.png){: width="20%" height="20%" }{: .center}

위 구조대로 간단하게 숫자 하나를 입력 받아서 입력받은 숫자까지 출력하는 것을 하나 출력해보겠습니다.  

```python
a = int(input("숫자를 입력하세요 "))
i = 0
while i < a:
    i = i+1
    print(i)
```


이번에는 while loop문으로 log함수를 구현해볼까요?  

```python
a = int(input("밑수를 입력하세요 ~"))
b = int(input("진수를 입력하세요 ~ "))
c=a
cnt=1
while a < b:
    cnt += 1
    a=a*c
print("로그 값은 %i 입니다" %cnt)
```


이번에는 간단한 알고리즘을 풀어보도록 하겠습니다. 지겹도록 많이 풀었던 팩토리얼을 while문으로 구현해보겠습니다.  

```python
a = int(input("팩토리얼 숫자를 입력하세요 ~ "))
x=a 
    
while x > 1:
    x -= 1
    a=a*x
print(a)
```
