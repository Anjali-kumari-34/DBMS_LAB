# SQL EXPERIMENT: Creating Employee and Department Tables and performing queries

---

## Step 1 :  Show Database
``` sql
SHOW DATABASES;
```
**OUTPUT :**
```
MariaDB [(none)]> SHOW DATABASES;
+--------------------+
| Database           |
+--------------------+
| college            |
| iilm               |
| information_schema |
| mysql              |
| performance_schema |
| phpmyadmin         |
| test               |
+--------------------+
7 rows in set (0.011 sec)
```
## Step 2 :  Use Database

```sql
USE iilm;
```
**OUTPUT :**
```
Database changed
```
## Step 3 : Creating DEPARTMENT Table
```sql
MariaDB [iilm]> CREATE TABLE Department (
    ->     Deptno INT(2) PRIMARY KEY,
    ->     Dname VARCHAR(15) NOT NULL
    -> );

```
**OUTPUT :**
```
Query OK, 0 rows affected (0.014 sec)
```
## Step 4 : Creating EMPLOYEE Table
```sql
MariaDB [iilm]> CREATE TABLE Employee (
    ->     Empno INT(4) PRIMARY KEY,
    ->     Ename VARCHAR(20) NOT NULL,
    ->     Job VARCHAR(20),
    ->     Mgr INT(4),
    ->     Hiredate DATE,
    ->     Sal DECIMAL(10,2),
    ->     Comm DECIMAL(7,2),
    ->     Deptno INT(2),
    ->     FOREIGN KEY (Deptno) REFERENCES Department(Deptno)
    -> );
```
**OUTPUT :**
```
Query OK, 0 rows affected (0.033 sec)
```
## Step 5 : Inserting Values in DEPARTMENT Table
```sql
MariaDB [iilm]> INSERT INTO Department VALUES
    -> (10, 'RESEARCH'),
    -> (20, 'ACCOUNTING'),
    -> (30, 'SALES'),
    -> (40, 'OPERATIONS');
```
**OUTPUT :**
```
Query OK, 4 rows affected (0.006 sec)
Records: 4  Duplicates: 0  Warnings: 0
```
## Step 6 : Inserting Values in EMPLOYEE Table
```sql
MariaDB [iilm]> INSERT INTO Employee VALUES
    -> (7369,'SMITH','CLERK',7902,'1980-12-17',800,NULL,20),
    -> (7499,'ALLEN','SALESMAN',7698,'1981-02-20',1600,300,30),
    -> (7521,'WARD','SALESMAN',7698,'1981-02-22',1250,300,30),
    -> (7566,'JONES','MANAGER',7839,'1981-04-02',2975,NULL,20),
    -> (7654,'MARTIN','SALESMAN',7698,'1981-09-28',1250,1400,30),
    -> (7698,'BLAKE','MANAGER',7839,'1981-05-01',2850,NULL,30),
    -> (7782,'CLARK','MANAGER',7839,'1981-06-09',2450,NULL,20),
    -> (7788,'SCOTT','ANALYST',7566,'1982-12-09',3000,NULL,20),
    -> (7839,'KING','PRESIDENT',NULL,'1981-11-17',5000,NULL,20),
    -> (7844,'TURNER','SALESMAN',7698,'1981-09-08',1500,0,30),
    -> (7876,'ADAMS','CLERK',7788,'1983-01-12',1100,NULL,20),
    -> (7900,'JAMES','CLERK',7698,'1981-12-03',950,NULL,30),
    -> (7902,'FORD','ANALYST',7566,'1981-12-03',3000,NULL,20),
    -> (7934,'MILLER','CLERK',7782,'1982-01-23',1300,NULL,10);
```
**OUTPUT :**
```
Query OK, 14 rows affected (0.006 sec)
Records: 14  Duplicates: 0  Warnings: 0
```
## Step 7 : Displaying the Tables
```sql
MariaDB [iilm]> SELECT * FROM Employee;
```
**OUTPUT :**
```
+-------+--------+-----------+------+------------+------+------+--------+
| EMPNO | ENAME  | JOB       | MGR  | HIREDATE   | SAL  | COMM | DEPTNO |
+-------+--------+-----------+------+------------+------+------+--------+
|  7369 | SMITH  | CLERK     | 7902 | 1980-12-17 |  800 | NULL |     20 |
|  7499 | ALLEN  | SALESMAN  | 7698 | 1981-02-20 | 1600 |  300 |     30 |
|  7521 | WARD   | SALESMAN  | 7698 | 1981-02-22 | 1250 |  300 |     30 |
|  7566 | JONES  | MANAGER   | 7839 | 1981-04-02 | 2975 | NULL |     20 |
|  7654 | MARTIN | SALESMAN  | 7698 | 1981-09-28 | 1250 | 1400 |     30 |
|  7698 | BLAKE  | MANAGER   | 7839 | 1981-05-01 | 2850 | NULL |     30 |
|  7782 | CLARK  | MANAGER   | 7839 | 1981-06-09 | 2450 | NULL |     20 |
|  7788 | SCOTT  | ANALYST   | 7566 | 1982-12-09 | 3000 | NULL |     40 |
|  7839 | KING   | PRESIDENT | NULL | 1981-11-17 | 5000 | NULL |     20 |
|  7844 | TURNER | SALESMAN  | 7698 | 1981-09-08 | 1500 |    0 |     30 |
|  7876 | ADAMS  | CLERK     | 7788 | 1983-01-12 | 1100 | NULL |     20 |
|  7900 | JAMES  | CLERK     | 7698 | 1981-12-03 |  950 | NULL |     30 |
|  7902 | FORD   | ANALYST   | 7566 | 1981-12-03 | 3000 | NULL |     20 |
|  7934 | MILLER | CLERK     | 7782 | 1982-01-23 | 1300 | NULL |     10 |
+-------+--------+-----------+------+------------+------+------+--------+
14 rows in set (0.001 sec)
```
```sql
MariaDB [iilm]> SELECT * FROM Department;
```
**OUTPUT :**
```
+--------+------------+
| Deptno | Dname      |
+--------+------------+
|     10 | RESEARCH   |
|     20 | ACCOUNTING |
|     30 | SALES      |
|     40 | OPERATIONS |
+--------+------------+
4 rows in set (0.001 sec)
```


## <u> Step 6 : Perform the following queries:</u>
## Q1: Create EMPLOYEE_MASTER table using EMPLOYEE table
```sql
MariaDB [iilm]> CREATE TABLE Employee_Master AS
    -> SELECT * FROM Employee;
```
**OUTPUT:**
```
Query OK, 14 rows affected (0.016 sec)
Records: 14  Duplicates: 0  Warnings: 0

MariaDB [iilm]> SELECT * FROM Employee_master;
```
**OUTPUT :**
```
+-------+--------+-----------+------+------------+------+------+--------+
| EMPNO | ENAME  | JOB       | MGR  | HIREDATE   | SAL  | COMM | DEPTNO |
+-------+--------+-----------+------+------------+------+------+--------+
|  7369 | SMITH  | CLERK     | 7902 | 1980-12-17 |  800 | NULL |     20 |
|  7499 | ALLEN  | SALESMAN  | 7698 | 1981-02-20 | 1600 |  300 |     30 |
|  7521 | WARD   | SALESMAN  | 7698 | 1981-02-22 | 1250 |  300 |     30 |
|  7566 | JONES  | MANAGER   | 7839 | 1981-04-02 | 2975 | NULL |     20 |
|  7654 | MARTIN | SALESMAN  | 7698 | 1981-09-28 | 1250 | 1400 |     30 |
|  7698 | BLAKE  | MANAGER   | 7839 | 1981-05-01 | 2850 | NULL |     30 |
|  7782 | CLARK  | MANAGER   | 7839 | 1981-06-09 | 2450 | NULL |     20 |
|  7788 | SCOTT  | ANALYST   | 7566 | 1982-12-09 | 3000 | NULL |     40 |
|  7839 | KING   | PRESIDENT | NULL | 1981-11-17 | 5000 | NULL |     20 |
|  7844 | TURNER | SALESMAN  | 7698 | 1981-09-08 | 1500 |    0 |     30 |
|  7876 | ADAMS  | CLERK     | 7788 | 1983-01-12 | 1100 | NULL |     20 |
|  7900 | JAMES  | CLERK     | 7698 | 1981-12-03 |  950 | NULL |     30 |
|  7902 | FORD   | ANALYST   | 7566 | 1981-12-03 | 3000 | NULL |     20 |
|  7934 | MILLER | CLERK     | 7782 | 1982-01-23 | 1300 | NULL |     10 |
+-------+--------+-----------+------+------------+------+------+--------+
14 rows in set (0.001 sec)
```
## Q2 : Delete records from EMPLOYEE_MASTER where DeptNo = 10
```sql
MariaDB [iilm]> DELETE FROM Employee_Master
    -> WHERE Deptno = 10;
Query OK, 0 rows affected (0.004 sec)

MariaDB [iilm]> SELECT * FROM employee_master;
```
**OUTPUT :**
```
+-------+--------+-----------+------+------------+------+------+--------+
| EMPNO | ENAME  | JOB       | MGR  | HIREDATE   | SAL  | COMM | DEPTNO |
+-------+--------+-----------+------+------------+------+------+--------+
|  7369 | SMITH  | CLERK     | 7902 | 1980-12-17 |  800 | NULL |     20 |
|  7499 | ALLEN  | SALESMAN  | 7698 | 1981-02-20 | 1600 |  300 |     30 |
|  7521 | WARD   | SALESMAN  | 7698 | 1981-02-22 | 1250 |  300 |     30 |
|  7566 | JONES  | MANAGER   | 7839 | 1981-04-02 | 2975 | NULL |     20 |
|  7654 | MARTIN | SALESMAN  | 7698 | 1981-09-28 | 1250 | 1400 |     30 |
|  7698 | BLAKE  | MANAGER   | 7839 | 1981-05-01 | 2850 | NULL |     30 |
|  7782 | CLARK  | MANAGER   | 7839 | 1981-06-09 | 2450 | NULL |     20 |
|  7788 | SCOTT  | ANALYST   | 7566 | 1982-12-09 | 3000 | NULL |     40 |
|  7839 | KING   | PRESIDENT | NULL | 1981-11-17 | 5000 | NULL |     20 |
|  7844 | TURNER | SALESMAN  | 7698 | 1981-09-08 | 1500 |    0 |     30 |
|  7876 | ADAMS  | CLERK     | 7788 | 1983-01-12 | 1100 | NULL |     20 |
|  7900 | JAMES  | CLERK     | 7698 | 1981-12-03 |  950 | NULL |     30 |
|  7902 | FORD   | ANALYST   | 7566 | 1981-12-03 | 3000 | NULL |     20 |
+-------+--------+-----------+------+------------+------+------+--------+
13 rows in set (0.001 sec)
```
## Q3 : Update 10% salary of employees of DeptNo 20
```sql
MariaDB [iilm]> UPDATE Employee_Master
    -> SET Sal = Sal + (Sal * 0.10)
    -> WHERE Deptno = 20;
Query OK, 7 rows affected (0.002 sec)
Rows matched: 7  Changed: 7  Warnings: 0

MariaDB [iilm]> SELECT * FROM employee_master;
```
**OUTPUT :**
```
+-------+--------+-----------+------+------------+------+------+--------+
| EMPNO | ENAME  | JOB       | MGR  | HIREDATE   | SAL  | COMM | DEPTNO |
+-------+--------+-----------+------+------------+------+------+--------+
|  7369 | SMITH  | CLERK     | 7902 | 1980-12-17 |  880 | NULL |     20 |
|  7499 | ALLEN  | SALESMAN  | 7698 | 1981-02-20 | 1600 |  300 |     30 |
|  7521 | WARD   | SALESMAN  | 7698 | 1981-02-22 | 1250 |  300 |     30 |
|  7566 | JONES  | MANAGER   | 7839 | 1981-04-02 | 3273 | NULL |     20 |
|  7654 | MARTIN | SALESMAN  | 7698 | 1981-09-28 | 1250 | 1400 |     30 |
|  7698 | BLAKE  | MANAGER   | 7839 | 1981-05-01 | 2850 | NULL |     30 |
|  7782 | CLARK  | MANAGER   | 7839 | 1981-06-09 | 2695 | NULL |     20 |
|  7788 | SCOTT  | ANALYST   | 7566 | 1982-12-09 | 3000 | NULL |     40 |
|  7839 | KING   | PRESIDENT | NULL | 1981-11-17 | 5500 | NULL |     20 |
|  7844 | TURNER | SALESMAN  | 7698 | 1981-09-08 | 1500 |    0 |     30 |
|  7876 | ADAMS  | CLERK     | 7788 | 1983-01-12 | 1210 | NULL |     20 |
|  7900 | JAMES  | CLERK     | 7698 | 1981-12-03 |  950 | NULL |     30 |
|  7902 | FORD   | ANALYST   | 7566 | 1981-12-03 | 3300 | NULL |     20 |
+-------+--------+-----------+------+------------+------+------+--------+
13 rows in set (0.001 sec)
```
## Q4 : Alter SAL column size to 10,2 in EMPLOYEE_MASTER
```sql
MariaDB [iilm]> ALTER TABLE Employee_Master
    -> MODIFY Sal DECIMAL(10,2);
Query OK, 0 rows affected (0.011 sec)
Records: 0  Duplicates: 0  Warnings: 0

MariaDB [iilm]> DESCRIBE employee_master;
```
**OUTPUT :**
```+----------+---------------+------+-----+---------+-------+
| Field    | Type          | Null | Key | Default | Extra |
+----------+---------------+------+-----+---------+-------+
| EMPNO    | int(11)       | NO   |     | NULL    |       |
| ENAME    | varchar(20)   | NO   |     | NULL    |       |
| JOB      | varchar(20)   | YES  |     | NULL    |       |
| MGR      | int(11)       | YES  |     | NULL    |       |
| HIREDATE | date          | YES  |     | NULL    |       |
| SAL      | decimal(10,2) | YES  |     | NULL    |       |
| COMM     | decimal(7,0)  | YES  |     | NULL    |       |
| DEPTNO   | int(11)       | YES  |     | NULL    |       |
+----------+---------------+------+-----+---------+-------+
8 rows in set (0.013 sec)
```
## Q5 : Drop EMPLOYEE_MASTER table
```sql
MariaDB [iilm]> DROP TABLE Employee_Master;
Query OK, 0 rows affected (0.012 sec)

MariaDB [iilm]> SHOW TABLES;
```
**OUTPUT :**
```
+-------------------+
| Tables_in_company |
+-------------------+
| department        |
| employee          |
| employee_master   |
+-------------------+
3 rows in set (0.001 sec)
+-------------------+
| Tables_in_company |
+-------------------+
| department        |
| employee          |
+-------------------+
2 rows in set (0.001 sec)
```

## Name : Anjali kumari(2410031047)