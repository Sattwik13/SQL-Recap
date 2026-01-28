## Pseudo column:-
- This are false column present in every table in the data analsist
- To view that they have to be called explicitly.

### Classification :-
    1. RowID
    2. RowNum

###  1. RowID  :- 
- It is an 18 digit value indicating the particular row.
- The RowId Is created as the time of inserting the record.
- RowId are unique.
- RowId can't be changed.
- RowID is the static value.

###  2. RowNum :-
- It is a squencial order of a number starting with number.
- RowNum increment it self  with nth +1 only if the condition is true. 
- RowNum is dynamic value.
- RowNum is assigned at the time of execution.

#### WAQTD the 3rd record

Step 1--> Assign a Alias NAME to ROWNUM
    
    SELECT ROWNUM AS SLNO, EMP.*
    FROM EMP;

    SELECT ROWID AS SLNO, EMP.*
    FROM EMP;

STEP 2--> PASS the above query inside clause of another query

    SELECT *
    FROM(SELECT ROWNUM AS SLNO, EMP.*
    FROM EMP);

#### WAQTD THE 3RD RECORD
    SELECT *
    FROM(SELECT ROWNUM AS SLNO, EMP.*
        FROM EMP)
    WHERE SLNO=3;

#### WAQTD the 2,4,8th record

    SELECT *
    FROM(SELECT ROWNUM AS SLNO, EMP.*
        FROM EMP)
    WHERE SLNO in(2,4,8);           

#### WAQTD the last 5 record.

    SELECT *
    FROM(SELECT ROWNUM AS SLNO, EMP.*
        FROM EMP)
    WHERE SLNO>(SELECT COUNT(*)-5 FROM EMP);  

#### WAQTD the last 50% of the employee.

    SELECT *
    FROM(SELECT ROWNUM AS SLNO, EMP.*
        FROM EMP)
    WHERE SLNO>(SELECT COUNT(*)/2 FROM EMP);
    
#### WAQTD the even records in the wmp table

    SELECT *
    FROM(SELECT ROWNUM AS SLNO, EMP.*
        FROM EMP)
    WHERE MOD(SLNO, 2)=0;

#### WAQTD the ODD records in the wmp table

    SELECT *
    FROM(SELECT ROWNUM AS SLNO, EMP.*
        FROM EMP)
    WHERE MOD(SLNO, 2) !=0;    