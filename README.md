# Task-3-Writing-Basic-SELECT-Queries
SELECT it is a statement which is used to retrieve the data from the database by selecting both columns as well as Records 

1.Use SELECT * and specific columns

SQL> select * 
  2  from emp;

     EMPNO ENAME      JOB              MGR HIREDATE         SAL       COMM     DEPTNO
---------- ---------- --------- ---------- --------- ---------- ---------- ----------
      7369 SMITH      CLERK           7902 17-DEC-80        800                    20
      7499 ALLEN      SALESMAN        7698 20-FEB-81       1600        300         30
      7521 WARD       SALESMAN        7698 22-FEB-81       1250        500         30
      7566 JONES      MANAGER         7839 02-APR-81       2975                    20
      7654 MARTIN     SALESMAN        7698 28-SEP-81       1250       1400         30
      7698 BLAKE      MANAGER         7839 01-MAY-81       2850                    30
      7782 CLARK      MANAGER         7839 09-JUN-81       2450                    10
      7788 SCOTT      ANALYST         7566 19-APR-87       3000                    20
      7839 KING       PRESIDENT            17-NOV-81       5000                    10
      7844 TURNER     SALESMAN        7698 08-SEP-81       1500          0         30
      7876 ADAMS      CLERK           7788 23-MAY-87       1100                    20
      7900 JAMES      CLERK           7698 03-DEC-81        950                    30
      7902 FORD       ANALYST         7566 03-DEC-81       3000                    20
      7934 MILLER     CLERK           7782 23-JAN-82       1300                    10

14 rows selected.

2.so basically this is my table where i do the query to select specific columns.

SQL> SELECT ENAME,JOB,SAL
  2  FROM EMP;
  
ENAME      JOB              SAL
---------- --------- ----------
SMITH      CLERK            800
ALLEN      SALESMAN        1600
WARD       SALESMAN        1250
JONES      MANAGER         2975
MARTIN     SALESMAN        1250
BLAKE      MANAGER         2850
CLARK      MANAGER         2450
SCOTT      ANALYST         3000
KING       PRESIDENT       5000
TURNER     SALESMAN        1500
ADAMS      CLERK           1100
JAMES      CLERK            950
FORD       ANALYST         3000
MILLER     CLERK           1300   

14 rows selected.

SO HERE I WANT TO DISPLAY ONLY NAME,DESIGNATION AND SAL COLUMN AND THE ABOVE ARE THE RESULTS.

3.NOW I AM USING WHERE CLAUSE FOR SOME OPERATIONS 

SQL> SELECT JOB
  2  FROM EMP
  3  WHERE ENAME='BLAKE';

JOB
---------
MANAGER

SQL> SELECT *
  2  FROM EMP
  3  WHERE JOB='MANAGER';

     EMPNO ENAME      JOB              MGR HIREDATE         SAL       COMM     DEPTNO
---------- ---------- --------- ---------- --------- ---------- ---------- ----------
      7566 JONES      MANAGER         7839 02-APR-81       2975                    20
      7698 BLAKE      MANAGER         7839 01-MAY-81       2850                    30
      7782 CLARK      MANAGER         7839 09-JUN-81       2450                    10

4. NOW AM USING AND,OR OPERATOR WHICH ARE KNOWN AS LOGICAL OPERATOR IN SQL

     
SQL> SELECT *
  2  FROM EMP 
  3  WHERE JOB='CLERK' AND DEPTNO='10';

     EMPNO ENAME      JOB              MGR HIREDATE         SAL       COMM     DEPTNO
---------- ---------- --------- ---------- --------- ---------- ---------- ----------
      7934 MILLER     CLERK           7782 23-JAN-82       1300                    10

SQL> SELECT *
  2  FROM EMP 
  3  WHERE SAL>1000 AND DEPTNO=30 AND JOB='MANAGER';

     EMPNO ENAME      JOB              MGR HIREDATE         SAL       COMM     DEPTNO
---------- ---------- --------- ---------- --------- ---------- ---------- ----------
      7698 BLAKE      MANAGER         7839 01-MAY-81       2850                    30

AND operators only returns through if the both condition gets satisfied, We used AND operators in between 2 conditions.

5.OR OPERATOR

SQL> SELECT *
  2  FROM EMP
  3  WHERE JOB='PRESIDENT' OR JOB='ANALYST' OR JOB='CLERK';

     EMPNO ENAME      JOB              MGR HIREDATE         SAL       COMM     DEPTNO
---------- ---------- --------- ---------- --------- ---------- ---------- ----------
      7369 SMITH      CLERK           7902 17-DEC-80        800                    20
      7788 SCOTT      ANALYST         7566 19-APR-87       3000                    20
      7839 KING       PRESIDENT            17-NOV-81       5000                    10
      7876 ADAMS      CLERK           7788 23-MAY-87       1100                    20
      7900 JAMES      CLERK           7698 03-DEC-81        950                    30
      7902 FORD       ANALYST         7566 03-DEC-81       3000                    20
      7934 MILLER     CLERK           7782 23-JAN-82       1300                    10
7 rows selected.

SQL> SELECT * 
  2  FROM EMP
  3  WHERE JOB='MANAGER' AND (DEPTNO=10 OR DEPTNO=30);

     EMPNO ENAME      JOB              MGR HIREDATE         SAL       COMM     DEPTNO
---------- ---------- --------- ---------- --------- ---------- ---------- ----------
      7698 BLAKE      MANAGER         7839 01-MAY-81       2850                    30
      7782 CLARK      MANAGER         7839 09-JUN-81       2450                    10

OR operator returns through if atleast one condition gets satisfied.

6.Now am using like and between operator for opeartions which are known as special operators in SQL.

SQL> SELECT ENAME
  2  FROM EMP
  3  WHERE ENAME LIKE '%R';

ENAME
----------
TURNER
MILLER

SQL> SELECT ENAME
  2  FROM EMP 
  3  WHERE ENAME LIKE '%S%';

ENAME
----------
SMITH
JONES
SCOTT
ADAMS
JAMES

The LIKE operator is used to match the pattern with special characters like % and _ (percentile and UnderScore )

7.Between operator 

SQL> SELECT *
  2  FROM EMP
  3  WHERE HIREDATE BETWEEN '01-JAN-82' AND '31-DEC-82';

     EMPNO ENAME      JOB              MGR HIREDATE         SAL       COMM     DEPTNO
---------- ---------- --------- ---------- --------- ---------- ---------- ----------
      7934 MILLER     CLERK           7782 23-JAN-82       1300                    10

SQL> SELECT *
  2  FROM EMP
  3  WHERE HIREDATE BETWEEN '01-JAN-81'AND '31-DEC-83';

     EMPNO ENAME      JOB              MGR HIREDATE         SAL       COMM     DEPTNO
---------- ---------- --------- ---------- --------- ---------- ---------- ----------
      7499 ALLEN      SALESMAN        7698 20-FEB-81       1600        300         30
      7521 WARD       SALESMAN        7698 22-FEB-81       1250        500         30
      7566 JONES      MANAGER         7839 02-APR-81       2975                    20
      7654 MARTIN     SALESMAN        7698 28-SEP-81       1250       1400         30
      7698 BLAKE      MANAGER         7839 01-MAY-81       2850                    30
      7782 CLARK      MANAGER         7839 09-JUN-81       2450                    10
      7839 KING       PRESIDENT            17-NOV-81       5000                    10
      7844 TURNER     SALESMAN        7698 08-SEP-81       1500          0         30
      7900 JAMES      CLERK           7698 03-DEC-81        950                    30
      7902 FORD       ANALYST         7566 03-DEC-81       3000                    20
      7934 MILLER     CLERK           7782 23-JAN-82       1300                    10
BETWEEN OPERATOR which is used for whenever we have a Range.

8.ORDER BY CLAUSE

SQL>  SELECT ENAME,SAL*12 AS ANNUALSAL,SAL*6 AS MIDTERM
  2   FROM EMP
  3   WHERE DEPTNO IS NOT NULL
  4   ORDER BY SAL*6 ASC;

ENAME       ANNUALSAL    MIDTERM
---------- ---------- ----------
SMITH            9600       4800
JAMES           11400       5700
ADAMS           13200       6600
WARD            15000       7500
MARTIN          15000       7500
MILLER          15600       7800
TURNER          18000       9000
ALLEN           19200       9600
CLARK           29400      14700
BLAKE           34200      17100
JONES           35700      17850
SCOTT           36000      18000
FORD            36000      18000
KING            60000      30000


SQL> SELECT ENAME,JOB,SAL
  2  FROM EMP
  3  ORDER BY JOB ASC,SAL DESC;

ENAME      JOB              SAL
---------- --------- ----------
FORD       ANALYST         3000
SCOTT      ANALYST         3000
MILLER     CLERK           1300
ADAMS      CLERK           1100
JAMES      CLERK            950
SMITH      CLERK            800
JONES      MANAGER         2975
BLAKE      MANAGER         2850
CLARK      MANAGER         2450
KING       PRESIDENT       5000
ALLEN      SALESMAN        1600
TURNER     SALESMAN        1500
MARTIN     SALESMAN        1250
WARD       SALESMAN        1250

ORDER CLAUSE is used to SORT the values.
By Default OrderBy clause executes in ascending order.

Thankyou!!

















