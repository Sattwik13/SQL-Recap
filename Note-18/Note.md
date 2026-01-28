#### 3. DISPLAY ALL THE EMPLOYEES OF DEPARTMENT 30, 20 WITH THEIR ANNUAL SALARY AND HAVING ATLEAST 3 EMPLOYEES

    SELECT E1.ENAME, (E1.SAL*12) AS ANNUAL_SALARY, E1.DEPTNO
    FROM EMP E1
    WHERE E1.DEPTNO IN (20,30)
    AND E1.DEPTNO IN (SELECT E2.DEPTNO
                      FROM EMP E2
                      GROUP BY E2.DEPTNO
                      HAVING COUNT(*)>=3);

#### 4. DISPLAY THE LAST HIRED EMPLOYEE RECORD WITH 25% HIKE IN SALARY.

    SELECT E1.ENAME, E1.SAL, E1.HIREDATE, (E1.SAL*1.25) AS NEW_SALARY
    FROM EMP E1
    WHERE E1.HIREDATE=(SELECT MAX(E2.HIREDATE)
                       FROM EMP E2);

#### 5. Display the names of employees who are hired on the same date as the employee with the minimum salary.

    SELECT E1.ENAME
    FROM EMP E1
    WHERE E1.HIREDATE=(SELECT E2.HIREDATE
                       FROM EMP E2
                       WHERE E2.SAL=(SELECT MIN(E3.SAL)
                                     FROM EMP E3));

#### 6. Display employee names whose salaries are equal to the maximum salary among employees who were hired before "FORD".

    SELECT E1.ENAME
    FROM EMP E1
    WHERE E1.SAL=(SELECT MAX(E2.SAL)
                  FROM EMP E2
                  WHERE E2.HIREDATE<(SELECT E3.HIREDATE
                                     FROM EMP E3
                                     WHERE E3.ENAME='FORD'));
#### 7. Find the employee who earns the lowest salary in the department where the highest salary is more than 4000.

    SELECT *
    FROM EMP 
    WHERE (SAL,DEPTNO) IN(SELECT (MIN(SAL), DEPTNO)
                          FROM EMP
                          GROUP BY DEPTNO
                          HAVING MAX(SAL)>4000);


#### 8. List the names of employees whose salaries are more than the average salary of department 20, but less than the highest salary of department 30.
#### 9. SELECT THE EMPLOYEES WHOSE DNAME IS HAVING AT LEAST TWO 'E' IN IT.
#### 13. WAQTD THE DNAME HAVING MAX EMPLOYEES 
#### 14.DISPLAY THE EMPLOYEE NUMBER AND NAME OF EMPLOYEE WORKING AS CLERK AND EARNING HIGHEST SALARY AMONG CLERKS.