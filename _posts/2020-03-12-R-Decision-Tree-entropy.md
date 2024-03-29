---
title:  의사 결정트리와(Decision Tree)엔트로피(entropy)
date:   2020-03-12 09:00:00 +0300
categories:  [Machine Learning, ML]
sitemap :
math: true
mermaid: true
changefreq : always
priority : 1.0
use_math: true
---

의사 결정트리에 대해 알아볼껀데, 의사 결정트리가 어떤 상황에서 사용되는지 구현하려면 무엇이 필요한지에 대해 알아보겠습니다.

## 의사 결정트리(Decision Tree)

회귀식을 세울 때 중요한 변수(컬럼)들을 선택해야 하는 상황에서 어떠한 컬럼이 중요한지 판단이 안설때, 의사 결정트리를 이용하면 중요한 변수를 골라낼 수 있습니다. 

예를 들어 회사 지원자에게 떨어진 이유를 명확히 설명해줘야 하는 경우나 은행에서 대출을 해줄 때, 대출을 해줄지 말지의 여부를 기업 데이터를 보고 결정해야 하는 경우 등이 있습니다. 또 의학면에서는 질병에 대한 진행바탕으로 올바른 처방을 위해 결정해야하는 경우에 사용되기도 합니다. 

<center><img src="../../assets//images/tree.png" ></center>
<center>Decision Tree 예시</center>

## 엔트로피(entropy)와 정보획득량 

의사 결정트리를 이야기 하다가 왜 갑자기 엔트로피 이야기가 나올까요 ?   
결정트리를 만들 때, 가장 먼저 해야할 일은 **중요한 변수(컬럼)**을 찾는 것입니다. 즉, 정보획득량이 높은 변수를 찾아야하는데, 그때 엔트로피 함수를 사용합니다.  

* 엔트로피(entropy) 함수  

엔트로피는 **"데이터의 불확실성이 얼마나 되는가?"**를 알수 잇는 지표입니다. 즉, **엔트로피 지수가 높다는 것은 불확실성이 높다**는 것을 알 수 있습니다.

* 엔트로피 그래프 

```r
curve(-x * log2(x) - (1 - x) * log2(1 - x),
      col="red", xlab = "x", ylab = "Entropy", lwd=4)
```

<center><img src="../../assets//images/entro.png" ></center>

정보획득량은 분할전 엔트로피에서 분할 후 엔트로피를 빼면 정보획득량을 구할 수 있습니다.