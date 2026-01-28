## CASES :-
## 2. <U>Whenever the data will be selected, is present in one table , and the condition to be executed is present in another table we use subquery.</U>

#### WAQTD DNAME of the employees whose Name is BLAKE.

        SELECT DNAME
        FROM DEPT
        WHERE DEPTNO=(SELECT DEPTNO
                       FROM EMP
                       WHERE ENAME='BLAKE');

#### WQATD the details of the employees working in loc NEW YORK.
        SELECT *
        FROM EMP
        WHERE DEPTNO=(SELECT DEPTNO
                       FROM DEPT
                       WHERE LOC='NEW YORK');

#### WAQTD the dept details the employees whose names end with 'R'.

        SELECT *
        FROM DEPT
        WHERE DEPTNO IN (SELECT DEPTNO
                         FROM EMP
                         WHERE ENAME LIKE '%R');   

### <u>NOTE</u>:- use in when multiple output will came.          

#### WAQTD the details of the employees working in the same DEPTNO i.e. more than 1 employee in a dept.
 
        SELECT *
        FROM EMP
        WHERE DEPTNO IN(SELECT DEPTNO 
                        FROM EMP
                        GROUP BY DEPTNO
                        HAVING COUNT(*)>1);

#### 21. WAQTD DNAME of the employees whos name is smith.
        
        SELECT DNAME 
        FROM DEPT
        WHERE DEPTNO=(SELECT DEPTNO
                      FROM EMP
                      WHERE ENAME='SMITH'); 

#### 22. WAQTD DNAME AND LOC of the employee whos ENAME is KING.
 
        SELECT DNAME, LOC 
        FROM DEPT
        WHERE DEPTNO=(SELECT DEPTNO
                      FROM EMP
                      WHERE ENAME='KING');

#### 23. WAQTD LOC of the EMP whos employee number is 7902.
        SELECT LOC 
        FROM DEPT
        WHERE DEPTNO=(SELECT DEPTNO
                      FROM EMP
                      WHERE EMPNO=7902);

#### 24. WAQTD DNAME and LOC along with deptno. of the employee who's name ends with 'R'.
  
        SELECT DNAME,LOC
        FROM DEPT
        WHERE DEPTNO IN (SELECT DEPTNO
                         FROM EMP
                         WHERE ENAME LIKE '%R');

#### 25. WAQTD DNAME of the employees whos designation is PRESIDENT.

       SELECT DNAME
       FROM DEPT
       WHERE DEPTNO IN (SELECT DEPTNO
                        FROM EMP
                        WHERE JOB='PRESIDENT'); 

#### 26. WAQTD NAMES of the employees working in ACCOUNTING DEPARTMENT.
 
       SELECT ENAME 
       FROM EMP
       WHERE DEPTNO IN (SELECT DEPTNO
                        FROM DEPT
                        WHERE DNAME='ACCOUNTING');  

#### 31. WAQTD NAMES OF THE EMPLOYEES EARNING MORE THAN SCOTT IN ACCOUNTING DEPARTMENT.
       
         SELECT ENAME
         FROM EMP
         WHERE SAL>(SELECT SAL
                     FROM EMP
                     WHERE ENAME='SCOTT')
         AND DEPTNO IN (SELECT DEPTNO
                          FROM DEPT
                          WHERE DNAME='ACCOUNTING');

#### 32. WAQTD DETAILS of the employees working as manager in the Location chicago.

        SELECT *
        FROM EMP
        WHERE JOB='MANAGER' AND
        DEPTNO IN(SELECT DEPTNO
                        FROM DEPT
                        WHERE LOC='CHICAGO'); 

#### 33. WAQTD NAME and SAL of the employeess earning more than KING in the dept ACCOUNTING.

        SELECT ENAME,SAL
        FROM EMP
        WHERE SAL>(SELECT SAL
                   FROM EMP
                   WHERE ENAME='KING')
            AND DEPTNO=(SELECT DEPTNO
                        FROM DEPT
                        WHERE DNAME='ACCOUNTING');

#### 34. WAQTD details of the EMPLOYEES working as SALESMAN in the department SALES.
        SELECT *
        FROM EMP
        WHERE DEPTNO IN (SELECT DEPTNO
                         FROM DEPT
                         WHERE DNAME='SALES')
              AND JOB='SALESMAN';           ;

#### 35. WAQTD NAME,SAL,JOB,HIREDATE of the employees working in operations department and hired before KING.

        SELECT ENAME,SAL,JOB,HIREDATE
        FROM EMP
        WHERE DEPTNO IN (SELECT DEPTNO
                         FROM DEPT
                         WHERE DNAME='OPERATIONS')
              AND HIREDATE<(SELECT HIREDATE
                            FROM EMP
                            WHERE ENAME='KING');
   
        

        

                                

