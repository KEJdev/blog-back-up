---
layout: post
title: 파이썬 컨벤션에 대해 알아보자
date: 2020-12-12 09:00:00 +0300
category : Python
use_math : true
---   

회사에서 일하다보면 간혹 파이참에서 내 코드에 노란줄 표시하는 것을 볼 수 있다. 이 노란줄은 "컨벤션 좀 지켜주세요" 라는 뜻이다. Go 같은 경우는 무조건 지켜야 실행이 가능하지만, 다른 언어들은 지키지 않아도 문제 없기 때문에 사실 안지키는 사람이 많다. 나도 지키지 않는 경우가 많은데, 이제는 깔끔하게 코드를 짜고 싶어 이렇게 한번 되돌아보는 시간을 가져볼까 한다. 

사실 컨벤션은 필수가 아니고 "코드를 이렇게 작성하는게 좋을 것 같습니다." 하는 **스타일 가이드**이다. 스타일 가이드가 중요한 이유는 혼자 보는 코드가 아니기 때문이다. 다른 사람들과 함께 협업해서 일을 하는 것이기 때문에 어느정도 코드에 대한 일관성이 있어야 보기 편하다.

## PEP8 -- tyle Guide for Python Code

파이썬 창시자가 만든 파이썬 스타일 가이드이다. 중요하기 때문에 무조건 읽어봐야 한다. 하지만 난 읽지 않았기 때문에 같이 함께 보도록 하자. 

### **1 . 들여쓰기** 

들여쓰기는 공백 4개를 쓰도록 하며, 첫번째 줄에는 인수가 오면 안된다. 또한 fun name과 인수를 구별을 명확하게 하기 위해 들여쓰기(공백 4개)를 한번 더 해야 한다. 


```python
# 올바른 예 
# Aligned with opening delimiter.
foo = long_function_name(var_one, var_two,
                         var_three, var_four)

# Add 4 spaces (an extra level of indentation) to distinguish arguments from the rest.
def long_function_name(
        var_one, var_two, var_three,
        var_four):
    print(var_one)

# Hanging indents should add a level.
foo = long_function_name(
    var_one, var_two,
    var_three, var_four)

# 잘못된 예    
# Arguments on first line forbidden when not using vertical alignment.
foo = long_function_name(var_one, var_two,
    var_three, var_four)

# Further indentation required as indentation is not distinguishable.
def long_function_name(
    var_one, var_two, var_three,
    var_four):
    print(var_one)
```

또한 들여쓰기 할 때, 탭은 탭으로, 스페이스는 스페이스로 명확하게 일관성을 유지해야 한다. Python3 같은 경우는 혼합하는 것을 허용하지 않으므로 들여쓰기 하는 방법은 통일해야 한다. 통상적으로 탭을 사용한다. 

### **2. Blank Lines(빈줄)** 

2개의 빈줄로 함수와 클래스 정의를 구분한다. 클래스 내의 함수는 하나의 빈줄로 구분한다.  

### **3. Import (임포트)**

import는 반드시 행을 분리해서 선언한다. 또한 모듈의 이름은 소문자로 한다.  

```python
# 올바른 예 
import os 
import sys

# 잘못된 예 
import sys, os  

# 아래의 경우는 허용
from subprocess import Popen, PIPE
```

import는 절대경로를 이용한 절대 import가 권장된다. 

```python
import mypkg.sibling
from mypkg import sibling
from mypkg.sibling import example
```

그리고 import한 클래스의 이름이 지역 변수와 충돌나면 아래처럼 사용해도 된다.

```python
from myclass import MyClass
from foo.bar.yourclass import YourClass

# 충돌 나면 이렇게 사용 
import myclass 
import foo.bar.yourclass
```

### **4. String Quotes(따움표)**

파이썬에서는 문자열을 표현할 때, 큰 따옴표와 작은 따옴표 구분 없이 편하게 사용하면 된다. 

### **5. Pet Peeves**

무의미한 공백은 자제하자.  

```python
# 올바른 예
spam(ham[1], {eggs: 2})

# 잘못된 예
spam( ham[ 1 ], { eggs: 2 } )
```

쉼표와 닫는 괄호도 아래와 같다. 

```python
# 올바른 예
foo = (0,)

# 잘못된 예
bar = (0, )
```

### **6. 주석**

주석은 영어로 쓰도록 하자. 또한 마침표 뒤에는 두 칸의 공백을 주고, 반드시 문장 형태여야 한다. 
인라인 주석의 경우( 한 구문과 같은 줄에 쓰는 주석 ) 구문과 2칸 이상의 공백을 두고 # 기호와는 한칸의 공백을 주고 사용한다. 그러나 인라인 주석의 경우 잘 사용되지는 않는다. 

### **7. Docstrings**

public 모듈, 함수, 클래스, 함수에 대해서는 Docstrings을 사용하도록 하자. 무슨 역활을 하는지에 대해 작성하는 것이 좋으며 def문장 바로 아래줄에 작성하자.

```python 
# 한줄 Docstrings
def kos_root():
    """Return the pathname of the KOS root directory."""
    global _kos_root
    if _kos_root: return _kos_root
    ...

# 여러 줄 Docstrings
def complex(real=0.0, imag=0.0):
    """Form a complex number.

    Keyword arguments:
    real -- the real part (default 0.0)
    imag -- the imaginary part (default 0.0)
    """
    if imag == 0.0 and real == 0.0:
        return complex_zero
    ...
```

### **8. Descriptive Naming Styles**

변수명에서 _(밑줄)은 위치에 따라 여러 의미가 있다.  

* _single_leading_underscore : 내부에서 사용하는 변수이다. 앞에 언더스코어를 사용한 객체는 import 되지 않는다. 
* single_trailing_underscore_ : 파이썬 기본 키워드와 충돌을 피하려고 사용한다.  
* __double_leading_underscore : 클래스 속성으로 사용되면 그 이름을 변경한다. (ex. FooBar에 정의된 __boo는 _FooBar__boo로 바뀝니다.)  
* __double_leading_and_trailing_underscore__:  magic 객체', 사용불가, 미리 정의되어 있는 이름만 사용 가능하다.  
 
### **9. Names**

* 소문자 l, 대문자 O, 대문자 I는 변수명으로 사용하지 말자. 숫자 1과 0은 구별하기 힘들기 때문이다.
* 클래스 이름은 일반적으로 capWords(CamelCase)규칙을 사용한다. 
* 함수명은 소문자를 사용하자. 
* 서브 클래스의 경우 이름의 충돌을 막기 위해 밑줄 2개를 붙이자. 









