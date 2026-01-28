# DATA DEFINITION LANGUAGE(DDL) -->

`DDL --> DATA DEFINITION LANGUAGE --> CREATE AN OBJECT ( TABLE ) AND MANIPULATE THE STRUCTURE OF THE OBJECT` 

CREATE A TABLE 

SYNTAX 

```
   CREATE TABLE TAB_NAME ( 
   COL_NAME 1 DATATYPE CONSTRAINT , 
   COL_NAME 2 DATATYPE CONSTRAINT , 
   .
   .
   .
   COL_NAME n DATATYPE CONSTRAINT ) ; 
```

### DATATYPES 
1. CHAR 
2. VARCHAR 
3. NUMBER 
4. DATE 

###  CONSTRAINTS 
1. UNIQUE 
2. NOT NULL 
3. CHECK 
4. PK 
5. FK 
6. DEFAULT 
------------------------------------------------------------------------------
### CREATE A USER 

## STEP 1 
```
--> LOGIN AS SYSTEM ( DBA ) 
PWD --> TIGER 
```

## STEP 2 
```
--> CREATE USER USER_NAME IDENTIFIED BY PWD ; 
--> CREATE USER M79 IDENTIFIED BY TIGER ; 
```

## STEP 3 ( GRANT PERMISSIONS ) 
```
--> GRANT CONNECT TO M79 
--> GRANT DBA TO M79 
--> GRANT CREATE VIEW TO M79 
--> GRANT CREATE MATERIALIZED VIEW TO M79 
```

### NOTE --> 
```
IF ERROR --> ACCOUNT LOCKED 
CONNECT -- > SYSTEM 

ALTER USER USER_NAME ACCOUNT UNLOCK ; 
ALTER USER USER_NAME IDENTIFIED BY PWD ; 
```

teams ->

    CREATE TABLE TEAMS ( 
    TID CHAR(3) PRIMARY KEY , 
    TNAME VARCHAR(5) NOT NULL , 
    LOC VARCHAR(5) NOT NULL UNIQUE ); 

players ->

    CREATE TABLE PLAYERS 
    ( PID CHAR(2) PRIMARY KEY , 
    PNAME VARCHAR(10) NOT NULL , 
    JERSEY_NO NUMBER(3) NOT NULL , 
    TID CHAR(3) REFERENCES TEAMS(TID) ) ; 

1. **Create a table** `LIBRARY_BOOKS` with the following structure:

   * `BOOK_ID` (Number, Primary Key)
   * `TITLE` (Varchar2(100))
   * `AUTHOR` (Varchar2(100))
   * `PRICE` (Number(7,2))
   * `PUBLISHED_YEAR` (Number(4))

2. **Create a table** `STUDENTS` with columns:

   * `STUDENT_ID` (Number, Primary Key)
   * `NAME` (Varchar2(50), Not Null)
   * `COURSE` (Varchar2(30))
   * `PHONE` (Char(10), Unique)

3. Create a table `EMPLOYEE` with these constraints:

   * `EMP_ID` (Number) â€” Primary Key
   * `EMP_NAME` (Varchar2(50)) â€” Not Null
   * `DEPT_ID` (Number)
   * `SALARY` (Number) â€” Must be greater than 5000
   * `JOIN_DATE` (Date)


      CREATE TABLE EMPLOYEE(
   EMP_ID NUMBER PRIMARY KEY,
   EMP_NAME VARCHAR2(50) NOT NULL,
   DEPT_ID NUMBER,
   SALARY NUMBER CHECK (SALARY>5000),
   JOIN_DATE DATE);
# SEMI JOIN= CO-RELATED SUBQUERY
# ANTI JOIN= INNER JOIN
