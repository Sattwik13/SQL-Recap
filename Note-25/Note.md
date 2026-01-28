# DML(DATA MANIPULATION LANGUAGE)-->

#### WAQ TO DELETE THE RECORDS OF  THE EMPLOYEES REPORTING  TO SMITH

#### WAQ TO DELETE THE DUPLICATE RECORDS WRT NAME

    DELETE
    FROM EMP
    WHERE ROWID IS NOT(SELECT MIN(ROWID) 
    FROM EMP
    GROUP  BY ENAME;)

6. Modify the `STUDENTS` table to **increase the length of the column** `NAME` to 100 characters.

7. Drop the column `COURSE` from the `STUDENTS` table.

8. Add a **foreign key** constraint to the `EMPLOYEE.DEPT_ID` column that references a new table `DEPARTMENTS(DEPT_ID)`.( create a dept table having deptid , dname , loc ) 

9. Rename the table `LIBRARY_BOOKS` to `BOOK_CATALOG`.

10. Truncate the `EMPLOYEE` table. What is the difference between `TRUNCATE` and `DELETE`?

11. Drop the `SUPPLIERS` table permanently from the database.

12. Create a table `CUSTOMERS` with the following constraints:

* `CUSTOMER_ID` (Primary Key)
* `EMAIL` (Unique)
* `AGE` (Must be greater than 18 using `CHECK`)
* `GENDER` (Only values 'M', 'F', or 'O')

13. Add a **NOT NULL** constraint to the `EMPLOYEE.EMP_NAME` column.

14. Add a **CHECK constraint** to `PRICE` in the `BOOK_CATALOG` table such that the price should always be more than 100.

check constraints 
select * 
from user_constraints
WHERE TABLE_NAME = TAB_NAME ;  
---------------------------------------------------------------------------------------------------------------------------------------------------------
DML --> IT IS USED TO PERFORM TRANSACTIONS SUCH AS INSERT , UPDATE AND DELETE 

INSERT --> 

TID    
TNAME  
LOC    
OWNER  

SYNTAX 1 

INSERT INTO TAB_NAME VALUES ( VALUE 1 , VALUE 2 ....VALUE n ) ; 

INSERT INTO IPL VALUES ( '1A1' , 'RCB' , 'BLR' , 'VM' ) ; 

INSERT INTO IPL VALUES ( '1B1' , 'CSK' , 'CHE' , 'KS' ) ; 
 
SYNTAX 2 

INSERT INTO TAB_NAME ( COL_NAME 1 , COL_NAME 2 ...COL_NAME n ) VALUES ( VALUE 1 , VALUE 2 ....VALUE n ) ; 

INSERT INTO IPL (TID , TNAME , LOC, OWNER ) VALUES ('2A2' , 'MI' , 'MUM' , 'JIO') ; 

SYNTAX 3 

INSERT INTO TAB_NAME VALUES ( &COL_NAME 1 , &COL_NAME 2 ...&COL_NAME n ) ; 

INSERT INTO IPL VALUES ( &TID , &TNAME , &LOC , &OWNER ) ; 

----------------------------------------------------------------------------------------------------------------------------
UPDATE --> UPDATING THE RECORDS 

SYNTAX 

UPDATE TAB_NAME 
SET COL_NAME 1 = VALUES , COL_NAME 2 = VALUES ....COL_NAME n = VALUES 
WHERE < CONDITION > ; 

UPDATE IPL 
SET TNAME = 'PBKS' , LOC = 'PUN' , OWNER = 'PZ' 
WHERE TID = '5F5' ; 

WAQ TO UPDATE THE SAL OF THE EMPLOYEES BY 10% HIKE IF THE EMPLOYEES REPORT TO KING 

WAQ TO UPDATE THE SAL OF THE EMPLOYEES BY 1000 IF THE EMPLOYEE WORKS IN LOC NEW YORK 

---------------------------------------------------------------------------------------------------------------------------------------

DELETE 

SYNTAX

DELETE 
FROM TAB_NAME 
WHERE < CONDITION > ; 

DELETE 
FROM IPL 
WHERE TID = '5F5' ; 

WAQ TO DELETE THE RECORDS OF THE EMPLOYEES REPORTING TO SMITH 

WAQ TO DELETE THE DUPLICATE RECORDS WRT NAME 

DELETE 
FROM EMP 
WHERE ROWID NOT IN (SELECT MIN(ROWID) 
FROM EMP 
GROUP BY ENAME ) ; 
----------------------------------------------------------------------------------------------------------------------------------------------------------
TCL --> 
USED TO CONTROL THE TRANSACTIONS PERFORMED BY DML 

1. COMMIT 
2. ROLLBACK 
3. SAVEPOINT 

WORKS LIKE TCL --> BUT DOES NOT COME UNDER TCL 
4. EXIT 
-----------------------------------------------------------------------------
COMMIT --> SAVE 

COMMIT ; 
----------------------------------------------------------------------------
ROLLBACK --> GO BACK --> LAST COMMIT POINT 

ROLLBACK ; 
------------------------------------------------------------------------------
SAVEPOINT --> 

SAVEPOINT savepoint_name ; 

SAVEPOINT S1 ; 
--------------------------------------------------------------------------------
EXIT --> SAVE EVERYTHING AND EXIT THE UI 

EXIT ;     