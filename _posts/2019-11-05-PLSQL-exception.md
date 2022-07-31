---
layout: post
title: PL/SQL의 예외처리(exception)란?
date: 2019-11-05 09:00:00 +0300
category : PLSQL
---

이번 포스팅에서는 PL/SQL의 예외처리(exception)처리에 대해서 알아보겠습니다. 그리고 예외처리를 왜 해야하는지와 종류에 대해 알아보겠습니다. 

## 예외처리(exception) ?   

에외처리는 오라클에 에러가 났을 때, 엔드유져(프로그램 사용자)의 눈높이를 맞추기위해 사용하는 문법입니다. 예를들어 홈플러스 계산원이 컴퓨터 프로그램 화면에 고객번호를 입력하고 해당고객정보를 보려고 했는데, 오라클 에러메세지가 화면에 "ORA-0001 Data not found ...." 이런식으로 나온다면 사용자의 경우 알 수 없습니다. 그렇기 때문에 "해당 고객은 존재하지 않습니다."와 같이 에러 메세지를 바꿔주어야 합니다.  

또한 비정상장적으로 프로그램이 종료되지 않기 위해서도 사용합니다. Data가 잘못되어서 프로그램이 종료되버린 현상을 막기위해서 프로그램이 종료되는게 아니라 정상적으로 처리가 되고 Data가 잘못되어서 발생하는 에러 메세지만 따로 출력해주겠금 하려고 예외를 쓰기도 합니다.  

## 예외처리(exception) 종류 3가지 

PL/SQL의 예외처리에는 3가지의 종류가 있습니다. 오라클에서 미리 정의한 예외처리, 오라클에서 미리 정의하지 않은 예외처리, 사용자 정의 에외처리가 있습니다. 

우리가 알아야 할것은 사용자 정의 예외처리입니다. 사용자 정의 예외처리는 오라클에서 미리 정의한 예외나 오라클에서 미리 정의하지 않는 예외는 둘다 오라클 에러 메세지가 출력될 때, 발생하는 예외인데, 그에 반해 사용자 정의 예외는 오라클에서 에러가 발생하지 않지만 이것은 예외다 라고 사용자가 정의하는 것을 말합니다.  

## 예외처리(exception) 사용하기 

PL/SQL을 이용하여 사원번호를 입력하면 해당 사원의 월급이 출력 해보겠습니다. 

```sql
accept p_empno prompt ' 사원번호?  : '
declare
  v_empno emp.empno%type := &p_empno;
  v_sal  emp.sal%type;
begin
  select sal into v_sal
    from emp
    where empno = v_empno;
  dbms_output.put_line(v_sal);
end;
/
```

위와 같이 입력하면 출력이 되는데, 저 코드에서 예외처리를 해보겠습니다. 예외처리를 할때에는 begin절에 exception~ 을 넣으면 됩니다.  


```sql
accept p_empno prompt ' 사원번호?  : '
declare
  v_empno emp.empno%type := &p_empno;
  v_sal  emp.sal%type;
begin
  select sal into v_sal
    from emp
    where empno = v_empno;
  dbms_output.put_line(v_sal);
	
  exception
    when no_data_found then
      dbms_output.put_line('없는 사원입니다.');
end;
/
```

위의 코드는 실행절에 넣는 예외처리였습니다. 그렇다면 declare절에도 예외처리를 할 수 있을까요?  물론 가능합니다. declare 절에서 예외처리를 사용할 경우는 보통 먼저 체크해야할 부분이 있을 때 사용합니다. 예를 들어 월급을 물어보고 월급을 입력하지 않고 enter를 치면 '월급을 반드시 입력해야 합니다' 라는 메세지를 출력하는 경우에 declare절에 사용 할 수 있습니다.  


```sql
accept p_empno prompt ' 사원번호를 입력하세요 : '
accept p_ename prompt ' 이름을 입력하세요 : '
accept p_sal prompt ' 월급을 입력하세요  : '
declare
  e_sal_nl exception;
  pragma exception_init( e_sal_nl, -01400 ) ;
begin
  insert into emp(empno, ename, sal)
  values(&p_empno, '&p_ename', '&p_sal');
dbms_output.put_line(SQL%rowcount || ' 건이 입력되었다. ');

exception
  when e_sal_nl then
    dbms_output.put_line ( '월급을 반드시 입력해야 합니다.');
end;
/
```

