### Experiment 5

## Q1. Display the total number of employee working in the company
```sql
MariaDB [anjali_kumari]> SELECT COUNT(*) AS TOTAL_EMPLOYEES             
    -> FROM Employee;
+-----------------+
| TOTAL_EMPLOYEES |
+-----------------+
|              14 |
+-----------------+
1 row in set (0.001 sec)
```

## Q2.Display the total salary being paid to all employess.
```sql
MariaDB [anjali_kumari]> SELECT SUM(SAL) AS TOTAL_SALARY
    -> FROM Employee;
+--------------+
| TOTAL_SALARY |
+--------------+
|     31367.50 |
+--------------+
1 row in set (0.001 sec)
```
## Q3. Display the maximum salary from employee table .
```sql
MariaDB [anjali_kumari]> SELECT MAX(SAL) AS MAX_SALARY
    -> FROM Employee;
+------------+
| MAX_SALARY |
+------------+
|    5500.00 |
+------------+
1 row in set (0.001 sec)
```
## Q4. Display the minimum salary from employee table.
```sql
MariaDB [anjali_kumari]> SELECT MIN(SAL) AS MIN_SALARY
    -> FROM Employee;
+------------+
| MIN_SALARY |
+------------+
|     880.00 |
+------------+
1 row in set (0.001 sec)
```
## Q5.Display the average salary from employee table.
```sql
MariaDB [anjali_kumari]> SELECT AVG(SAL) AS AVG_SALARY
    -> FROM Employee;
+-------------+
| AVG_SALARY  |
+-------------+
| 2240.535714 |
+-------------+
1 row in set (0.001 sec)
```
## Q6.Display the maximum salary being paid to clerk.
```sql
MariaDB [anjali_kumari]> SELECT MAX(SAL) AS MAX_CLERK_SALARY
    -> FROM Employee
    -> WHERE JOB = 'CLERK';
+------------------+
| MAX_CLERK_SALARY |
+------------------+
|          1430.00 |
+------------------+
1 row in set (0.000 sec)
```
## Q7.Display the maximum salary paid in dept no 20.
```sql
MariaDB [anjali_kumari]> SELECT MAX(SAL) AS MAX_DEPT20_SALARY
    -> FROM Employee
    -> WHERE DEPTNO = 20;
+-------------------+
| MAX_DEPT20_SALARY |
+-------------------+
|           5500.00 |
+-------------------+
1 row in set (0.002 sec)
```
## Q8. Display the minimum salary paid to any salesman.
```sql
MariaDB [anjali_kumari]> SELECT MIN(SAL) AS MIN_SALESMAN_SALARY
    -> FROM Employee
    -> WHERE JOB = 'SALESMAN';
+---------------------+
| MIN_SALESMAN_SALARY |
+---------------------+
|             1250.00 |
+---------------------+
1 row in set (0.001 sec)
```
## Q9. Display the average salary drawn by managers.
```sql
MariaDB [anjali_kumari]> SELECT AVG(SAL) AS AVG_MANAGER_SALARY
    -> FROM Employee
    -> WHERE JOB = 'MANAGER';
+--------------------+
| AVG_MANAGER_SALARY |
+--------------------+
|        3034.166667 |
+--------------------+
1 row in set (0.001 sec)
```

## Q10. Display the total salary drwn by analyst working in dept no 40.
```sql
MariaDB [anjali_kumari]> SELECT SUM(SAL) AS TOTAL_ANALYST_SALARY
    -> FROM Employee
    -> WHERE JOB = 'ANALYST'
    -> AND DEPTNO = 40;
+----------------------+
| TOTAL_ANALYST_SALARY |
+----------------------+
|                 NULL |
+----------------------+
1 row in set (0.007 sec)
```

## Q11. Display the names of the employee in uppercase.
```sql
MariaDB [anjali_kumari]> SELECT UPPER(ENAME) AS NAME_UPPER
    -> FROM Employee;
+------------+
| NAME_UPPER |
+------------+
| SMITH      |
| ALLEN      |
| WARD       |
| JONES      |
| MARTIN     |
| BLAKE      |
| CLARK      |
| SCOTT      |
| KING       |
| TURNER     |
| ADAMS      |
| JAMES      |
| FORD       |
| MILLER     |
+------------+
14 rows in set (0.001 sec)
```

## Q12. Display the names of the employee in lowercase
```sql
MariaDB [anjali_kumari]> SELECT LOWER(ENAME) AS NAME_LOWER
    -> FROM Employee;
+------------+
| NAME_LOWER |
+------------+
| smith      |
| allen      |
| ward       |
| jones      |
| martin     |
| blake      |
| clark      |
| scott      |
| king       |
| turner     |
| adams      |
| james      |
| ford       |
| miller     |
+------------+
14 rows in set (0.001 sec)
```

## Q13.Display the names of the employee in proper case.
```sql
MariaDB [anjali_kumari]> SELECT CONCAT(UCASE(LEFT(ENAME,1)), LCASE(SUBSTRING(ENAME,2)))
    -> FROM Employee;
+---------------------------------------------------------+
| CONCAT(UCASE(LEFT(ENAME,1)), LCASE(SUBSTRING(ENAME,2))) |
+---------------------------------------------------------+
| Smith                                                   |
| Allen                                                   |
| Ward                                                    |
| Jones                                                   |
| Martin                                                  |
| Blake                                                   |
| Clark                                                   |
| Scott                                                   |
| King                                                    |
| Turner                                                  |
| Adams                                                   |
| James                                                   |
| Ford                                                    |
| Miller                                                  |
+---------------------------------------------------------+
14 rows in set (0.001 sec)
```

## Q14. Display the length of Your name using appropriate function.
```sql
MariaDB [anjali_kumari]> SELECT LENGTH('ANJALI') AS NAME_LENGTH;
+-------------+
| NAME_LENGTH |
+-------------+
|           6 |
+-------------+
1 row in set (0.001 sec)
```

## Q15. Display the length of all the employees names.
```sql
MariaDB [anjali_kumari]> SELECT ENAME, LENGTH(ENAME) AS NAME_LENGTH
    -> FROM Employee;
+--------+-------------+
| ENAME  | NAME_LENGTH |
+--------+-------------+
| SMITH  |           5 |
| ALLEN  |           5 |
| WARD   |           4 |
| JONES  |           5 |
| MARTIN |           6 |
| BLAKE  |           5 |
| CLARK  |           5 |
| SCOTT  |           5 |
| KING   |           4 |
| TURNER |           6 |
| ADAMS  |           5 |
| JAMES  |           5 |
| FORD   |           4 |
| MILLER |           6 |
+--------+-------------+
14 rows in set (0.000 sec)
```
