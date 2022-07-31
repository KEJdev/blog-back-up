---
layout: post
title: 이름없는 한줄짜리 함수(Lambda)
date: 2020-07-02 09:00:00 +0300
category : Python
use_math : true
---   

함수나, 클래스를 만들때 보통은 함수에 이름을 붙여서 사용한다. 그러나 함수를 재사용하지 않으려고 하는 경우에 Lambda 함수를 사용한다. 

## Lambda

람다식은 아래와 같다.

![lambda](/public/img/lambda.png){: width="30%" height="30%" }{: .center}

그래서 위의 식을 이용해서 간단하게 덧셈 함수를 만들면 이렇게 할 수 있다.


```python
add = lambda x, y: x+y
               #매개변수  :  #실행문
ret = add(1, 3)
print(ret)    # 4가 출력됨
```

람다는 간단하지만, 처음 사용할땐 어려울 수 있다.

```python
funcs = [lambda x: x+'.pptx', lambda x: x+'.docx']
ret1 = funcs[0]('Intro')
ret2 = funcs[1]('Report')
print(ret1)   # intro.pptx가 출력됨
print(ret2)   # Report.docx가 출력됨
```

이번엔 람다식을 이용해 key를 부르면 아래와 같이 간단하게 작성할 수 있다.


```python
names = {'Mary':10999, 'Sams':2111, 'Aimy':9778, 'Tom':20245, 'Michale':27115,
          'Bob':5887, 'Kelly':7855}
ret3 = sorted(names.items(), key=lambda x: x[0])
                              #0번째 요소(key)를 불러오는 함수식
print(ret3)
```
