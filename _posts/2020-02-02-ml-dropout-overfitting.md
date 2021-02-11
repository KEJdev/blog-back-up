---
title:  오버피팅 억제를 위한 방법! Dropout!
date:   2020-02-01 09:00:00 +0300
categories:  [Machine Learning, Machine Learning-Python]
tags : [ML,Python, 신경망]
sitemap :
math: true
mermaid: true
changefreq : always
priority : 1.0
use_math: true
---

오버피팅을 억제하기 위한 방법으로 Dropout에 대해 알아보도록 하겠습니다. 오버피팅은 학습을 시키면서 흔히 접할 수 있는 문제이며, 풀어야 할 문제 중 하나 입니다. 오늘은 이러한 오버피팅에 대한 문제를 바로 잡을 수 있는 방법 중 가장 간단한 방법에 대해 알아보겠습니다.

--------

### Dropout

Dropout은 오버피팅을 억제하기 위해 뉴런을 임의로 삭제하면서 학습하는 방법입니다. 

<img src="../../assets//images/Dropout.png" >

신경망 전체를 학습시키지 않고 일부 노드만 무작위로 골라 학습 시키는 방법입니다. 학습하는 중간중간 일정 비율로 노드들을 무작위로 골라 출력을 0으로 만들어 신경망의 출력을 계산하는 방법입니다. Dropout을 적용하면 학습되는 노드와 가중치들이 매번 달라지기 때문에 신경망이 과적합에 빠지는 것을 예방할 수 있습니다.

Dropout의 개념을 쉬운 예를 들어서 애기하면, 전문가가 많으면 오히려 오답이 나올 수 있으며, 사공이 많으면 배가 산으로 간다. 라는 속담을 생각하면 조금 더 쉽게 이해 할 수 있습니다. 

여기서 사공이 많으면 배가 산으로 가기 때문에 몇 명의 전문가만 선별하여 반복적으로 같은 결과가 나오면 그것을 답으로 선택하겠다. 라고 하는 것이 **앙상블**이라고 하는 학습 방법이 있는데, Dropout과 자주 사용 되는 학습 방식입니다. 

<center><img src="../../assets//images/Dropout2.png" ></center>

예를 들어 위와 같은 결과를 내는 신경망이 있다고 할 때, 드롭아웃(Dropout)을 적용하게 되면 아래 그림과 같을 수 있습니다.

<center><img src="../../assets//images/Dropout3.png" ></center>

Dropout은 신호를 보내지 않기 때문에 이런 결과를 얻을 수 있습니다. 

<center><img src="../../assets//images/Dropout4.png" ></center>


