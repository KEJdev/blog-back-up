---
layout: post
title: 간단한 K-Nearest Neighbors(Knn)자동화 스크립트 만들기
date: 2020-02-10 09:00:00 +0300
category : R
---

이제 knn알고리즘이 무엇인지나, 코드짜는 것에 익숙해졌는데, 앞으로 다양한 데이터를 만나더라도 손쉽게 스크립트 하나로 knn을 돌리기 위해 간단하게 만들어보겠습니다. 

## knn 자동화 스크립트 

우선 파일명을 입력 받고, 컬러명이 있는지에 관한 유무와 라벨이 위치한 번호 마지막으로 제거할 컬럼의 위치를 입력 받아보겠습니다. 

```r
library(data.table)
library(class)

input_table <- readline('csv파일을 입력하세요. ex) emp.csv : ')
input_header <- readline('컬럼명이 있습니까? ex)T OR F : ')
input_label_num <- readline('라벨이 위치한 번호을 입력하세요. ex)N (N>=1) : ')
input_rm_num <- readline('제거할 컬럼 위치의 번호를 입력하세요. ex) n,n,n') 
```

그리고 헤더 유무 검사 그리고 셔플 기능과 라벨 위치를 정수형으로 변경하고, 혹시 모를 na 값을 제거가 필요할 것 같으니 작성해보겠습니다.

```r
### 셔플 기능 추가
table_name <- table_name[sample(nrow(table_name)), ]

### na값 제거
table_name <- na.omit(table_name)

### 라벨 위치를 정수형으로 변경(추후 사용을 위해)
input_label_num <- as.integer(input_label_num
```

그리고 가장 중요한 컬럼제거와 라벨을 factor로 변경하는 것, 그리고 라벨을 가장 마지막 컬럼으로 이동하는 것을 작성해보겠습니다.

```r
### 제거할 컬럼 제거
split_num<-strsplit(input_rm_num, ',')
for(i in split_num){
table_name <- table_name[,-as.integer(i)]
}

### 라벨 위치보다 앞에 위치한 컬럼들의 갯수를 카운트함
cnt <- 0
split_num <- unlist(split_num)
cnt<-sum(ifelse(as.integer(split_num) < input_label_num, 1, 0))

### 컬럼을 제거하고 실제 라벨 위치
label_loc <- input_label_num - cnt

### 라벨을 factor로 변경
label_tmp <- factor(table_name[,label_loc])

### 라벨을 가장 마지막 컬럼으로 이동
table2 <- table_name[,-label_loc]
table2$label <- label_tmp
```

그리고 가장 중요한 데이터를 정규화 해주는 함수와 데이터 나눠보겠습니다. 

```r
### 정규화 함수
normalize <- function(x){
return((x-min(x))/(max(x)-min(x)))
}

### 정규화 데이터 삽입
table2[,1:(ncol(table2)-1)] <- as.data.frame(lapply(table2[,1:(ncol(table2)-1)],normalize))

### 데이터 나누기
mm <- round(nrow(table2)*2/3)

### 데이터 설정
train_data <- table2[1:mm,1:(ncol(table2)-1)]
test_data <- table2[(mm+1):nrow(table2), 1:(ncol(table2)-1)]

train_label <- table2[1:mm,'label']
test_label <- table2[(mm+1):nrow(table2),'label']
```

그리고 마지막으로 k값을 훈련 데이터 건수의 제곱근으로 취하고 knn결과를 확인해보겠습니다.

```r
### k값을 훈련데이터 건수의 제곱근으로 취하는 방법
k_n <- round(sqrt(nrow(train_data)))

###knn 결과 확인
result <- knn(train = train_data, test = test_data, cl = train_label, k=k_n)
round(prop.table(table(ifelse(test_label==result,'o','x')))*100,1)

knn_fun()
```

이러면 간단하게 knn 자동화 스크립트가 완성되네요. 복잡하게 만든게 아니고 간단한 데이터에서 사용하려고 만든 것이기 때문에 아마 복잡한 데이터에서는 돌아가지 않을수 있지만, 그래도 공부하면서 간단하게 돌려보기엔 좋을 것 같습니다. 다음엔 나이브 베이지 분류에 대해 알아보겠습니다. 전체 코드는 Github에 있습니다. 
