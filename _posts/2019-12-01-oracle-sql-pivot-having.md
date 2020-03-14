---
layout: post
title:  "[SQL]SQL group 함수에서 검색 조건(having)과 테이블 회전(pivot)"
date:   2019-12-01 09:00:00 +0300
image:  SQL_cover1.png
tags:   sql
sitemap :
changefreq : always
priority : 1.0
---

오랜만에 찾아온 SQL입니다. 오늘은 데이터 분석 함수로 자주 사용 되는 pivot 함수에 대해 알아보겠습니다.
오늘 사용 되는 SQL 테이블은 첫 포스팅에 작성한 emp 테이블을 이용 할 예정입니다. 테이블이 없으신 분들은 [여기](https://kejdev.github.io/SQL-Grammar-1)를 클릭하여 테이블을 긁어서 사용하시기를 바랍니다.

-------

> #### having  

우선 having이 먼지 알기전에 간단하게 출력 하나 먼저 해보겠습니다.  
emp 테이블에서 직업과 직업별 토탈 월급을 간단하게 먼저 출력해보도록 하겠습니다.  

```sql
select job, sum(sal)
from emp
group by job;
```

이번에는 위 결과를 다시 출력하긴 하는데, 직업별 토탈월급이 5000이상인 것들만 출력 해보겠습니다. 아마 다들 아래와 같이 작성했을꺼라 생각합니다.  

```sql
select job, sum(sal)
from emp
where sum(sal)>=5000
group by job;
```

위 코드처럼 작성했는데 만약 출력이 정상적으로 잘 된다면, 컴퓨터에 이상이 있는거니 수리점에 맡겨주세요.  

아마 **오류: ORA-00934: group function is not allowed here (그룹 함수는 허가되지 않는다.)** 라는 문구를 만나실 수 있습니다. 
그 이유는 where절은 group by함수로 조건을 주는 절로 사용 할 수 없기 때문입니다. 그렇기 때문에 우리는 having 절을 사용합니다. **having**절은 group 함수에서 사용해서 검색 조건을 주려고 할때 사용하는 함수입니다.

그래서 직업별 토탈 월급을 출력하려면, having을 사용해서 아래와 같이 출력해야 합니다.

```sql
select job, sum(sal)
from emp
group by job
having sum(sal) >=5000;
```

마지막으로 함수 쓰는 순위와 사용법을 더 익혀보기 위해 group, having과 order by 함수 세개를 사용해서 출력해보겠습니다.  

이번에는 직업, 직업별 토탈월급을 출력하는데, 직업이 SALESMAN은 제외하고 출력하고 토탈월급이 4000이상인 것들만 출력하는데, 직업별 토탈월급이 높은 것부터 출력해보겠습니다.


```sql

select job, sum(sal)
from emp
where job <> 'SALESMAN'
group by job
having sum(sal) >=4000
order by sum(sal) desc;
```

-------

> #### pivot  

emp 테이블을 사용하여 부서번호, 부서번호을 가로로  출력해보겠습니다.


```sql
select sum(decode(deptno, 10, sal)) as "10",
sum(decode(deptno, 20, sal)) as "20",
sum(decode(deptno, 30, sal)) as "30"
from emp;
```

이 코드를 조금 더 간단하게 구현하려면 어떻게 해야 댈까요 ? 현재 작성한 예제 테이블은 컬럼이 몇개없다고 쳐도 실제 DB데이블은 어마무시한 양의 데이터를 저장하고 있는데, 컬럼 하나하나를 가로로 출력하기 위해  sum과 decode를 사용하면 너무 비효율적이지 않을까요 ? 이럴때 사용하는 함수가 pivot 함수입니다.

**pivot**은 회전하다 라는 뜻을 가지고 있습니다. 그래서 가로 세로 회전시킬때 자주 사용하는 함수입니다.  
그래서 위 코드를 조금 더 간결하게 만든다면, 아래와 같이 만들 수 있습니다. 

```sql
select *
from ( select deptno, sal from emp ) 
pivot ( sum(sal) for deptno in (10, 20, 30) ) ;
```

코드가 많이 간단해졌네요. DB같은 경우는 쿼리를 어떻게 날리느냐에 따라 속도차이가 심하니까 항상 조심해야 합니다. 다음 포스팅에서는 조인에 관해 알아보도록 하겠습니다.
