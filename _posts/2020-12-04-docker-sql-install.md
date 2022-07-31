---
layout: post
title: 도커로 오라클을 사용해보자
date: 2020-12-04 09:00:00 +0300
category : Docker
use_math : true
---   

어쩌다보니, 집에서 SQL쿼리문을 간단하게 짜야하는 일이 생겨버렸다. 그러나 집에서 오라클을 설치해서 사용해야하는데, 그러기에는 너무 번거롭다..  
어떻게 할까? 생각하다가 왠지 도커로 오라클 설치해서 사용할 수 있을 것 같아 시도해봤는데, 역시나 도커!기대를 저버리지 않는다. 

## Docker Oracle 

Docker Hub에 가면 Oracle 11g 이미지를 [다운](https://hub.docker.com/r/jaspeen/oracle-11g)받아 사용할 수 있다. 

```
docker pull jaspeen/oracle-11g
```  

![docker](/public/img/docker.png){: width="100%" height="100%" }{: .center}

이미지를 다운 받았으면, 실행을 해보자. 

```
docker run --name oracle11g -d -p 1521:1521 jaspeen/oracle-xe-11g
```

![docker2](/public/img/docker2.png){: width="100%" height="100%" }{: .center}

간단하게 SQL문을 쓰는게 목적이라면, 아래와 같이 적자.


```
docker exec -it oracle11g sqlplus
```

참고로 user name과 password는 system / oracle 이다. 

![docker3](/public/img/docker3.png){: width="80%" height="80%" }{: .center}

그런데, 이렇게 쓸수는 없기에... SQL Developer를 다운받아 사용하였다.
 
![docker5](/public/img/docker5.png){: width="100%" height="100%" }{: .center}

접속 정보는 위와 같다. 

![docker4](/public/img/docker4.png){: width="100%" height="100%" }{: .center}

이제 집에서도 편하게 SQL공부 할 수 있다. 




