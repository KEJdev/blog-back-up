---
title:  백준 10869번, 사칙연산 
date:   2020-07-11 11:00:00 +0300
categories:  [Program Language , Algorithm]
sitemap :
math: true
mermaid: true
changefreq : always
priority : 1.0
use_math: true
---

BAEKJOON 10869번 문제를 풀어보았다. 간단하게 print에 사칙연산 출력만 하면 되기 때문에 금방 할 수 있다.

### 백준 10869번

문제는 아래와 같다.

<center><img src="../../assets/images/baekjoon4.png" ></center>

**Answer:**

```python 
a,b = map(int , input().split(' '))
print(a+b)
print(a-b)
print(a*b)
print(int(a/b))
print(a%b)
```
