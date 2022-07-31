---
layout: post
title: 파이썬 for문에서 if문 안쓰고 특정 블럭만 실행하기(continue,break)
date: 2019-12-05 09:00:00 +0300
category : Python
---

for문 같은 반복문에서 쓸 수 있는 문법들이 꽤나 많은데요, 오늘은 반복문이 실행되는 동안에 다른 코드 블럭만 실행되게 할 때, 사용하는 문법에 대해 알아보도록 하겠습니다.  

## continue 문   

continue문은 반복문이 실행되는 동안 특정 코드 블럭을 실행하지 않고 다른 블럭만 실행하게 할 때 사용하는 문법입니다.  
예를 들어가면서 continue문을 작성해보겠습니다. 숫자 1부터 10까지 출력하는데 중간에 5가 나오지 않게 할때, continue문을 사용한다면 아래와 같습니다.  

```python
for i in range(1,11):
  if i == 5:
      continue
print(i)
```

continue문은 생각보다 유용하게 많이 사용되는데, 조금 더 응용해서 사용한다면 60점 이상인 학생에게 축하 메세지를 보내고 나머지한테는 안보는 프로그램을 짜게 된다면 아래와 같이 짧게 짤 수 있습니다.  

```python
jumsu = [ 90, 25, 67,45,80 ]
num = 0 

for i in jumsu:
  num = num +1 
  if i < 60:
      continue
print("%d 번 학생 축하합니다." %num)
```

생각보다 continue문은 유용하죠?

## break문  

break문은 말 그대로 루프를 중단 시키는 역활을 하는 문법입니다. 그래서 예를 들어보면 아래와 같이 사용할 수 있습니다.  

```python
scope = [ 1,2,3 ] 
for x in scope:
  print(x)
  break
else:
  print('perfect')
```

위와 같이 쓸 수 있습니다. 
