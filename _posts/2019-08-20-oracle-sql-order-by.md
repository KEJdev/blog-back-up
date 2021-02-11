---
layout: post
title:  SQL에서 테이블 정렬하기(order by)
date:   2019-08-20 09:00:00 +0300
image:  assets/images/SQL_cover1.png
categories:  [DB,SQL]
tags : [DB, Oracle, SQL]
sitemap :
math: true
mermaid: true
changefreq : always
priority : 1.0
---


저번 포스팅에 이어서 계속해서 SQL의 데이터 제한 및 정렬에 필요한 연산자와 order by절에 대해 알아보겠습니다.
우선 여태까지 배워본 것을 생각하며 간단하게 사원번호가 7788, 7902, 7369번인 사원들의 사원번호와 이름을 출력해보겠습니다. 출력하는 문법은 두가지로 쓸 수 있는데요. 첫번째 방법은 아래와 같이 **or**을 사용하여 넣는 방법이 있습니다.  

```sql
selete empon, ename
from emp
where empon = 7788 or empon = 7902 or empon = 7369;
```

두번째 방법은 간단하게 **in**을 사용하는 방법이 있습니다.  

```sql
selete empon, ename
from emp
where empon in (7788,7902,7369)
```

두번째 방법처럼 작성하시면 깔끔한 SQL문법을 작성하실 수 있습니다.  
in을 이용한 문법을 좀 더 응용해서 직업이 SALESMAN, ANALYST가 아닌 사원들의 이름과 직업을 출력해보겠습니다. 영어 문법이라고 생각하고 작성하시면 쉽습니다.  

```sql
selete ename, job
from emp
where job not in ('SALESMAN', 'ANALYST');
```

조금 더 응용해서 커미션이 null인 사원들의 이름과 커미션을 출력해보겠습니다. null은 저번 포스팅에서도 애기했듯이, 알 수 없는 값이므로 비교할 수 없습니다. 

```sql
selete ename, comm
from emp
where comm is null;
```

만약에 아래와 같이 작성하셨다면, 에러를 확인할 수 있습니다. 에러가 나는 이유는 아까 위에서도 말을 했지만, 알 수 없는 값이므로 비교 할 수 없기 때문에 에러가 나는 것입니다. 

```sql
selete ename, comm
from emp
where comm = null;
```  

--------


### order by 

**order by**절은 데이터를 정렬할 때 쓰는 절입니다. **order by** 다음에 **ascending**를 쓰면 오름차순으로 정렬됩니다. 생략 시에는 디폴트로 **asc**가 사용되며, **descending**을 사용하게 되면 내림차순으로 정렬됩니다.  

그럼 이름과 월급을 출력하는데 월급이 낮은 사원부터 출력되게 해보겠습니다.

```sql
selete ename, sal
from emp
order by sal asc;
```  

여기서 주의할 점은 order by절은 selete문에서도 **맨 마지막에 사용**되고, 실행 또한 **맨 마지막에 실행** 되는 사실을 알아둬야 합니다. 직업이 SALESMAN인 사원들의 이름과 월급을 출력하는 월급이 높은 사원부터 출력하는 SQL 쿼리를 작성해보겠습니다.

```sql
selete ename, sal 
from emp 
where job = 'SALESMAN'
order by sal desc; 
```




