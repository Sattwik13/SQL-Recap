# SPECIAL OPERATORS

1. IN
2. NOT IN
3. BETWEEN
4. NOT BETWEEN
5. IS
6. IS NOT
7. LIKE
8. NOT LIKE
---
## IN OPERATOR -->
- It works similar to `=` operator, but can accept multiple value at RHS.
  
### SYNTAX :-
     COL_NAME IN(VALUE1, VALUE2,...VALUEn);

#### WAQTD THE DETAILS OF THE EMPLOYEES WOKRING IN DEPTNO 10, 20, 30
    SELECT *
    FROM EMP  
    WHERE DEPTNO IN (10,20,30);

#### WAQTD  THE DETAILS OF THE EMPLOYEES WORKING AS A MANAGER AND CLERK
    SELECT *
    FROM EMP
    WHERE JOB IN ('MANAGER','CLERK');    
---
## NOT IN OPERATOR (!=) -->
- It works similar to `!=` operator but can accept multiple values and RHS. 

####  WAQTD DETAILS OF ALL EMPLOYEES ALONG WITH ANNUAL SALARY EXCEPT THE EMPLOYEES WORKING AS ANALYST OR MANAGER.   
    SELECT EMP.*,SAL*12
    FROM JOB NOT IN('ANALYST','MANAGER');

##  BETWEEN OPERATOR (RANGE OF VALUES)
- It is use it to accept range of values. 
### SYNTAX
    COL_NAME BETWEEN LOWER_RANGE AND HIGHRE_RANGE

#### P1. WAQTD THE DETAILS OF THE EMPLOYEE EARNING SAL BETWEEN 1000 AND 4000    
     SELECT *
     FROM EMP
     WHERE SAL BETWEEN 1000 AND 4000;

#### P2. WAQTD THE DETAILS OF THE EMPLOYEE HIREDATE BETWEEB 1981 AND 1987
     SELECT *
     FROM EMP
     WHERE HIREDATE BETWEEN '01-JAN-1981' AND '31-DEC-1987';     
---

## NOT BETWEEN -->
- It works similar to between operator but instead of accepting the range, it will reject the range.

#### WAQTD THE DETAILS OF THE EMPLOYEE EARNING SAL BETWEEN 1000 AND 4000   
    SELECT * 
    FROM EMP 
    WHERE SAL NOT BETWEEN 1000 AND 4000;
---  

## IS OPERATOR --> 
- It is use it to compare only with `NULL` value.

### SYNTAX :-
    COL_NAME IS NULL;

#### WAQTD THE DETAILS OF THE EMPLOYEE WHOSE COMM IS NULL
    SELECT *
    FROM EMP
    WHERE COMM IS NULL;

---

## IS NOT OPERATOR -->
- It is use it to compare with not null values.

### SYNTAX :-
    COL_NAME IS NOT NULL;

#### WAQTD THE DETAILS OF THE EMPLOYEE WHOSE COMM IS NOT NULL
    SELECT *
    FROM EMP
    WHERE COMM IS NOT NULL;

---

## LIKE OPERATOR (PATTERN MATCHING) -->
- It is use it to perform pattern matching. to perform pattern matching we need to use 2 special characters `%` & `_`.  

 ### SYNTAX :-
    COL_NAME LIKE 'pattern_mathing';

 ### PERCENTILE (%)--
 - This special character can accept any number  of character, an character and no character also.

#### WAQTD THE DETAILS OF  THE EMPLOYEE WHOSE NAME STARTS WITH 'S'
    SELECT *
    FROM EMP
    WHERE ENAME LIKE 'S%'; 

#### WAQTD THE DETAILS OF THE EMPLOYEE WHOSE NAME END WITH 'H'
    SELECT * 
    FROM EMP  
    WHERE ENAME LIKE '%H';

#### WAQTD THE DETAILS OF THE EMPLOYEE WHOSE NAME HAS A CHARACTER 'M'
    SELECT *
    FROM EMP 
    WHERE ENAME LIKE '%M%';

#### WAQTD THE DEATILS OF THE EMPLOYEE HIRED IN JAN
    SELECT *
    FROM EMP
    WHERE HIREDATE LIKE '%JAN%';

#### WAQTD THE DETAILS OF THE EMPLOYEE WHOSE NAME HAS 2L'S
    SELECT *
    FROM  EMP
    WHERE ENAME LIKE '%L%L%';     
----

## UNDERSCORE ( _ ) :-    
- It can accept one character but it can be any character. 

#### WAQTD THE DETAILS OF THE EMPLOYEE WHOSE NAME 2ND CHARACTER IS 'A'
    SELECT *
    FROM EMP
    WHERE ENAME LIKE '_A%';
---

## NOT LIKE -->
- It works similarity `like` operator but, instead of accepting the values it will reject the values.

  ### Syntax:-
       COL_NAME NOT LIKE 'pattern_matching';
  #### WAQTD the details of  the employee whose name does not start with A and ends with n
       SELECT *
       FROM EMP
       WHERE ENAME NOT LIKE 'A%N';      

