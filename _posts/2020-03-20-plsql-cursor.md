---
layout: post
title:  PLSQL에서 커서(cursor)가 필요한 이유.(메모리에 데이터 올리기)
date: 2020-03-20 09:00:00 +0300
category : PLSQL
use_math : true
---     

오랜만에 PL/SQL에 관한 포스팅을 쓰네요. 오늘은 PLSQL에서 커서(cursor)라는 것에 대해 알아보겠습니다.

## 커서(cursor)

커서는 4단계로 볼 수 있습니다. 커서선언, 커서오픈, 커서패치, 커서닫기가 있습니다.  
커서는 메모리에 올릴 데이터를 결정하고 메모리에 올린 데이터를 한건씩 가져올때 사용합니다. 커서의 진행 단계는 아래와 같습니다.

**1. 커서선언: 메모리에 올랄 데이터를 결정**  
**2. 커서오픈: 메모리에 올린 데이터를 쓰기 위해 메모리를 여는 단계**  
**3. 커서패치: 메모리에 올린 데이터를 한건씩 가져오는 작업**  
**4. 커서닫기:  메모리 닫기 Close**  

위 절차대로 사용해야하며 아래와 같이 사용 하실 수 있습니다.

```sql
accept p_ename prompt ' 이름을 입력하세요 ~   ' 
declare 
    v_ename emp.ename%type := upper('&p_ename');
    v_sal emp.sal%type;
    v_job emp.job%type;
    
    cursor emp_cursor is 
    select ename ,sal ,job
    from emp 
    where job = v_job;  ---- 커서 선언 
    
begin 
    open emp_cursor;   ----- 커서 열기 
    
    loop 
    fetch emp_cursor into v_ename , v_sal, v_job ;  ----- 커서 패치 
    exit when emp_cursor%notfound;  
    dbms_output.put_line(v_ename ||' ' ||v_sal || ' '|| v_job);
    end loop;    ---------- 커서 문 닫음 
    
    Close emp_cursor;
    
end;
/
```






