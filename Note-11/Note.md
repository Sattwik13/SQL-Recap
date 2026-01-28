# NESTED SUBQUERY -->
- One SubQuery Written inside another subQuery is known as nested subQuery.
- We can nest upto `255` times.

#### 1. WAQTD the 2nd MAX SAL

    SELECT MAX(SAL)
    FROM EMP
    WHERE SAL<(SELECT MAX(SAL)
    FROM EMP);

#### 2. WAQTD the 3rd MAX SAL

    SELECT MAX(SAL)
    FROM EMP
    WHERE SAL<(SELECT MAX(SAL)
    FROM EMP
    WHERE SAL<(SELECT MAX(SAL)
    FROM EMP));

#### 3. WAQTD the 4th MAX SAL

    SELECT MAX(SAL)
    FROM EMP
    WHERE SAL<(SELECT MAX(SAL)
    FROM EMP
    WHERE SAL<(SELECT MAX(SAL)
    FROM EMP
    WHERE SAL<(SELECT MAX(SAL)
    FROM EMP)));

#### P1. WAQTD the details of the employee earning 3rd max SAL

    SELECT *
    FROM EMP
    WHERE SAL=(SELECT MAX(SAL)
    FROM EMP
    WHERE SAL<(SELECT MAX(SAL)
    FROM EMP
    WHERE SAL<(SELECT MAX(SAL)
    FROM EMP)));

#### P2. WAQTD the DEPT details of the employee earning 2nd max SAL

    SELECT *
    FROM DEPT
    WHERE DEPTNO IN(SELECT DEPTNO 
    FROM EMP
    WHERE SAL=(SELECT MAX(SAL)
    FROM EMP
    WHERE SAL<(SELECT MAX(SAL)
    FROM EMP)));

#### P3. WAQTD the 3rd min SAL.
        
    SELECT MIN(SAL)
    FROM EMP
    WHERE SAL>(SELECT MIN(SAL)
    FROM EMP
    WHERE SAL>(SELECT MIN(SAL)
    FROM EMP));    

#### P4. WAQTD the details of the employees earning SAL more than SMITH AND working in LOC NEW YORK.

    SELECT *
    FROM EMP
    WHERE SAL>(SELECT SAL
    FROM EMP
    WHERE ENAME='SMITH') AND DEPTNO IN(SELECT DEPTNO
    FROM DEPT
    WHERE LOC='NEW YORK');
#### P5. WAQTD the details of the employees earning SAL more than SMITH working in LOC NEW YORK.

    SELECT *
    FROM EMP 
    WHERE SAL>(SELECT SAL
                FROM EMP
                WHERE ENAME='SMITH' AND DEPTNO IN(SELECT DEPTNO FROM DEPT WHERE LOC='NEW YORK'));

#### P6. WAQTD the details of the employee who earns 2nd MAX SAL and has a REPORTING MANAGER. ---*---   

    SELECT *
    FROM EMP     //---[3000]
    WHERE SAL IN(SELECT MAX(SAL)
                FROM EMP       //---[5000]
                WHERE MGR IS NOT NULL AND SAL<(SELECT MAX(SAL)
                                            FROM EMP)) AND MGR IS NOT NULL;
