# GROUP BY CLAUSE
- It is used it to group the records.
## Characteristics:-
1. Group by clause executes row by row. 
2. We can pass the column name or expression as an argument inside group by clause.
3. It is not mandatory to use where clause where using group by clause.
4. The column name  or expression written in group by clause can be written select clause which is known as group by expression. 

```
❌ Your Query
SELECT DEPTNO, SAL, COUNT(*)
FROM EMP
WHERE JOB = 'SALESMAN'
GROUP BY DEPTNO;

🚫 Why This Is Wrong

In SQL:

Every column in the SELECT list must be either

Aggregated (COUNT, SUM, AVG, etc.)
OR

Present in the GROUP BY clause

Problem here 👇

DEPTNO → ✅ in GROUP BY

COUNT(*) → ✅ aggregate

❌ SAL → neither aggregated nor grouped

SQL doesn’t know which salary to display for a department that may have multiple salesmen with different salaries.
```  

## Syntax :-
    SELECT GROUP FUNCTION/GRP_BY_EXPRESION
    FROM  TAB_NAME
    [WHERE <FILTER CONDITION>]
    GROUP BY COL_NAME/EXPRESSION;

## NOTE:- 
`any clause that execute after group by clause will execute group by group; `

## ORDER OF EXECUTION
1. FROM 
2. WHERE[ROW BY ROW]  
3. GROUP BY[ROW BY ROW]  
4. SELECT[GRP BY GRP] 

#### WAQTD the no of employees working in each dept
    SELECT COUNT(*),DEPTNO
    FROM EMP
    GROUP BY DEPTNO;

#### WAQTD the no of employees working as a salesman in each dept
    SELECT COUNT(*),DEPTNO
    FROM EMP
    WHERE JOB='SALESMAN'
    GROUP BY DEPTNO;

#### 1. WAQTD number of employees working in each department except president.

        SELECT COUNT(*), DEPTNO
        FROM EMP 
        WHERE JOB!='PRESIDENT'
        GROUP BY DEPTNO;

#### 2.  WAQTD total salary needed to pay all the employees in each jobs.

        SELECT JOB,SUM(SAL) AS TOTAL_SALARY
        FROM EMP
        GROUP BY JOB;
    
#### 3.  WAQTD number of employees working as manager ineach department.  
    
        SELECT DEPTNO,COUNT(*)
        FROM EMP
        WHERE JOB='MANAGER'
        GROUP BY DEPTNO;   

#### 4.  WAQTD avg salary needed to pay all the employees in each department excluding the employees of deptno. 20.

        SELECT DEPTNO,AVG(SAL) AS AVERAGE_SALARY 
        FROM EMP
        WHERE DEPTNO!=20
        GROUP BY DEPTNO;

#### 5.  WAQTD number of employees having character 'A' in their names in the job 

        SELECT JOB,COUNT(*)
        FROM EMP
        WHERE ENAME LIKE '%A%'
        GROUP BY JOB;

#### 6.  WAQTD number of employees and avg salary needed to pay the employees who salary in greater than 2000
in each dept

        SELECT DEPTNO,COUNT(*),AVG(SAL) AS AVERAGE_SALARY
        FROM EMP
        WHERE SAL>2000
        GROUP BY DEPTNO;

#### 7. WAQTD total salary needed to pay and number of salesman in each dept.

            SELECT DEPTNO,SUM(SAL),COUNT(*)
            FROM EMP
            WHERE JOB='SALESMAN'
            GROUP BY DEPTNO;    

#### 8.  WAQTD number of employees with their maximum salaries in each job.  

        SELECT JOB,COUNT(*),MAX(SAL)
        FROM EMP
        GROUP BY JOB;  

#### 9.  WAQTD maximum salaries given to an employee working ineach dept

        SELECT DEPTNO,MAX(SAL)
        FROM EMP
        GROUP BY DEPTNO;

#### 10. WAQTD number of times the salaries have been related in employee table.

        SELECT COUNT(*),SAL
        FROM EMP
        GROUP BY SAL;

#### 11. WAQTD the no. of employees hired in the same date into the same dept.

    
     SELECT COUNT(*),HIREDATE, DEPTNO
     FROM EMP
     GROUP BY HIREDATE, DEPTNO
     HAVING COUNT(*)<1;
    