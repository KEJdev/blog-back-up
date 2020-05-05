---
layout: post
title:  "SQL에서 컬럼검색과 별칭(Keyword)"
date:   2019-08-18 09:00:00 +0300
image:  assets/images/SQL_cover1.png
tags:   [SQL]
sitemap :
changefreq : always
priority : 1.0
---



저번 포스팅 때는 간단하게, SQL 테이블을  법을 배웠습니다.
이번 포스팅에선 SQL 컬럼 검색과 컬럼 별칭을 사용하는 법에 대해 간단하게 알아보겠습니다.

--------


> #### EMP Tabel Column  

emp table 컬럼은 아래와 같습니다.

|  <center>column</center> |  <center> 설명 </center> | 
|:--------:|:--------:|
|**empno**|사원번호|
|**ename**|사원이름|
|**sql**|월급|
|**job**|직업|
|**mgr**|사원의 관리자|
|**hiredate**|입사일|
|**comm**|커미션|
|**deptno**|부서번호|


<br>


--------  



> #### DEPT Table Column  

dept table 컬럼은 아래와 같습니다.  

|  <center>column</center> |  <center> 설명 </center> | 
|:--------:|:--------:|
|**deptno**|부서번호|
|**dname**|부서명|
|**loc**|부서위치|   

<br>

table column에 대해 알았으니, emp 테이블에서 사원번호와 이름, 월급을 출력해보겠습니다.

--------


> #### SQL column Search 

```sql
selete empon, ename, sql
from emp;
```

위와 같이 코드를 치면 emp 테이블에서  이름, 월급만 출력됩니다.
그렇다면 이번엔 이름, 직업, 입사일, 부서번호를 출력해보겠습니다.


```sql
selete ename, job, hiredate, deptno
from emp;
```

이벤어는 이름, 월급, 커미션을 출력해보겠습니다.

```sql
selete ename, sal, comm
from emp;
```


이번엔 이름과 월급, 커미션 그리고 월급 + 커미션을 출력해보겠습니다.


```sql
selete ename, sal, comm, sal+comm
from emp;
```

그런데 실제로 출력하면 에러가 출력됩니다. 그 이유는 **null 값 때문**입니다.
잠깐, **null** 값에 대해 알아보겠습니다.

**<center>1. 데이터가 없는 상태</center>** 
**<center>2. 알 수 없는 값(unknown)</center>**

위와 같은 상태에 있을 때, null 값이라고 합니다.  
그래서 null 대신에 다른 값이 출력되게 하는 **nvl 함수를 사용**해야합니다.  
**nvl**함수는 null 대신 다른 값이 출력되게 하는 함수입니다.   

그럼 이제 nvl 함수를 사용하여 comm에 있는 null값을 0으로 바꾸어 출력해보겠습니다.

```sql
selete ename, comm, nal(comm,0)
from emp;
```

위와 같이 작성 하면 comm에 있는 null이 0으로 바뀐 것을 확인 할 수 있습니다.  
그러면 아까 출력하지 못했던 위의 문제를 다시 작성해서 출력해보겠습니다.

```sql
selete ename, sal, comm, sal+nvl(comm,0)
from emp;
```

--------


> #### Keyword  

중복을 제거할때는 **distinct** 키워드를 사용해야합니다. 

```sql
selete distinct job
from emp;
```

이름과 월급을 연결해서 출력하려면 연결연산자를 사용해야 합니다.  
**||** 연결연산자는 두 컬럼의 데이터를 연결해서 출력하는 키워드 입니다.  


```sql
selete ename, || sal
from emp;
```

위와 같이 짜면 보기에 불편하니, 예쁘게 문자열과 함께 출력해보겠습니다.

```sql
selete ename || '의 월급은' || sal
from emp;
```


-------- 


> #### 별칭

컬럼별칭을 사용할때는 너무 길게 써서도 안되고, 언더바를 사용하셔도 안된다는 점을 기억해두세요.
컬럼명을 변경해서 출력할때는 아랴와 같이 하시면 됩니다.  

```sql
selete ename || '의 직업은' || job || '입니다' as 사원
from emp;
```

별칭을 사용하여 아래와 같이 출력되게 하려면 어떻게 해야댈까요?

<center><img src="../assets//images/as.png" ></center>  


위 쿼리를 그대로 가져와서 조금만 수정하면 되겠네요.

```sql
select ename||'의 부서번호는 '||deptno||'번 입니다.' as "사원에 대한 부서번호 정보"
from emp;
```

