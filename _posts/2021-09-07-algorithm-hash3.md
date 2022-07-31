---
layout: post
title: 프로그래머스 - 완주하지 못한 선수
date: 2021-09-07 09:00:00 +0300
category : Algorithm
---

링크 : [프로그래머스 - 완주하지 못한 선수](https://programmers.co.kr/learn/courses/30/lessons/42576)   


**Answer:**

```python 
def solution(participant, completion):
    find_val, find_val2 = {},{}

    for j,i  in zip(participant,completion):
        count = find_val.get(j,0)
        find_val[j] = count + 1
        count = find_val2.get(i,0)
        find_val2[i] = count + 1
    
    for key in find_val:
        try:
            if find_val[key] != find_val2[key]:
                answer = key
        except KeyError:
            answer = key
    return answer
```
