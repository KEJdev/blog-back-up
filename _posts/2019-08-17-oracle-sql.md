---
layout: post
title:  "[SQL]Oracle SQL이란?"
date:   2019-08-17 09:05:55 +0300
image:  SQL_cover1.png
tags:   SQL
sitemap :
changefreq : daily
priority : 1.0
---


이번 포스팅에서는 가볍게 SQL이 무엇인지, SQL 명령의 종류, 마지막으로 기본 문법에 대해 알아보겠습니다. 

--------


> ### What is SQL?

 **S**tructure **Q**uery **L**anguage는 Database에서 Data를 검색하거나 조작하기 위해 사용하는 언어입니다. Database record를 삽입, 검색, 업데이트 및 삭제하는데 사용할 수 있으며, 이 외에도 Database 최적화 및 유지 관리를 포함하여 많은 작업을 수행할 수 있습니다.  


--------


> ### Type of SQL

SQL의 종류에는 아래와 같이 크게 5가지가 있습니다.  
  

|  <center></center> |  <center>명령어</center> | 
|:--------:|:--------:|
|**Query**| <center>select문 6가지(Select, From, Where, Group by, Hiving, Order by)</center> |
|**DML**| <center>insert, update, delete, merge</center> |
|**DDL**| <center>create, alter, drop, truncate, rename</center> |
|**DCL**| <center>grant, revoke</center> |
|**TCL**| <center> commit, rollback, savepoint</center> |

<br> 
Database에 접근하여 조회, 그룹, 정렬 등을 할 수 있는 기본적인 SELECT문 6가지가 있습니다. 우리는 이것을 크게  **Query**라고 이야기합니다. Query는 가장 기본적인 것이기 때문에 SQL를 배울 필요성을 못느끼는 사람이라도, 기본적으로 SELECT 문은 알고 계셔야 합니다.  

**DML**은 **D**ata **M**anipulation **L**anguage의 약자입니다. 데이터 조회 및 변형을 위한 명령어이며, 명령어는 INSERT, UPDATE, DELETE, MARGE가 있습니다. 

**DDL**은 **D**ata **D**efinition **L**anguage의 약자입니다. 데이터의 구조를 정의 하기 위한 테이블 생성, 삭제 같은 명령어가 있으며, 명령어는 CREATE, ALTER, DROP, TRUNCATE, RENAME 이 있습니다. 

**DCL**은 **D**ata **C**ontrol **L**anguage의 약자입니다. 사용자에게 권한 또는 삭제 같은 명령어이며, 명령어는 GRANT,REVOKE가 있습니다. 

**TCL**은 **T**ransaction **C**ontrol **L**anguage의 약자입니다. 트렌잭션을 제어하는 명령어이며, 명령어는 COMMIT,ROLLBACK, SAVEPOINT가 있습니다.


--------  


> ### SQL Grammar

아래의 코드는 앞으로 포스팅에서 사용되는 SQL emp, dept table입니다.  

```sql
alter session set nls_Date_format='RR/MM/DD';

drop table emp;
drop table dept;

CREATE TABLE DEPT
       (DEPTNO number(10),
        DNAME VARCHAR2(14),
        LOC VARCHAR2(13) );

INSERT INTO DEPT VALUES (10, 'ACCOUNTING', 'NEW YORK');
INSERT INTO DEPT VALUES (20, 'RESEARCH',   'DALLAS');
INSERT INTO DEPT VALUES (30, 'SALES',      'CHICAGO');
INSERT INTO DEPT VALUES (40, 'OPERATIONS', 'BOSTON');

CREATE TABLE EMP (
 EMPNO               NUMBER(4) NOT NULL,
 ENAME               VARCHAR2(10),
 JOB                 VARCHAR2(9),
 MGR                 NUMBER(4) ,
 HIREDATE            DATE,
 SAL                 NUMBER(7,2),
 COMM                NUMBER(7,2),
 DEPTNO              NUMBER(2) );

INSERT INTO EMP VALUES (7839,'KING','PRESIDENT',NULL,'81-11-17',5000,NULL,10);
INSERT INTO EMP VALUES (7698,'BLAKE','MANAGER',7839,'81-05-01',2850,NULL,30);
INSERT INTO EMP VALUES (7782,'CLARK','MANAGER',7839,'81-05-09',2450,NULL,10);
INSERT INTO EMP VALUES (7566,'JONES','MANAGER',7839,'81-04-01',2975,NULL,20);
INSERT INTO EMP VALUES (7654,'MARTIN','SALESMAN',7698,'81-09-10',1250,1400,30);
INSERT INTO EMP VALUES (7499,'ALLEN','SALESMAN',7698,'81-02-11',1600,300,30);
INSERT INTO EMP VALUES (7844,'TURNER','SALESMAN',7698,'81-08-21',1500,0,30);
INSERT INTO EMP VALUES (7900,'JAMES','CLERK',7698,'81-12-11',950,NULL,30);
INSERT INTO EMP VALUES (7521,'WARD','SALESMAN',7698,'81-02-23',1250,500,30);
INSERT INTO EMP VALUES (7902,'FORD','ANALYST',7566,'81-12-11',3000,NULL,20);
INSERT INTO EMP VALUES (7369,'SMITH','CLERK',7902,'80-12-09',800,NULL,20);
INSERT INTO EMP VALUES (7788,'SCOTT','ANALYST',7566,'82-12-22',3000,NULL,20);
INSERT INTO EMP VALUES (7876,'ADAMS','CLERK',7788,'83-01-15',1100,NULL,20);
INSERT INTO EMP VALUES (7934,'MILLER','CLERK',7782,'82-01-11',1300,NULL,10);

commit;
```


위의 코드를 사용하여 emp와 dept 테이블을 생성 해주세요.

자, 그럼 테이블을 만들었으니   
SQL selete문을 사용해서 데이터를 검색 하는 방법을 알아볼까요?

간단하게 emp 테이블을 검색해봅시다.
SQL을 이용하여 테이블을 검색할 때는 아래와 같이 하시면 됩니다.

```sql
selete * from emp;
```


문장을 해석하면, 아래와 같습니다.  
 



<center><img src="{{ site.baseurl }}/images/selete.png" ></center>  


그렇다면 dept 테이블을 검색하려면 어떻게 해야 댈까요 ?  
dept 테이블을 검색하는 코드는 아래와 같습니다.  

```sql
selete * from dept;
```  

오늘은 간단하게 SQL이 무엇인지 배웠습니다.  
다음 포스팅부터는 emp테이블과 nvl 함수와 disinct등에 대해 알아보겠습니다. 
