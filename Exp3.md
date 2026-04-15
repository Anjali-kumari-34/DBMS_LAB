
### Experiment 3:

## Q1.List all employee and jobs in department 30 in descending order by salary
```sql
MariaDB [anjali_kumari]> SELECT ENAME, JOB, SAL
    -> FROM EMPLOYEE
    -> WHERE DEPTNO = 30
    -> ORDER BY SAL DESC;
+--------+----------+---------+
| ENAME  | JOB      | SAL     |
+--------+----------+---------+
| BLAKE  | MANAGER  | 2850.00 |
| ALLEN  | SALESMAN | 1600.00 |
| TURNER | SALESMAN | 1500.00 |
| WARD   | SALESMAN | 1250.00 |
| MARTIN | SALESMAN | 1250.00 |
| JAMES  | CLERK    |  950.00 |
+--------+----------+---------+
6 rows in set (0.005 sec)
```

## Q2.List job and department number of employees whose name are five letters long begin with "A" and end with "N"
```sql
MariaDB [anjali_kumari]> SELECT JOB, DEPTNO
    -> FROM EMPLOYEE
    -> WHERE ENAME LIKE 'A___N';
+----------+--------+
| JOB      | DEPTNO |
+----------+--------+
| SALESMAN |     30 |
+----------+--------+
1 row in set (0.001 sec)
```
## Q3. Display the name of employees whose name start with alphabet S 
```sql
MariaDB [anjali_kumari]> SELECT ENAME
    -> FROM EMPLOYEE
    -> WHERE ENAME LIKE 'S%';
+-------+
| ENAME |
+-------+
| SMITH |
| SCOTT |
+-------+
2 rows in set (0.001 sec)
```

## Q4.Display the names of employees whose name ends with alphabat S 
```sql
MariaDB [anjali_kumari]> SELECT ENAME
    -> FROM EMPLOYEE
    -> WHERE ENAME LIKE '%S';
+-------+
| ENAME |
+-------+
| JONES |
| ADAMS |
| JAMES |
+-------+
3 rows in set (0.001 sec)
```

## Q5.Display the names of employees working in department number 10 or 20 or 40 or employees working as clerks,salesman or analyst
```sql
MariaDB [anjali_kumari]> SELECT ENAME
    -> FROM EMPLOYEE
    -> WHERE DEPTNO IN (10, 20, 40)
    ->    OR JOB IN ('CLERK', 'SALESMAN', 'ANALYST');
+--------+
| ENAME  |
+--------+
| SMITH  |
| ALLEN  |
| WARD   |
| JONES  |
| MARTIN |
| CLARK  |
| SCOTT  |
| KING   |
| TURNER |
| ADAMS  |
| JAMES  |
| FORD   |
+--------+
12 rows in set (0.004 sec)
```

## Q6.Display employee number and names for employees who earn commission
```sql
MariaDB [anjali_kumari]> SELECT EMPNO, ENAME
    -> FROM EMPLOYEE
    -> WHERE COMM IS NOT NULL;
+-------+--------+
| EMPNO | ENAME  |
+-------+--------+
|  7499 | ALLEN  |
|  7521 | WARD   |
|  7654 | MARTIN |
|  7844 | TURNER |
+-------+--------+
4 rows in set (0.002 sec)
```

## Q7.Display employee number and total salary for each employee
```sql
MariaDB [anjali_kumari]> SELECT EMPNO, SAL + IFNULL(COMM, 0) AS TOTAL_SALARY
    -> FROM EMPLOYEE;
+-------+--------------+
| EMPNO | TOTAL_SALARY |
+-------+--------------+
|  7369 |       800.00 |
|  7499 |      1900.00 |
|  7521 |      1550.00 |
|  7566 |      2975.00 |
|  7654 |      2650.00 |
|  7698 |      2850.00 |
|  7782 |      2450.00 |
|  7788 |      3000.00 |
|  7839 |      5000.00 |
|  7844 |      1500.00 |
|  7876 |      1100.00 |
|  7900 |       950.00 |
|  7902 |      3000.00 |
+-------+--------------+
13 rows in set (0.006 sec)
```

## Q8.Display employee number and annual salary for each employee
```sql
MariaDB [anjali_kumari]> SELECT EMPNO, SAL * 12 AS ANNUAL_SALARY
    -> FROM EMPLOYEE;
+-------+---------------+
| EMPNO | ANNUAL_SALARY |
+-------+---------------+
|  7369 |       9600.00 |
|  7499 |      19200.00 |
|  7521 |      15000.00 |
|  7566 |      35700.00 |
|  7654 |      15000.00 |
|  7698 |      34200.00 |
|  7782 |      29400.00 |
|  7788 |      36000.00 |
|  7839 |      60000.00 |
|  7844 |      18000.00 |
|  7876 |      13200.00 |
|  7900 |      11400.00 |
|  7902 |      36000.00 |
+-------+---------------+
13 rows in set (0.001 sec)
```

## Q9.Display the names of all employees working as clerks and drawing a salary more than 3000
```sql
MariaDB [anjali_kumari]> SELECT ENAME
    -> FROM EMPLOYEE
    -> WHERE JOB = 'CLERK'
    ->   AND SAL > 3000;
Empty set (0.005 sec)
```

## Q10.Display the names of employees who are working as clerk,salesman or analyst and drawing a salary more than 3000
```sql
MariaDB [anjali_kumari]> SELECT ENAME
    -> FROM EMPLOYEE
    -> WHERE JOB IN ('CLERK', 'SALESMAN', 'ANALYST')
    ->   AND SAL > 3000;
Empty set (0.001 sec)
```
