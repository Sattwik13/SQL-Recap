# Co-related subquery -->

- The query written inside another query in a way that both the queries are interdepndent on each other is known as corelated query.

 
- Let  us consider two queries Outer query, Inner Query
- The Outer query executes first(partially) and produces a partial output.
- The  partial output is sent as an input to inner query
- The inner query executes and produces an output.
- The output of inner query is sent as an input to outer query
- Executes fully and produces the result.
- Therefore both the queries are interrelated on each other.

### To find the nth max sal


    select distinct e1.sal
    from emp e1
    where n-1 in (select count(distinct e2.sal)
                  from emp e2
                  where e1.sal < e2.sal);
             

### WAQTD THE 3RD MAX SAL


    select distinct e1.sal
    from emp e1
    where 2 in (select count(distinct e2.sal)
    from emp e2
    where e1.sal < e2.sal);


### To find the nth min sal 

    select distinct e1.sal
        from emp e1
        where n-1 in (select count(distinct e2.sal)
        from emp e2
        where e1.sal > e2.sal);

### co related subquery operators 

1. exists
2. not exists

#### 1.EXISTS 
- It is a uniary opertaor that checks for the existing value from the inner query 


#### WAQTD THE DEPT DETAILS OF THE EMPLOYEES WORKING IN THE EMP TABLE 

    SELECT *
    FROM DEPT
    WHERE EXISTS (SELECT EMP.DEPTNO
    FROM EMP
    WHERE EMP.DEPTNO=DEPT.DEPTNO);

2. NOT EXISTS 
- It is a uniary opertaor that checks for the  not existing value from the inner query 

        SELECT *
            FROM DEPT
            WHERE  NOT EXISTS (SELECT EMP.DEPTNO
            FROM EMP
            WHERE EMP.DEPTNO=DEPT.DEPTNO);
## VIEWS :-
- views are the virtual table from existing table.

- views dont accomidate any space.

- Mainly use for timely analysis.

    CREATE VIEW VIEW_NAME
    AS
    SQL STATEMENT;

 EXAMPLE--> CREATE A VIEW TO STORE ONLY THE DETAILS OF THE SALESMAN

    SELECT VIEW SALESMAN
    AS
    SELECT  *
    FROM EMP
    WHOSE JOB='SALESMAN';

## MATERIALIZED VIEW :-
- It is similar to views but stores the data physically.
- No changes can be done of the materialized view created.
- It is mainly use for report purposes.

    CREATE MATERIALIZED VIEW VIEW_NAME
    AS
    SQL STATEMENTS;

    CREATE MATERIALIZED VIEW SALES_REPORT
    AS
        




