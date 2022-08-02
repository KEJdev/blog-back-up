---
title:  백준 10871번, x보다 작은 수 출력하기
date:   2020-07-10 11:00:00 +0300
categories:  [Program Language , Algorithm]
sitemap :
math: true
mermaid: true
changefreq : always
priority : 1.0
use_math: true
---

BAEKJOON 10871번 문제를 풀어보았다. for문만 사용할 줄 안다면, 푸는데는 2분도 채 걸리지 않을것이다.

### 백준 10871번 

문제는 아래와 같다.

<center><img src="../../assets/images/baekjoon3.png" ></center>

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

