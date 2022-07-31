---
layout: post
title: 나이브 베이즈(Naive Bayes)를 이용한 영화 장르 분류
date: 2020-02-12 09:00:00 +0300
category : R
use_math : true
---

나이브 베이즈를 활용한 영화 장르 분류를 이번에 해보겠습니다. 예전에 포스팅했던 knn과 마찬가지로 그리 어렵지도, 코드가 길지도 않아서 한두번 해보면 금방 익숙해 질꺼 같습니다.

## DataSet

데이터는 선호하는 영화장르 데이터를 사용했으며, 데이터는 [여기](https://github.com/KEJdev/DataSet/tree/master/DataSet)에서 다운받아 보실 수 있습니다. 물론 포스팅에서 사용된 코드는 제 Github에서 전부 보실 수 있습니다.

```r
# 패키지 설치 
install.packages("e1071")
library(e1071)

movie <- read.csv("movie.csv", header=T)
```

![NB2](/public/img/NB2.png){: width="70%" height="70%" }{: .center}

## Naive Bayes

나이브 베이즈는 아래와 같이 한줄이면, 모델이 완성됩니다. knn과 마찬가지로 그리 어렵지도 않으며 간단합니다.

```r
model <- naiveBayes(movie[1:5], movie$장르, laplace=0)
```

예측은 아래와 같이 작성하실 수 있습니다.

```r
result <- predict(model, movie[1:5]) # 장르를 제외한 라벨들로 예측을 해보겠다는 코드
```

![NB3](/public/img/NB3.png){: width="70%" height="70%" }{: .center}

예측이 일치하는지 확인하는 코드는 아래와 같습니다.

```r
movie$result <- result
```
![NB4](/public/img/NB4.png){: width="70%" height="70%" }{: .center}

거의 일치함을 알수 있습니다.

