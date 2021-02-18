---
title: 데이터 사이언스란? 
date:   2021-02-10 09:00:00 +0300
categories:  [Machine Learning, Statistics]
tags : [통계]
sitemap :
math: true
mermaid: true
changefreq : always
priority : 1.0
use_math: true
---


### 데이터 사이언스 ? 

**데이터 사이언스**는 단순하게 애기하면 곡선형 그래프를 찾는 작업이다.  
아래처럼 같은 데이터에 대해 선형 함수와 비선형 함수가 있다고 가정하자. 


<img src="../../assets/images/data-science.jpg">


그림에서 선형 함수와 비선형 함수 중 어느 함수가 주어진 데이터를 더 잘 설명하고 있는가? (지금 현재 그래프만 봐서는) 선형함수에 비해 비선형함수가 데이터에 대해 더 잘 설명하고 있다고 볼 수 있다. **데이터 속에 복잡한 규칙이 숨겨져 있을 때, 최적의 (비)선형 함수를 찾아내는 작업**을 데이터 사이언스라고 이야기 할 수 있다. 

여기서 기억해야 댈 점은, 머신러닝 또한 데이터의 규칙을 찾기 위한 하나의 도구라는 점이다. 즉, 머신러닝은 데이터 속에 숨겨진 규칙들을 찾아내는 모델링 작업의 일환임을 기억하자. 


### 비선형 패턴을 찾기 어려운 이유 ? 

그런데 왜 우리는 비선형 패턴을 찾아내기 어려운걸까?   
비선형 패턴의 종류는 무한하지만 우리가 보유하고 있는 샘플 데이터는 전체를 아우르지 못한다. 그 이유는 우리가 찾아낸 패턴은 전체가 아니라 샘플 데이터에 불과하기 때문이다. 모든 데이터는 시간이 지남에 따라 데이터의 패턴이 바뀌고 모델을 새롭게 업데이트 해야하는 경우가 발생하게 되기 때문이다. 이 뜻은 선형 모델에 비해 비선형 모델은 모델 학습에 필요한 계산 비용이 매우 크다는 것을 의미한다. 


### 머신러닝? 딥러닝? 인공지능? 데이터 사이언스? 

포스팅 주제와 약간 떨어진 이야기일 수 있지만, 머신러닝 개발자로 4년차 접어드니 들면서 다른 사람들의 이력서를 보거나 면접을 보면서 느끼게 되는 것들이 꽤 있어 이번에 이야기 해볼까한다.  

주변을 살펴보면 **딥러닝**이라는거 배우고 싶은데요 ? **인공지능**이라는거 배우고 싶은데요? 또는 **제가 만든 신경망이 이렇게나 좋은 정확도를 내었습니다** 하며 이력서를 내는 경우가 많다. 실제 면접에서 이야기해보면 정말 잘 정제되어 있는 데이터를 가지고 신경망을 만든 사람이 있고 날것의 데이터를 직접 처음부터 정제해서 신경망을 만드는 사람들도 있다.  

내가 이야기 하고 싶은 것은 신경망이 모든 문제 풀이에 대해 만능이 아니라는 것이다. 어떤 데이터에는 통계로도 풀 수 있으며, 신경망으로도 풀 수 있다. **데이터 분석이 그만큼 중요**하다. **데이터의 특성을 이해**하고 모델을 만들도록 하자. 



