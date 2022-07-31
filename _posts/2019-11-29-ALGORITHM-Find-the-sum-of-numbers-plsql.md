---
layout: post
title: PLSQL로 두개의 숫자의 합 구하기
date: 2019-11-29 09:00:00 +0300
category : Algorithm
---

주 사용언어는 Python이지만, 복습의 의미로 다양한 언어로 알고리즘을 차근차근 풀어볼까 합니다. 
오늘은 간단하게 오래전에 습득했지만, 전혀 사용하고 있지 않은 언어인PLSQL을 복습할겸, PLSQL로 간단한 문제를 풀겠습니다.   

PLSQL로 어떻게 알고리즘을 풀 수 있는가? 를 물어보신다면, **PLSQL이 무엇인가?** 라는 포스팅이 있으니 참고 하라고 말씀드리고 싶습니다만!
안보실꺼 같으니 다시 한번 설명 드리자면, PLSQL은 비절차적 언어인 SQL + 프로그래밍(if,loop)를 이야기합니다. 즉, 절차적 언어로 만드는 프로그래밍입니다. if문과 loop문을 사용할 수 있습니다.  

그렇다면 가장 기본적인 두 수자의 덧셈을 만들어보겠습니다.

```sql 
accept p_num1 prompt '첫번째 숫자를 입력하세요 ~ '
accept p_num2 prompt '두번째 숫자를 입력하세요 ~ '

declare              
  v_num1 number(10) :=&p_num1;
  v_num2 number(10) :=&p_num2;
  v_num3 number(10);
  
begin 
  v_num3 := v_num1 + v_num2;
  dbms_output.put_line('총합은 : ' || v_num3);
end;
/
```

사실 너무 쉬운거라 알고리즘이라고 하기가 좀 그렇지만, 그래도 간단하게 PLSQL로 숫자의 합을 구하는 문제를 풀어보았습니다. 


