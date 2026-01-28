## PL-SQL  
- It is an procedural languae SQL is an extension of SQL language that supports programming features.

### Syntax:-
    Declare
           declaration & initialization
    Begin
           SQL statement 
    Exception
           set server output value;
    End;

Declare and Initialize:-

    A NUMBER :=10;

    B VARCHAR :='BHARAT';

SYNTAX:- 

    VARIABLE DATATYPE := VALUE;

PRINT STATEMENT:-

    DBMS_OUTPUT.PUT_LINE('DATA TO BE PRINTED');
---
#### TWO NUMBER OF SUM:-

    DECLARE
    A NUMBER :=10;
    B NUMBER :=20;
    BEGIN
        dbms_output.put_line('SUM:'||(A+B));
    END;  
    /   

#### WAP TO  ADD TWO NUMBERS(USER INPUTS)

    DECLARE
    A NUMBER :=&A;
    B NUMBER :=&B;
    C NUMBER :=A+B;
    BEGIN
    DBMS_OUTPUT.PUT_LINE('THE ADDITION IS:'||C);
    END;
    /

## Stored Produces:-

- It is a `PL/SQL` block like structure, which stores instructions in the database and can be used when required    

### SYNTAX :-
    CREATE OR REPLACE PROCEDURE PRO_NAME(PARAMETERS)
    IS
    BEGIN
        SQL STATEMENTS
    END;
    /    

### PARAMETERS:-
    1. IN--> It is used to recieve the value    
    2. OUT--> It is used to send the value

#### WAQTD A SP TO ADD TWO NUMBER

    CREATE OR REPLACE PROCEDURE ADD_NUMBER(A IN NUMBER, B IN NUMBER)
    IN
    BEGIN
    DBMS_OUTPUT.PUTLINE(A+B);
    END;
    /


#### WRITE A STORED PROCEDURES TO GIVE NAME,SAL ,HIREDATE OF THE EMPLOYEES WRT NAME AND DEPTNO.

    CREATE OR REPLACE PROCEDURE EMP_DETAILS(NAME IN VARCHAR2, DEPTNO IN NUMBER)
    IS
    BEGIN
    FOR RECORD IN (SELECT ENAME,SAL,HIREDATE FROM EMP WHERE ENAME=NAME AND DEPTNO=DEPTNO)
    LOOP
    DBMS_OUTPUT.PUT_LINE('NAME:'||RECORD.ENAME||' SAL:'||RECORD.SAL||' HIREDATE:'||RECORD.HIREDATE);
    END LOOP;
    END;
    /