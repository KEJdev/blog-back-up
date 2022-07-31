---
layout: post
title: 프로그래머스 - 베스트 앨범
date: 2021-11-18 09:00:00 +0300
category : Algorithm
---

링크 : [프로그래머스 - 베스트 앨범](https://programmers.co.kr/learn/courses/30/lessons/42579)   


**Answer:**

```python 
def solution(genres, plays):
    temp,temp_index = {},{}
    answer = []

    for val, key in zip(plays, genres):
        if temp.get(key):
            temp[key].append(val)
        else:
            temp[key] = [val]

    sort_temp = dict(sorted(temp.items(), key = lambda item: sum(item[1]), reverse=True))

    for k in sort_temp:
        df_val = sorted(sort_temp[k], reverse=True)
        if len(sort_temp[key]) >= 2:
            sort_temp[k] = df_val[:2]

    for key in set(genres):
        temp_index[key] = [i for i, ele in enumerate(genres) if ele == key]

    for k in sort_temp:
        for v1, v2 in zip(sort_temp[k], temp_index[k]):
            if len(sort_temp[k]) != len(set(sort_temp[k])):
                df = [i for i, ele in enumerate(plays) if ele == v1]
                answer.extend(df)
                break
            else:
                answer.append(plays.index(v1))
    return answer
```
