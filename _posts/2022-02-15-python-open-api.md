---
title: 간단하게 오픈 API 사용하기
date:   2022-02-15 09:00:00 +0300
categories:  [Program Language , python]
tags : [Python]
sitemap :
math: true
mermaid: true
changefreq : always
priority : 1.0
use_math: true
---

요즘은 읽고 싶은 논문이나, 만들고 싶었던 것들이나, (벽보고)면접 준비하며 하루하루를 보내고 있다.
작년에 의료 데이터 받으려고 심사 한번 거쳤는데, 떨어졌다가 드디어 IRB심사를 통과해서 데이터를 받게 되어 기분이 좋다. 
이제 논문에 올릴 GAN기반 모델을 만들어야는데, 아직까진 조금 여유가 있어서 이번에 오픈 API를 사용하는 방법에 대해 포스팅을 할까한다. 

------

회사 그만두고 잠시, 다른 회사 노가다 업무 하나 맡아서 했었는데, 그에 대한 일이다. 
내가 맡았던 업무는 각종 병원 관련 데이터를 긁어모으는 일이였는데, 생각보다 너무 노가다!
크롤링을 하면 직접하는 것보다 빠르겠지만, 그래도 한국인의 성격을 생각하면 느리게만 느껴진다! 
그래서 오픈 API를 찾아보니 있어서 그걸로 대체해서 사용했다. 

우선 오픈 API를 사용하려면 [공공데이터포털](https://www.data.go.kr/index.do)에 로그인을 해야한다. 

<center><img src="../../assets/images/open_api_1.png" ></center> 

그리고 찾고자 하는 것을 검색해서 사용하고자 하는 API를 찾으면 된다. 

<center><img src="../../assets/images/open_api_2.png" ></center> 

API를 사용하려면 활용 신청을 해야는데, 오픈 API는 따로 심사를 하지 않고, 활용 신청 후 바로 사용이 가능하다.

<center><img src="../../assets/images/open_api_3.png" ></center> 

신청 후에 마이페이지 들어가서 확인해보면 아래와 같은 개발 계정을 볼 수 있다. 여기서 아래 인증키 두개 중에서 decoding 인증키만 복사한다. 

<center><img src="../../assets/images/open_api_4.png" ></center> 

그리고 아래로 내리면 인증키 설정하는 부분에 복사한 키를 넣는다.

<center><img src="../../assets/images/open_api_5.png" ></center> 

설정 완료되면 바로 API 테스트를 할 수 있다. 

<center><img src="../../assets/images/open_api_6.png" ></center> 

key - b_no에 검색하고자 하는 사업자 번호를 넣어서 테스트 해본다. 

<center><img src="../../assets/images/open_api_7.png" ></center> 

그럼 아래와 같이 리턴 값을 받을 수 있다. 

<center><img src="../../assets/images/open_api_8.png" ></center> 

이제 여기서 Python으로 실행해보기 위해 Curl을 복사한다. 복사 후 [링크](https://curlconverter.com/)를 눌러 Json으로 변환 시키자!

<center><img src="../../assets/images/open_api_9.png" ></center> 

json으로 변환이 끝나면 파이참에 붙여넣기를 해보자. 
그럼 아래와 같이 결과를 볼 수 있다. 그리고 검색하고자 하는 번호를 josn_data에 넣고 돌리면 끝난다. 

```python
import requests
import pprint

headers = {
    'accept': 'application/json',
    'Authorization': [본인의 인증키],
    'Content-Type': 'application/json',
}

params = (
    ('serviceKey', [본인의 인증키]),
)

json_data = {
    'b_no': [
        '1082122133',
        '1081296521',
        '1010158608',
        '1010201835'
    ],
}

response = requests.post('https://api.odcloud.kr/api/nts-businessman/v1/status', headers=headers, params=params, json=json_data)
result = response.json()["data"]

for val in result:
    pprint.pprint(val['b_stt'])
```

아래와 같이 결과를 확인 할 수있다. 

<center><img src="../../assets/images/open_api_10.png" ></center> 

아무래도 크롤링 보다 훨씬 빠른데, 1회 호출시 최대 100개씩 받을 수 있기 때문에 빠르고 편리하다.



