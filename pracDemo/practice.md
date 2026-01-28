#### Display maximum sal, avg salary, minimum salary,count of employees using windoow function.

    SELECT MAX(SAL) OVER() AS MAX_SAL
           ,AVG(SAL) OVER() AS AVG_SAL
           ,MIN(SAL) OVER() AS MIN_SAL,
           COUNT(SAL) OVER() AS COUNT_SAL
    FROM EMP;


    SELECT DISTINCT E1.SAL
    FROM EMP E1
    WHERE 2 IN(SELECT COUNT(DISTINCT E2.SAL)
                FROM EMP E2
                WHERE E1.SAL<E2.SAL);    