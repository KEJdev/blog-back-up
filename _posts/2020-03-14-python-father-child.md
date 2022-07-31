---
layout: post
title: 파이썬의 클래스 상속과 super함수
date: 2020-03-14 14:00:00 +0300
category : Python
use_math : true
---   

다른 언어와 마찬가지로 파이썬에도 상속 개념이 존재합니다. 클래스 상속을 사용하게 되면 반복적으로 코드를 짜지 않어도 되기 때문에 많이 사용합니다. 

## 상속


상속은 클래스들끼리 기능을 서로에게 물려주는 것이기 때문에 같은 코드를 반복해서 짜지 않아도 됩니다.

![class](/public/img/class.png){: width="40%" height="40%" }{: .center}

상속을 받기 위해 클래스 두개를 작성하고 자식 클래스에 상속시켜보겠습니다.  

```python
class father:
    def base_method(self):
        print("hello~")
        
class child(father):
    pass

father=father()
father.base_method()
child=child()
child.base_method()
```

코드를 보면 자식 클래스가 아빠 클래스를 상속을 받았는데, 이상태로 출력을 하면 아래와 같은 결과를 얻을 수 있습니다. 

![class2](/public/img/class2.png){: width="40%" height="40%" }{: .center}

결과를 보면 알수 있듯이 child class에는 함수를 쓰지 않았지만 클래스를 상속 받았으므로 father의 함수를 사용할 수 있습니다. 

그러면 여기서 father에 속성이 하나 더 생긴다면 child는 어떻게 될까요 ? 


```python
class father:
    def __init__(self):
        print("hello~")
        self.message="Good Morning"
        
class child(father):
    def __init__(self):
        father
        print ("hello~~ I am Child")

father=father()
father.message
```

![class3](/public/img/class3.png){: width="40%" height="40%" }{: .center}

father는 출력이 잘 되지만, child를 출력하면 에러가 출력됩니다.

![class4](/public/img/class4.png){: width="40%" height="40%" }{: .center}

이 오류를 해결하기 위해선 우선 class와 변수명 대소문자를 구분하여 작성해야 합니다. 

```python
class Father:
    def __init__(self):
        print("hello~")
        self.message="Good Morning"
        
class Child(Father):
    def __init__(self):
        Father.__init__(self) # 추가된 부분
                # Father의 __init__을 실행하겠다는 명령어
        print ("hello~~ I am Child")

father1=Father()
print(father1.message)

child1=Child()
print(child1.message)
```

그러나 파이썬은 암묵적인것을 싫어하고 명시적인 것을 좋아하는 성격이 있는데 위와 같이 father.__init__(self)라고 해도 되지만 파이썬의 내장 함수 중 super()를 사용하여 아래와 같이 사용할 수 있습니다. 


```python
class Father:
    def __init__(self):
        print("hello~")
        self.message="Good Morning"
        
class Child(Father):
    def __init__(self):
        #Father.__init__(self) #추가된 부분
        super().__init__() #super()
        print ("hello~~ I am Child")
```

사실 super를 사용하는 것을 권장하는데, 그 이유는 상속시에 나타나는 가장 큰 문제점을 해결할 수 있기 때문입니다. 

## 다중 상속, 죽음의 다이아몬드

상속에 가장 큰 문제점은 다중 상속 시에 나타나는 죽음의 다이아몬드 때문입니다. 

* 다중 상속

다중 상속이란, 두 개 이상의 클래스를 상속 받는 것을 이야기 합니다. 이 경우에는 두 클래스의 모든 속성을 물려받게 됩니다. 이는 하나의 자식 클래스가 두 개 이상의 부모 클래스를 가지는 경우를 이야기 할 수 있습니다. 

![class5](/public/img/class5.png){: width="40%" height="40%" }{: .center}

예를 들면 아래와 같습니다. 


```python
class Grandfather:
    def __init__(self):
        print('튼튼한 두팔')
        
class Father1(Grandfather):
    def __init__(self):
        Grandfather.__init__(self)
        print('지식')
        
class Father2(Grandfather):
    def __init__(self):
        Grandfather.__init__(self)
        print('지혜')
        
class Grandchild(Father1, Father2):
    def __init__(self):
        Father1.__init__(self)
        Father2.__init__(self)
        print('자기 만족도가 높은 삶')
        
grandchild=Grandchild()
```

![class7](/public/img/class7.png){: width="40%" height="40%" }{: .center}

만약 튼튼한 두팔, 지혜, 지식, 자기 만족도가 높은 삶을 출력한다고 했을 때, 실제로 출력 되는 것을 확인해보면 튼튼한 두팔이 두번 나오는 경우를 확인 할 수 있습니다. 

![class6](/public/img/class6.png){: width="40%" height="40%" }{: .center}

이것이 다중 상속시 볼 수 있는 죽음의 다이아몬드 상속입니다. 이를 해결하기 위해서 super 함수를 사용해야 이 문제를 피할 수 있습니다. 


```python
class Grandfather:
    def __init__(self):
        print('튼튼한 두팔')
        
class Father1(Grandfather):
    def __init__(self):
        super().__init__()
        print('지식') 
        
class Father2(Grandfather):
    def __init__(self):
        super().__init__()
        print('지혜')
        
class Grandchild(Father1, Father2):
    def __init__(self):
        super().__init__()
        print('자기 만족도가 높은 삶')
```

![class8](/public/img/class8.png){: width="40%" height="40%" }{: .center}

