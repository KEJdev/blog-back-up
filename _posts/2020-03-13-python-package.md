---
layout: post
title: 파이썬 패키지(package)란?
date: 2020-03-13 10:00:00 +0300
category : Python
use_math : true
---  

파이썬에서 패키지 사용하는 법에 대해 알아보겠습니다. 

## 패키지(package) 

우리가 음악 파일을 저장할때도 장르별로 폴더를 만들어서 별도로 저장하듯이 파이썬 모둘도 음악처럼 갯수가 많아지면 폴더(모듈 꾸러미) 별로 관리를 해야 관리가 편해지는데 이 폴더(디렉토리)가 패키지입니다. 

평범한 폴더가 패키지로 인정을 받으려면 반드시 갖고 있어야 하는 파일은 __init__파일입니다. __init__파일은 대게 비워두는 것이 보통인데 이 파일을 손데는 경우는 __all__변수를 조정할 때 사용합니다. 즉, 패키지로부터 반입할 목록을 정의할 때 사용합니다. 

![package](/public/img/package.png){: width="80%" height="80%" }{: .center}

그래서 실제로 적용해서 사용하자면 아래와 같이 사용할 수 있습니다.

![package2](/public/img/package2.png){: width="50%" height="50%" }{: .center}

```python
import my_loc.cal_test3 #패키지 안의 모듈을 불러온 뒤 

print(my_loc.cal_test3.plus(10,7)) #함수를 실행
```

## site-package

site-packages란, 파이썬의 기본 라이브러리 패키지외에 추가적인 패키지를 설치하는 디렉토리입니다. 이 디렉토리에 여러가지 소프트웨어가 사용할 공통 모듈을 넣어두면 **물리적인 장소에 구애받지 않고 모듈이 접근하여 반입**할 수 있습니다. 즉, 모듈을 site-packages에 넣어두면 무조건 실행할 수 있습니다. 

![package3](/public/img/package3.png){: width="60%" height="60%" }{: .center}

