---
layout: post
title: 파이썬 REST API을 만들어보자
date: 2020-10-19 09:00:00 +0300
category : Python
use_math : true
---   

회사에서 머신러닝 개발자로 일하고 있지만, 1년 내내 머신러닝 모델을 만들거나 논문만 읽거나 그러지는 않는다. 나름대로 Python API 나, 자바 컨트롤러 정도는 만들면서 다른 업무도 도와주거나, 데이터 분석도 하는 편이다.  

그중에서 입사 초에 Python API 하나를 못 만들어서 정말 고생했던 것을 이번 포스팅에서 풀어볼까 한다. 이번 포스팅에서는 Python API를 만들면서 테스트 하는 것을 중점으로 포스팅 할 것이다.

## REST API 

우선 API를 만들기전에 API로 만들어야 할 함수를 간단하게 두개 만들것이다. 나는 Study.py 라는 파일을 생성하여 아래와 같은 함수를 만들었다. 

```python
# Study.py
def add(a,b):
    return a+b

def same(a,b):
    if a == b:
        return True
    else:
        return False
```

add함수는 덧셈 함수이고 , same함수는 a와 b를 입력 받았을 때, True 인지 False 인지를 반환해주는 함수이다. 이제 REST API 함수를 만들텐데, 일단 간단하게 app.py 파일을 생성하고 TEST 가능한지 TEST API를 먼저 만들어보겠다.

```python
# app.py
from flask import Flask
app = Flask(__name__)

@app.route('/')
def greeting():
    return "This is Test API ! "
```

API 띄울때는 app.py 파일이 있는 곳에서 아래와 같이 두 줄만 치만 된다. 

```
export FLASK_APP="app.py"  # 리눅스 일때 <-
set FLASK_APP=app.py # 윈도우 일때 <-
flask run --host=0.0.0.0
```

테스트용으로 만드는 것이기 때문에 flask run --host를 0.0.0.0이라고 했지만, 실제 현업이나 중요한 곳에서 사용해야 한다면, 실제 IP와 포트로 바꿔서 사용해야한다.   


이제 "http://127.0.0.1:5000/" 주소로 들어가서 확인 하면 This is Test API ! 라는 문구를 볼 수 있다.   
여기서 아까 만들었던 add 함수와 same 함수를 API로 만들어보자.

```python
from flask import Flask, request
from flask_api import status
import json 
from Study import *
app = Flask(__name__)

@app.route('/')
def greeting():
    return "This is Test API ! "
    
@app.route('/add', methods=['POST'])
def get_add():
    if request.method == 'POST':
        a = request.json["a"]
        b = request.json["b"]
        c = add(a,b)
        result = json.dumps(c)
    return result, status.HTTP_200_OK, {"Content-Type": "application/json; charset=utf-8", "Access-Control-Allow-Origin": "*"}
    
@app.route('/same', methods=['POST'])
def get_same():
    if request.method == 'POST':
        a = request.json["a"]
        b = request.json["b"]
        c = same(a,b)
        result = json.dumps(c)
    return result, status.HTTP_200_OK, {"Content-Type": "application/json; charset=utf-8", "Access-Control-Allow-Origin": "*"}
```

갑자기 코드가 길어져서 아마 놀랬을 것이다. 그래서 아래의 그림을 준비했다.

![api](/public/img/api.png){: width="100%" height="100%" }{: .center}

코드를 보자마자 @app.route에 주소를 적고 아래 함수를 보자.   
**add 함수에 넣어야 할 매개변수를 어디에 있는가?** Study.py에 있는 add 함수에는 a,b라는 매개변수를 받아 서로 더하고 나서 리턴하는 구조인데, get_add() 함수는 그렇지 않다. **함수 안에서 데이터를 처리**하기 때문에 함수 생성시 , 직접 매개변수를 작성하지 않는다.

이제 생성된 API를 테스트하려고 하는데, 어떻게 해야할까? 

당연히 아까와 마찬가지로 http://127.0.0.1:5000/add 를 치고 들어가면 "Method Not Allowed
The method is not allowed for the requested URL." 를 볼 수 있을것이다. 전달할 데이터도 뭣도 없으니 저런 문구가 뜨는 것이 당연하다.   

여기서부터 실제 만든 API를 테스트하고 확인하려면 간단하게 [Postman](https://chrome.google.com/webstore/detail/postman/fhbjgbiflinjbdggehcddcbncdddomop/related?hl=ko)이라는 툴을 이용하면 된다. 설치도 사용법도 무척이나 간단하다. 

![api2](/public/img/api2.png){: width="100%" height="100%" }{: .center}

위처럼 똑같이 세팅해주면 postman으로 API결과를 확인 할 수 있다. add와 마찬가지로 same도 테스트 하면 결과를 확인 할 수있다. 








