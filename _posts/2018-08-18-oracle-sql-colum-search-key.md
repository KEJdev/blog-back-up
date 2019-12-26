---
layout: post
current: post
cover:  ../assets/images/SQL_cover1.png
navigation: True
title: SQL에서 컬럼검색과 별칭(Keyword)
date: 2018-08-18 09:00:00
tags: [SQL]
sitemap :
  changefreq : daily
  priority : 1.0
class: post-template
subclass: 'post tag-sql'
author: KEJdev
use_math: true
---  

저번 포스팅 때는 간단하게, SQL 테이블을 블러오는 법을 배웠습니다.  
이번 포스팅에선 SQL 컬럼 검색과 컬럼 별칭을 사용하는 법에 대해 간단하게 알아보겠습니다. 

우선 저번 시간에 만든 EMP과 DEPT 테이블에 있는 컬럼에 대해 알아볼까요?

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


--------  



> #### DEPT Table Column  

dept table 컬럼은 아래와 같습니다.  

|  <center>column</center> |  <center> 설명 </center> | 
|:--------:|:--------:|
|**deptno**|부서번호|
|**dname**|부서명|
|**loc**|부서위치|

table colunm에 대해 알았으니,  
emp 테이블에서 사원번호와 이름, 월급을 출력해볼까요 ?

--------


> #### SQL Column Search 

```sql
selete empon, ename, sql
from emp;
```

위와 같이 코드를 치면 emp 테이블에서 사원번호와 이름, 월급만 출력이 된답니다.  
그렇다면 이번엔 이름, 직업, 입사일, 부서번호를 출력해볼까요?  

```sql
selete ename, job, hiredate, deptno
from emp;
```

이제 좀 감이 잡히나요 ?
그렇다면 이름, 월급, 커미션을 출력해볼까요?

```sql
selete ename, sal, comm
from emp;
```

이제 원하는 컬럼을 잘 출력할 수 있겠죠?  
그렇다면 이번엔 이름과 월급, 커미션 그리고 월급 + 커미션을 출력해볼까요?    
월급과 커미션을 더한 값을 출력하려면 어떻게 해야댈까요?  
간답합니다. 아래와 같이 작성하시면 됩니다.

```sql
selete ename, sal, comm, sal+comm
from emp;
```

그런데 출력하시면 에러가 뜰꺼예요.왜그럴까요? 그 이유는 **null 값 때문**이랍니다.   
그렇다면 여기서 잠깐, **null** 값에 대해 알아볼까요 ?  

**※ null**
1. 데이터가 없는 상태
2. 알 수 없는 값(unknown)

위와 같은 상태에 있을 때, null 값이라고 합니다.  
그래서 null 대신에 다른 값이 출력되게 하는 **nvl 함수를 사용**해야합니다.  
**nvl**함수는 null 대신 다른 값이 출력되게 하는 함수입니다.   

그럼 이제 nvl 함수를 사용하여 comm에 있는 null값을 0으로 바꾸어 출력을 해볼까요?  

```sql
selete ename, comm, nal(comm,0)
from emp;
```

위와 같이 작성 하면 comm에 있는 null이 0으로 바뀐 것을 확인 할 수 있습니다.  
그러면 아까 풀지못했던 위의 문제를 다시 작성해서 풀어볼까요 ?

```sql
selete ename, sal, comm, sal+nvl(comm,0)
from emp;
```

위와 같이 작성하면 월급과 커미션을 더한 값이 함께 출력 된답니다.  
그렇다면 직업을 출력하는데 **중복을 제거**하고 싶은데 어떻게 해야댈까요?  
중복을 제거하는 것을 배워볼까요 ?  

--------


> #### Keyword  

중복을 제거할때는 **distinct** 키워드를 사용하시면 된답니다.  
그럼 직업을 출력하는데 중복을 제거해서 출력해볼까요?  

```sql
selete distinct job
from emp;
```

자 이제 이름과 월급을 연결해서 출력하는 것을 배워볼까요 ?  
이름과 월급을 연결해서 출력하려면 연결연산자를 사용해야 합니다.  
**||** 연결연산자는 두 컬럼의 데이터를 연결해서 출력하는 키워드 입니다.  

연결연산자를 알았으니 아름과 월급을 연결해서 출력해볼까요?  

```sql
selete ename, || sal
from emp;
```

연결해서 연락이 잘 되는 것을 확인 하셨나요 ?  
하지만 보기에 불편하니, 예쁘게 문자열과 함께 출력해볼까요 ?  

```sql
selete ename || '의 월급은' || sal
from emp;
```

예쁘게 출력 된 것을 확인 하셨나요 ?
이제 컬럼에 대한 **별칭**을 사용하여 출력해볼까요?  

-------- 


> #### 별칭

컬럼별칭을 사용할때는 너무 길게 써서도 안되고, 언더바를 사용하셔도 안된다는 점을 기억해두세요.
컬럼명을 변경해서 출력할때는 아랴와 같이 하시면 됩니다.  

```sql
selete ename || '의 직업은' || job || '입니다' as 사원
from emp;
```

그렇다면 별칭을 사용하여 아래와 같이 출력되게 하려면 어떻게 해야댈까요 ?  

<center><img src="/../assets/images/as.png" width="420" height="200"></center>  

위와 같이 출력하려면 어떻게 해야댈까요 ?

```sql
select ename||'의 부서번호는 '||deptno||'번 입니다.' as "사원에 대한 부서번호 정보"
from emp;
```

이렇게 작성하면 별칭을 사용하여 출력할 수 있습니다.  
이제 별칭을 사용하여 잘 출력할 수 있겠죠?  

오늘도 이렇게 간단하게 SQL문법을 알아봤습니다.   
다음 포스팅때는 데이터 제한 및 정렬에 관한 함수와 연산자를 사용하여 출력하는 것을 알아보겠습니다.  
