---
layout: post
title: 백준 2588번, 빈 칸에 들어갈 수는? (곱셈) 
date: 2020-07-15 11:00:00 +0300
category : Algorithm
use_math : true
---   

BAEKJOON 2588번 문제는 빈 칸에 들어갈 수를 출력하는 문제이다. 사실 혼자서 어렵게 풀고 있었다가 나중에서야 "아.." 하고 나의 바보스러움에 감탄하며 문제를 풀었다. 

## 백준 2588번 

문제는 아래와 같다.

![baekjoon5](/public/img/baekjoon5.png){: width="100%" height="100%" }{: .center}

**Answer:**

```python 
a = int(input())
b = list(input())
b.reverse()
for i in range(3):
    num = str(a*int(b[i]))
    print(num)
print(a*int(b[2]+b[1]+b[0]))
```
