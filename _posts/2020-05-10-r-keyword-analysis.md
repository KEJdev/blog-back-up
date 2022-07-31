---
layout: post
title: 미디어 트렌드 분석?헤드라인 뉴스 키워드 분석(사회)
date: 2020-05-10 09:00:00 +0300
category : R
use_math : true
---   

미디어는 한국 사회의 흐름을 압축적으로 담고 있는 Snapshot입니다. 지난 19년, 가장 대표적이고 강력한 미디어, **헤드라인 뉴스**로 한국 사회를 되돌아 볼까합니다.   

이번 포스팅은 사회 부분을 다뤄보겠습니다. SBS뉴스 사회 부분의 헤드라인 부분을 다 크롤링하여 문장을 단어별로 나눈 후 count 하였습니다.

## Web Crawling 

R을 이용하여 크롤링을 하려고 할때 아래와 같은 라이브러리가 필요합니다.

```r
# 필요 패키지 설치
library(gsubfn)
library(stringr)
library(XML)
```

크롤링 함수는 아래와 같이 URL을 입력받아 긁어오도록 하였습니다.

```r
SBSnews <- function(url){
  doc <- htmlTreeParse(url, useInternalNodes = T, trim = T, encoding="utf-8") 
  rootNode <- xmlRoot(doc)
-
  xmlName(rootNode)
  names(rootNode)

  result <- xpathSApply(rootNode, "//strong[@class='spml_tit']", xmlValue)
  print(idx)
  return(result)
}
```

크롤링 기간은 아래와 같이 정하겠습니다. 저는 1년씩 하나씩 긁어서 1년 단위로 정리하겠습니다. 

```r
urlbase <- "http://news.sbs.co.kr/news/programMain.do?prog_cd=R1&broad_date="
Start <- as.Date("2018/01/01")
yyyy <- substr(Start, 1, 4)
End <- as.Date("2018/12/31")
list <- seq(from = Start, to = End, by=1) 
list2 <- format(list, format="%Y%m%d")
urlfinal<- str_c(urlbase,list2)
```

그리고 for문으로 Crawling 해줍니다.

```r
idx <- 1 ## 초기화
result <- as.character()

for(url in urlfinal){ 
  print(idx)
  result <- c(result,SBSnews(url))
  idx <- idx + 1
}
str(result)
```

크롤링한 데이터를 저장하기 전에 1차적으로 간단하게 전처리 해주고 파일을 저장합니다. 

```r
fulltitle <- gsub("[\r\t\n]", "", result) 

news_df <- data.frame(category = substr(fulltitle,1,2),
                      fulltitle = fulltitle,
                      stringsAsFactors = F) 
str(news_df)

idx <- as.numeric(which(news_df$category=="스포")) # Category가 "스포" -> "스포츠"로 변경

for(n in idx){
  news_df$category[n] <- "스포츠"
}

news_df$title <- substring(news_df$fulltitle,3)
for(n in idx){
  news_df$title[n] <- substring(news_df$fulltitle[n],4)
}

news_df2 <- subset(news_df, !grepl("*클로징*", news_df$title)) 
news_df2 <- subset(news_df2,news_df2$title != "오늘의 주요뉴스")
rownames(news_df2) <- 1:nrow(news_df2) 
nrow(news_df)-nrow(news_df2) 
```

## Keyword

파일을 저장 후 데이터를 따로 전처리를 끝내고 나면 아래와 같이 사회관련 뉴스 부분을 정리 할 수 있는데, 여기서 가장 많은 키워드는 아무래도 ..... 검찰과 경찰이겠죠?

![keyword2](/public/img/keyword2.png){: width="100%" height="100%" }{: .center}

그리고 주기적으로 보이는 키워드는 아무래도 날씨와 관련 있는 재해 부분 키워드 입니다. 

![keyword3](/public/img/keyword3.png){: width="100%" height="100%" }{: .center}

저 부분을 제외하면 중요해 보이는 키워드는 아래와 같습니다. 

![keyword4](/public/img/keyword4.png){: width="100%" height="100%" }{: .center}

잠깐만 봐도 해당 키워드들은 한 해를 떠들썩하게 했던 사건사고 키워드라는 것을 알 수 있습니다. 잊으면 안되는 2003년도 대구지하철 참사부터 2009년 신종플루 2010년 김길태, 천안함 사건, 2014년 세월호 등 많은 중요 키워드를 보고 한국 사회에서 일어난 모든 흐름을 알 수 있습니다. 

다음에는 경제 관련해서 얼마나 많은 일이 있었는지에 대해 알아보겠습니다. 