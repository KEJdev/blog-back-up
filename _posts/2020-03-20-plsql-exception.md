---
layout: post
title:  PLSQL에서 예외처리(exception)하기
date: 2020-03-20 09:00:00 +0300
category : PLSQL
use_math : true
---     

예외처리는 모든 프로그래밍에서 사용되며, PLSQL도 여김 없이 예외처리가 있습니다.  예외처리가 무엇인지와 종류에 대해서 이야기 해보겠습니다.

## 예외(exception)

PLSQL에서 예외는 오라클에서 에러나 갔을 때, 엔드유저(프로그램 사용자)의 눈높이를 맞추기 위해 사용하는 문법입니다. 

예를 들어 홈플러스 계산원이 컴퓨터 프로그램 화면에 고객 번호를 입력하고 해당 고객 정보를 보려고 하는데, 오라클 에러 메시지가 화면에 **ORA-0001 Data not found ....** 이런식으로 나온다면 사용자는 알아보기 힘드니, **해당 고객은 존재하지 않습니다**등의 문구를 띄웁니다.

이 경우 외에도 비정상적으로 프로그램이 종료되지 않기 위해서 사용되는데, data가 잘못되어서 프로그램이 종료되버리는 현상을 막기 위해 프로그램이 종료되는게 아니라 정상적으로 처리가 되고 data가 잘못되어서 발생하는 에러 메세지만 따로 출력해주겠금 하려고 예외를 사용합니다. 

## 예외(exception)의 종류 3가지

예외처리는 총 3가지 종류로 나눌 수 있습니다. 

**1. 오라클에서 미리 정의한 예외처리**  
예를 들면 no data found , too many rows 같은 일반적인 예외에 대한 예외처리가 있습니다. 

**2. 오라클에서 미리 정의하지 않는 예외처리**  
오라클에서 미리 정의 하지 않는 예외를 따로 예외처리하는 방법이 있습니다. 

**3. 사용자 정의 예외처리**  
오라클에서 미리 정의한 예외나 오라클에서 미리 정의하지 않는 예외는 둘다 오라클 에러 메세지가 출력될 때, 발생하는 예외인데, 그에 반해 사용자 정의 예외는 오라클에서 에러가 발생하지 않았지만 이것은 예외다 라고 사용자가 정의하는 것을 말합니다. 

사원번호를 물어봤는데, 만약 없는 사원번호를 입력할 경우 아래와 같이 쓸 수 있습니다. 아래의 오류는 프로그램 문법상의 오류가 아니라 data가 없어서 발생하는 오류이므로 예외처리를 해줘야 합니다. 

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
	
	exception    ------ 예외처리
		when no_data_found then
			dbms_output.put_line('없는 사원입니다.');
end;
/
```

중복으로 예외처리를 걸 경우 아래와 같이 쓸 수 있습니다. 

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
        when no_data_found then   ------ 예외처리 1
            dbms_output.put_line('없는 사원입니다.');
        when too_many_rows then   ------ 예외처리 2
            dbms_output.put_line('이 사원의 경우는 데이터가 많습니다.');
end;
/
```

