---
title:  SQL에서 문자 함수 사용하기(Rpad,substr,replace)
date:   2019-08-21 09:00:00 +0300
categories:  [DB,SQL]
tags : [DB, Oracle, SQL]
sitemap :
math: true
mermaid: true
changefreq : always
priority : 1.0
---

이번 포스팅 부터는 SQL의 문자 함수와 날짜 함수에 대해 자세하게 배워보겠습니다.  
우선 함수를 왜 사용해야 하는지와 함수의 종류들에 대해 알아보겠습니다.  

--------

### 함수를 사용해야 하는 이유?  

간단한 이유인데, SQL에서 함수를 사용해야 하는 이유는 함수를 이용하면 데이터 검색을 더 쉽고 자세하게 구현할 수 있기 때문입니다.  

--------


### 함수의 종류  

함수의 종류는 크게 2가지로 볼 수 있습니다.  

|<center></center>|<center>함수의 종류</center>| 
|:--------:|:--------:|
|**단일행 함수**|<center>문자, 숫자, 날짜, 변환, 일반</center>|
|**복수행 함수**|<center>max, min, avg, sum, count</center>|  

<br>

문자 함수의 종류에는 아래와 같습니다.  

|<center></center>|<center>문자 함수 </center>|
|:--------:|:--------:|
|**upper**|문자를 대문자로 변환하는 함수|
|**lower**|문자를 소문자로 변환하는 함수|
|**initcap**|첫 문자는 대문자로, 나머지는 소문자로 변환하는 함수|
|**substr**|특정 철자만 잘라서 출력하는 함수|
|**Instr**|단어에서 철자의 위치를 출력하는 함수|
|**Rpad**|특정 철자나 공백을 채워넣는 함수|
|**Pad**|특정 철자나 공백을 채워넣는 함수|
|**Length**|철자의 개수를 세는 함수|
|**Concat**|두 컬럼의 데이터를 연결해서 출력하는 함수|
|**replace**|어떤 특정 절차를 다른 철자로 변경해서 출력하는 함수|  


<br>


문자 함수를 이용하여 이름을 출력하는데 대문자로도 출력하고 소문자로도 출력하고 첫번째 철자는 대문자로 나머지는 소문자로 출력해보겠습니다. 


```sql
select upper(ename), lower(ename), initcap(ename)
from emp;
```

이번에 조건을 살짝 걸어서 이름이 king인 사원의 이름과 월급을 출력하는데 철자를 모두 소문자로 작성해서 검색되게 해보겠습니다.

```sql
select ename, sal
from emp
where lower(ename) = 'king';
```

이번엔 **substr**(특정 철자만 잘라서 출력하는 함수)사용해서 이름의 첫 글자가 S로 시작하는 사원의 이름을 출력 해보겠습니다. like를 사용하지말고 위에서 말한 **substr**함수를 사용해서 SQL 쿼리를 작성해볼께요.


```sql
select ename
from emp
where substr(ename,1,1) = 'S';
```


조금 더 응용해서 **initcap**을 사용하지 말고 substr, upper, lower를 사용해서 출력해보겠습니다.



```sql
select initcap(ename)
from emp;
```  

위의 SQL의 출력 결과를 한번 바꿔보면 아래와 같습니다.  

```sql
select upper(substr(ename,1,1)) || lower(substr(ename,2))
from emp
```

다음 문자 함수는 **instr**입니다. 단어에서 철자의 위치를 출력하는 함수인데요. 간단하게 사원들의 이름 철자에 'M'자의 위치를 출력해보겠습니다. 

```sql
select ename, instr(ename,'M')
from emp;
``` 


다음으로 철자의 개수를 세는 함수인 length 함수를 사용하여 사원들의 이름 철자의 개수를 세보겠습니다.

```sql
select ename, length(ename)
from emp;
```
