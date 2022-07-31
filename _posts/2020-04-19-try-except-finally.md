---
layout: post
title: 파이썬에서 에러가 발생해도 특정 코드는 무조건 실행되게 하기 (try ~ except ~ finally)
date: 2020-04-19 09:00:00 +0300
category : Python
use_math : true
---     

에외처리에도 여러가지 방법이 있는데, 이번에는 실행한 코드가 정상적으로 작동을 하든, 에러가 나던 무조건 실행되는 블록을 추가해보는 것을 해보겠습니다.

## 예외처리 (try ~ except ~ finally)

try ~ except ~ finally문법은 아래와 같습니다. try ~ except과 별반 다를 것이 없고 그냥 한줄만 추가하면 되는거라 복잡하지는 않습니다. 

![try3](/public/img/try3.png){: width="40%" height="40%" }{: .center}

```python
def my_power():
    try:
        x = input('분자 숫자를 입력하세요 ~ ')
        y = input('분모 숫자를 입력하세요 ~ ')
        z = int(x) / int(y)
    except:
        print(' 0 으로 나눌 수 없습니다. ')
    finally:
        print('저는 무조건 실행할꺼라구요! 아.시.겠.어.요.?')

print(my_power())
```

