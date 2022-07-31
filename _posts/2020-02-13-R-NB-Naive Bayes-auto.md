---
layout: post
title: 나이브 베이즈(Naive Bayes)자동화 스크립트 만들기
date: 2020-02-13 09:00:00 +0300
category : R
use_math : true
---

knn에 이어서 나이브 베이도 자동화 스크립트로 만들어보겠습니다. 

## Naive Bayes 자동화 스크립트 

우선 파일명을 입력 받고, 컬러명이 있는지에 관한 유무와 라벨이 위치한 번호 마지막으로 제거할 컬럼의 위치를 입력 받아보겠습니다. 추가로 if문을 돌려서 패키지 설치가 되어 있으면 패스하고 아니면 설치하도록 하겠습니다.

```r
if (length(setdiff(packages, rownames(installed.packages()))) > 0) {
    install.packages(setdiff(packages, rownames(installed.packages())))  
}
    
library(tm)
library(gmodels)

input_table <- readline('csv파일을 입력하세요. ex) emp.csv : ')
input_header <- readline('컬럼명이 있습니까? ex)T OR F : ')
input_label <- readline('라벨 컬럼의 번호를 입력하세요. ex)N (N>=1) : ')
input_laplace <- readline('라플라스를 입력하세요. ex)n (0<n<1) : ')
```

그리고 헤더 유무 검사를 하겠습니다. 

```r
### 해더 유무 검사
if (input_header == 'T'){
table_name <- read.csv(input_table, stringsAsFactors = F, header=T)  
}
else {
table_name <- read.csv(input_table, stringsAsFactors = F, header=F)
}
```

이제 거의 다 끝났네요. 마지막으로 factor로 변환하고 라벨 번호와 라플라스 값을 숫자화 합니다.

```r
for (i in 1:ncol(table_name)){
table_name[,i] <- factor(table_name[,i])
}

### 라벨 번호, 라플라스 값 숫자화
input_label <- as.integer(input_label)
input_laplace <- as.numeric(input_laplace)
```

그리고 데이터를 나누고 나이브 베이즈합니다. 

```r
set.seed(1)
train_cnt <- round(0.75*dim(table_name[1]))
train_index <- sample(1:dim(table_name)[1], train_cnt,replace=F)

train_data <- table_name[train_index,]
test_data <- table_name[-train_index,]

table_name[,input_label]

model <- naiveBayes(train_data[,input_label]~., data=train_data, laplace = input_laplace)
result <- predict(model, test_data[,-input_label])

CrossTable(result, test_data[,input_label])
```

knn보다 더 간단하게 나이브 베이즈 자동화 스크립트가 완성 됫네요. 