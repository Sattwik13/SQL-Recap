# Types of SubQuery

### 1. Single-Row subQuery
### 2. Multi-Row subQuery

## 1. Single-Row subQuery -->
- Whenever the inner query executes and produces a single output it is known as `Single-Row subQuery`.

#### WAQTD the details of the employeees earning sal more than SMITH
  
     SELECT *
     FROM EMP
     WHERE SAL>(SELECT SAL
     FROM EMP
     WHERE ENAME='SMITH');

## 2. Multi-Row subQuery -->
- Whenever the inner query executes and produces more than one output it is known as multiRow subquery.
- To consider a subQuery as MultiRow subQuery we need to use subQuery operators such as --
   - IN
   - ALL
   - ANY

## SubQuery Operands :-

### 1. `IN` -
- It works similar to `=` operators. But can accept multiple values even as an output from the inner query. 

#### WAQTD the details of the employees in the SAME DEPT as the employees whose NAME end with 'R'.
  
    SELECT *
    FROME EMP
    WHERE DEPTNO IN(SELECT DEPTNO
    FROM EMP
    WHERE ENAME LIKE '%R');

### 2. `ALL` -
- It is use it when we have to satifying all the given condition of the inner Query.
- The `ALL` operator can be only used with `relational operators`.

#### WAQTD the details of the employees earning more than ALL the SALESMAN.

    SELECT *
    FROM EMP
    WHERE SAL>ALL(SELECT SAL
    FROM EMP
    WHERE JOB='SALESMAN');

### 3. `ANY` -
- It is used when we have to satifying any one of the given condition from the inner Query.    
- The `ANY` operator can be used to with relational operator.

#### WAQTD the details of the employees earning more than ANY ONE of the SALESMAN.

     SELECT  *
     FROM EMP
     WHERE SAL>ANY(SELECT SAL
     FROM EMP
     WHERE JOB='SALEMAN')

#### WAQTD the details of the employees whose earn MAX sal if MIN SAL of the dept is lesser than 1500.

    SELECT *
    FROM EMP
    WHERE SAL=(SELECT MAX(SAL)
    FROM EMP
    WHERE DEPTNO IN(SELECT DEPTNO
    FROM EMP
    GROUP BY DEPTNO
    HAVING MIN(SAL)<1500));

#### 51.WAQTD NAME OF THE EMPLOYEES EARNING SALARY MORE THAN THE SALESMAN.

     SELECT ENAME 
     FROM EMP
     WHERE SAL>ALL(SELECT SAL
     FROM EMP
     WHERE JOB='SALESMAN');   

#### 52.WAQTD DETAILS OF THE EMPLOYEES HIRED AFTER ALL THE CLERKS.
    
    SELECT *
    FROM EMP
    WHERE HIREDATE>ALL(SELECT HIREDATE
    FROM EMP
    WHERE JOB='CLERK');


#### 53.WAQTD NAME AND SALARY FOR ALL THE EMPLOYEES IF THEY ARE EARNING LESS THAN ATLEST A MANAGER.

    SELECT ENAME,SAL
    FROM EMP
    WHERE SAL<ANY(SELECT SAL
    FROM EMP
    WHERE JOB='MANAGER'); 

#### 54.WAQTD NAME AND HIREDATE OF EMPLOYEES HIRED BEFORE ALL THE MANAGERS.

    SELECT ENAME, HIREDATE
    FROM EMP
    WHERE HIREDATE<ALL(SELECT HIREDATE
    FROM EMP
    WHERE JOB='MANAGER'); 

#### 55.WAQTD NAMES OF THE EMPLOYEES HIRED AFTER ALL THE MANAGERS AND EARNING SALARY MORE THAN ALL THE CLERKS.        

    SELECT ENAME
    FROM EMP
    WHERE HIREDATE>ALL(SELECT HIREDATE
    FROM EMP
    WHERE JOB='MANAGER') AND SAL>ALL(SELECT SAL
    FROM EMP
    WHERE JOB='CLERK');

 



 