---
layout: post
current: post
cover:  ../assets/images/SQL_cover1.png
navigation: True
title: SQL에서 검색 조건 주기(where)
date: 2018-08-19 09:00:00
tags: [SQL]
sitemap :
  changefreq : daily
  priority : 1.0
class: post-template
subclass: 'post tag-sql'
author: KEJdev
use_math: true
---  

오늘은 SQL의 데이터 제한 및 정렬하는 법에 대해 알아보겠습니다.  
여기서 말하는 데이터 제한은 검색에 조건을 건다거나, 특정 조건에 부합하는 사람만 출력할 때를 말한답니다.  

그럼 저번에 만든 테이블을 이용하여 계속해서 공부해볼까요?  


--------

> #### where 

SQL에서 검색에 조건을 줄때는 **where**를 사용합니다.  
그렇다면 where를 사용하여 월급이 3000인 사원들의 이름과 월급을 출력해볼까요?  

```sql
selete ename, sal
from emp
where sal = 3000;
```

위와 같이 from 다음에 where 조건 절을 사용하시면 된답니다.  
그럼 다시 직업이 SALESMAN인 사람들의 이름과 직업을 출력해볼까요?  
여기서 알아둬야 할 점은 문자와 날짜의 경우에는 양쪽에 싱글 쿼테이션(' ')마크를 사용해야합니다.  

```sql
selete ename, job
from emp
where job = 'SALESMAN';
```

잘 출력되는 것을 알 수 있습니다.  

이제부터 연산자를 이용해서 조건에 맞는 사원들만 출력해볼까요?  
일단 연산자의 종류에 대해 먼저 알아봅시다.  

**※ 연산자 3가지**
1. 산술 연산자 : * / + -
2. 비교 연산자: > , < , >=, <=, =, !=, <>, ^= (같지 않거나)
3. 논리 연산자 : and, or, not

위 연산자를 이용해서 월급이 2500 이상인 사원들의 이름과 출력을 해볼까요? 

```sql
selete ename, sal
from emp
where sal >= 2500;
```

출력이 잘 되었나요?   
그렇다면 이번엔 저번에 알려드린 별칭을 함께 사용해볼까요 ?

연봉이 3600 이상인 사원들의 이름과 연봉을 출력하는데, 컬럼명은 한글로 연봉으로 출력되게 해볼까요 ?
연봉은 월급의 12개월을 말하는 건 아시죠 ?  

```sql
select ename, sal*12 as 연봉
from emp
where sal*12>=36000;
```

그런데 아래와 같이 쓰는 분도 있을꺼예요.  
**where 연봉 >= 3600**  
이렇게 쓰시면 에러가 나는데, 왜그럴까요 ?  
그것은 SQL이 실행될 때의 순서때문입니다.  
SQL은 from - where - select 순으로 실행하기 때문에 미리 만든 "연봉" 별칭을 사용할 수 없는거랍니다.  

이번에는 두개의 연산자를 이용해서 출력해볼까요?  
월급이 1000에서 3000 사이인 사원들의 이름과 월급을 출력해보겠습니다.  

```sql
selete ename, sal
from emp
where sal > 1000 and sal < 3000;
```

또는 betwen을 사용하여 조건절을 완성 할 수 있습니다.  

```sql
selete ename , sal
from emp
where sal between 1000 and 3000;
```

이번에는 81년 2월 23일에 입사한 사원의 이름과 입사일을 출력해볼까요 ?  
아까 말했던 것 처럼 문자와 날짜는 양쪽에 싱글 쿼테이션 마크를 둘러줘야 한답니다.  

```sql
select ename, hiredate
from emp
where hiredate = '81/02/23';
```

그렇다면 between을 사용하여, 1981년도에 입사한 사원들의 입사일을 출력해볼까요?  

```sql
select ename, hiredate
from emp
where hiredate between '81/01/01' and '81/12/31';
```  

이번엔 조금 더 재밌는 조건을 줘서 출력 해볼까요 ?   
이름의 첫 글자가 S로 시작하는 사원들의 이름을 출력하려면 어떻게 해야댈까요 ? 

**like**와 **%(wild card)**를 사용하면 된답니다.  
**%**는 like 연산자를 사용할때만 **wild card**가 됩니다.  
이 자리에는 뭐가 와도 관계가 없으며 또한 철자의 개수가 몇 개가 와도 관계 없습니다. 한번 해볼까요?  

```sql
selete ename
from emp
where ename like 'S%';
```

위와 같이 하면 첫글자가 S로 시작하는 사원들이 나온답니다.  
그렇다면 이번엔 이름의 끝글자가 T로 끝나는 사원들의 이름을 출력해볼까요?

```sql
selete ename 
from emp
where ename like '%T';
```

그렇다면 이름의 두번 째 철자가 M인 사원들의 이름을 출력해볼까요?  
두번째 철자는 어떻게 해야댈까요?  

**like와 짝궁인 키워드**에 대해 알아야대요.  
1. %: 이 자리에 뭐가 와도 관계 없다.  
2. _: 이 자리에 뭐가 와도 관계 없지만 한자릿수여야 한다.  

**_**를 사용해서 한번 해볼까요?  

```sql
selete ename
from emp
where ename like '_M%';
```

이번엔 이름의 세번째 철자가 L인 사원들의 이름을 출력해볼까요?  

```sql
select ename
from emp
where ename like '_ _L%';
```

이번엔 이름에 %가 들어간 사원의 이름을 출력해볼까요?  
우선 기존에 있는 테이블에 data 한 건 추가해볼께요.

```sql
insert into emp (empno, ename, sal)
values (1234, 'A%B', 3400);
```

자 이제 이름에 두 번째 철자가 %인 사원의 이름을 출력해봅시다.  
like를 사용할 때, %가 와일드 카드가 아니라 특수문자 %로 인식하게 하려면 아래와 같이 작성해야합니다.    
m 바로 다음에 나오는 것은 와일드 카드가 아니라 특수문자 %입니다.  

```sql
selete ename
from emp
where ename like '_m%%' escape 'm';
```

자 그렇다면 두번째 철자와세번째 철자가 %인 사원의 이름을 출력해볼까요?  
우선 기존에 있는 테이블에 data를 한 개 더 추가해볼께요.  

```sql
insert into emp(empno, ename, sal)
values (2919, 'A%%B', 4300);
```  

자 이제 이름에 두번째 철자와 세번째 철자가 %인 사원의 이름을 출력해볼까요?  

```sql
select ename
from emp
where ename like '_m%m%%' escape 'm';
```

이제 like에 익숙해지셨나요?   
마지막으로 이름의 첫번째 철자가 S가 아닌 사원들의 이름을 출력해볼까요?  

```sql
selete ename
from emp
where ename not like 'S%';
```

출력이 잘되는 것을 확인하셨나요?  
이제 like와 연산자에 많이 익숙해졌을꺼라 생각해요!   
다음 포스팅에서는 계속해서 데이터 제한 및 정렬에 필요한 기타 비교연산자와 order by절에 대해 알아볼께요.  
