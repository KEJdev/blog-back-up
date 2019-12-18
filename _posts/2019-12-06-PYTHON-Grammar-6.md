---
layout: post
current: post
cover:  ../assets/images/python_cover1.png
navigation: True
title: Python while문 (while ~ continue ~ break)
date: 2019-12-05 10:00:00
tags: [PYTHON]
sitemap :
  changefreq : daily
  priority : 1.0
class: post-template
subclass: 'post tag-python'
author: KEJdev
use_math: true
---  

for문과 if문은 가장 흔하고 많이 쓰이는 문법이지만, while문도 자주 쓰이는 문법 중 하나입니다. 문법도 어렵지 않아서 금방 익힐 수 있습니다. while문이 가장 쓰기 편한 문법 중 하나인데, 그 이유는 조건이 참일 때, 실행시킨다던가, 아니면 무한루프로 계속 돌리다가 어느 순간에 멈추는 등 편리하기 때문입니다. 

<br>   

> #### while   

while문 구조는 아래와 같습니다.  

<center><img src="../assets/images/python_a5.png" width="180" height="80"></center> 

위 구조대로 간단하게 숫자 하나를 입력 받아서 입력받은 숫자까지 출력하는 것을 하나 출력해보겠습니다.  

```python
a = int(input("숫자를 입력하세요 "))
i = 0
while i < a:
    i = i+1
    print(i)
```

간단하죠?  
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

조건에 맞으면 while문이 돌아가는 것! 이제 잘 아시겠죠?  
이번에는 간단한 알고리즘을 풀어보도록 할까요?  

지겹도록 많이 풀었던 팩토리얼을 while문으로 구현해보겠습니다.  

```python
a = int(input("팩토리얼 숫자를 입력하세요 ~ "))
x=a 
    
while x > 1:
    x -= 1
    a=a*x
print(a)
```

오늘도 파이썬은 간단하네요.  
다음에는 대입연산자를 이용하는 것에 대해 알아보도록 하겠습니다.  

