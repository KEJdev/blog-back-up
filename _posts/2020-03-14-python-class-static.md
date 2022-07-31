---
layout: post
title: 파이썬 static method (정적 메소드)
date: 2020-03-14 14:00:00 +0300
category : Python
use_math : true
---   

정적 메소드를 사용하여 클래스가 같은 메모리를 바라보는 것을 해보도록 하겠습니다.

## 정적 메소드 (static method)

정적 메소드는 self를 매개변수로 받지 않는 메소드를 말하며 여러 인스턴스가 공유해서 사용하는 메소드입니다.
저번에 만든 코드를 이용하여 예를 들어보겠습니다. 

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

이 클래스에서 총을 두개를 만들면 아래와 같습니다.

```python
#gun_1
gun_1=gun()
gun_1.charge(10)
gun_1.shoot(3)
gun_1.print()

#gun_2
gun_2=gun()
gun_2.charge(10)
gun_2.shoot(6)
gun_2.print()
```

여기서 gun_1과 gun_2는 서로 별개의 총입니다. 같은 클래스로 만들었지만 별개의 총이죠. 실제로 print를 찍어 확인해보면 메모리 주소가 다른 것을 확인 할 수 있습니다. 

![gun2](/public/img/gun2.png){: width="40%" height="40%" }{: .center}

그런데, 여기서 static method를 사용해서 클래스를 다시 만들면 아래와 같습니다.


```python
class Gun():
    
    bullet=0 #class 변수 선언
        
    @staticmethod #static method 사용 선언
    def charge(num): #충전
        Gun.bullet=num
        
    @staticmethod 
    def shoot(num): #발포
        for i in range(num):
            if Gun.bullet>0:
                print('탕 !')
                Gun.bullet-= 1
            elif Gun.bullet == 0:
                print('총알이 없습니다.')
                break
            
    @staticmethod
    def print(): #출력하는 기능
        print('{}발 남았습니다.'.format(Gun.bullet))
```

그리고 아까와 똑같이 만드는데, gun_2에는 총알을 장전하지 않고 총을 쏘게 되면 아래와 같은 결과를 얻을 수 있습니다.

![gun3](/public/img/gun3.png){: width="40%" height="40%" }{: .center}

결과를 보면 다른 총이지만 장전된 총알을 공유하는 것을 알 수 있습니다. 즉 , gun_2는 장전은 하지 않았지만 발포가 가능합니다. 월래라면 에러가 나야 하지만 메모리를 공유하기 때문인데 총알을 공유하는 것입니다.

![gun4](/public/img/gun4.png){: width="40%" height="40%" }{: .center}

print을 찍어보면 메모리를 같음을 알 수 있습니다.