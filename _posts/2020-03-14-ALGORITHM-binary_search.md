---
layout: post
title: 검색 알고리즘? 파이썬으로 이진탐색 구현하기
date: 2020-03-14 11:00:00 +0300
category : Algorithm
use_math : true
---  

이진 검색 알고리즘(binary search algorithm)은 오름차순으로 정렬된 리스트에서 특정한 값의 위치를 찾는 알고리즘입니다. 처음 중간의 값을 임의의 값으로 선택하여, 그 값과 찾고자 하는 값의 크고 작음을 비교하는 방식입니다. 


```python
data = [ 1, 7, 11 , 12, 14 , 23, 33, 47, 51, 64, 67, 77, 130, 672, 871 
```

위와 같은 데이터가 있을 때, 이진 탐색을 구현하면 아래와 같습니다. 

```python
def binary_search(in_data, input_num):
    
    in_data = sorted(in_data)
    start_num = 0
    end_num = len(in_data) - 1

    while start_num <= end_num:

        mid_num = int((start_num + end_num) / 2)

        if in_data[mid_num] == input_num:
            return print('입력하신 {0}이(가) 있습니다.'.format(input_num))

        elif in_data[mid_num] > input_num:
            end_num = mid_num - 1

        elif in_data[mid_num] < input_num:
            start_num = mid_num + 1

    return print('입력하신 {0}이(가) 없습니다.'.format(input_num))
```

데이터의 중간의 값을 선택하고 값의 크고 작음을 비교하는 방식이기 때문에 if문을 사용하면 간단히 구현할 수 있습니다. 





