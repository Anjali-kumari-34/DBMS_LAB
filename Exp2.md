
### Experiment 2

## Q1. List all distinct job in employee
```sql
MariaDB [anjali_kumari ]> SELECT DISTINCT job FROM EMPLOYEE;
+-----------+
| job       |
+-----------+
| CLERK     |
| SALESMAN  |
| MANAGER   |
| ANALYST   |
| PRESIDENT |
+-----------+
5 rows in set (0.002 sec)
```

## Q2 : List all information about employee in Department Number 30
```sql
MariaDB [anjali_kumari]> SELECT * FROM EMPLOYEE WHERE deptno = 30;
+-------+--------+----------+------+------------+---------+---------+--------+
| Empno | Ename  | Job      | Mgr  | Hiredate   | Sal     | Comm    | Deptno |
+-------+--------+----------+------+------------+---------+---------+--------+
|  7499 | ALLEN  | SALESMAN | 7698 | 1981-02-20 | 1600.00 |  300.00 |     30 |
|  7521 | WARD   | SALESMAN | 7698 | 1981-02-22 | 1250.00 |  300.00 |     30 |
|  7654 | MARTIN | SALESMAN | 7698 | 1981-09-28 | 1250.00 | 1400.00 |     30 |
|  7698 | BLAKE  | MANAGER  | 7839 | 1981-05-01 | 2850.00 |    NULL |     30 |
|  7844 | TURNER | SALESMAN | 7698 | 1981-09-08 | 1500.00 |    0.00 |     30 |
|  7900 | JAMES  | CLERK    | 7698 | 1981-12-03 |  950.00 |    NULL |     30 |
+-------+--------+----------+------+------------+---------+---------+--------+
6 rows in set (0.001 sec)
```

## Q3.Find all department number with department names greater than 20
```sql 
MariaDB [anjali_kumari]> SELECT DISTINCT deptno FROM employee WHERE deptno > 20;
+--------+
| deptno |
+--------+
|     30 |
+--------+
1 row in set (0.002 sec)
```

## Q4.Find all information about all the managers as well as the clerks in department 30
```sql
MariaDB [anjali_kumari]> SELECT * FROM employee
-> WHERE deptno = 30 AND job IN ('MANAGER','CLERK');
+-------+-------+---------+------+------------+---------+------+--------+
| Empno | Ename | Job     | Mgr  | Hiredate   | Sal     | Comm | Deptno |
+-------+-------+---------+------+------------+---------+------+--------+
|  7698 | BLAKE | MANAGER | 7839 | 1981-05-01 | 2850.00 | NULL |     30 |
|  7900 | JAMES | CLERK   | 7698 | 1981-12-03 |  950.00 | NULL |     30 |
+-------+-------+---------+------+------------+---------+------+--------+
2 rows in set (0.002 sec)
```

## Q5.List the employee name, employee numbers and department of all clerks
```sql 
MariaDB [anjali_kumari]> SELECT ename,empno,deptno
    -> FROM EMPLOYEE
    -> WHERE job = 'CLERK';
+--------+-------+--------+
| ename  | empno | deptno |
+--------+-------+--------+
| SMITH  |  7369 |     20 |
| ADAMS  |  7876 |     20 |
| JAMES  |  7900 |     30 |
| MILLER |  7934 |     10 |
+--------+-------+--------+
4 rows in set (0.001 sec)
```

## Q6.Find all managers not in department 30
```sql
MariaDB[anjali_kumari]> SELECT * FROM EMPLOYEE
    -> WHERE job = 'MANAGER' AND deptno <> 30;
+-------+-------+---------+------+------------+---------+------+--------+
| Empno | Ename | Job     | Mgr  | Hiredate   | Sal     | Comm | Deptno |
+-------+-------+---------+------+------------+---------+------+--------+
|  7566 | JONES | MANAGER | 7839 | 1981-04-02 | 2975.00 | NULL |     20 |
|  7782 | CLARK | MANAGER | 7839 | 1981-06-09 | 2450.00 | NULL |     20 |
+-------+-------+---------+------+------------+---------+------+--------+
2 rows in set (0.003 sec)
```

## Q7.List information about all Employees in department 10 who are not manager or clerks
```sql
MariaDB [anjali_kumari]> SELECT * FROM EMPLOYEE
    -> WHERE deptno = 10 AND job NOT IN ('MANAGER','CLERK');
Empty set (0.001 sec)
```

## Q8 : Find employee and jobs earning between 1200 and 1400
```sql
MariaDB [anjali_kumari]> SELECT * FROM EMPLOYEE
  -> WHERE sal BETWEEN 1200 AND 1400;
+-------+--------+----------+------+------------+---------+---------+--------+
| Empno | Ename  | Job      | Mgr  | Hiredate   | Sal     | Comm    | Deptno |
+-------+--------+----------+------+------------+---------+---------+--------+
|  7521 | WARD   | SALESMAN | 7698 | 1981-02-22 | 1250.00 |  300.00 |     30 |
|  7654 | MARTIN | SALESMAN | 7698 | 1981-09-28 | 1250.00 | 1400.00 |     30 |
|  7934 | MILLER | CLERK    | 7782 | 1982-01-23 | 1300.00 |    NULL |     10 |
+-------+--------+----------+------+------------+---------+---------+--------+
3 rows in set (0.001 sec)
```

## Q9.List name and department number of employee who are clerks,analyst or salesman 
```sql
MariaDB [anjali_kumari]> SELECT ename,deptno
    -> FROM employee
    -> WHERE job IN ('CLERK','ANALYST','SALESMAN');
+--------+--------+
| ename  | deptno |
+--------+--------+
| SMITH  |     20 |
| ALLEN  |     30 |
| WARD   |     30 |
| MARTIN |     30 |
| SCOTT  |     20 |
| TURNER |     30 |
| ADAMS  |     20 |
| JAMES  |     30 |
| FORD   |     20 |
| MILLER |     10 |
+--------+--------+
10 rows in set (0.001 sec)
```

## Q10.LIST name and department number of employee whose names begin with M
```sql
MariaDB [anjali_kumari]> SELECT ename,deptno
    -> FROM EMPLOYEE
    -> WHERE ename LIKE 'M%';
+--------+--------+
| ename  | deptno |
+--------+--------+
| MARTIN |     30 |
| MILLER |     10 |
+--------+--------+
2 rows in set (0.001 sec)
```
