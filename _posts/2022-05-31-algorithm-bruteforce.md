---
layout: post
title:  백준 - 브루트포스(Brute Force) 단계별 문제 풀이(Python).
date: 2022-05-31 09:00:00 +0300
category : Algorithm
---

**링크 : [브루트 포스 문제집](https://www.acmicpc.net/step/22)**  

앞으로 꾸준하게 알고리즘을 풀려고 한다.  
최근 여러 일이 겹치다보니, '자기계발을 꾸준히 해야겠다!'는 생각이 많이 들어서 최대한 1일 1알고리즘을 해보려고 한다. 물론 어려운 문제 만나면 그게 안될 수 있겠지만, 한번  풀어봐야지!    

5월 29일~31일동안 백준에 있는 단계별 - 브루트 포스 문제집 풀었다.   
총 5문제였고 시간이 약간 걸렸던 문제는 '체스판 다시 칠하기' 였다.   
문제 이해하는데 좀 걸렸던 것 같다.   


## 브루트 포스

브루트 포스는 **모든 경우의 수를 무식하게 탐색** 하는 것을 말한다.  
데이터 전체를 탐색하기 때문에 완전 탐색, 전체 탐색이라고도 불린다.  

* 장점 
    1. 모든 경우의 수를 다 검색하기 때문에 (이론상)정확도 100%를 보장함.
    2. 알고리즘 구현하기 쉽다.

* 단점  
    1. 문제의 복잡도(Complexity)에 매우 민감하다.
    2. 실행 시간이 오래 걸리고 메모리 효율면에서 비효율적이다. 


브루트 포스 종류에는 순차탐색, 백트래킹, DFS, BFS가 있다.


## 백준 - [블랙잭 (2798번)](https://www.acmicpc.net/problem/2798)

### 문제 요약
N장의 카드에 써져 있는 숫자가 주어졌을 때, M을 넘지 않으면서 M에 최대한 가까운 카드 3장의 합을 구해 출력하시오.


#### 내 풀이
입력 받은 수를 반복문으로 수의 합을 M에서 빼고, 음수가 아닐 경우에는 리스트에 담고, 마지막에 MAX을 출력한다. 

#### Answer:

```python 
k_cnt = list(map(int,input().split(' ')))
k_num = list(map(int, input().split(' ')))

temp = []
for i in range(0, len(k_num), 2):
    for j in range(1, len(k_num), 2):        
        for k in range(len(k_num)):
            k_sum = k_cnt[1]
            if k_num[k] not in [k_num[i], k_num[j]]:
                k_sum-=(k_num[i]+k_num[j]+k_num[k])
                if k_sum >= 0  :
                    temp.append(k_sum)
k_sum = k_cnt[1]
print(k_sum-min(temp))
```

## 백준 - [분해합 (2231번)](https://www.acmicpc.net/problem/2231)

### 문제 요약
자연수 N이 주어졌을 때, N의 가장 작은 생성자를 구해내는 프로그램을 작성하시오.

#### 내 풀이 
1부터 N까지 반복문을 통해 구한 분해값이 주어진 생성자랑 같으면 그 값을 출력한다.

#### Answer:

```python 
num = int(input())

ck = 0
for i in range(1,num+1):
    temp = 0
    temp = sum([int(j) for j in str(i)])
    if (temp+i) == num:
        print(i)
        ck+=1
        break
if ck == 0:
    print(0)
```

## 백준 - [덩치 (7568번)](https://www.acmicpc.net/problem/7568)

### 문제 요약
 각각 (x, y), (p, q)라고 할 때 x > p 그리고 y > q 이라면 우리는 A의 덩치가 B의 덩치보다 "더 크다"고 말한다. 학생 N명의 몸무게와 키가 담긴 입력을 읽어서 각 사람의 덩치 등수를 계산하여 출력해야 한다. 단, 서로 다른 덩치끼리 크기를 정할 수 없는 경우도 있다


#### 내 풀이
모든 경우의 수로 덩치가 큰 사람을 세면 된다. 

#### Answer:

```python 
num = int(input())
temp = []
for i in range(num):
    temp.append(list(map(int, input().split(' '))))

for i in temp:
    count = 1
    for j in temp:
        if i[0] < j[0] and i[1] < j[1]:
            count += 1
    print(count, end=" ")
```    

## 백준 - [체스판 다시 칠하기 (1018번)](https://www.acmicpc.net/problem/1018)

### 문제 요약
  MN개의 단위 정사각형으로 나누어져 있는 M×N 크기의 보드를 8×8 크기의 체스판으로 만들려고 한다. 
  체스판은 검은색, 흰색 번갈아 칠해졌다. 
  체스판을 색칠하는 경우는 두 가지인데, 하나는 맨 왼쪽 위 칸이 흰색인 경우, 하나는 검은색인 경우이다.  
  보드가 체스판처럼 칠해져 있다는 보장이 없어서, 아무대나 골라서 8x8로 잘랐을 경우, 다시 칠해야 하는 정사각형의 최소 개수를 구하는 프로그램을 작성하시오.

#### 내 풀이
행렬의 값에 따라 경우의 수를 나누어 흰색이라면 검은색으로 바꿔야 하는 수를 증가시키고,
검은색이라면 흰색으로 바꿔야 하는 수를 증가 시키고 둘 중에 가장 작은 값을 출력 리스트에 담고 마지막에 출력함. 


#### **Answer:**

```python 
N,M = map(int, input().split())
board, temp = [],[]
for _ in range(N) :
    board.append(input())

for i in range(N-7):
    for k in range(M-7):
        b,w = 0,0 
        for i_a in range(i,i+8):
            for k_a in range(k,k+8):
                if (i_a+k_a)%2 == 0:
                    if board[i_a][k_a] != 'W':
                        b+=1
                    else:
                        w+=1
                else:
                    if board[i_a][k_a] != 'B':
                        b+=1
                    else:
                        w+=1
        temp.append(min(b,w))
print(min(temp))
```   


## 백준 - [영화 감독 숌 (1436번)](https://www.acmicpc.net/problem/1436)

### 문제 요약
종말의 숫자란 어떤 수에 6이 적어도 3개이상 연속으로 들어가는 수를 말한다. 종말의 숫자란 어떤 수에 6이 적어도 3개이상 연속으로 들어가는 수를 말한다.
숌은 첫 번째 영화의 제목은 세상의 종말 666, 두 번째 영화의 제목은 세상의 종말 1666 이렇게 이름을 지을 것이다. 일반화해서 생각하면, N번째 영화의 제목은 세상의 종말 (N번째로 작은 종말의 숫자) 와 같다. 숌이 만든 N번째 영화의 제목에 들어간 숫자를 출력하는 프로그램을 작성하시오. 숌은 이 시리즈를 항상 차례대로 만들고, 다른 영화는 만들지 않는다.


#### 내 풀이
반복문으로 1부터 수를 증가시키면서 666이 나올 때마다 +1 씩 증가 시킴. N번째와 증가 시킨 값이 같아지면 break 문으로 탈출함.


#### Answer:

```python
num = int(input())
temp, cnt = 0,0

while cnt <= num:
    temp+=1
    if '666' in str(temp):
        cnt += 1
        
    if cnt == num:
        print(temp)
        break
```

