### Experiment 4

## Q1. Display the list of employees who have joined the company before 30th june 80 or after 31st Dec 81
```sql
MariaDB [anjali_kumari]> SELECT *
    -> FROM Employee
    -> WHERE HIREDATE < '1980-06-30'
    ->    OR HIREDATE > '1981-12-31';
+-------+--------+---------+------+------------+---------+------+--------+
| Empno | Ename  | Job     | Mgr  | Hiredate   | Sal     | Comm | Deptno |
+-------+--------+---------+------+------------+---------+------+--------+
|  7788 | SCOTT  | ANALYST | 7566 | 1982-12-09 | 3000.00 | NULL |     20 |
|  7876 | ADAMS  | CLERK   | 7788 | 1983-01-12 | 1100.00 | NULL |     20 |
|  7934 | MILLER | CLERK   | 7782 | 1982-01-23 | 1300.00 | NULL |     10 |
+-------+--------+---------+------+------------+---------+------+--------+
3 rows in set (0.001 sec)
```
## Q2.Display the names of employee whose names have second alphabet A in their names.
```sql
MariaDB [anjali_kumari]> SELECT ENAME
    -> FROM Employee
    -> WHERE ENAME LIKE '_A%';
+--------+
| ENAME  |
+--------+
| WARD   |
| MARTIN |
| JAMES  |
+--------+
3 rows in set (0.000 sec)
```
## Q3. Display the names of employees whose name is exactly five characters in length
```sql
MariaDB [anjali_kumari]> SELECT Ename
    -> FROM Employee
    -> WHERE Ename LIKE'_____';
+-------+
| Ename |
+-------+
| SMITH |
| ALLEN |
| JONES |
| BLAKE |
| CLARK |
| SCOTT |
| ADAMS |
| JAMES |
+-------+
8 rows in set (0.001 sec)
```
## Q4.Display the names of employees whose name whose names have second alphabet E in their names.
```sql
MariaDB [anjali_kumari]> SELECT Ename
    -> FROM Employee
    -> WHERE Ename LIKE '%E';
+-------+
| Ename |
+-------+
| BLAKE |
+-------+
1 row in set (0.001 sec)
```
## Q5.Display the names of employee who are not working as salesman or clerk or analyst.
```sql
MariaDB [anjali_kumari]> SELECT ENAME
    -> FROM Employee
    -> WHERE JOB NOT IN ('SALESMAN','CLERK','ANALYST');
+-------+
| ENAME |
+-------+
| JONES |
| BLAKE |
| CLARK |
| KING  |
+-------+
4 rows in set (0.001 sec)
```
## Q6.Display the names of employee along with their annual salary(sal*12). The name of employee earning highest salary should appear first.
```sql
MariaDB [anjali_kumari]> SELECT Ename,Sal*12 AS ANNUALSALARY
    -> FROM Employee
    -> ORDER BY (Sal*12) DESC;
+--------+--------------+
| Ename  | ANNUALSALARY |
+--------+--------------+
| KING   |     60000.00 |
| SCOTT  |     36000.00 |
| FORD   |     36000.00 |
| JONES  |     35700.00 |
| BLAKE  |     34200.00 |
| CLARK  |     29400.00 |
| ALLEN  |     19200.00 |
| TURNER |     18000.00 |
| MILLER |     15600.00 |
| MARTIN |     15000.00 |
| WARD   |     15000.00 |
| ADAMS  |     13200.00 |
| JAMES  |     11400.00 |
| SMITH  |      9600.00 |
+--------+--------------+
14 rows in set (0.001 sec)
```
## Q7. Display name,sal,hra,pf,da,totalsal for each employee. The output should be in the order of total sal,hra 15% of sal, da 10% of sal, pf 5% of sal. Total salary will be (sal*hra*da)-pf.
```sql
MariaDB [anjali_kumari]> SELECT Ename,Sal,
    -> (Sal*0.15) AS HRA,
    -> (Sal*0.10) AS DA,
    -> (Sal*0.05) AS PF,
    -> (Sal + Sal*0.15 + Sal*0.10 - Sal*0.05) AS TOTALSALARY
    -> FROM Employee
    -> ORDER BY TOTALSALARY;
+--------+---------+----------+----------+----------+-------------+
| Ename  | Sal     | HRA      | DA       | PF       | TOTALSALARY |
+--------+---------+----------+----------+----------+-------------+
| SMITH  |  800.00 | 120.0000 |  80.0000 |  40.0000 |    960.0000 |
| JAMES  |  950.00 | 142.5000 |  95.0000 |  47.5000 |   1140.0000 |
| ADAMS  | 1100.00 | 165.0000 | 110.0000 |  55.0000 |   1320.0000 |
| WARD   | 1250.00 | 187.5000 | 125.0000 |  62.5000 |   1500.0000 |
| MARTIN | 1250.00 | 187.5000 | 125.0000 |  62.5000 |   1500.0000 |
| MILLER | 1300.00 | 195.0000 | 130.0000 |  65.0000 |   1560.0000 |
| TURNER | 1500.00 | 225.0000 | 150.0000 |  75.0000 |   1800.0000 |
| ALLEN  | 1600.00 | 240.0000 | 160.0000 |  80.0000 |   1920.0000 |
| CLARK  | 2450.00 | 367.5000 | 245.0000 | 122.5000 |   2940.0000 |
| BLAKE  | 2850.00 | 427.5000 | 285.0000 | 142.5000 |   3420.0000 |
| JONES  | 2975.00 | 446.2500 | 297.5000 | 148.7500 |   3570.0000 |
| FORD   | 3000.00 | 450.0000 | 300.0000 | 150.0000 |   3600.0000 |
| SCOTT  | 3000.00 | 450.0000 | 300.0000 | 150.0000 |   3600.0000 |
| KING   | 5000.00 | 750.0000 | 500.0000 | 250.0000 |   6000.0000 |
+--------+---------+----------+----------+----------+-------------+
14 rows in set (0.001 sec)
```
## Q8.Update the salary of each employee by 10% increment who are not eligible for commission 
```sql
MariaDB [anjali_kumari]> UPDATE Employee
    -> SET SAL = SAL \* 1.10
    -> WHERE COMM IS NULL;
Query OK, 10 rows affected (0.011 sec)
Rows matched: 10  Changed: 10  Warnings: 0
```

## Q9. Display those employees whose salary is more than 3000 after giving 20% increment.
```sql
MariaDB [anjali_kumari]> SELECT *
    -> FROM Employee
    -> WHERE SAL * 1.20 > 3000;
+-------+-------+-----------+------+------------+---------+------+--------+
| Empno | Ename | Job       | Mgr  | Hiredate   | Sal     | Comm | Deptno |
+-------+-------+-----------+------+------------+---------+------+--------+
|  7566 | JONES | MANAGER   | 7839 | 1981-04-02 | 3272.50 | NULL |     20 |
|  7698 | BLAKE | MANAGER   | 7839 | 1981-05-01 | 3135.00 | NULL |     30 |
|  7782 | CLARK | MANAGER   | 7839 | 1981-06-09 | 2695.00 | NULL |     20 |
|  7788 | SCOTT | ANALYST   | 7566 | 1982-12-09 | 3300.00 | NULL |     20 |
|  7839 | KING  | PRESIDENT | NULL | 1981-11-17 | 5500.00 | NULL |     20 |
|  7902 | FORD  | ANALYST   | 7566 | 1981-12-03 | 3300.00 | NULL |     20 |
+-------+-------+-----------+------+------------+---------+------+--------+
6 rows in set (0.001 sec)
```
