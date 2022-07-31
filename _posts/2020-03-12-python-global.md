---
layout: post
title: 파이썬에서 지역변수와 전역변수 사용하기
date: 2020-03-12 11:00:00 +0300
category : Python
---

이번에 파이썬에서 지역변수와 전역변수를 사용하는 것에 대해 배워보겠습니다. 

## 지역변수와 전역변수 

**변수는 자신이 생성된 범위(코드 블럭)안에서만 유효**합니다. 함수안에서 만든 변수는 함수 안에서만 살아 있다가 함수 코드의 실행이 종료되면 그 생명을 다합니다. 이것을 **지역변수**라고 합니다. 

이와는 반대로 함수 외부에서 만든 변수는 프로그램이 살아 있는 동안에 함께 살아 있다가 프로그램이 종료가 되면 같이 소멸합니다. 이렇게 **프로그램 전체를 유효범위로 가지는 변수를 전역변수**라고 합니다.


```python
param = 10
strdata = '전역변수'

def func1():
    strdata = '지역변수'
    print(strdata)
    
def func2(param):
    param = 1
    
def func3():
    global param  # global 을 사용하면 지역변수를 전역변수처럼 사용하겠다.  라는 뜻
                  # 그래서 값이 10에서 50으로 바귄다. 
    param = 50
    
func1()   # ‘지역변수’가 출력됨

print(strdata)  # ‘전역변수’가 출력됨
print(param)  # 10이 출력됨

func2(param)            
print(param)  # 10이 출력됨

func3()
print(param)  # 50이 출력됨  #global 을 사용했으니 값이 바뀐 것을 확인하기 위한 출력 
```

그러나 보통 지역변수를 사용하며, global를 사용하는 것은 매우 위험합니다. 전역변수를 프로그램에서 사용하는 경우는 프로그램 전체에서 공통적으로 사용되고, 잘 변하지 않는 데이터는 전역변수로 사용합니다. 예를 들면 아래와 같습니다.


```python
# pi 값은 공통적으로 사용하니 그냥 전역변수로 선언한다.
pi = 3.141592653589793 

# 원의 넓이를 구하는 함수 
def area_of_circle(radius):
    area=radius*radius*pi
return area


# 두개의 원의 넓이를 구하는 함수

def sum_circle(radius1, radius2):
    area1=area_of_circle(radius1)
    area2=area_of_circle(radius2)
    sumcircle=area1+area2
return sumcircle
```

![pi](/public/img/pi.png){: width="50%" height="50%" }{: .center}
