---
title:  Oracle 조인(join)의 종류(equi join, 1999 ANSI)
date:   2019-12-11 09:00:00 +0300
categories:  [DB,SQL]
sitemap :
math: true
mermaid: true
changefreq : always
priority : 1.0
---

오늘부터는 오라클 조인에 대해 알아보도록 하겠습니다. 오라클 조인문법은 어떻게 쓰느냐에 따라 성능 차이가 많이 나기도 하며, 상당히 자주 사용하기 때문에 꼭 알아두어야 합니다. 우선 오늘은 간단하게 오라클 조인의 종류와 간단한 조인 문법에 대해 알아보도록 하겠습니다. 

## Oracle join 이란 ?  

Oracle이 무엇인지는 아마 잘 알고 계실껍니다. 오라클은 오라클이라는 회사에서 판매하는 제품 이름입니다. 요즘은 DB제품이 다양하여 꼭 무거운 오라클이 아니더라도 다른 여러 제품을 컨택하여 사용하는 회사들이 많습니다. 여태까지 포스팅 했던 문법들도 전부 Oracle 문법입니다. 그러나 다행이도 DB문법은 다른 회사 제품이더라도 엄청 크게 다르지 않으니, 다른 DB를 사용하고 있어도 큰틀 잡기에는 무리는 없을 것입니다. 

Oracle에서 조인(join)이란, 여러 개의 테이블의 컬럼의 결과를 하나의 결과값으로 출력할 떄 사용하는 SQL 문법을 이야기 합니다. 조인 문법은 equi join, non equi join, outer join, self join을 사용하는 오라클 조인 문법과 1999 ANSI 조인 문법이 있습니다. 

## 오라클 조인 문법  

오라클 조인 문법에는  equi join, non equi join, outer join, self join이 있다고 위에서 언급했습니다. 생각보다 많아서 어려워 보이지만 어렵지 않습니다. 아래의 표를 참고 한다면 쉽게 이해할 수 있습니다.  

|  <center> 종류 </center> |  <center>Oracle join </center> | 
|:--------:|:--------:|
|**equi join**| <center>조인하려는 테이블 사이의 연결고리가 = 인 경우의 조인 문법</center> |
|**non equi join**| <center>조인하려는 테이블 사이의 연결고리가 /= 인 경우의 조인 문법</center> |
|**outer join**| <center>equi 조인으로는 볼 수 없는 결과를 볼 때 사용하는 조인 문법</center> |
|**self join**| <center>자기 자신의 테이블과 조인하는 조인 문법</center> |

두 번째 조인인 1999 ANSI 문법 종류는 아래와 같습니다. 

|  <center> 종류 </center> | 
|:--------:|
|on 절을 이용한 join|
|using 절을 이용한  join|
|left/right/full outer join|
|natural join|
|cross join|

이렇게 오라클 조인과 1999 ANSI조인으로 나뉘는 이유는 오라클 조인으로도 조인이 되지 않는 데이터가 있기 때문에 1999 ANSI조인을 사용하여 데이터를 뽑아냅니다.
