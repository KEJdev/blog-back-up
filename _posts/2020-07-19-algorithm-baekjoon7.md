---
layout: post
title: 백준 10951번 while문으로 A+B를 출력하자(EOF) 
date: 2020-07-19 11:00:00 +0300
category : Algorithm
use_math : true
---   

이번 문제는 간단하게 예외처리만 하면 되는 문제인데, 문제에 EOF라고 명시가 되어 있지 않아서 조금 해맸다. 나중에 EOF라는 것를 밖에 링크 누를때 확인하고 나서야 풀 수 있었다...ㅠㅠ

## 백준 10951번 

문제는 아래와 같다.

![baekjoon7](/public/img/baekjoon7.png){: width="100%" height="100%" }{: .center}

**Answer:**

```python 
while(True):
    try :
        a, b = list(map(int, input().split(' ')))
        print(a + b)
    except EOFError:
        break
```
