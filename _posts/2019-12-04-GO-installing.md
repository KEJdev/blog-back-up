---
 
title:  GO 언어 설치하기
date:   2019-12-04 09:00:00 +0300
image:  assets/images/go1.png
categories:  [Program Language , Go]
sitemap :
math: true
mermaid: true
changefreq : always
priority : 1.0
---

GO언어를 설치해보도록 하겠습니다. 생각보다 설치하는 건 어렵지도 않고 여러가지 설정 할 것도 별로 없으니 10분이면 설치할 수 있습니다.   
우선 설치파일 다운해봅시다. [여기](https://golang.org/dl/)를 클릭하면 아래와 같은 화면이 나오는데 OS에 맞는 설치파일 다운합니다.  

<center><img src="../../assets//images/go1.png" ></center>  

저는 맥과 윈도우 두가지를 같이 쓰고 있는데, 우선 윈도우랑 맥이랑 그렇게 설치방법이 다르지 않으니 그냥 윈도우로 진행하겠습니다.
혹시나 GO언어를 설치는 하기 싫지만, 예제나, 코드를 구현하고 싶다면 [여기](https://play.golang.org/)에 들어가시면 GO언어를 사용하실 수 있습니다. 이 웹은 Go놀이터라고 합니다. 설치도 안해도 되면서 항상 최신버전으로 유지하고 있으니 간접적으로 체험하시고 싶거나 간단히 테스트 할때, 사용하시면 유용할 것같네요. 

설치를 끝냈으면 GOROOT를 설정해야합니다. 만약 설치 경로가 C:\Go라면 GOROOT를 설정할 필요가 없습니다. 그렇지 않은 경우에는 따로 설정을 해주셔야 합니다. 따로 설정 할 경우에는 시스템 속성 -> 환경변수 -> '새로 만들기(N)' 선택 후 설정 해주시면 되겠습니다.  

GOPATH설정 또한 해줘야하는데, 아래와 같이 설정하시면 됩니다.  

<center><img src="../../assets//images/go2.png" ></center>  

전 gogo라는 폴더를 따로 만들었고 GOROOT 잡은것과 동일하게 gogo폴더로 PATH잡아주면 설정은 끝납니다. cmd.exe실행 해서 아래와 같이 명령어를 치면 설정했던 경로를 확인 해볼 수 있습니다. 

    echo %GOROOT%
    echo %GOPATH%


이제 설치는 끝났습니다. 생각보다 간단하네요. 
다음 포스팅때, 기본 문법과 실행법에 대해 알아보겠습니다.  
