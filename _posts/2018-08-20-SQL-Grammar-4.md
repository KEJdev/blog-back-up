---
layout: post
current: post
cover:  ../assets/images/SQL_cover1.png
navigation: True
title: 데이터 제한 및 정렬 2
date: 2018-08-20 09:00:00
tags: [SQL]
sitemap :
  changefreq : daily
  priority : 1.0
class: post-template
subclass: 'post tag-sql'
author: KEJdev
use_math: true
---  

저번 포스팅에 이어서 계속해서 SQL의 데이터 제한 및 정렬에 필요한 연산자와 order by절에 대해 알아볼께요.  

우선 여태까지 배워본 것을 생각하며 간단하게 사원번호가 7788, 7902, 7369번인 사원들의 사원번호와 이름을 출력해볼까요 ? 
출력하는 문법은 두가지로 쓸 수 있는데요.  
첫번째 방법은 아래와 같이 **or**을 사용하여 넣는 방법이 있습니다.  

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
이번엔 in을 이용한 문법을 좀 더 응용해볼까요?  
직업이 SALESMAN, ANALYST가 아닌 사원들의 이름과 직업을 출력해볼까요?  
영어 문법이라고 생각하고 작성하시면 쉽습니다.  

```sql
selete ename, job
from emp
where job not in ('SALESMAN', 'ANALYST');
```

위와 같이 **not in**을 사용해서 출력하면 됩니다.  
생각보다 어렵지 않죠 ?  

재밌는 문제를 한번 풀어볼까요?  
커미션이 null인 사원들의 이름과 커미션을 출력하려면 어떻게 해야댈까요? null은 저번 포스팅에서도 알려드렸듯이, 알 수 없는 값이므로 비교할 수 없습니다. 그렇다면 null만 출력하려면 어떻게 해야댈까요?  

아래와 같이 SQL을 작성하시면 null값을 출력할 수  있습니다. 

```sql
selete ename, comm
from emp
where comm is null;
```

만약에 아래와 같이 작성하셨다면, 에러를 확인할 수 있을꺼예요.
에러가 나는 이유는 아까 위에서도 말을 했지만, 알 수 없는 값이므로 비교 할 수 없기 때문에 에러가 난답니다.  

```sql
selete ename, comm
from emp
where comm = null;
```  

> #### order by 

이번에는 **order by**절에 대해 알아볼까요? 

**order by**절은 데이터를 정렬할 때 쓰는 절입니다.  
**order by** 다음에 **acsending**를 쓰면 오름차순으로 정렬됩니다. 생략 시에는 디폴트로 **acs**가 사용되며, **descending**을 사용하게 되면 내림차순으로 정렬됩니다.  

우선 간단하게 order by를 사용하여 SQL을 출력해볼까요?  
이름과 월급을 출력하는데 월급이 낮은 사원부터 출력되게 하려면 어떻게 해야댈까요?  

```sql
selete ename, sal
from emp
order by sal asc;
```  

위와 같이 문법을 작성하면 된답니다. 출력이 잘되는 것을 확인하셨나요? 앗 ! 여기서 주의할 점은 order by절은 selete문에서도 **맨 마지막에 사용**되고, 실행 또한 **맨 마지막에 실행**된답니다.  

한번 더 order by절을 사용해 출력해볼까요?  
직업이 SALESMAN인 사원들의 이름과 월급을 출력하는 월급이 높은 사원부터 출력하는 SQL문법을 짜볼까요?  

```sql
selete ename, sal 
from emp 
where job = 'SALESMAN'
order by sal desc; 
```

이번엔 높은 사원부터 출력하는 것이기 때문에 **desc**를 사용했습니다.  
order by절은 생각보다 어렵지 않죠? 
오늘도 이렇게 간단하고 쉽게 SQL문법에 대해 알아봤습니다.  

다음 포스팅 때는 문자함수와 날짜 함수에 대해 알아볼께요.



