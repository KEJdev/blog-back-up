---
layout: post
title: 백준 10871번, x보다 작은 수 출력하기
date: 2020-07-03 10:00:00 +0300
category : Algorithm
use_math : true
---   

BAEKJOON 10871번 문제를 풀어보았다. for문만 사용할 줄 안다면, 푸는데는 2분도 채 걸리지 않을것이다.

## 백준 10871번 

문제는 아래와 같다.  

![baekjoon3](/public/img/baekjoon3.png){: width="100%" height="100%" }{: .center}

**Answer:**

```python 
a = list(map(int,input().split(' ')))
b = list(map(int,input().split(' ')))

num = []
for i in b:
    if a[1] > i:
        num.append(i)
    else:
        pass
print(*num, sep = " ")
```

