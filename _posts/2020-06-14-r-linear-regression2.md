---
layout: post
title: 회귀로 삼성전자와 현대자동차 주식 수익률 분석하기
date: 2020-06-14 09:00:00 +0300
category : R
use_math : true
---   

단순 선형회귀를 이용해서 이번에 코스피 지수 수익율과 삼성, 현대자동차 주식 수익율의 상관 괸계를 간단하게 분석해볼까 한다. 데이터는 한국 거래소에서 다운 받을 수 있다. 

## plot

우선 그레프를 그릴껀데, plot 그래프를 그리기 쉽게 모든 데이터를 merge를 한다.

```r
k_index <- read.csv("K_index.csv", header=T, stringsAsFactors = F)
s_stock <- read.csv("S_stock.csv", header=T, stringsAsFactors = F)
h_stock <- read.csv("H_stock.csv", header=T, stringsAsFactors = F)

all_data <- merge(merge(k_index, s_stock), h_stock)
```

head로 데이터를 보면 아래와 같이 볼 수 있다.

```r
head(all_data)
``` 

![all_data](/public/img/all_data.png){: width="50%" height="50%" }{: .center}

그래프는 아래와 같고, x축은 코스피 등락 비율, y축은 삼성 수익율 등락 비율이다.

```r
attach(all_data)
plot(k_rate, s_rate, col='blue')
```

![s_stock2](/public/img/s_stock2.png){: width="50%" height="50%" }{: .center}

여기서 회귀 직선을 그으면 아래와 같은 그림을 볼 수 있다.

```r
s_model <- lm(s_rate~k_rate, all_data)
abline(s_model, col='red
```

![s_stock3](/public/img/s_stock3.png){: width="50%" height="50%" }{: .center}

현대도 삼성과 마찬가지로 그래프를 그리면 아래와 같다.

```r
plot(k_rate, h_rate, col='purple')
h_model <- lm(h_rate~k_rate, all_data)
abline(h_model, col='brown')
```

![h_stock](/public/img/h_stock.png){: width="50%" height="50%" }{: .center}

## 데이터 분석 

10년치 데이터를 가지고 그래프를 그리면 아래와 같이 그릴 수 있고, 기울기를 보면 현대는 1.06, 삼성은 1.02임을 알 수 있다. 

![10Ydata](/public/img/10Ydata.png){: width="50%" height="50%" }{: .center}

전체적으로 봣을때는 비슷비슷 한거 같다. 그렇다면 상관 계수를 한번 살펴보자. 처음 데이터를 가지고 상관 계수를 구하면 아래와 같다.

![cor](/public/img/cor.png){: width="50%" height="50%" }{: .center}

그리고 10년치 데이터를 사용하여 상관 계수를 구하면 아래와 같다.

![cor2](/public/img/cor2.png){: width="50%" height="50%" }{: .center}

그렇다면 상관계수와 기울기를 가지고 어떤 결론을 낼 수 있을까? 

이 작업에 **베타**라는 것을 구하는데 베타는 **시장과의 상관성**을 말한다. 시장과의 상관성이란 시장을 움직이는 것에 따라 얼마나 탄력적으로 움직이는지를 말한다. **기울기**가 낮을수록 뚝심이 강해 시장과 상관없이 움직이는 주식이고, 기울기가 높을수록 탄력적으로 움직이는 주식이다. 수익률이 낮더라도 안전하게 벌고 있다면 기울기가 낮은 것을 선택해야 하며, 위험성이 높아도 수익률이 높은 것을 하려면 기울기가 높은 것을 선택해야 한다. **상관계수**는 시장과 얼마나 비슷하게 움직이냐는 것을 찾는 것이다. 현업에서는 0.65에서 0.70위부터 가치 있다고 판단하고 투자 분석을 한다고 한다. 


현재 주식 투자를 하지는 않겠지만, 아무튼 재밌는 데이터였다.



