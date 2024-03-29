---
title:  파이썬에서 언더바(_)를 사용하는 경우
date:   2020-03-14 12:00:00 +0300
categories:  [Program Language , Python]
sitemap :
math: true
mermaid: true
changefreq : always
priority : 1.0
use_math: true
---

파이썬 코드를 가끔 보다보면 _ 같은것을 볼 수 있습니다. 이 언더바(_)는 언제 사용하는 걸까요? 

## 언더바(_)를 사용하는 경우

언더바를 사용하는 경우는 주로 아래의 4가지 경우입니다.


1. 인터프리터에서 마지막 값을 저장할 때
2. 값을 무시하고 싶을 때
3. 변수나 함수명에 특별한 의미를 부여하고 싶을 때
4. 숫자 또는 문자값의 자릿수 구분을 위한 구분자로써 사용할 때

우선 첫번째, 인터프리터에서 마지막 값을 저장 할때 사용하는데, 아래와 같이 사용할 수 있습니다. 

<center><img src="../../assets//images/pass.png" ></center>

그래서 이런 출력도 가능합니다. 

<center><img src="../../assets//images/pass2.png" ></center>

두번째는 값을 무시하고 싶을 때 사용하는데, for 문을 사용할 때 가장 많이 사용됩니다. 

<center><img src="../../assets//images/pass3.png" ></center>

2를 무시하고 값이 출력되는 것을 알 수 있으며, for 문을 사용하면 아래와 같이 사용할 수있습니다.

<center><img src="../../assets//images/pass_for.png" ></center>

세번짼 변수나 함수명에 특별한 의미를 부여하고 싶을 때 사용합니다. 패키지를 만들기 위해 폴더 안에 _init_ 파일 만들때 사용합니다. 또한 함수명에 언더바를 붙이는 것에 따라 두가지 의미를 가지 수 있습니다.


```python
class Message:
    def __init__(self, msg):
        self.msg=msg
        
    def __repr__(self):
return "Message: %s" %self.msg
```

1. '_'이 앞에 붙으면 외부 사용자는 사용하지말라는 권유의 문법입니다.
2. '__'이 앞에 붙으면 private이 되어 외부에서 사용할 수 없고, 다른 클래스에서 사용하거나 override 할 수 없습니다. 


__를 붙인 함수와 안붙인 함수는 두가지 차이점을 가지고 있습니다.


1. 이 클래스 파일을 다른 파일에 import 할 때, __가 붙은 함수는 import가 되지 않습니다.
2. 클래스를 인스턴스화 하고 함수를 호출할때, 객체명만 사용하고 함수이름을 쓰지 않아도 실행을 할 수 있습니다. 


마지막으로 언더바는 숙자 또는 문자값의 자릿수 구분을 위한 구분자로써 사용할 수 있는데, 아래와 같이 사용할 수 있습니다. 

```python
dec_base= 1_000_000 
print(dec_base)
```

<center><img src="../../assets//images/pass4.png" ></center>