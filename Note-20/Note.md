## Single Row Function -->
- If there are n number of outputs, all the inputs executes individually and produce n number of outputs.

### 1. Length():- It is used to find length of the given string.

Display length of the ENAME & ENAME and ALLEN

DUAL--> 

       SELECT LENGTH('manas')
       FROM DUAL;

### 2. Upper()--> Uppercase 

    SELECT UPPER('bharat')
    from DUAL;

    --> BHARAT   

###  3. LOWER() --> lowercase

    SELECT LOWER('BHaRaT')
    FROM DUAL;

    --> bharat

###  4. INITCAP()--> INITIAL LETTER TO UPPER CASE

    SELECT INITCAP('bHaRaT')
    FROM DUAL;

    --> Bharat    

### 5. SUBSTR() --> USED TO FIND A PART OF THE STRING  
    
####  Syntax :-

    SUBSTR('ORG_STR',LENGTH, POSITION)

| Q | S | P | I | D | E | R | S |
|---|---|---|---|---|---|---|---|
| 1 |  2| 3 | 4 | 5 | 6 | 7 | 8 |
| -8| -7| -6| -5| -4| -3| -2| -1|


    SELECT SUBSTR('QSPIDER', 1, 3)
    FROM DUAL;
    --> QSP

    SELECT SUBSTR('QSPIDER',3 ,3)
    FROM DUAL;
    --> PID

#### WAQTD the details of the employees whose name ends with 'R' without using REG EXP or like op

    SELECT * 
    FROM EMP
    WHERE SUBSTR(ENAME, -1, 1)='R';

---

### 6. INSTR() --> FIND THE POSITION OF THE GIVEN CHARACTER IN THE STRING.

| B | A | N | A | N | A |
|---|---|---|---|---|---|
| 1 |  2| 3 | 4 | 5 | 6 |
| -8| -7| -6| -5| -4| -3|

#### Syntax-
    
    INSTR('ORG_STR','CHAR',POSITION, OCCURANCE);

    SELECT INSTR('BANANA','A',1,1)
    FROM DUAL; -> 2

    SELECT INSTR('BANANA','A',3,1)
    FROM DUAL; --> 4

    SELECT INSTR('BANANA','A',2,1)
    FROM DUAL; --> 2

---

### 7.REPLACE() --> REPLACE THE GIVEN VALUES IN THE STRING

#### Syntax-

    REPLACE('ORG_STR','CHAR','NEW_CHAR');

    BANANA

    SELECT REPLACE('BANANA','A','Y')
    FROM DUAL;

    --> BYNYNY

### 8.REVERSE() --> It is used to REVERSE the given string

    SELECT REVERSE('BHARAT')
    FROM DUAL;

    --> TARAHB

### 9. ABS() --> ABSOLUTE VALUE

    SELECT ABS(-100)
    FROM DUAL;

    --> 100

### 10. ROUND() --> USED TO ROUND OFF TO THE NEAREST VALUE

    ROUND(10.2) --> 10

    ROUND(10.5) --> 11

### 11. TRUNC() --> USED TO ROUND OFF TO LOWEST VALUE

    TRUNC(10.9) --> 10
    TRUNC(-10.9) --> -10

### 12. CEIL() --> ROUND OFF TO HIGHEST VALUE

    SELECT CEIL(10.3)
    FROM DUAL; --> 11

    SELECT CEIL(-10.3)
    FROM DUAL;
    --> -10          

### 13. FLOOR() --> ROUND OF TO THE LOWEST VALUE

    SELECT FLOOR(10.3)
    FROM DUAL; --> 10

    SELECT FLOOR(-10.3)
    FROM DUAL; --> -11     

### 14. ROUND() --> USED TO ROUND OFF TO THE NEAREST VALUE

    ROUND(10.2) --> 10
    ROUND(10.5) --> 11

    ROUND(100.2345)-->100

### 15. MOD() --> MODULUS --> REMAINDER VALUE

    MOD(5,2) --> 1
    MOD(8,2) --> 0

### 16. MONTHS_BETWEEN()

#### Syntax :-

    MONTHS_BETWEEN(DATE 1, DATE 2);

    SELECT MONTHS_BETWEEN(SYSDATE, HIREDATE)
    FROM EMP;

### ADD_MONTHS()

#### Syntax :-

    ADD_MONTHS(DATE, NO_OF_MONTHS);

    SELECT ADD_MONTHS(SYSDATE, 12)
    FROM DUAL;

#### WAQTD the details of employees hired after 2 years of the 1st employee

    SELECT *
    FROM EMP
    WHERE HIREDATE>(SELECT ADD_MONTHS(MIN(HIREDATE), 24) FROM EMP);    

### 17. TO_CHAR-->
- It is used it to convert a given value to the desired string value.

```
    08-JAN-2026 -- 08/01/26 01:36:00

    SELECT TO_CHAR(SYSDATE,'DD/MM/YY HH12:MI:SS')
    FROM DUAL;

    1234567 --> $12,34,567
```

#### WAQTD the details of the employees hired on sunday.

    SELECT *
    FROM EMP 
    WHERE TO_CHAR(HIREDATE, 'DY')='SUN';

## NVL (Null Value Logic)
- It is used it to substitute null value of the given column with user defined values.

        SELECT COMM,NVL(COMM, 1)
        FROM EMP;

#### WAQTD the sal, comm, sal+comm for all the employees.

    SELECT SAL, NVL(COMM,0), SAL+NVL(COMM,0)
    FROM EMP;    

## WINDOW function
- It is used it perform calculation on a group of related rows while showing every row in the result.
- Window function do not reduce rows like group by.

### 1. OVER() --
- It turns an ordinary function into window function.

    SELECT ENAME, SAL, MAX(SAL) OVER()
    FROM EMP;

### 2. OVER (PARTITION BY COL_NAME ORDER BY COL_NAME ASC/DESC) --

    SELECT MAX(SAL) OVER(PARTITION BY DEPTNO ORDER BY SAL DESC), DEPTNO, SAL 
    FROM EMP;

    SELECT MAX(SAL) OVER(PARTITION BY DEPTNO), DEPTNO, SAL 
    FROM EMP;

### 3. RANK() -- USED TO PROVIDE RANK
- If two values are of the same rank then the upcoming rank value 

`RANK FUNCTION  will skip  upcoming rank, but DENSE-RANK FUNCTION WILL NOT SKIP(NUMBERING SERIALIZING).`


    RANK() OVER(PARTITION BY COL_NAME ORDER BY COL_NAME DESC/ASC)

#### WAQTD THE DETAILS OF THE EMPLOYEE WITH DEPT WISE SAL RANK()

    SELECT EMP.*, RANK() OVER (PARTITON BY DEPTNO ORDER BY SAL DESC) 
    FROM EMP;


### 4. DENSE_RANK() -- 

    DENSE_RANK() OVER(PARTITION BY COL_NAME ORDER BY COL_NAME DESC/ASC)

#### WAQTD the DEPT WISE top 2 sal

    SELECT *
    FROM (SELECT DENSE_RANK() OVER(PARTITION BY DEPTNO ORDER BY SAL DESC)AS RANK
    FROM EMP)
    WHERE RANK<3;

#### WAQTD THE JOB WISE MIN 2 SAL

    SELECT  *
    FROM (SELECT EMP.*, DENSE_RANK() OVER(PARTITION BY DEPTNO ORDER BY SAL)AS RNK
    FROM EMP)
    WHERE RANK <3;

### WAQTD THE JOB WISE MIN 2 MIN SAL IF THE EMPLOYEE WORKS IN MY

    SELECT *
    FROM(SELECT EMP.*, DENSE_RANK() OVER(PARTITION BY DEPTNO ORDER BY SAL)AS RNK FROM EMP) E1, DEPT D1
    WHERE E1.DEPTNO  = D1.DEPTNO AND LOC='NEW YORK' AND  RNK=2;  

## 17. CTE--> COMMON TABLE EXPRESSION

#### WAQTD the details of the employee earning sal more than AVG sal of dept 20

    SELECT *
    FROM EMP
    WHERE SAL>(SELECT AVG(SAL)
    FROM EMP
    WHERE DEPTNO=20);

## Syntax- 

    WITH CTE_NAME AS(
        sql statements
    )    

    WITH AVG_SAL AS (SELECT AVG(SAL) AS A_SAL
    FROM EMP
    WHERE DEPTNO=20)
    SELECT *
    FROM EMP, AVG_SAL
    WHERE SAL>A_SAL;

#### WAQTD the details of the employee whose sal is greater than AVG SAL of their MANAGER(MGR) dept

