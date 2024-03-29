---
title:  Relu함수에서 변형된 활성화 함수들(leake Relu,Swish)
date:   2019-11-07 09:00:00 +0300
categories:  [Machine Learning, ML]
sitemap :
math: true
mermaid: true
changefreq : always
priority : 1.0
use_math: true
---

저번 포스팅에서 이야기 한 활성화 함수 3가지는 가장 기본적인 활성화 함수이며, 흔히 쓰이는 활성화 함수입니다. 그런데 이 활성화 함수 외에도 더 많은 활성화 함수가 있습니다. 오늘은 그 외 나머지 활성화 함수에 대해서 이야기 해보도록 하겠습니다.  

오늘 포스팅할 대부분의 활성화 함수는 Relu함수의 변형 버전이 많습니다.  

## Relu 함수에서 변형된 활성화 함수들  

Relu 함수에서 변형된 활성화 함수들은 아래와 같습니다. 물론 여기서 Softplus와 Tanh함수는 변형된 함수는 아니라는 점! 기억해주세요.  

<center><img src="../../assets//images/at.png" ></center>  

위의 그래프에서 Leaky ReLu, ELU가 Relu의 변형 함수입니다. 위 그래프 외에도 p-Relu와 swish함수도 다루어보겠습니다.  

Relu함수는 저번 포스팅때 현업에서도 많이 쓰인다고 이야기 했습니다. 그런데 왜, Relu의 번형들이 많이 생겨나는 걸까요?  
Relu 또한 저번에 말했던 vanishing현상이 생긴답니다. 왜냐하면 $$x < 0$$ 때는 0을 출력하고 $$x>0$$을 출력하기 때문에 학습할 때, 뉴런이 죽는 경우가 발생하기 때문입니다. 그래서 Relu에 약간의 변화를 줘서 0이 되어 뉴런이 죽지 않도록, 신경망이 죽지 않도록 활성화 함수를 변형 시킨겁니다.

우선 **leake Relu**함수에 대해 알아보겠습니다.  

<center><img src="../../assets//images/leake.png" ></center>  

leake Relu는 기존의 Relu의 음수 부분에 약간의 기울기를 준 함수입니다. 때문에 이 활성화 함수는 기울기가 0일때의 문제점을 해결하기 위해 나온 함수입니다.   

두번째 활성화 함수는 **P-Relu**입니다.  

<center><img src="../../assets//images/prelu.png" ></center>  

P-Relu는 leake Relu와 비슷하지만 피라미터는 $$∂$$를 추가해서 $$x < 0$$ 때 학습에 따라 각도를 바꾸는 활성화 함수입니다. 좋아보이는 이 활성화 함수도 단점이 존재합니다. Out of memory라는 에러를 만날 수 있는데, 그 이유는 학습을 하는 동안에 그 속에서도 또 다시 학습을 하기 때문입니다.   

세번째 함수는 **ELU**함수입니다.  
ELU 함수는 OOM(Out of memory)를 해결하기 위해 나온 함수입니다.  0이하의 기울기가 곡선이므로 미분이 잘되며, OOM이 뜨지 않으며 정확도가 높다고 합니다. 대신 계산량이 많아 학습시간이 오래걸리는 단점이 있습니다. 

마지막 함수는 비교적 최근에 나온 함수인 **Swish**함수입니다. 

<center><img src="../../assets//images/swish.png" ></center>  

2017년 11월 경 구글에서 만든 함수라고 합니다. 가장 효율성이 좋았다고 이야기 합니다.  

아마 그래프를 보면서 느끼셨겠지만, 정확도와 효율이 좋은 함수를 보면 음수 기 울기 부분이 상당히 매끄러운 모습을 볼 수 있습니다. 이 뜻은 미분과 기울기의 매끈함이 활성화 함수의 가장 주요 포인트라 할 수있습니다.   

Relu와 Swish, 이 두가지의 차이점을 분명하게 보여주는 그래프는 아래와 같습니다.  

<center><img src="../../assets//images/des.png" ></center>  

Relu와 Swish의 차이점이 분명하게 보이네요. Swish 또한 미분으로 인한 계산량이 많다는 단점은 존재하지만, 정확도와 OOM, vanishing현상을 막기 위해 여러가지 연구를 하고 있다는 점을 잘 알아둬야겠네요. 