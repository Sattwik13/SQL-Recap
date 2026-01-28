### 1.Display hiredate and job of all the employees working for sales department earning more than SMITH.

    SELECT HIREDATE,JOB FROM EMP
    WHERE DEPTNO=(SELECT DEPTNO FROM DEPT
    WHERE DNAME='SALES')
    AND SAL>(SELECT SAL FROM EMP
    WHERE ENAME='SMITH');    ;   
### 2. Display location and dname of employee who working as manager will 2000 salary and reporting to king. 
    SELECT LOC , DNAME
    FROM DEPT 
    WHERE DEPTNO IN (SELECT DEPTNO 
                    FROM EMP
                    WHERE JOB = MANAGER AND SAL = 2000 ) AND 
                    (SELECT DEPTNO
                    FROM EMP
                    WHERE MGR IN (SELECT EMPNO
                    FROM EMP 
                    WHERE ENAME = 'KING'));


### 3. Display the dname employees whose salaary is maximum salary but lesser than 3000.
    SELECT DMANE 
    FROM DEPT
    WHERE DEPTNO IN( SELECT DEPTNO 
    FROM EMP
    WHERE SAL IN (SELECT MAX (SAL )
                FROM EMP 
                WHERE SAL < 3000));
### 4. Display the department name of the emmployees who are reporting to ADAMS.

        SELECT DNAME
        FROM DEPT
        WHERE DEPTNO IN(SELECT DEPTNO
                        FROM EMP
                        WHERE MGR IN(SELECT EMPNO
                                    FROM EMP
                                    WHERE ENAME='ADAMS'));

### 5. Display the details of the employee hired 2nd.

    SELECT *
    FROM EMP
    WHERE HIREDATE =(SELECT MIN(HIREDATE)
                    FROM EMP
                    WHERE HIREDATE>(SELECT MIN(HIREDATE)
                    FROM EMP));

### 6. Display all employee whose salary is greater than average salary of all the salesman working in department 30.   

    SELECT *
    FROM EMP
    WHERE SAL>(SELECT AVG(SAL)
                FROM EMP
                WHERE JOB='SALESMAN'
                AND DEPTNO=30);

### 7. Display the number of employees who work research dept and their salary is lesser than one of the salary in department 30.

    SELECT COUNT(*)
    FROM EMP
    WHERE DEPTNO=(SELECT DEPTNO
                  FROM DEPT
                  WHERE DNAME='RESEARCH')
    AND SAL<(SELECT MIN(SAL) 
            FROM EMP
            WHERE DEPTNO=30);               
### 8. Display the dname that are having clerk in it.
### 9. Display the departemnt names that are having at least two employees working in it.
### 10. Display all the employees who work for salesman's manager manager.
### 11. List the dept name that are having at least 3 employees but not more than 5 employees in it.
### 12. Display the location of all employees whose reporting manager salary is greater than 2000.
### 13. Select the ename and salary of the employees dname is having a charater '0' but ends with 's'.
### 14. Display ename,sal of employees who are earning more than any of the analyst working in loc NEW YORK.