---
layout: post
title: 파이썬에서 간단하게 예외처리하기(try ~ except ~ else)
date: 2020-04-19 09:00:00 +0300
category : Python
use_math : true
---     

파이썬에서 예외처리는 프로그램에서 에러가 발생 했을 때, 에러를 핸들링하는 기능을 이야기합니다.

## 예외처리 (try ~ except ~ else)

에러가 나면 보통 프로그램이 종료되기 때문에 큰 문제가 발생하게 됩니다. 예를들면 API를 구현했는데, 어떠한 이유로 에러가 나서 종료가 된다면 큰 문제가 될 수 밖에 없습니다. 그래서 보통 예외처리를 하게 되는데, 예외처리를 하게 된다면 에러가 나는 부분을 제외하고 나머지 프로그램은 정상 작동하기 때문에 문제가 발생되지 않습니다. 

```python
def my_power():
    x =input(" 분자 숫자를 입력하세요 " )
    y =input(" 분모 숫자를 입력하세요 ")
    return int(x)/int(y)

print(my_power())
```

위와 같이 코드를 작성하고 에러를 출력해보겠습니다.

![try](/public/img/try.png){: width="70%" height="70%" }{: .center}
 
여기서 try ~ except를 사용하겠습니다.

![try2](/public/img/try2.png){: width="50%" height="50%" }{: .center}

```python
def my_power():
    try:
        x = input('분자 숫자를 입력하세요 ~ ')
        y = input('분모 숫자를 입력하세요 ~ ')
        z = int(x) / int(y)
    except:
        print(' 0 으로 나눌 수 없습니다. ')
    else:
        print('나눈 값을 잘 추출했습니다.')
        return z
	
print(my_power())
```

여기서 복수개의 except절을 사용하여 예외처리를 여러 개 나열해보겠습니다. 

```python
def my_power():
        try:
            x = input('분자 숫자를 입력하세요 ~ ')
            y = input('분모 숫자를 입력하세요 ~ ')
            z = int(x) / int(y)
            return z
        except ZeroDivisionError as err:
            print(' 0 으로 나눌 수 없습니다.')
        except:
            print(' 다른 예외 상황입니다. ')
			
print(my_power())
```

이렇게 되면 에러로 인한 비정상 종료를 막을 수 있기 때문에 코드를 작성할때, 꼭 사용해야 합니다. 