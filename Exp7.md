### Experiment 7:

## Q1: Compute the no. of days remaining in this year
```sql
MariaDB [anjali_kumari]> SELECT DATEDIFF(
    ->     CONCAT(YEAR(CURDATE()),'-12-31'),CURDATE());

+-----------------------------------------------------------+
| DATEDIFF(
    CONCAT(YEAR(CURDATE()),'-12-31'),CURDATE()) |
+-----------------------------------------------------------+
|                                                       281 |
+-----------------------------------------------------------+
1 row in set (0.006 sec)
```
## Q2: Find the highest and lowest salaries and the difference between them
```sql
MariaDB [anjali_kumari]> SELECT
    -> MAX(SAL) AS HIGHEST_SALARY,
    -> MIN(SAL) AS LOWEST_SALARY,
    -> MAX(SAL) - MIN(SAL) AS DIFFERENCE
    -> FROM EMPLOYEE;

+----------------+---------------+------------+
| HIGHEST_SALARY | LOWEST_SALARY | DIFFERENCE |
+----------------+---------------+------------+
|        5500.00 |        880.00 |    4620.00 |
+----------------+---------------+------------+
1 row in set (0.056 sec)
```
## Q3:List employee whose commission is greater than 25 % of their salaries
```sql
MariaDB [anjali_kumari]> SELECT ENAME, SAL, COMM
    -> FROM EMPLOYEE
    -> WHERE COMM > (SAL * 0.25);
+--------+---------+---------+
| ENAME  | SAL     | COMM    |
+--------+---------+---------+
| MARTIN | 1250.00 | 1400.00 |
+--------+---------+---------+
1 row in set (0.004 sec)
```
## Q4:Make a query that displays salary in dollar format
```sql
MariaDB [anjali_kumari]> SELECT ENAME,
    -> CONCAT('$', FORMAT(SAL, 2)) AS SALARY_IN_DOLLAR
    -> FROM EMPLOYEE;
+--------+------------------+
| ENAME  | SALARY_IN_DOLLAR |
+--------+------------------+
| SMITH  | $880.00          |
| ALLEN  | $1,600.00        |
| WARD   | $1,250.00        |
| JONES  | $3,272.50        |
| MARTIN | $1,250.00        |
| BLAKE  | $3,135.00        |
| CLARK  | $2,695.00        |
| SCOTT  | $3,300.00        |
| KING   | $5,500.00        |
| TURNER | $1,500.00        |
| ADAMS  | $1,210.00        |
| JAMES  | $1,045.00        |
| FORD   | $3,300.00        |
| MILLER | $1,430.00        |
+--------+------------------+
14 rows in set (0.007 sec)
```

## Q5:Create a matrix query to display the job, the salary for that job based on department number, and the total salary for that job for all departments, giving each column an appropriate heading
```sql
MariaDB [anjali_kumari]> SELECT
    -> JOB,
    -> SUM(CASE WHEN DEPTNO = 10 THEN SAL ELSE 0 END) AS DEPT10,
    -> SUM(CASE WHEN DEPTNO = 20 THEN SAL ELSE 0 END) AS DEPT20,
    -> SUM(CASE WHEN DEPTNO = 30 THEN SAL ELSE 0 END) AS DEPT30,
    -> SUM(CASE WHEN DEPTNO = 40 THEN SAL ELSE 0 END) AS DEPT40,
    -> SUM(SAL) AS TOTAL_SALARY
    -> FROM EMPLOYEE
    -> GROUP BY JOB;
+-----------+---------+---------+---------+--------+--------------+
| JOB       | DEPT10  | DEPT20  | DEPT30  | DEPT40 | TOTAL_SALARY |
+-----------+---------+---------+---------+--------+--------------+
| ANALYST   |    0.00 | 6600.00 |    0.00 |   0.00 |      6600.00 |
| CLERK     | 1430.00 | 2090.00 | 1045.00 |   0.00 |      4565.00 |
| MANAGER   |    0.00 | 5967.50 | 3135.00 |   0.00 |      9102.50 |
| PRESIDENT |    0.00 | 5500.00 |    0.00 |   0.00 |      5500.00 |
| SALESMAN  |    0.00 |    0.00 | 5600.00 |   0.00 |      5600.00 |
+-----------+---------+---------+---------+--------+--------------+
5 rows in set (0.008 sec)
```

## Q6:Query that will display the total no of employees, and of that total the number who were hired in 1980,1981,1982 and 1983. Give appropriate column heading
```sql
MariaDB [anjali_kumari]> SELECT
    -> COUNT(*) AS TOTAL_EMPLOYEES,
    -> SUM(CASE WHEN YEAR(HIREDATE) = 1980 THEN 1 ELSE 0 END) AS "1980",
    -> SUM(CASE WHEN YEAR(HIREDATE) = 1981 THEN 1 ELSE 0 END) AS "1981",
    -> SUM(CASE WHEN YEAR(HIREDATE) = 1982 THEN 1 ELSE 0 END) AS "1982",
    -> SUM(CASE WHEN YEAR(HIREDATE) = 1983 THEN 1 ELSE 0 END) AS "1983"
    -> FROM EMPLOYEE;
+-----------------+------+------+------+------+
| TOTAL_EMPLOYEES | 1980 | 1981 | 1982 | 1983 |
+-----------------+------+------+------+------+
|              14 |    1 |   10 |    2 |    1 |
+-----------------+------+------+------+------+
1 row in set (0.001 sec)
```

## Q7:Query to get the last Sunday of Any Month
```sql
MariaDB [anjali_kumari]> SELECT
    -> DATE_SUB(
    ->     LAST_DAY('2026-02-01'),
    ->     INTERVAL (WEEKDAY(LAST_DAY('2026-02-01')) + 1) DAY
    -> ) AS LAST_SUNDAY;
+-------------+
| LAST_SUNDAY |
+-------------+
| 2026-02-22  |
+-------------+
1 row in set (0.005 sec)
```

## Q8:Display department numbers and total number of employees working in each department
```sql
MariaDB [anjali_kumari]> SELECT DEPTNO, COUNT(*) AS TOTAL_EMPLOYEES
    -> FROM EMPLOYEE
    -> GROUP BY DEPTNO;
+--------+-----------------+
| DEPTNO | TOTAL_EMPLOYEES |
+--------+-----------------+
|     10 |               1 |
|     20 |               7 |
|     30 |               6 |
+--------+-----------------+
3 rows in set (0.005 sec)
```

## Q9:Display the various jobs and total number of employees within each job group
```sql
MariaDB [anjali_kumari]> SELECT JOB, COUNT(*) AS TOTAL_EMPLOYEES
    -> FROM EMPLOYEE
    -> GROUP BY JOB;
+-----------+-----------------+
| JOB       | TOTAL_EMPLOYEES |
+-----------+-----------------+
| ANALYST   |               2 |
| CLERK     |               4 |
| MANAGER   |               3 |
| PRESIDENT |               1 |
| SALESMAN  |               4 |
+-----------+-----------------+
5 rows in set (0.001 sec)
```

## Q10:Display the depart numbers and total salary for each department
```sql
MariaDB [anjali_kumari]> SELECT DEPTNO, SUM(SAL) AS TOTAL_SALARY
    -> FROM EMPLOYEE
    -> GROUP BY DEPTNO;
+--------+--------------+
| DEPTNO | TOTAL_SALARY |
+--------+--------------+
|     10 |      1430.00 |
|     20 |     20157.50 |
|     30 |      9780.00 |
+--------+--------------+
3 rows in set (0.004 sec)
```

