# NATURAL JOIN -->

- NATURAL JOIN have 2 behaviour :-
    #### CASE 1: 
    - If there is a relationship between the given 2  tables it behaviour has `inner join`.
    #### CASE 2: 
    - If there is no relationship between the given 2 tables it behaviour as `cross join`.

## SYNTAX :-

    SELECT  */COL_NAME/EXPRESSION
    FROM TAB_NAME1 NATURAL JOIN TAB_NAME2;

---

# SELF JOIN -->
- Joining the table by it self is known as `Self join`.

### CASE :- 
- Whenever The data to be selected is present in the same table but in different records simultaneously we use `Self join`.

### SYNTAX :-
    SELECT */COL_NAME/EXPRESSION
    FROM TAB_NAME1,TAB_NAME2
    WHERE <JOIN CONDITION>;

1. WAQTD the employee details along with MGR details of an employees.
    ```
    SELECT *
    FROM EMP E1, EMP E2
    WHERE E1.MGR=E2.EMPNO
    ```
   ```
    Emp ---> E1(Employee)       Emp ---> E2(Employee)
   ``` 

    | EID |  ENAME| MGR  |    | EID | ENAME | MGR  |     
    |-----|-------|------|----|-----|-------|------|  
    |  1  | ALLEN | 4    |    | 1   | ALLEN | 4    |
    |  2  | BLAKE | 1    |    | 2   | BLAKE | 1    |
    |  3  | KING  | 2    |    | 3   | KING  | 2    |
    |  4  | SMITH | 3    |    | 4   | SMITH | 3    |

    `E1.MGR = E2.EID` 

    ### REBUILT TABLE :-  
    | EID |  ENAME| MGR  |    | EID | ENAME | MGR  |     
    |-----|-------|------|----|-----|-------|------|  
    |  1  | ALLEN | 4    |    | 4   | SMITH | 3    |
    |  2  | BLAKE | 1    |    | 1   | ALLEN | 4    |
    |  3  | KING  | 2    |    | 2   | BLAKE | 1    |
    |  4  | SMITH | 3    |    | 3   | KING  | 2    |

#### 1. WAQTD NAME OF THE EMPLOYEE AND HIS MANAGER'S NAME IF EMPLOYEE IS WORKING AS CLERK 

#### 2. WAQTD NAME OF THE EMPLOYEE AND MANAGER'S DESIGNATION IF MANAGER AGE WHO WORKS IN DEPT 10 0R 20

    SELECT E1.ENAME, E2.HIREDATE
    FROM EMP E1, EMP E2
    WHERE E1.MGR=E2.EMPNO
    AND E1.DEPTNO IN (10,20);

#### 4. WAQTD EMP NAME AND MANAGER'S Hiredate IF EMPLOYEE WAS HIRED BEFORE 1982 

    SELECT E1.ENAME, E2.HIREDATE
    FROM EMP E1, EMP E2
    WHERE E1.MGR=E2.EMPNO
    AND E1.HIREDATE<'01-JAN-1982';


    <!-- SELECT E1.NAME,E2.NAME
    FROM EMP E1, EMP E2
    WHERE E1.MGR=E2.EMPNO 
    AND E1.SAL>2000
    AND E2.SAL>2000 -->

#### 5. WAQTD EMP NAME AND MANAGER'S COMM IF EMPLOYEE WORKS AS SALESMAN AND MANAGER WORKS IN DEPT 30

    SELECT E1.NAME, E2.COMM
    FROM EMP E1, EMP E2
    WHERE E1.MGR=E2.EMPNO 
    AND E1.JOB='SALESMAN'
    AND DEPTNO IN 30;
    

    <!-- SELECT E1.ENAME,E2.MGR
    FROM EMP E1, EMP E2
    WHERE E1.MGR=E2.EMPNO 
    AND E1.JOB='CLERK'; -->

#### 6. WAQTD EMP NAME AND MANAGER NAME AND THEIR SALARIES IF EMPLOYEE EARNS MORE THAN MANAGER---

    SELECT E1.SAL, E1.ENAME, E2.ENAME, E2.SAL
    FROM EMP E1, EMP E2
    WHERE E1.MGR=E2.EMPNO 
    AND E1.SAL>E2.SAL;

#### 7. WAQTD EMP NAME AND HIREDATE, MANAGER NAME AND HIREDATE IF MANAGER WAS HIRED BEFORE EMPLOYEE

    SELECT E1.SAL, E1.ENAME, E2.ENAME, E2.SAL
    FROM EMP E1, EMP E2
    WHERE E1.MGR=E2.EMPNO AND E1.SAL>E2.SAL;

#### 8. WAQTD EMP NAME AND MANAGER NAME IF BOTH ARE WORKING IN SAME JOB 

    SELECT E1.ENAME, E2.HIREDATE, E2.ENAME, E2.HIREDATE
    FROM EMP E1, EMP E2
    WHERE E1.MGR=E2.EMPNO 
    AND E2.HIREDATE<E1.HIREDATE;

#### 9. WAQTD EMP NAME AND MANAGER NAME IF MANAGER IS WORKING AS ACTUAL MANAGER 

    SELECT E1.ENAME, E2.NAME
    FROM EMP E1, EMP E2
    WHERE E1.MGR=E2.EMPNO
    AND E2.JOB='MANAGER';

#### 10. WAQTD EMP NAME AND MANAGER NAME ALONG WITH THEIR ANNUAL SALARIES IF EMPLOYEE WORKS IN DEPT 10, 20 AND MANAGER'S SAL IS GREATER THAN EMPLOYEES SALARY.

    SELECT E1.ENAME, E2.ENAME, E1.SAL*12, E2.SAL*12
    FROM EMP E1, EMP E2
    WHERE E1.MGR=E2.EMPNO 
    AND E1.DEPTNO IN (10,20)
    AND E2.SAL>E1.SAL;

#### 11. WAQTD Empname and ManagerName if  both are working in same job.

    SELECT E1.NAME,E2.NAME
    FROM EMP E1, EMP E2
    WHERE E1.MGR=E2.EMPNO
    AND E1.JOB=E2.JOB;

#### 12. WAQTD the emp details along manager NAME AND SAL.

    SELECT E1.*,E2.ENAME,E2.SAL
    FROM EMP E1, EMP E2
    WHERE E1.MGR = E2.EMPNO;    