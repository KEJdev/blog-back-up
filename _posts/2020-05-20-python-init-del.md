---
layout: post
title: 파이썬에서의 클래스 생성자와 소멸자
date: 2020-05-20 09:00:00 +0300
category : Python
use_math : true
---   

파이썬에서의 클래스 생성자와 소멸자에 관해 알아보겠습니다. 생성자는 이름에서 알 수 있듯이 객체가 만들어질 때 호출되는 함수를 생성자라고 이야기 하며, 객체가 사라질 때 호출되는 함수를 소멸자라고 이야기합니다.

## init 

위에서 생성자가 무엇인지 이야기를 했는데, 생성자는 왜 사용하는 걸까요?  
생성자는 객체를 초기화 할 때, 자주 사용합니다. 

```python
class MyClass:    
    def __init__(self):
        self.var = '안녕하세요!'
        print('MyClass 인스턴스 객체가 생성되었습니다')

obj = MyClass()   # ‘MyClass 인스턴스 객체가 생성되었습니다’가 출력됨
print(obj.var)      # ‘안녕하세요’가 출력됨
```

## del 

def __init__으로 객체를 생성했으므로 이번엔 객체를 __del__를 사용하여 소멸시켜보겠습니다.

```python
class MyClass:    
    def __init__(self):
        self.var = '안녕하세요!'
        print('MyClass 인스턴스 객체가 생성되었습니다')

    def __del__(self):
        print('MyClass 인스턴스 객체가 메모리에서 제거됩니다')

obj = MyClass()
del obj 
```

![init](/public/img/init.png){: width="50%" height="50%" }{: .center}
