# DCL
- GRANT 권한부여
- REVOKE 회수

[Oracle - 권한 부여]    
 - GRANT Create User To SCOTT;      
 - CONN SCOTT     
 CREATE USER 유저명 Identified By 비밀번호;    
 - CONN SCOTT    
 GRANT CREATE SESSION TO 유저명;    
 - CONN 유저명/패스워드
     
[SQL Server - 권한 부여]
- CREATE LOGIN 로그인명 WITH PASSWORD = '비번', DEFAULT_DATABASE = 최초 접속할 데이터베이스명;
-  USE 데이터베이스명;
-  GO
-  CREATE USER 유저명 FOR LOGIN 로그인명 WITH DEFAULT_SCHEMA = dbo;
 
# 오브젝트 권한 부여
 A유저가 Tab1에 Select 권한을 갖고있는데, A의 권한을 B에게도 부여하고싶다.
 - GRANT INSERT ON 테이블명 TO 유저명;    
     
[SQL Server]는 단지  "스키마”에 대한 권한"만을 가짐 
# ROLE (권한 그룹)
다양한 권한을 그룹으로 묶어 관리, 사용자와 권한 사이에서 중개 역할 수행 
-  각 유저별로 어떤 권한이 있는지 관리해야함
-  시스템 권한, 오브젝트 권한 모두 부여 가능    
     
[Oracle]    
CONN SYSTEM/MANAGER     
CREATE ROLE 롤이름;     
GRANT 부여권한, 부여권한, ... TO 롤이름;       
GRANT 롤이름 TO 유저명;    
     
# Oracle에서 제공하는 ROLE 종류
- CONNECT : Create Session과 같은 “로그인 권한”    
- RESOURCE : Create Table과 같은 “오브젝트(=리소스) 생성 권한"


유저삭제 : DROP USER 유저명 CASCADE;
