# 절차형 SQL 특징
-  모듈화
-  DBMS에서 직접 실행
-  저장 모듈
-  한번에 block 전부를
-  서버에 보냄
-  통신량 줄임
-  응용프로그램 성능 향상
-  프로시저(PL/SQL, T-SQL), 사용자정의함수, 트리거

 # 프로시저(procedure)
 - DB에 저장
 - 매개변수 있음
 - 트랜잭션 처리 (COMMIT,ROLLBACK)
 - 직접호출 EXECUTE 프로시저명(파라미터);, EXEC 프로시저명(파라미터);, CALL 프로시저명(파라미터);
 - 내부의 절차적 코드는 PL/SQL 엔진이 처리, SQL문은 SQL실행기가 처리
 - 프로시저에서 DDL문장 실행법 : EXECUTE IMMEDIATE 'DDL문';

[오라클]  
CREATE OR REPLACE PROCEDURE 프로시저명(매개변수명 IN 타입)    
IS    
BEGIN    
 SQL문;   
 EXCEPTION SQL문;    
 COMMIT;    
END;    
     
[SQL server]       
CREATE Procedure 프로시저명(@매개변수명 타입)      
BEGIN      
END;   

     프로시저삭제: [오라클]DROP PROCEDURE 프로시저명; , [SQL server]DROP PROCEDURE 스키마명.프로시저명
      
 # 사용자정의함수(UDF)
 - 프로시저랑 같은 구조     
 - DB에 저장하지 않고 호출한 곳으로 리턴함     
    
[오라클]    
CREATE OR REPLACE FUNCTION(매개변수명 in 타입)    
return 타입     
IS 변수초기화등    
BEGIN    
RETURN 변수명;    
END;
       
[SQL_server]    
CREATE FUNCTION dbo.함수이름(@매개변수명 타입)   
RETURNS 리턴타입 AS    
DECLARE @리턴변수명 타입    
BEGIN      
SET @변수명=대입    
RETURN @리턴변수명   
END;     
        
 # 트리거(Trigger)
 - 파라미터x,트랜잭션X
 - 매개변수 없음!!
 - 자동호출,자동생성
 - 데이터무결성+일관성 유지, 로그저장할때 사용
    
CREATE OR REPLACE Trigger SUMMARY_SALSE → 트리거 선언    
AFTER INSERT ON 테이블명 FOR EACH ROW → 레코드가 입력되면 트리거 발생     
DECLARE     
BEGIN     
END;     
