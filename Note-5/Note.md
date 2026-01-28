# FUNCTIONS -->
- A set of instruction ot Block of code use it to perform a specific task is known as a function.

| FUNCTION-      |       |      |
|--------------- |-------|------|
| InBuilt |
| User Defined --| --SRF | --MRF |


## Multi Row functions:-
- There are `N` number of input on the input execute at once and produced a single output.
### <U>Classification</U> :-
1. MAX()
2. MIN()
3. AVG()
4. SUM()
5. COUNT()

### *1000 + NULL = NULL;

### 1. MAX()--
- It is used it to fetch a maximum value present from the given column.

### 2. MIN()--
- It is used it to fetch a minimum value present from the given column.

### 3. AVG()--
- It is used it to fetch a average value present from the given column.

### 4. SUM()--
- It is used it to fetch a total value present from the given column.

### 5. COUNT()--
- It is used it to fetch a number of value present from the given column.

## <u>Rules Of Multi Row Functions/ AGGERGATE FUNCTION/ GROUP FUNCTION/ ANALYTICAL FUNCTION</u>:-
- We can pass only one argument inside a multi-row function.
- We can not write another column name or, expression along with a multi-row function.
- Multi-Row function ignores null values.
- We can't use multi-row function in `where` clause.
- Count is  the only multi-row function that can accept `asterisk(*)` as an argumment.

#### WAQTD the no. of employees working
    SELECT COUNT(*)
    FROM EMP;

#### WAQTD the max sal, min sal, no of employees, avg sal, sum sal    
    SELECT MAX(SAL),MIN(SAL),COUNT(*),AVG(SAL),SUM(SAL)
    FROM EMP;



1.

    SELECT COUNT(*)
    FROM EMP WHERE SAL<2000 AND DEPTNO=10;

2.

    SELECT SUM(SAL)
    FROM EMP WHERE JOB='CLERK';

3. 

    SELECT AVG(SAL)
    FROM EMP;      

4.

    SELECT COUNT(*)
    FROM EMP WHERE ENAME LIKE 'A%';

5.

    SELECT COUNT(*)
    FROM EMP WHERE JOB IN('CLERK','MANAGER');  

6. 

    SELECT SUM(SAL)
    FROM EMP WHERE HIREDATE LIKE '%FEB%';

7.
                   
    SELECT COUNT(*)
    FROM EMP WHERE MGR=7839;

8.

    SELECT COUNT(*)
    FROM EMP WHERE COMM IS NOT NULL AND DEPTNO=30;

9.

    SELECT AVG(SAL),SUM(SAL),COUNT(*),MAX(SAL)
    FROM EMP WHERE JOB='PRESIDENT';

18.

    SELECT COUNT(DISTINCT JOB)
    FROM EMP;

19.
    SELECT AVG(SAL)
    FROM EMP WHERE JOB='CLERK';        
