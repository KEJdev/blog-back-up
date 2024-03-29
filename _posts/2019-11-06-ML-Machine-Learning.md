---
title:  퍼셉트론(Perceptron)이란?
date:   2019-11-06 09:00:00 +0300
categories:  [Machine Learning ]
sitemap :
math: true
mermaid: true
changefreq : always
priority : 1.0
---

퍼셉트론(Perceptron)이란 무엇인지, 딥러닝의 역사에 대해 알아보겠습니다. 아시다시피 "딥러닝" 이라는 분야가 이렇게까지 뜨거워진지는 그리 오래되지는 않았습니다. 하지만 딥러닝 분야는 1943년부터 조금씩 조금씩 시작하고 있었습니다.

그렇다면 이제 퍼셉트론이 무엇인지, 역사가 어떻게 되는지 알아보겠습니다.

## History  

- 1943년  
미국의 **신경외과** 의사인 워렌 맥걸록에 의해서 발단이 되었습니다.   


- 1957년  
프랑크 로젠 블라크가 퍼셉트론 알고리즘을 보안했습니다.
사람의 뇌의 동작을 전기 스위치 on/off로 흉내낼 수 있다는 이론을 증명했습니다.

## **Perceptron?**  

퍼셉트론은 인간의 신경세포 하나를 컴퓨터로 흉내낸 것을 말합니다. 인간의 신경세포라고해서 어려운 개념이 아닙니다. 고등학교 생물시간으로 돌아가보겠습니다. 우리는 고등학교 생물시간에 배운 3가지 용어가 있습니다.  

<center>1. 자극 ( Stimulus )  </center>
<center>2. 반응 (Response)</center>
<center>3. 역치 (Threshold)</center>

**<center>"특정 자극이 있다면 그 자극이 어느 역치 이상이여야만 세포가 반응한다"</center>**  


저 문장을 예를 들어서 이야기 해보겠습니다. 짜게 먹는 사람은 자기가 평소에 먹는만큼 음식이 짜지 않으면 싱겁다고 느낍니다. 즉,역치 이하의 자극은 무시하는거죠. 반대로 싱겁게 먹던 사람이 짜게 먹기 시작해서 오랜 시간이 지나면 예전에 먹던 싱거운 음식에 만족을 하지 못하게 됩니다. 즉, 역치가 올라가게 됩니다. 이제 퍼셉트론의 개념에 대해 알았으니 계속해서 역사에 대해 알아보겠습니다.


- 1969년  
이때, "퍼셉트론은 단순 선형분류기에 불과하다."라고 민스키라는 사람이 지적하게 됩니다.   
왜 이런 결론이 나왔냐면 xor 분류를 못한다고 단정했기 때문입니다.  


|  <center>입력(xor)</center> |  <center> x1 </center> | <center> x2 </center> | <center> t (타겟)</center> | 
|:--------:|:--------:|:--------:|:--------:|
|**i1**|0|0|0|
|**i2**|0|1|1|
|**i3**|1|0|1|
|**i4**|1|1|0|

이후에, 인공지능의 침체기라고해서 겨울기가 시작되었습니다.
그러다 중간층을 넣는다라는 해결책(다층 퍼셉트론)을 발견하게 되고 다시 인공지능에게 봄이 오는 시기가 오기 시작했습니다.  

|<center>입력(xor)</center>|<center> x1 </center>|<center> x2 </center>|<center> or 게이트 결과 (중간층) </center> | <center> not and 게이트 결과 </center> |<center> and </center> | 
|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|
|**i1**|0|0|0|1|0|
|**i2**|0|1|1|1|1|
|**i3**|1|0|1|1|1|
|**i4**|1|1|0|0|0|  


- 1970년 중반  
논문을 하나 발표하게 됩니다. 바로 **역전파**알고리즘(다층 퍼셉트론)입니다.
당시 컴퓨터의 연산으로는 이 이론을 구현하기 어려웠기 때문에 논문으로만 존재했다고 합니다.  

- 1986년  
은닉층을 갖는 다층 퍼셉트론 + 오류 역전파 학습 알고리즘 구현에 성공했고 덕분에 현재의 인공지능이 있게 되었습니다. 

퍼셉트론은 상당히 간단했는데, 이것이 쭉 이어져 인공지능을 만들어 낸것이 신기한거 같네요.