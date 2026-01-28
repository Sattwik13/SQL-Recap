
## SYNTAX:-

     REGEXP_LIKE(COL_NAME, '^[CHARACTER]$');

#### WAQTD THE DETAILS OF THE EMPLOYEES WHOSE NAME START WITH VOWELS

      WHERE REGEXP_LIKE(ENAME, '^[AEIOU]');

#### WAQTD THE DETAILS OF THE EMPLOYEES WHOSE NAME ENDS WITH VOWELS      

      WHERE REGEXP_LIKE(ENAME, '[AEIOU]$');

#### WAQTD THE DETAILS OF THE EMPLOYEES WHOSE NAME HAS VOWELS      

      WHERE REGEXP_LIKE(ENAME, '[AEIOU]');
      

## SUB QUERY -->
-  A query written inside another query is known as subquery.

``` 
 Inner Query --(o/p)---AS---(I/p)---> Outer Query --> Result
``` 
- Let us consider 2 pins outer query and inner query.

- The inner query extinguises first & produces an output.

- The output of the inner query is send,as an input to outer query.

- The outer query execute and produces the result.

- Therefore we can state that, Outer query is dependent on inner query.


## CASES :-
## 1. Whenever there is an unknown present in the query and question.

#### WAQTD The details of the employees who earn more than ALLEN.

        SELECT * FROM EMP
        WHERE SAL > (SELECT SAL FROM EMP WHERE ENAME='ALLEN');

#### WAQTD The details of the employees working in same Dept as KING        .
       
        SELECT *
        FROM EMP
        WHERE DEPTNO=(SELECT DEPTNO FROM EMP WHERE ENAME='KING');

#### WAQTD the ENAME and HIREDATE of the employees hired after SMITH.
        
        SELECT ENAME,HIREDATE
        FROM EMP
        WHERE HIREDATE>(SELECT HIREDATE FROM EMP WHERE ENAME='SMITH');

#### WAQTD the details of the employees earning sal more than king and working in same dept as smith.

        SELECT *
        FROM EMP
        WHERE SAL>(SELECT SAL FROM EMP WHERE ENAME='KING')
        AND DEPTNO=(SELECT DEPTNO
        FROM EMP
        WHERE ENAME='SMITH');  

#### 1. WAQTD ENAME AND SALARY OF ALL THE EMPLOYEES WHO ARE EARNING MORE THAN MILLER LESS THAN ALLEN.

        SELECT ENAME,SAL
        FROM EMP 
        WHERE SAL<(SELECT SAL FROM EMP WHERE ENAME='ALLEN') AND SAL>(SELECT SAL FROM EMP WHERE ENAME='MILLER');

#### 2. WAQTD all the details of the employees wokring as manager in the same dept as turner.

        SELECT *
        FROM EMP WHERE JOB='MANAGER' AND DEPTNO=(SELECT DEPTNO FROM EMP WHERE ENAME='TURNER');        

#### 3. WAQTD name and hiredate of the employees hired after 1980 and before KING.

        SELECT ENAME,HIREDATE
        FROM EMP WHERE HIREDATE>'31-DEC-80' AND HIREDATE<(SELECT HIREDATE FROM EMP WHERE ENAME='KING');

#### 4. 

        SELECT ENAME,SAL
        FROM EMP WHERE SAL>(SELECT SAL FROM EMP WHERE ENAME='BLAKE') AND SAL>3500;

#### 5. 

        SELECT ENAME
        FROM EMP WHERE ENAME LIKE 'A%' AND DEPTNO=(SELECT DEPTNO FROM EMP WHERE ENAME='BLAKE');

#### 6.

        SELECT ENAME,COMM
        FROM EMP WHERE JOB=(SELECT JOB FROM EMP WHERE ENAME='SMITH') AND COMM IS NOT NULL;

#### 7. 

        SELECT *
        FROM EMP WHERE DEPTNO=(SELECT DEPTNO FROM EMP WHERE ENAME='TURNER') AND JOB='CLERK';


        