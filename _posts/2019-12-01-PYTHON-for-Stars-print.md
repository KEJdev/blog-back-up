---
layout: post
title: 파이썬 for문을 사용하여 별찍기
date: 2019-12-01 09:00:00 +0300
category : Python
---

반복문은 어떤 언어라고 할 것도 없이 정말 중요하고, 자주 쓰이는 문법입니다. 특히나 for문은 더욱 더 그렇죠. 그럼 오늘은 간단하게 for문의 기본적인 구조와 별찍기를 해보겠습니다 .

## for

파이썬의 for 문의 기본적인 구조는 아래와 같습니다.  

![python_a3](/public/img/python_a3.png){: width="50%" height="50%" }{: .center}

for문은 리스트나 튜플, 문자열의 첫번째 요소부터 마지막 요소까지 차례로 변수에 대입되어 "수행할 문장1", "수행할 문장2"등이 수행됩니다. 
그래서 조금 더 자세하게 문법을 설명하자면, 아래와 같습니다.  

![python_a6](/public/img/python_a6.png){: width="50%" height="45%" }{: .center}

숫자 1부터 3까지를 for문을 이용하여 출력해보겠습니다. 

```python
for i in (1,2,3):
  print(i)
```

문자열도 for문으로 돌려보겠습니다.  

```python
for i in 'i like tteokbokki':
  print(i)
```

 이번에 range를 사용하여 1부터 10까지 증가하는데, 2씩 증가하도록 출력해보도록 하겠습니다.  

```python
for i in range(1,11,2): # 1부터 10까지 증가하는데, 2씩 증가시켜라
  print(i)
# 출력 결과 1,3,5,7,9
```

 range를 사용하여, 별찍기를 해보도록 하겠습니다. 

![for1](/public/img/for1.png){: width="20%" height="20%" }{: .center}

```python
a=str("★")

for i in range(1,11):
  print(a*i)
``` 

또는 

```python
for i in range(1,11):
  print("★"*i)
``` 

이번에 반대로 별을 찍어볼까요?

![for2](/public/img/for2.png){: width="20%" height="20%" }{: .center}

이렇게 별을 찍어보겠습니다. 

```python
a=str("★")

for i in range(10,0,-1):
    print(a*i)
```

이번엔 조금 더 응용해서 ★으로 사각형을 만들어보겠습니다.
단, 이번에는 가로/세로를 입력을 받아서 ★를 출력하되, 중첩 for문을 사용하지 않고 작성해보도록 하겠습니다.  

![for3](/public/img/for3.png){: width="20%" height="20%" }{: .center}

```python
a=int(input("가로의 숫자를 입력하세요 "))
b=int(input("세로의 숫자를 입력하세요 " ))

for i in range(b):
  print("★"*a)
```

중첩 for문을 작성하여 사용한다면 아래와 같이 작성 할 수 있습니다.

```python
for i in range(b):
    c = ' ' # 초기화
    for j in  range(a):
        c += '★ '
    print(c)
```

마지막으로 for문으로 구구단을 출력해보겠습니다.


```python 
for i in range(1,10):
    result = ' '
    for j in range(2,10):
        result += (str(j) + 'X'+ str(i) + '=' 
        + str(i*j).ljust(13))
  print(result)
```

또는 

```python
for i in range(1,10):
    result = ' '
    for j in range(2,10):
        result += (str(j) + 'X'+ str(i) + '=' 
        + str(i*j) + \'t' )
  print(result)
```
