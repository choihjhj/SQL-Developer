# ORDER BY절
ASC(오름차순), DESC(내림차순)    
< NULL >     
-오라클에서는 가장 큰값으로 여김    
-SQL서버에서는 가장 작은 값으로 여김  
      
<rownum, TOP() WITH TIES>   
[예제] SELECT ENAME, SAL FROM (SELECT ENAME, SAL FROM EMP ORDER BY SAL DESC) WHERE ROWNUM < 4 ; -상위3명, 인라인뷰사용   
[예제] SELECT TOP(2) WITH TIES ENAME, SAL FROM EMP ORDER BY SAL DESC; -3개행 출력, WITH TIES옵션은 같은값도 출력해서 최고2개랑 같이 출력해라 뜻    
TOP() WITH TIES은 ORDER BY랑 같이 쓰임
