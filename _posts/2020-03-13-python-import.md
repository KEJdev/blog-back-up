---
layout: post
title: 파이썬 모듈(import)사용하기
date: 2020-03-13 11:00:00 +0300
category : Python
use_math : true
---

파이썬에서 모듈(import)을 이해하고 사용해보도록 하겠습니다.

## 모듈(import) 이란?

이미 만들어져 있고 안정성이 검증된 함수들을 성격에 맞게 하나의 파일로 묶어놓은 것들을 모듈이라고 합니다. 외부의 모듈을 사용하려면 이 모듈을 먼저 코드로 가져와서 자유롭게 사용할 수 있도록 해야하는데 이런일을 파이썬에서는 모듈을 import라고 합니다. 


```python
import time 

print('5초간 프로그램을 정지합니다 ')
time.sleep(5)
```

또는 아래와 같이 사용할 수 있습니다. 

![import](/public/img/import.png){: width="50%" height="50%" }{: .center}

같은 위치에 test3.py 라는 이름으로 아래의 코드를 생성하면 사용할 수 있습니다. 

![import2](/public/img/import2.png){: width="50%" height="50%" }{: .center}

## 메인 모듈과 하위 모듈

__name__(내장 전역변수)를 이용하면 지금 쓰고 있는 모듈이 하위 모듈인지를 확인 할 수 있습니다. 메인 모듈의 경우 __name__를 사용하면 main이라고 나오며 하위모듈의 경우 __name__을 이용하여 출력을 하면 모듈명이 출력됩니다. 

![import3](/public/img/import3.png){: width="50%" height="50%" }{: .center}

