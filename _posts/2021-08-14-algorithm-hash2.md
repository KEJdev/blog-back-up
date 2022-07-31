---
layout: post
title: 프로그래머스 - 위장
date: 2021-08-14 09:00:00 +0300
category : Algorithm
---

내 방식대로 [프로그래머스 - 위장](https://programmers.co.kr/learn/courses/30/lessons/42578)을 풀었다. 풀고나면 항상 다른 사람 풀이를 꼼꼼히 보는데, 다들 해시에 대해 이해를 잘하신거 같다.. 대단해...


**Answer:**

```python 
import collections

def solution(clothes):
    answer = 1
    for i in collections.Counter(dict(clothes).values()).values():
        answer *= (i+1)
    answer = answer-1
    return answer
```
