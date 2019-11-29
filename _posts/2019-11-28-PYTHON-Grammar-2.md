---
layout: post
current: post
cover:  ../assets/images/python_cover1.png
navigation: True
title: Python if문 개념 ①
date: 2019-11-26 09:00:00
tags: [PYTHON]
sitemap :
  changefreq : daily
  priority : 1.0
class: post-template
subclass: 'post tag-python'
author: KEJdev
use_math: true
---  


Python의 if문 개념에 대해 알아보겠습니다. Python 이라는 언어 자체가 사람의 언어와 비슷하기 때문에 문법을 금방 습득 하실 수 있습니다. 그럼 이제 예제와 함께 알아보도록 하겠습니다.  

<br>
 


> #### if문   

문법은 역시 예를 들면서 봐야 빠르겠죠?  
x와 y를 비교하여 x가 크면 "x가 y보다 크거나 깉습니다"를 출력하고 그것이 아니라면 "x가 y보다 작습니다" 라는 문구를 출력해보겠습니다. Python은 다른 문법과 다르게 사람의 언어와 비슷하다고 했지요? 아래의 예를 보면 더 쉽게 이해실 수 있을꺼예요.

```python
# x가 1이고 y가 2인 변수가 있다.
x = 1
y = 2

# 만약에(if) x가 y보다 크다면(>) 
if x > y:
  # print문을 출력해주세요
  print('x가 y보다 크거나 같습니다')

# 만약에 x가 y보다 크지 않다면,
else:
  # print문을 출력해주세요.
  print('x가 y보다 작습니다.')
``` 

쉽죠?  조금더 간단하게 보자면 아래와 같이 볼 수 있습니다.  

```python
# 조건이 true이면 실행이 되고 
#false이면 다른 실행문 실행

if 조건 1:
  실행문
elif 조건 2:
  실행문
else:
  실행문
```

그리고 파이썬에서는 콜론(:)을 쓰는 경우는 if문, for loop문, while loop문, def함수문등에서 사용한다는 사실 기억해두세요!  

그럼 if문에 조금 더 익숙해지기 위해 간단하게 숫자를 입력받아서 짝수인지, 홀수인지를 출력하는 파이썬 코드를 작성해볼까요?

파이썬에서 입력을 받을때는 간단하게 "input"을 써주시면 입력받을 수 있습니다. 정수만을 처리 하기 위해 int로 input을 한번 둘러주면 아래와 같이 작성할 수 있습니다. 

```python
a = int(input("숫자를 입력해주세요"))
```

그럼 이제 다시 if문을 작성해보겠습니다.   
만약 코드 짜는 것에 어려움을 느낀다면, 먼저 글로 작성하고 짜셔도 익히는데는 아무런 지장이 없으니 그렇게 하셔도 좋습니다.  

```python
if a%2 == 0:
  print("짝수입니다.")
else:
  print("홀수입니다.")
```

간단하죠?  
이번엔 조금 응용해서 함수로 만들어보겠습니다.  
if문은 그대로 두고 위에 한줄만 추가한다면 함수가 될 수 있습니다.  

```python 
def mod(a): # 추가 된 한줄
  if a%2 == 0:
    print("짝수입니다.")
  else:
    print("홀수입니다.")
```

앞에 def를 쓰게 될 경우에 함수로 만들겠다는 의미입니다. def[함수 이름](입력받을 곳) 라고 생각하시면 된답니다. 그래서 제가 만든 위의 함수 이름은 mod 가 되는 것이고 괄호 안에는 변수를 넣거나 숫자를 넣기 위해 빈공간을 생성한 거라 생각하면 쉽습니다.  

그래서 아래와 같이 mod함수를 작성하셔도 무방합니다.  

```python
def mod(a): 
  if a%2 == 0:
    print("짝수입니다.")
  else:
    print("홀수입니다.")
  
mod(10) # 짝수입니다가 출력됨
```

또는 아래와 같이 사용하실 수 있습니다. 

```python
def mod(a): 
  if a%2 == 0:
    print("짝수입니다.")
  else:
    print("홀수입니다.")

b = 10  
mod(b) # 짝수입니다가 출력됨
```

그럼 이번에 재밌는 문제 하나를 풀면서 익혀볼까요?  
가우스 덧셈 공식은 아래와 같습니다.

<center><img src="../assets/images/if1.png" width="200" height="120"></center>

이 가우스 덧셈 공식을 이용하여 1부터 10까지 숫자의 합을 출력해볼까요?  
문법에 조금 익숙해지기 위해 숫자를 입력 받아서 작성해보겠습니다.  

```python
a = int(input("첫번째 숫자를 입력하세요"))
b = int(input("마지막 숫자를 입력하세요"))

if a < b :
  result = (a + b) * int( b/2)
print(result)
```

어떤가요?  
생각보다 어렵지 않죠?  
다음에는 for문의 개념에 대해 알아보도록 하겠습니다.  









