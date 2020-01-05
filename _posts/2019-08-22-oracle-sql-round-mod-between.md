---
layout: post
title:  "[SQL]SQL의 반올림과 비교함수 사용하기(round,between_months)"
date:   2019-08-22 09:00:00 +0300
image:  SQL_cover1.png
tags:   SQL
sitemap :
changefreq : daily
priority : 1.0
---


저번 포스팅에 이어서 날짜함수와 간단하게 숫자함수에 대해 알아보겠습니다.  
숫자함수는 간단하지만 날짜 함수는 생각보다 간단하지 않답니다. 그래서 날짜 함수는 잘봐두셔야합니다.  
그러면 오늘도 SQL에 대해 알아보러 갈까요?

--------


> #### 숫자함수와 날짜함수  

숫자 함수는 생각보다 간단하답니다.  
프로그래밍을 조금 해보신 분들은 금방 자주 하는 함수일 수도 있겠습니다.   

숫자함수의 종류는 아래와 같습니다.  

|<center></center>|<center>숫자 함수</center>| 
|:--------:|:--------:|
|**round**|<center>반올림하는 함수</center>|
|**trunc**|<center>반올림하지 않고 버리는 함수</center>| 
|**mod**|<center>나눈 나머지값을 출력하는 함수</center>|


날짜 함수의 정류는 아래와 같습니다.  

|<center></center>|<center>날짜 함수</center>| 
|:--------:|:--------:|
|**between_months**|<center>날짜와 날짜 사이의 개월 수를 출력하는 함수</center>|
|**add_months**|<center>특정 개월 수 후의 날짜를 출력하는 함수</center>| 
|**next_day**|<center> 돌아올 요일의 날짜를 출력하는 함수</center>|
|**last_day**|<center>그 달의 마지막 날이 언제인지 출력하는 함수</center>|

날짜 함수는   

날짜 - 숫자 = 날짜  
날짜 + 숫자 = 날짜  
날짜 - 날짜 = 숫자  

등으로도 사용할수 있습니다. 잘 기억해두세요~!
자, 그럼! 이제 숫자 함수를 사용하여 SQL문법 예시를 볼까요?  
숫자 함수는 너무 간단하게 한번 슬쩍 보시면 된답니다.  

**round**함수를 사용할때는 아래와 같이 작성하시면 됩니다.

```sql
select 748.876, round(748.876,1), round(748.876,2), round(748.876,0), round(748.876,-1)  
from dual;
```

**trunc**함수를 사용할때는 아래와 같이 작성하시면 됩니다.  

```sql
select 748.876, trunc(748.876,1), trunc(748.876,2), trunc(748.876,0), trunc(748.876,-1)  
from dual;
```  

**mod**함수를 사용할때는 아래와 같이 작성하시면 됩니다.  

```sql
select mod(10,3)
from dual;
```

자, 이제 어려운 날짜 함수에 대해 알아볼까요?  

이름과 입사한 날짜부터 오늘까지 총 몇일 근무했는지를 출력하려면 SQL을 어떻게 짜야댈까요?  
아까 말했던 **-**를 사용하면 된답니다?

```sql
select ename, trunc(sysdate-hiredate,0)
from emp;
```

위와 같이 SQL문법을 작성하면 된답니다.  
조금 어렵죠? 계속 계속 이어서 작성해볼까요 ?

이름과 입사한 날짜가 오늘부터 총 몇 달을 근무했는 출력하려면 SQL을 어떻게 짜야댈까요?  

```sql
select ename, months_between(sysdate,hiredate)
months_between(최신날짜,입사일)
from emp;
```

위와 같이 SQL문법을 작성하면 되는데요. 그렇다면 오늘부터 100달 뒤에 날짜가 어떻게 되는지는 어떻게 해야댈까요?  

```sql
select add_months(sysdate,100)
from dual;
```

이렇게 작성하시면 된답니다.  
생각보다 날짜 함수는 꽤 어렵답니다. 날짜함수는 나중에 사용할 곳이 많으니까, 잘 기억해두세요! 



