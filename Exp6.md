### Experiment 6

## Q1. Display empno, ename , deptno from employee table. Instead of display department numbers display the related department name( use decode function).
```sql
MariaDB [anjali_kumari]> SELECT EMPNO,ENAME,
    -> CASE DEPTNO
    -> WHEN 10 THEN 'RESEARCH'
    -> WHEN 20 THEN 'ACCOUNTING'
    -> WHEN 30 THEN 'SALES'
    -> WHEN 40 THEN 'OPERATIONS'
    -> END AS DEPARTMENT
    -> FROM EMPLOYEE;
+-------+--------+------------+
| EMPNO | ENAME  | DEPARTMENT |
+-------+--------+------------+
|  7369 | SMITH  | ACCOUNTING |
|  7499 | ALLEN  | SALES      |
|  7521 | WARD   | SALES      |
|  7566 | JONES  | ACCOUNTING |
|  7654 | MARTIN | SALES      |
|  7698 | BLAKE  | SALES      |
|  7782 | CLARK  | ACCOUNTING |
|  7788 | SCOTT  | ACCOUNTING |
|  7839 | KING   | ACCOUNTING |
|  7844 | TURNER | SALES      |
|  7876 | ADAMS  | ACCOUNTING |
|  7900 | JAMES  | SALES      |
|  7902 | FORD   | ACCOUNTING |
|  7934 | MILLER | RESEARCH   |
+-------+--------+------------+
14 rows in set (0.052 sec)
```

## Q2. Display your age in months.
```sql
MariaDB [anjali_kumari]> SELECT TIMESTAMPDIFF(MONTH,'2006-10-30',CURDATE()) AS DOB_IN_MONTHS;
+---------------+
| DOB_IN_MONTHS |
+---------------+
|           231 |
+---------------+
1 row in set (0.002 sec)
```
## Q3.Display your age in days.
```sql
MariaDB [anjali_kumari]> SELECT DATEDIFF(CURDATE(),'2006-10-30') AS AGE_IN_DAYS;
+-------------+
| AGE_IN_DAYS |
+-------------+
|        7053 |
+-------------+
1 row in set (0.045 sec)
```

## Q4. Display the current date as 15th August Friday Nineteen Ninety-Seven.
```sql
MariaDB [anjali_kumari]> SELECT DATE_FORMAT(CURDATE(),'%D %M %W %Y');
+--------------------------------------+
| DATE_FORMAT(CURDATE(),'%D %M %W %Y') |
+--------------------------------------+
| 20th February Friday 2026            |
+--------------------------------------+
1 row in set (0.001 sec)
```
## Q5.Display the following output for each row from employee table.
```sql
MariaDB [anjali_kumari]> SELECT CONCAT(
    -> ENAME,
    -> 'has joined the company on',
    -> DATE_FORMAT(HIREDATE, '%W %D %M %Y')
    -> ) AS Required_Format
    -> FROM EMPLOYEE;
+------------------------------------------------------------+
| Required_Format                                            |
+------------------------------------------------------------+
| SMITHhas joined the company onWednesday 17th December 1980 |
| ALLENhas joined the company onFriday 20th February 1981    |
| WARDhas joined the company onSunday 22nd February 1981     |
| JONEShas joined the company onThursday 2nd April 1981      |
| MARTINhas joined the company onMonday 28th September 1981  |
| BLAKEhas joined the company onFriday 1st May 1981          |
| CLARKhas joined the company onTuesday 9th June 1981        |
| SCOTThas joined the company onThursday 9th December 1982   |
| KINGhas joined the company onTuesday 17th November 1981    |
| TURNERhas joined the company onTuesday 8th September 1981  |
| ADAMShas joined the company onWednesday 12th January 1983  |
| JAMEShas joined the company onThursday 3rd December 1981   |
| FORDhas joined the company onThursday 3rd December 1981    |
| MILLERhas joined the company onSaturday 23rd January 1982  |
+------------------------------------------------------------+
14 rows in set (0.042 sec)
```

## Q7. Find the date for nearest Saturday after current date.
```sql
MariaDB [anjali_kumari]> SELECT DATE_ADD(CURDATE(),
    -> INTERVAL(5 - WEEKDAY(CURDATE())) DAY) AS NEXT_SATURDAY;
+---------------+
| NEXT_SATURDAY |
+---------------+
| 2026-02-21    |
+---------------+
1 row in set (0.046 sec)
```
## Q8. Display current time.
```sql
MariaDB [anjali_kumari]> SELECT CURTIME() AS CURR_TIME;
+-----------+
| CURR_TIME |
+-----------+
| 14:57:11  |
+-----------+
1 row in set (0.042 sec)
```

## Q9. Display the date three months before the current date.
```sql
MariaDB [anjali_kumari]> SELECT DATE_SUB(CURDATE(), INTERVAL 3 MONTH) AS THREE_MONTHS_BEFORE;
+---------------------+
| THREE_MONTHS_BEFORE |
+---------------------+
| 2025-11-20          |
+---------------------+
1 row in set (0.001 sec)
```

## Q10. Display those employess who jained in the company in the month of Dec.
```sql
MariaDB [anjali_kumari]> SELECT ENAME,HIREDATE
    -> FROM EMPLOYEE
    -> WHERE MONTH(HIREDATE) = 12;
+-------+------------+
| ENAME | HIREDATE   |
+-------+------------+
| SMITH | 1980-12-17 |
| SCOTT | 1982-12-09 |
| JAMES | 1981-12-03 |
| FORD  | 1981-12-03 |
+-------+------------+
4 rows in set (0.041 sec)
```

## Q11. Display those employess whose first 2 character from hire date last 2 characters of salary.
```sql
MariaDB [anjali_kumari]> SELECT *
    -> FROM EMPLOYEE
    -> WHERE DAY(HIREDATE) = RIGHT(SAL,2);
Empty set (0.001 sec)
```

## Q12.Display those employees whose 10% of salary is equal to the year of joining.
```sql
MariaDB [anjali_kumari]> SELECT *
    -> FROM EMPLOYEE
    -> WHERE (SAL * 0.10) = YEAR(HIREDATE);
Empty set (0.042 sec)
```

## Q13.Display those employees who joined the company before 15th of the months.
```sql
MariaDB [anjali_kumari]> SELECT *
    -> FROM EMPLOYEE
    -> WHERE DAY(HIREDATE) < 15;
+-------+--------+----------+------+------------+---------+------+--------+
| Empno | Ename  | Job      | Mgr  | Hiredate   | Sal     | Comm | Deptno |
+-------+--------+----------+------+------------+---------+------+--------+
|  7566 | JONES  | MANAGER  | 7839 | 1981-04-02 | 3272.50 | NULL |     20 |
|  7698 | BLAKE  | MANAGER  | 7839 | 1981-05-01 | 3135.00 | NULL |     30 |
|  7782 | CLARK  | MANAGER  | 7839 | 1981-06-09 | 2695.00 | NULL |     20 |
|  7788 | SCOTT  | ANALYST  | 7566 | 1982-12-09 | 3300.00 | NULL |     20 |
|  7844 | TURNER | SALESMAN | 7698 | 1981-09-08 | 1500.00 | 0.00 |     30 |
|  7876 | ADAMS  | CLERK    | 7788 | 1983-01-12 | 1210.00 | NULL |     20 |
|  7900 | JAMES  | CLERK    | 7698 | 1981-12-03 | 1045.00 | NULL |     30 |
|  7902 | FORD   | ANALYST  | 7566 | 1981-12-03 | 3300.00 | NULL |     20 |
+-------+--------+----------+------+------------+---------+------+--------+
8 rows in set (0.041 sec)
```

## Q14.Display those employees who joined the company after 15th of the months.
```sql
MariaDB [anjali_kumari]> SELECT *
    -> FROM EMPLOYEE
    -> WHERE DAY(HIREDATE) > 15;
+-------+--------+-----------+------+------------+---------+---------+--------+
| Empno | Ename  | Job       | Mgr  | Hiredate   | Sal     | Comm    | Deptno |
+-------+--------+-----------+------+------------+---------+---------+--------+
|  7369 | SMITH  | CLERK     | 7902 | 1980-12-17 |  880.00 |    NULL |     20 |
|  7499 | ALLEN  | SALESMAN  | 7698 | 1981-02-20 | 1600.00 |  300.00 |     30 |
|  7521 | WARD   | SALESMAN  | 7698 | 1981-02-22 | 1250.00 |  300.00 |     30 |
|  7654 | MARTIN | SALESMAN  | 7698 | 1981-09-28 | 1250.00 | 1400.00 |     30 |
|  7839 | KING   | PRESIDENT | NULL | 1981-11-17 | 5500.00 |    NULL |     20 |
|  7934 | MILLER | CLERK     | 7782 | 1982-01-23 | 1430.00 |    NULL |     10 |
+-------+--------+-----------+------+------------+---------+---------+--------+
6 rows in set (0.001 sec)
```

## Q15.Display those employees whose joining DATE is available in deptno.
```sql
MariaDB [anjali_kumari]> SELECT *
    -> FROM EMPLOYEE
    -> WHERE DAY(HIREDATE) = DEPTNO;
Empty set (0.001 sec)
```

