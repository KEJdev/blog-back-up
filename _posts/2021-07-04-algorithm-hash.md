---
title:  프로그래머스 - 전화번호 목록
date:   2021-07-04 09:00:00 +0300
categories:  [Program Language , Algorithm]
tags : [알고리즘,Python]
sitemap :
math: true
mermaid: true
changefreq : always
priority : 1.0
use_math: true
---


[프로그래머스 - 전화번호 목록](https://programmers.co.kr/learn/courses/30/lessons/42577)을 풀었는데, 다들 어쩜 그렇게 잘푸는걸까 .... 내가 푼 답이 부끄러워지는 순간..★

**Answer:**

```python 
import collections

def solution(phone_book):
    book = sorted(collections.Counter(phone_book).keys())
    for i in range(len(book)-1):
        if book[i+1].startswith(book[i]):
            answer = False
            break
        else:
            answer = True
    return answer
```
