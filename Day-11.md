Day_11_MySQL
=============

Aggregate Functions:
=====================
Count() :- count the number of records
sum()   :- returns the total sum of numeric column.
avg()   :- return the average value
min()   :- returns the minimum value
max()   :- returns the maximum value

mysql> use pfs4;
Database changed
mysql> show tables;
+----------------+
| Tables_in_pfs4 |
+----------------+
| company_staff  |
| emp            |
| employees      |
| orders         |
| products       |
| projects       |
| studentscores  |
+----------------+
7 rows in set (0.05 sec)

mysql> select * from employees;
+--------+----------+------------+----------+------------+------+
| emp_id | emp_name | department | salary   | experience | age  |
+--------+----------+------------+----------+------------+------+
|    101 | Ravi     | IT         | 65000.00 |          5 |   28 |
|    102 | Priya    | HR         | 45000.00 |          2 |   24 |
|    103 | Amit     | Finance    | 75000.00 |          8 |   35 |
|    104 | Sneha    | IT         | 55000.00 |          3 |   27 |
|    105 | Rahul    | Sales      | 40000.00 |          1 |   22 |
|    106 | Kiran    | Finance    | 90000.00 |         12 |   40 |
|    107 | Anjali   | HR         | 52000.00 |          4 |   29 |
|    108 | Suresh   | Sales      | 68000.00 |          7 |   33 |
+--------+----------+------------+----------+------------+------+
8 rows in set (0.00 sec)

mysql> select count(*) as total_records from employees;
+---------------+
| total_records |
+---------------+
|             8 |
+---------------+
1 row in set (0.02 sec)

mysql> select sum(salary) from employees;
+-------------+
| sum(salary) |
+-------------+
|   490000.00 |
+-------------+
1 row in set (0.00 sec)

mysql> select avg(salary) from employees;
+--------------+
| avg(salary)  |
+--------------+
| 61250.000000 |
+--------------+
1 row in set (0.00 sec)

mysql> select min(salary) from employees;
+-------------+
| min(salary) |
+-------------+
|    40000.00 |
+-------------+
1 row in set (0.00 sec)

mysql> select max(salary) from employees;
+-------------+
| max(salary) |
+-------------+
|    90000.00 |
+-------------+
1 row in set (0.00 sec)

mysql> SELECT CURTIME();
+-----------+
| CURTIME() |
+-----------+
| 11:26:05  |
+-----------+
1 row in set (0.00 sec)

mysql> SELECT CURDATE();
+------------+
| CURDATE()  |
+------------+
| 2026-07-24 |
+------------+
1 row in set (0.00 sec)

mysql> SELECT NOW();
+---------------------+
| NOW()               |
+---------------------+
| 2026-07-24 11:26:30 |
+---------------------+
1 row in set (0.00 sec)

mysql> SELECT DATABASE();
+------------+
| DATABASE() |
+------------+
| pfs4       |
+------------+
1 row in set (0.00 sec)

mysql> SELECT USER();
+----------------+
| USER()         |
+----------------+
| root@localhost |
+----------------+
1 row in set (0.00 sec)

mysql> SELECT VERSION();
+-----------+
| VERSION() |
+-----------+
| 8.0.46    |
+-----------+
1 row in set (0.01 sec)

mysql> SELCT UTC_DATE();
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'SELCT UTC_DATE()' at line 1
mysql> SELECT UTC_DATE();
+------------+
| UTC_DATE() |
+------------+
| 2026-07-24 |
+------------+
1 row in set (0.00 sec)

mysql> SELECT UTC_TIME();
+------------+
| UTC_TIME() |
+------------+
| 05:58:53   |
+------------+
1 row in set (0.00 sec)

mysql> SELECT UTC_TIMESTAMP();
+---------------------+
| UTC_TIMESTAMP()     |
+---------------------+
| 2026-07-24 05:59:06 |
+---------------------+
1 row in set (0.00 sec)

Clauses:
=========
In MySQL , Clauses are used to control how data is selected , filtered , grouped , sorted or modified in SQL queries.
Think of clauses like instructions given to the database.

Where clause
=============
filter records based on specified conditions where clause can be used as comparison operations , logical, operators.. etc operators
syntax:
========
select col1, col2..........
from table 
where condition.

Group By Clause 
================
the group by clause is used to group rows having the same values in one or more columns . it is commonly used with aggregate functions such as sum(),min().max(),avg(),count().
syntax
========
select col-name, aggregate_function(col-name)
from table
group by col-name;

Having Clause
==============
the having clause is used to filter grouped records after group by clause , it is similar to where but it works on grouped instead of individual rows 
syntax:
========
select col-name, aggregate_function(col-name)
from table
group by col-name
having condition;

Order by
=========
the order by clause is used to sort the results in the ascending order(ASC) and descending order(DESC)

ASC -> Ascending order by default
DESC -> Descending order

syntax:
=======
select col-name
from table-name
order by col-name;

mysql> CREATE TABLE STUDENTS (
    ->     StudentID INT AUTO_INCREMENT PRIMARY KEY,
    ->     Name VARCHAR(50),
    ->     Age INT,
    ->     Department VARCHAR(30),
    ->     Marks INT,
    ->     City VARCHAR(30)
    -> );
Query OK, 0 rows affected (0.07 sec)

mysql> INSERT INTO STUDENTS (Name, Age, Department, Marks, City) VALUES
    -> ('Anil', 20, 'CSE', 85, 'Hyderabad'),
    -> ('Sneha', 22, 'ECE', 75, 'Mumbai'),
    -> ('Ravi', 20, 'CSE', NULL, 'Hyderabad'),
    -> ('Divya', 23, 'MECH', 65, NULL),
    -> ('Kiran', 22, 'ECE', 75, 'Pune'),
    -> ('Varun', 21, 'CSE', 92, 'Chennai'),
    -> ('Priya', 20, 'EEE', 88, 'Delhi'),
    -> ('John', 22, 'MECH', 55, 'Mumbai'),
    -> ('Rekha', 21, 'ECE', 75, 'Pune'),
    -> ('Ramesh', 23, 'EEE', NULL, 'Delhi');
Query OK, 10 rows affected (0.01 sec)
Records: 10  Duplicates: 0  Warnings: 0

mysql> select*from students;
+-----------+--------+------+------------+-------+-----------+
| StudentID | Name   | Age  | Department | Marks | City      |
+-----------+--------+------+------------+-------+-----------+
|         1 | Anil   |   20 | CSE        |    85 | Hyderabad |
|         2 | Sneha  |   22 | ECE        |    75 | Mumbai    |
|         3 | Ravi   |   20 | CSE        |  NULL | Hyderabad |
|         4 | Divya  |   23 | MECH       |    65 | NULL      |
|         5 | Kiran  |   22 | ECE        |    75 | Pune      |
|         6 | Varun  |   21 | CSE        |    92 | Chennai   |
|         7 | Priya  |   20 | EEE        |    88 | Delhi     |
|         8 | John   |   22 | MECH       |    55 | Mumbai    |
|         9 | Rekha  |   21 | ECE        |    75 | Pune      |
|        10 | Ramesh |   23 | EEE        |  NULL | Delhi     |
+-----------+--------+------+------------+-------+-----------+
10 rows in set (0.00 sec)

mysql> select * from students where department = 'cse';
+-----------+-------+------+------------+-------+-----------+
| StudentID | Name  | Age  | Department | Marks | City      |
+-----------+-------+------+------------+-------+-----------+
|         1 | Anil  |   20 | CSE        |    85 | Hyderabad |
|         3 | Ravi  |   20 | CSE        |  NULL | Hyderabad |
|         6 | Varun |   21 | CSE        |    92 | Chennai   |
+-----------+-------+------+------------+-------+-----------+
3 rows in set (0.00 sec)

mysql> select * from students where marks>80;
+-----------+-------+------+------------+-------+-----------+
| StudentID | Name  | Age  | Department | Marks | City      |
+-----------+-------+------+------------+-------+-----------+
|         1 | Anil  |   20 | CSE        |    85 | Hyderabad |
|         6 | Varun |   21 | CSE        |    92 | Chennai   |
|         7 | Priya |   20 | EEE        |    88 | Delhi     |
+-----------+-------+------+------------+-------+-----------+
3 rows in set (0.00 sec)

mysql> select * from students where age = 22;
+-----------+-------+------+------------+-------+--------+
| StudentID | Name  | Age  | Department | Marks | City   |
+-----------+-------+------+------------+-------+--------+
|         2 | Sneha |   22 | ECE        |    75 | Mumbai |
|         5 | Kiran |   22 | ECE        |    75 | Pune   |
|         8 | John  |   22 | MECH       |    55 | Mumbai |
+-----------+-------+------+------------+-------+--------+
3 rows in set (0.00 sec)

mysql> select * from students where marks between 70 and 90;
+-----------+-------+------+------------+-------+-----------+
| StudentID | Name  | Age  | Department | Marks | City      |
+-----------+-------+------+------------+-------+-----------+
|         1 | Anil  |   20 | CSE        |    85 | Hyderabad |
|         2 | Sneha |   22 | ECE        |    75 | Mumbai    |
|         5 | Kiran |   22 | ECE        |    75 | Pune      |
|         7 | Priya |   20 | EEE        |    88 | Delhi     |
|         9 | Rekha |   21 | ECE        |    75 | Pune      |
+-----------+-------+------+------------+-------+-----------+
5 rows in set (0.00 sec)

mysql> select * from students where department = 'cse' and marks>80;
+-----------+-------+------+------------+-------+-----------+
| StudentID | Name  | Age  | Department | Marks | City      |
+-----------+-------+------+------------+-------+-----------+
|         1 | Anil  |   20 | CSE        |    85 | Hyderabad |
|         6 | Varun |   21 | CSE        |    92 | Chennai   |
+-----------+-------+------+------------+-------+-----------+
2 rows in set (0.00 sec)

mysql> select * from students where department in ('ECE','EEE');
+-----------+--------+------+------------+-------+--------+
| StudentID | Name   | Age  | Department | Marks | City   |
+-----------+--------+------+------------+-------+--------+
|         2 | Sneha  |   22 | ECE        |    75 | Mumbai |
|         5 | Kiran  |   22 | ECE        |    75 | Pune   |
|         7 | Priya  |   20 | EEE        |    88 | Delhi  |
|         9 | Rekha  |   21 | ECE        |    75 | Pune   |
|        10 | Ramesh |   23 | EEE        |  NULL | Delhi  |
+-----------+--------+------+------------+-------+--------+
5 rows in set (0.00 sec)

mysql> select * from students where department='ECE' or department='EEE';
+-----------+--------+------+------------+-------+--------+
| StudentID | Name   | Age  | Department | Marks | City   |
+-----------+--------+------+------------+-------+--------+
|         2 | Sneha  |   22 | ECE        |    75 | Mumbai |
|         5 | Kiran  |   22 | ECE        |    75 | Pune   |
|         7 | Priya  |   20 | EEE        |    88 | Delhi  |
|         9 | Rekha  |   21 | ECE        |    75 | Pune   |
|        10 | Ramesh |   23 | EEE        |  NULL | Delhi  |
+-----------+--------+------+------------+-------+--------+
5 rows in set (0.00 sec)

mysql> select department,count(*) from students group by department;
+------------+----------+
| department | count(*) |
+------------+----------+
| CSE        |        3 |
| ECE        |        3 |
| MECH       |        2 |
| EEE        |        2 |
+------------+----------+
4 rows in set (0.00 sec)

mysql> select department,count(*) as total_students from students group by department;
+------------+----------------+
| department | total_students |
+------------+----------------+
| CSE        |              3 |
| ECE        |              3 |
| MECH       |              2 |
| EEE        |              2 |
+------------+----------------+
4 rows in set (0.00 sec)

mysql> select department,avg(marks) as avg_dep_marks from students group by department;
+------------+---------------+
| department | avg_dep_marks |
+------------+---------------+
| CSE        |       88.5000 |
| ECE        |       75.0000 |
| MECH       |       60.0000 |
| EEE        |       88.0000 |
+------------+---------------+
4 rows in set (0.00 sec)

mysql> select department,max(marks) as max_dep_marks from students group by department;
+------------+---------------+
| department | max_dep_marks |
+------------+---------------+
| CSE        |            92 |
| ECE        |            75 |
| MECH       |            65 |
| EEE        |            88 |
+------------+---------------+
4 rows in set (0.00 sec)

mysql> select department,min(marks) as min_dep_marks from students group by department;
+------------+---------------+
| department | min_dep_marks |
+------------+---------------+
| CSE        |            85 |
| ECE        |            75 |
| MECH       |            55 |
| EEE        |            88 |
+------------+---------------+
4 rows in set (0.00 sec)

mysql> select department,sum(marks) as sum_dep_marks from students group by department;
+------------+---------------+
| department | sum_dep_marks |
+------------+---------------+
| CSE        |           177 |
| ECE        |           225 |
| MECH       |           120 |
| EEE        |            88 |
+------------+---------------+
4 rows in set (0.00 sec)

mysql> select city,count(*) as total_stu_city from students group by city;
+-----------+----------------+
| city      | total_stu_city |
+-----------+----------------+
| Hyderabad |              2 |
| Mumbai    |              2 |
| NULL      |              1 |
| Pune      |              2 |
| Chennai   |              1 |
| Delhi     |              2 |
+-----------+----------------+
6 rows in set (0.00 sec)

mysql> select department,avg(age) as avg_age_dep from students group by department;
+------------+-------------+
| department | avg_age_dep |
+------------+-------------+
| CSE        |     20.3333 |
| ECE        |     21.6667 |
| MECH       |     22.5000 |
| EEE        |     21.5000 |
+------------+-------------+
4 rows in set (0.00 sec)

mysql> select city,sum(marks) as total_stu_city from students group by city;
+-----------+----------------+
| city      | total_stu_city |
+-----------+----------------+
| Hyderabad |             85 |
| Mumbai    |            130 |
| NULL      |             65 |
| Pune      |            150 |
| Chennai   |             92 |
| Delhi     |             88 |
+-----------+----------------+
6 rows in set (0.00 sec)

mysql> select department,count(*) as total_students from students group by department having total_students>2;
+------------+----------------+
| department | total_students |
+------------+----------------+
| CSE        |              3 |
| ECE        |              3 |
+------------+----------------+
2 rows in set (0.00 sec)

mysql> select department,avg(marks) as avg_dep_marks from students group by department having avg_dep_marks>80;
+------------+---------------+
| department | avg_dep_marks |
+------------+---------------+
| CSE        |       88.5000 |
| EEE        |       88.0000 |
+------------+---------------+
2 rows in set (0.00 sec)

mysql> select department,avg(marks) as avg_dep_marks from students group by department having avg_dep_marks>75;
+------------+---------------+
| department | avg_dep_marks |
+------------+---------------+
| CSE        |       88.5000 |
| EEE        |       88.0000 |
+------------+---------------+
2 rows in set (0.00 sec)

mysql> select city,count(*) as total_stu_city from students group by city having total_stu_city>1;
+-----------+----------------+
| city      | total_stu_city |
+-----------+----------------+
| Hyderabad |              2 |
| Mumbai    |              2 |
| Pune      |              2 |
| Delhi     |              2 |
+-----------+----------------+
4 rows in set (0.00 sec)

mysql> select department,sum(marks) as sum_dep_marks from students group by department having sum_dep_marks>150;
+------------+---------------+
| department | sum_dep_marks |
+------------+---------------+
| CSE        |           177 |
| ECE        |           225 |
+------------+---------------+
2 rows in set (0.00 sec)

mysql> select age,count(*) as count_age from students group by age having count_age>2;
+------+-----------+
| age  | count_age |
+------+-----------+
|   20 |         3 |
|   22 |         3 |
+------+-----------+
2 rows in set (0.00 sec)

mysql> select city,avg(marks) as avg_marks from students group by city having avg_marks >70;
+-----------+-----------+
| city      | avg_marks |
+-----------+-----------+
| Hyderabad |   85.0000 |
| Pune      |   75.0000 |
| Chennai   |   92.0000 |
| Delhi     |   88.0000 |
+-----------+-----------+
4 rows in set (0.00 sec)

mysql> select department,min(marks) as min_marks from students group by department having min_marks >90;
Empty set (0.00 sec)

mysql> select department,max(marks) as max_marks from students group by department having max_marks >90;
+------------+-----------+
| department | max_marks |
+------------+-----------+
| CSE        |        92 |
+------------+-----------+
1 row in set (0.00 sec)

mysql> select department,min(marks) as min_marks from students group by department having min_marks <60;
+------------+-----------+
| department | min_marks |
+------------+-----------+
| MECH       |        55 |
+------------+-----------+
1 row in set (0.00 sec)

mysql> select city,sum(marks) as total_marks from students group by city having total_marks >100;
+--------+-------------+
| city   | total_marks |
+--------+-------------+
| Mumbai |         130 |
| Pune   |         150 |
+--------+-------------+
2 rows in set (0.00 sec)

mysql> select * from students;
+-----------+--------+------+------------+-------+-----------+
| StudentID | Name   | Age  | Department | Marks | City      |
+-----------+--------+------+------------+-------+-----------+
|         1 | Anil   |   20 | CSE        |    85 | Hyderabad |
|         2 | Sneha  |   22 | ECE        |    75 | Mumbai    |
|         3 | Ravi   |   20 | CSE        |  NULL | Hyderabad |
|         4 | Divya  |   23 | MECH       |    65 | NULL      |
|         5 | Kiran  |   22 | ECE        |    75 | Pune      |
|         6 | Varun  |   21 | CSE        |    92 | Chennai   |
|         7 | Priya  |   20 | EEE        |    88 | Delhi     |
|         8 | John   |   22 | MECH       |    55 | Mumbai    |
|         9 | Rekha  |   21 | ECE        |    75 | Pune      |
|        10 | Ramesh |   23 | EEE        |  NULL | Delhi     |
+-----------+--------+------+------------+-------+-----------+
10 rows in set (0.00 sec)

mysql> select * from students order by name;
+-----------+--------+------+------------+-------+-----------+
| StudentID | Name   | Age  | Department | Marks | City      |
+-----------+--------+------+------------+-------+-----------+
|         1 | Anil   |   20 | CSE        |    85 | Hyderabad |
|         4 | Divya  |   23 | MECH       |    65 | NULL      |
|         8 | John   |   22 | MECH       |    55 | Mumbai    |
|         5 | Kiran  |   22 | ECE        |    75 | Pune      |
|         7 | Priya  |   20 | EEE        |    88 | Delhi     |
|        10 | Ramesh |   23 | EEE        |  NULL | Delhi     |
|         3 | Ravi   |   20 | CSE        |  NULL | Hyderabad |
|         9 | Rekha  |   21 | ECE        |    75 | Pune      |
|         2 | Sneha  |   22 | ECE        |    75 | Mumbai    |
|         6 | Varun  |   21 | CSE        |    92 | Chennai   |
+-----------+--------+------+------------+-------+-----------+
10 rows in set (0.00 sec)

mysql> select * from students order by name asc;
+-----------+--------+------+------------+-------+-----------+
| StudentID | Name   | Age  | Department | Marks | City      |
+-----------+--------+------+------------+-------+-----------+
|         1 | Anil   |   20 | CSE        |    85 | Hyderabad |
|         4 | Divya  |   23 | MECH       |    65 | NULL      |
|         8 | John   |   22 | MECH       |    55 | Mumbai    |
|         5 | Kiran  |   22 | ECE        |    75 | Pune      |
|         7 | Priya  |   20 | EEE        |    88 | Delhi     |
|        10 | Ramesh |   23 | EEE        |  NULL | Delhi     |
|         3 | Ravi   |   20 | CSE        |  NULL | Hyderabad |
|         9 | Rekha  |   21 | ECE        |    75 | Pune      |
|         2 | Sneha  |   22 | ECE        |    75 | Mumbai    |
|         6 | Varun  |   21 | CSE        |    92 | Chennai   |
+-----------+--------+------+------------+-------+-----------+
10 rows in set (0.00 sec)

mysql> select * from students order by name desc;
+-----------+--------+------+------------+-------+-----------+
| StudentID | Name   | Age  | Department | Marks | City      |
+-----------+--------+------+------------+-------+-----------+
|         6 | Varun  |   21 | CSE        |    92 | Chennai   |
|         2 | Sneha  |   22 | ECE        |    75 | Mumbai    |
|         9 | Rekha  |   21 | ECE        |    75 | Pune      |
|         3 | Ravi   |   20 | CSE        |  NULL | Hyderabad |
|        10 | Ramesh |   23 | EEE        |  NULL | Delhi     |
|         7 | Priya  |   20 | EEE        |    88 | Delhi     |
|         5 | Kiran  |   22 | ECE        |    75 | Pune      |
|         8 | John   |   22 | MECH       |    55 | Mumbai    |
|         4 | Divya  |   23 | MECH       |    65 | NULL      |
|         1 | Anil   |   20 | CSE        |    85 | Hyderabad |
+-----------+--------+------+------------+-------+-----------+
10 rows in set (0.00 sec)

mysql> select * from students order by marks desc;
+-----------+--------+------+------------+-------+-----------+
| StudentID | Name   | Age  | Department | Marks | City      |
+-----------+--------+------+------------+-------+-----------+
|         6 | Varun  |   21 | CSE        |    92 | Chennai   |
|         7 | Priya  |   20 | EEE        |    88 | Delhi     |
|         1 | Anil   |   20 | CSE        |    85 | Hyderabad |
|         2 | Sneha  |   22 | ECE        |    75 | Mumbai    |
|         5 | Kiran  |   22 | ECE        |    75 | Pune      |
|         9 | Rekha  |   21 | ECE        |    75 | Pune      |
|         4 | Divya  |   23 | MECH       |    65 | NULL      |
|         8 | John   |   22 | MECH       |    55 | Mumbai    |
|         3 | Ravi   |   20 | CSE        |  NULL | Hyderabad |
|        10 | Ramesh |   23 | EEE        |  NULL | Delhi     |
+-----------+--------+------+------------+-------+-----------+
10 rows in set (0.00 sec)

mysql> select * from students order by marks;
+-----------+--------+------+------------+-------+-----------+
| StudentID | Name   | Age  | Department | Marks | City      |
+-----------+--------+------+------------+-------+-----------+
|         3 | Ravi   |   20 | CSE        |  NULL | Hyderabad |
|        10 | Ramesh |   23 | EEE        |  NULL | Delhi     |
|         8 | John   |   22 | MECH       |    55 | Mumbai    |
|         4 | Divya  |   23 | MECH       |    65 | NULL      |
|         2 | Sneha  |   22 | ECE        |    75 | Mumbai    |
|         5 | Kiran  |   22 | ECE        |    75 | Pune      |
|         9 | Rekha  |   21 | ECE        |    75 | Pune      |
|         1 | Anil   |   20 | CSE        |    85 | Hyderabad |
|         7 | Priya  |   20 | EEE        |    88 | Delhi     |
|         6 | Varun  |   21 | CSE        |    92 | Chennai   |
+-----------+--------+------+------------+-------+-----------+
10 rows in set (0.00 sec)

mysql> select * from students order by city;
+-----------+--------+------+------------+-------+-----------+
| StudentID | Name   | Age  | Department | Marks | City      |
+-----------+--------+------+------------+-------+-----------+
|         4 | Divya  |   23 | MECH       |    65 | NULL      |
|         6 | Varun  |   21 | CSE        |    92 | Chennai   |
|         7 | Priya  |   20 | EEE        |    88 | Delhi     |
|        10 | Ramesh |   23 | EEE        |  NULL | Delhi     |
|         1 | Anil   |   20 | CSE        |    85 | Hyderabad |
|         3 | Ravi   |   20 | CSE        |  NULL | Hyderabad |
|         2 | Sneha  |   22 | ECE        |    75 | Mumbai    |
|         8 | John   |   22 | MECH       |    55 | Mumbai    |
|         5 | Kiran  |   22 | ECE        |    75 | Pune      |
|         9 | Rekha  |   21 | ECE        |    75 | Pune      |
+-----------+--------+------+------------+-------+-----------+
10 rows in set (0.00 sec)

mysql> select * from students order by city desc;
+-----------+--------+------+------------+-------+-----------+
| StudentID | Name   | Age  | Department | Marks | City      |
+-----------+--------+------+------------+-------+-----------+
|         5 | Kiran  |   22 | ECE        |    75 | Pune      |
|         9 | Rekha  |   21 | ECE        |    75 | Pune      |
|         2 | Sneha  |   22 | ECE        |    75 | Mumbai    |
|         8 | John   |   22 | MECH       |    55 | Mumbai    |
|         1 | Anil   |   20 | CSE        |    85 | Hyderabad |
|         3 | Ravi   |   20 | CSE        |  NULL | Hyderabad |
|         7 | Priya  |   20 | EEE        |    88 | Delhi     |
|        10 | Ramesh |   23 | EEE        |  NULL | Delhi     |
|         6 | Varun  |   21 | CSE        |    92 | Chennai   |
|         4 | Divya  |   23 | MECH       |    65 | NULL      |
+-----------+--------+------+------------+-------+-----------+
10 rows in set (0.00 sec)

mysql> select * from students order by age;
+-----------+--------+------+------------+-------+-----------+
| StudentID | Name   | Age  | Department | Marks | City      |
+-----------+--------+------+------------+-------+-----------+
|         1 | Anil   |   20 | CSE        |    85 | Hyderabad |
|         3 | Ravi   |   20 | CSE        |  NULL | Hyderabad |
|         7 | Priya  |   20 | EEE        |    88 | Delhi     |
|         6 | Varun  |   21 | CSE        |    92 | Chennai   |
|         9 | Rekha  |   21 | ECE        |    75 | Pune      |
|         2 | Sneha  |   22 | ECE        |    75 | Mumbai    |
|         5 | Kiran  |   22 | ECE        |    75 | Pune      |
|         8 | John   |   22 | MECH       |    55 | Mumbai    |
|         4 | Divya  |   23 | MECH       |    65 | NULL      |
|        10 | Ramesh |   23 | EEE        |  NULL | Delhi     |
+-----------+--------+------+------------+-------+-----------+
10 rows in set (0.00 sec)

mysql> select * from students order by age desc;
+-----------+--------+------+------------+-------+-----------+
| StudentID | Name   | Age  | Department | Marks | City      |
+-----------+--------+------+------------+-------+-----------+
|         4 | Divya  |   23 | MECH       |    65 | NULL      |
|        10 | Ramesh |   23 | EEE        |  NULL | Delhi     |
|         2 | Sneha  |   22 | ECE        |    75 | Mumbai    |
|         5 | Kiran  |   22 | ECE        |    75 | Pune      |
|         8 | John   |   22 | MECH       |    55 | Mumbai    |
|         6 | Varun  |   21 | CSE        |    92 | Chennai   |
|         9 | Rekha  |   21 | ECE        |    75 | Pune      |
|         1 | Anil   |   20 | CSE        |    85 | Hyderabad |
|         3 | Ravi   |   20 | CSE        |  NULL | Hyderabad |
|         7 | Priya  |   20 | EEE        |    88 | Delhi     |
+-----------+--------+------+------------+-------+-----------+
10 rows in set (0.00 sec)

mysql> select * from students order by department desc;
+-----------+--------+------+------------+-------+-----------+
| StudentID | Name   | Age  | Department | Marks | City      |
+-----------+--------+------+------------+-------+-----------+
|         4 | Divya  |   23 | MECH       |    65 | NULL      |
|         8 | John   |   22 | MECH       |    55 | Mumbai    |
|         7 | Priya  |   20 | EEE        |    88 | Delhi     |
|        10 | Ramesh |   23 | EEE        |  NULL | Delhi     |
|         2 | Sneha  |   22 | ECE        |    75 | Mumbai    |
|         5 | Kiran  |   22 | ECE        |    75 | Pune      |
|         9 | Rekha  |   21 | ECE        |    75 | Pune      |
|         1 | Anil   |   20 | CSE        |    85 | Hyderabad |
|         3 | Ravi   |   20 | CSE        |  NULL | Hyderabad |
|         6 | Varun  |   21 | CSE        |    92 | Chennai   |
+-----------+--------+------+------------+-------+-----------+
10 rows in set (0.00 sec)

mysql> select * from students limit 5;
+-----------+-------+------+------------+-------+-----------+
| StudentID | Name  | Age  | Department | Marks | City      |
+-----------+-------+------+------------+-------+-----------+
|         1 | Anil  |   20 | CSE        |    85 | Hyderabad |
|         2 | Sneha |   22 | ECE        |    75 | Mumbai    |
|         3 | Ravi  |   20 | CSE        |  NULL | Hyderabad |
|         4 | Divya |   23 | MECH       |    65 | NULL      |
|         5 | Kiran |   22 | ECE        |    75 | Pune      |
+-----------+-------+------+------------+-------+-----------+
5 rows in set (0.00 sec)

mysql> select * from students order by marks desc limit 1;
+-----------+-------+------+------------+-------+---------+
| StudentID | Name  | Age  | Department | Marks | City    |
+-----------+-------+------+------------+-------+---------+
|         6 | Varun |   21 | CSE        |    92 | Chennai |
+-----------+-------+------+------------+-------+---------+
1 row in set (0.00 sec)

mysql> select * from students order by marks asc limit 1;
+-----------+------+------+------------+-------+-----------+
| StudentID | Name | Age  | Department | Marks | City      |
+-----------+------+------+------------+-------+-----------+
|         3 | Ravi |   20 | CSE        |  NULL | Hyderabad |
+-----------+------+------+------------+-------+-----------+
1 row in set (0.00 sec)

mysql> select department,avg(marks) as avg_marks from students where age>20 group by department having avg_marks>70 order by avg(marks) desc; 
+------------+-----------+
| department | avg_marks |
+------------+-----------+
| CSE        |   92.0000 |
| ECE        |   75.0000 |
+------------+-----------+
2 rows in set (0.00 sec)

mysql> select department,avg(marks) as avg_marks from students where age>20 group by department having avg_marks>70 order by avg(marks) desc limit 1; 
+------------+-----------+
| department | avg_marks |
+------------+-----------+
| CSE        |   92.0000 |
+------------+-----------+
1 row in set (0.00 sec)

mysql> select city,count(*) as count_city from students
    -> where marks>70
    -> group by city
    -> having count_city>1
    -> order by count_city;
+------+------------+
| city | count_city |
+------+------------+
| Pune |          2 |
+------+------------+
1 row in set (0.00 sec)
