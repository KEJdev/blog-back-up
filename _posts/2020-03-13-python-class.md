---
layout: post
title: 파이썬 클래스(class)란?
date: 2020-03-13 11:00:00 +0300
category : Python
use_math : true
---

파이썬에서의 클래스 정의와 구현하는 법에 대해 알아보겠습니다. 

## 클래스(class)

사실 클래스(class)하면 가장 많이 비유로 사용되는 붕어빵 틀과 붕어빵이 있는데, 이 부분은 그냥 패스하고 직접 구현하면서 알아보도록 하겠습니다. 우선 총이라는 클래스를 만들어 보겠습니다.


```python
class gun():

    # 클래스가 실체화 될때, 바로 작동하는 메소드(함수)
    def __init__(self): # 총을 만든다. (실체화)

        # 총알을 0으로 설정 
        self.bullet = 0
```

위에 있는 class가 기본 구조 입니다. 여기서 총알을 충전하는 기능을 추가해보겠습니다. 총알 충전해야 하니까 숫자를 입력 받아야겠죠? 그리고 class에서는 꼭 self가 들어가기 때문에 클래스내에 함수를 사용할 경우 앞에 self를 붙여줘야 합니다. 


```python
class gun():

    # 클래스가 실체화 될때, 바로 작동하는 메소드(함수)
    def __init__(self): # 총을 만든다. (실체화)

        # 총알을 0으로 설정 
        self.bullet = 0

    # class에는 꼭 self가 들어간다. 
    def charge(self, num):#충전하는 기능
        self.bullet=num
```

총알을 장전했으면 쏘는 기능을 만들어야 합니다. for문을 이용하여 총알을 탕탕! 쏘는 기능을 구현해보도록 하겠습니다.


```python
class gun():

    # 클래스가 실체화 될때, 바로 작동하는 메소드(함수)
    def __init__(self): # 총을 만든다. (실체화)

        # 총알을 0으로 설정 
        self.bullet = 0

    # class에는 꼭 self가 들어간다. 
    def charge(self, num):#충전하는 기능
        self.bullet=num

    def shoot(self, num): #쏘는 기능
        for i in range(num):
            if self.bullet>0:
                print('탕 !')
                self.bullet-= 1
            elif self.bullet == 0:
                print('총알이 없습니다.')
            break
```

마지막으로 총알이 몇발 남앗는지 출력하는 간단한 print 함수를 만들어보도록 하겠습니다.

```python
class gun():

    # 클래스가 실체화 될때, 바로 작동하는 메소드(함수)
    def __init__(self): # 총을 만든다. (실체화)

        # 총알을 0으로 설정 
        self.bullet = 0

    # class에는 꼭 self가 들어간다. 
    def charge(self, num):#충전하는 기능
        self.bullet=num

    def shoot(self, num): #쏘는 기능
        for i in range(num):
            if self.bullet>0:
                print('탕 !')
                self.bullet-= 1
            elif self.bullet == 0:
                print('총알이 없습니다.')
            break

    def print(self): #출력하는 기능
        print('{}발 남았습니다.'.format(self.bullet))
```

클래스를 만들었으니 이제 클래스를 실행해봐야겠죠 ?

```python
# 총을 실체화시킨다. 
gun=gun()

# 총알을 장전한다. 
gun.charge(10)

# 총을 쏜다.
gun.shoot(3)

# 몇 발 남았는지 확인한다. 
gun.print()
```

![gun](/public/img/gun.png){: width="30%" height="30%" }{: .center}

