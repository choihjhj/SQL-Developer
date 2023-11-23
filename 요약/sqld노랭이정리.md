# 1과목 요약    
데이터 모델링:      
- 현실세계를 일정한 형식에 맞추어 표현하는 추상화의 의미    
- 복잡한 현실을 제한된 언어나 표기법을 통해 이해하기 쉽게하는 단순화 의미    
- 애매모호함을 배제하고 누구나 이해 가능하도록 정확하게 현상을 기술하는 정확화 의미     
- 시스템 구현을 포함한 업무 분석 및 업무 형상화 하는 목적

데이터 모델링 유의점 :     
중복- 여러 장소의 데이터베이스에 같은 정보를 저장하지 않도록 하여 중복성 최소화    
비유연성- 데이터의 정의를 데이터의 사용 프로세스와 분리하여 유연성을 높인다.    
비일관성- 데이터간의 상호 연관관계를 명확하게 정의하여 일관성 있게 데이터가 유지되도록 한다.    

속성(단답으로 나옴) : 업무에서 필요로 하는 인스턴스에서 관리하고자 하는 의미상 더이상 분리되지 않는 최소의 데이터 단위    

제 1 정규형: 모든 속성의 도메인이 원자값으로만(다중값이 아닌) 구성되어 있으면 제 1 정규형에 속한다.     
제 2 정규형: 제 1 정규형에 속하고, 기본키가 아닌 모든 속성이 기본키에 완전 함수 종속이 되면 제 2 정규형에 속한다.(부분함수제거)    
제 3 정규형: 제 2 정규형에 속하고, 기본키가 아닌 모든 속성이 기본키에 이행적 함수 종속이 되지 않으면 제 3 정규형에 속한다. //유일하게 주식별자와 관련없는 정규형    
BCNF: 3차 정규화 만족하면서 모든 결정자가 후보키 집합에 속한 정규형


# 2과목 요약
비절차적 데이터 조작어(DML): What 만 명세   
절차적 데이터 조작어(DML): What, how 명세   

오라클 컬럼 속성 변경: ALTER TABLE 테이블명 MODIFY(컬럼명 타입 조건);   
SQL server 컬럼 속성 변경: ALTER TABLE 테이블명 ALTER COLUMN(컬럼명1 타입 조건, 컬럼명2 타입 조건);     

UNIQUE는 중복제외, NULL 입력은 가능(여러 NULL도 가능)    

DDL 참조동작 (Referential Action)   
* Insert Action    
1) Automatic ★: Child 삽입 시 Parent 테이블에 PK가 없으면, Parent PK 생성 후 Child에 삽입
2) Set Null : child 삽입 시 Parent 테이블에 PK가 없으면, Child 외부키를 Null값으로 셋팅
3) Set Default : child 시 Parent테이블에 PK 없으면, Child 외부키를 지정된 Default값으로 셋팅
4) Dependent★: Child 삽입 시 Parent 테이블에 PK가 존재할 때만, Child 삽입 허용 ★★
5) No Action : 참조 무결성을 위반하는 삽입 액션은 취하지 않는다.

* Delete / Modify Action     
1) Cascade ★ : Parent 삭제 시 Child 같이 삭제
2) Set Null : Parent 삭제 시 Child의 해당 필드는 Null로 셋팅
3) Set Default : Parent 삭제 시 Child의 해당 필드를 Default값으로 셋팅
4) Restrict ★ : Parent 삭제 시 Child 테이블에 PK가 없는 경우에만 Parent 삭제 허용
5) No Action : 참조 무결성을 위반하는 삭제/수정 액션은 취하지 않는다.

![image](https://github.com/choihjhj/SQL-Developer/assets/148078504/2f331c36-c72b-4058-a8e5-8615e2c7ef32)      

![image](https://github.com/choihjhj/SQL-Developer/assets/148078504/4bb3c203-3c71-43f2-9510-70890537b53d)     

DDL(create, drop, alter, rename) : 오라클은 Auto commit이라 rollback해도 적용 안됨. 그러나 SQL server는 사용자가 commit해야하고 rollback적용됨    

NULL : 오라클은 ''을 null로 인식 따라서 ISNULL ''은 true다 그리고 오라클에서는 NULL을 가장 큰 값으로 인식, SQL server은 ''을 공백문자로 인식하고 NULL을 가장 작은 값으로 인식한다.    
사칙연산을 null과 하면 결과는 무조건 null    

TO_DATE('201501','YYYYMM') 이렇게 하면 2015년 01월 01일 00시 00초 로 자동 1일로 셋팅됨     

REPLACE('hello','he') 결과는 'llo'이다. replace함수는 그냥 문자열에서 빼고 나머지 출력하는 함수   

중첩집계함수 AVG(count(*)) 이런거 select에 쓸 때 일반컬럼과 사용 못함. 집계합수만 써야함.     

ORDER BY 에 Alias랑 숫자 혼용가능    

catesican product = cross join = cross product = 카티시안곱, M*N건의 데이터 조합 발생, 적절한 join 조건 컬럼이 없는 경우에 사용    

(+) 있는건 LEFT OUTER JOIN의미. 속성에 (+) 붙은 건 ON절로 묶기.    

UNION,INTERSECT,EXCEPT는 UNION ALL보다 느리고 중복제거한다.    

1:1관계에서 EXCEPT,MINUS는 공집합, UNION과 INTERSECT,JOIN은 같은 결과, UNION ALL은 UNION의 2배임.    

![image](https://github.com/choihjhj/SQL-Developer/assets/148078504/b4656d5b-3140-4916-992d-b5563497dcd8)     
![image](https://github.com/choihjhj/SQL-Developer/assets/148078504/4ecbd57a-f867-41d4-b052-93d0790aba82)

LEFT OUTER JOIN + IS NULL = INNER JOIN + NOT EXISTS = INNER JOIN + NOT IN




