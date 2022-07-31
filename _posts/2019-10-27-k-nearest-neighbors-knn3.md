---
layout: post
title: K-Nearest Neighbors(Knn)을 이용한 구매여부 분류하기
date:  2019-10-27 09:00:00 +0300
category : R
---


knn을 사용하여 조금 의미 있는 결과를 가지고 결과를 뽑아내보려고 한다.  
데이터는 [여기](https://github.com/KEJdev/DataSet)에서 데이터를 다운 받을 수 있다.

## DataSet  

데이터를 열어보면 나이, 월수입, 상품 구매여부, 나이가 있다.  
이 데이터를 이용해, 백화점 또는 소셜커머스 회사에서 데이터 분석을 통해 구매자가 제품을 구매할 고객인지 아닌지를 알아내려고 한다고 가정해보고 knn을 이용하여 문제를 풀어보도록 한다. 


## Nomalize (정규화)

데이터를 불러오자.

```r
buy<-read.csv("buy.csv",fileEncoding = "euc-kr") 
```  

![dataset1](/public/img/dataset1.png){: width="25%" height="25%" }{: .center}

이 데이터에서 scale함수를 이용하여 나이 컬럼을 정규화 해주었다. 

```r
buy$age <- scale(buy$나이)
```

![dataset2](/public/img/dataset2.png){: width="30%" height="30%" }{: .center}


뒤에 age컬럼이 추가와 동시에 정규화 된 컬럼이 추가가 된 것을 확인할 수 있다.  

```r
buy$pay <- scale(buy$월수입)
```

![dataset3](/public/img/dataset3.png){: width="35%" height="35%" }{: .center}

위와 같이 컬럼이 또 추가 된 것을 확인 할 수 있다. 그럼 이제 knn을 이용하여 구매분류를 해보자.

## knn 구매여부 분류하기   
 
```r
train_data<-buy[,c(4,5)]
train_label<-buy[,3]
```

첫번째 줄은 4, 5번째 컬럼만 따로 train_data이라는 변수에 담겟다는 의미이다. 두번째 줄은 3번째 컬럼만 train_label이라는 변수에 담겠다는 의미이다. 

```r
test_data <- data.frame(age=44, pay=400)
```

나이가 44살에 월급이 400이라는 데이터를 하나 만들었다. 여기서 **주의!** test data도 마찬가지로 정규화를 해주어야 결과값을 볼 수 있다. test data도 정규화 작업을 한 후에 knn을 해준다. test data도 정규화 했다고 치고, 결과를 출력해 보겠다.

```r
result <-(test_data, test_data, train_label , k=5, prob =TRUE)
```

출력하면 "구매"라는 결과를 볼 수 있다.










