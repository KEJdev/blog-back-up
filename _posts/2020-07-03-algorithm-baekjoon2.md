---
layout: post
title:  "백준 1330번, 두 수 비교하기(if) "
date:   2020-07-03 11:00:00 +0300
image:  assets/images/baekjoon2.png
categories:  [Program Language , Algorithm]
tags : [알고리즘,Python]
sitemap :
math: true
mermaid: true
changefreq : always
priority : 1.0
use_math: true
---


간단하게 두 수 비교하는 백준 알고리즘을 풀어보았다.  
사실 if문 배우면서 누구나 한번쯤은 해본거라 사실 고민할거리도 되지 않았다 .....



----------

### 백준 1330번 

문제는 아래와 같이 간단하게 두 수를 비교하는 것이다.


<center><img src="../assets/images/baekjoon2.png" ></center>


**Answer:**

```python 
a,b = map(int, input().split())

if a > b :
    print(">")
elif a < b :
    print("<")
else:
    print("==")
```

그런데 문제 다 풀고 나서 숏코딩 코드를 보았는데, 정말 많이 놀랬다.

**숏코딩:**
```python
a,b=map(int,input().split())
print(['><'[a<b],'=='][a==b])
```

내가 진짜 공부를 안하고 놀기만 했구나라는 사실에 대해 알게 되었다. 
