---
layout: post
title: 파이썬 멤버체크(in)으로 특정 단어 개수 세기
date: 2020-03-12 11:00:00 +0300
category : Python
---

파이썬에서 특정 단어가 있는지 확인하기 위해 자주 쓰이는 함수 in입니다. 아마 for 사용할때 더 많이 사용해본 적 있을꺼예요. 이 맴버 함수에 대해 자세히 알아보겠습니다.

## list안에 있는지 없는지 확인하기

in을 사용하여 list안에 특정 숫자나 문자열이 있는지 체크해보겠습니다. 

```python
listdata =[1, 2, 3, 4]
ret1 = 5 in listdata    # False
ret2 = 4 in listdata    # True

print(ret1); print(ret2)

strdata = 'abcde'
ret3 = 'c' in strdata    # True
ret4 = '1' in strdata    # False

print(ret3); print(ret4)
```

## 텍스트(.txt)에서 특정 단어 및 라인 출력하기

겨울왕국 데이터를 사용하여 겨울왕국에서 elsa가 몇번 나오는지 확인하기 위해 우선 한라인씩 list변수에 담아보겠습니다. 겨울왕국 데이터는 [여기](https://github.com/KEJdev/DataSet/tree/master/DataSet)에서 다운 받으실 수 있습니다.


```python
file=open("winter.txt","r")

for winter_list in file:
    a = winter_list.split(' ')
    print(a)
```

![in](/public/img/in.png){: width="40%" height="40%" }{: .center}

이번엔 라인이 아니라 for문을 중첩시켜 겨울왕국의 단어들만 출력해보겠습니다. 

![in2](/public/img/in2.png){: width="80%" height="80%" }{: .center}

```python
file=open("winter.txt","r")

for winter_list in file:
    a = winter_list.split(' ')
    for b in a:
    print(b)
```

![in3](/public/img/in3.png){: width="10%" height="10%" }{: .center}

여기서 count 함수를 사용해서 elsa가 나오면 1씩 카운트 해보면 아래와 같이 쓸수 있습니다.


```python
file=open("winter.txt","r")
sum=0
for winter_list in file:
    a = winter_list.split(' ')
    for b in a:
        c = b.lower().count('elsa')
        sum += c 
	    
print(sum)
```