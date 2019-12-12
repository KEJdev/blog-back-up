---
layout: post
current: post
cover:  ../assets/images/python_cover1.png
navigation: True
title: Python for문 개념 ②
date: 2019-12-02 09:00:00
tags: [PYTHON]
sitemap :
  changefreq : daily
  priority : 1.0
class: post-template
subclass: 'post tag-python'
author: KEJdev
use_math: true
---  

if문에 조금 더 익숙해지기 위해 csv파일을 이용하여 if문과 for 문을 같이 사용해보도록 하겠습니다. 데이터는 [여기](https://github.com/KEJdev/DataSet/tree/master/DataSet)에서 다운받으실 수 있습니다.  

<br>  


> #### csv 파일 불러오기  

우선 csv 파일을 불러오겠습니다. python에서 csv 파일 읽은 모듈이 따로 있어서 코드가 길지 않습니다.  

```python
import csv

file = open("emp2.csv", "r")
emp_csv = csv.reader(file)

```
<br>  

> #### for문과 if문  


이제 불러왔으니, for 문을 이용하여 SCOTT인 사원의 월급을 출력해보도록 할까요?  

```python
for emp_list in emp_csv:
    if emp_list[1] =='SCOTT':
      print(emp_list[5])
```

사실 이렇게까지 힘들게 안해도 되지만,   
저는 for문과 if문에 익숙해지기 위해 이렇게 짜증나게 코드를 짜는것 뿐입니다.ㅠ

이번엔 조금 독특하게 input을 주고 출력하는 것을 만들어볼까요?  
for문으로 데이터를 하나씩 읽으면서 input값과 값이 일치한다면 출력하는 형태로 코드를 작성하면 된답니다. 
저는 이름을 입력받아서 월급을 출력하는 코드를 작성해보도록 하겠습니다. 

```python 
import csv

file = open("emp2.csv", "r")
emp_csv = csv.reader(file)

a = input("이름을 입력하세요 ")
for emp_list in emp_csv:
    if emp_list[1] == a:
        print(emp_list[5])
```

그럼 이번엔 if문을 여러개 사용하여 여러가지 조건을 걸어볼까요 ?  
python에서 if 문을 여러개 사용할때는 **elif**를 사용합니다.  

```python 
# if "조건1":
#   # 실행문
# elif "조건2":
#   # 실행문
# elif "조건3":
#   # 실행문 
# else: 
#   # 실행문 
```

해석하자면 조건이 true이면 실행하고 조건이 flese이면 실행을 하지 않다라는 뜻이고, 마지막 else는 위에 있는 조건 그 무엇도 암것도 걸리는게 없다면 실행하여라 라는 뜻입니다.  

그렇다면 위 코드 예제를 보고 이름을 입력했을때, 고소득자인지, 저소득자인지를 출력하는 python을 작성해볼까요 ?    

```python
import csv 
file=open("emp2.csv","r")
emp_csv = csv.reader(file)

a=input("이름을 입력하세요 ")
for emp_list in emp_csv:
    if emp_list[1]==a.upper():   # upper은 소문자를 입력해도 대문자로 바꿔준다.
        if int(emp_list[5]) >=3000:
            print("고소득자입니다")
        elif int(emp_list[5]) >=2000:
            print("적당합니다")
        else:
          print("저소득자입니다")
```

역시 파이썬은 코드가 간결하고 좋은 것 같네요. 











