mysql> UPDATE FROM PRODUCTS SET ID=4 WHERE QTY=(QTY*2);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'FROM PRODUCTS SET ID=4 WHERE QTY=(QTY*2)' at line 1
mysql> UPDATE FROM PRODUCTS QTY=(QTY*2) WHERE ID=4;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'FROM PRODUCTS QTY=(QTY*2) WHERE ID=4' at line 1
mysql> UPDATE PRODUCTS SET QTY=QTY+2;
Query OK, 10 rows affected (0.01 sec)
Rows matched: 10  Changed: 10  Warnings: 0

mysql> SELECT*FROM PRODUCTS;
+------+--------------+--------+------+
| id   | name         | price  | qty  |
+------+--------------+--------+------+
|    1 | Pen          |  10.00 |  102 |
|    2 | Notebook     |  25.00 |   52 |
|    3 | Pencil       |   5.00 |  202 |
|    4 | Eraser       |   3.00 |  302 |
|    5 | Marker       |  15.00 |   82 |
|    6 | Scale        |  20.00 |  152 |
|    7 | Sharpener    |   8.00 |  122 |
|    8 | Geometry Box | 120.00 |   42 |
|    9 | Sketch Pen   |  60.00 |   77 |
|   10 | Crayons      |  90.00 |   57 |
+------+--------------+--------+------+
10 rows in set (0.00 sec)

mysql> UPDATE PRODUCTS SET PRICE=PRICE-5;
Query OK, 10 rows affected (0.01 sec)
Rows matched: 10  Changed: 10  Warnings: 0

mysql> UPDATE PRODUCTS SET QTY=QTY*2 WHERE ID=4;
Query OK, 1 row affected (0.01 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql> SELECT*FROM PRODUCTS;
+------+--------------+--------+------+
| id   | name         | price  | qty  |
+------+--------------+--------+------+
|    1 | Pen          |   5.00 |  102 |
|    2 | Notebook     |  20.00 |   52 |
|    3 | Pencil       |   0.00 |  202 |
|    4 | Eraser       |  -2.00 |  604 |
|    5 | Marker       |  10.00 |   82 |
|    6 | Scale        |  15.00 |  152 |
|    7 | Sharpener    |   3.00 |  122 |
|    8 | Geometry Box | 115.00 |   42 |
|    9 | Sketch Pen   |  55.00 |   77 |
|   10 | Crayons      |  85.00 |   57 |
+------+--------------+--------+------+
10 rows in set (0.00 sec)

mysql> UPDATE PRODUCTS SET QTY=QTY/2 WHERE ID=5;
Query OK, 1 row affected (0.00 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql> SELECT*FROM PRODUCTS;
+------+--------------+--------+------+
| id   | name         | price  | qty  |
+------+--------------+--------+------+
|    1 | Pen          |   5.00 |  102 |
|    2 | Notebook     |  20.00 |   52 |
|    3 | Pencil       |   0.00 |  202 |
|    4 | Eraser       |  -2.00 |  604 |
|    5 | Marker       |  10.00 |   41 |
|    6 | Scale        |  15.00 |  152 |
|    7 | Sharpener    |   3.00 |  122 |
|    8 | Geometry Box | 115.00 |   42 |
|    9 | Sketch Pen   |  55.00 |   77 |
|   10 | Crayons      |  85.00 |   57 |
+------+--------------+--------+------+
10 rows in set (0.00 sec)

mysql> DELETE FROM PRODUCTS WHERE QTY<100;
Query OK, 5 rows affected (0.01 sec)

mysql> SELECT*FROM PRODUCTS;
+------+-----------+-------+------+
| id   | name      | price | qty  |
+------+-----------+-------+------+
|    1 | Pen       |  5.00 |  102 |
|    3 | Pencil    |  0.00 |  202 |
|    4 | Eraser    | -2.00 |  604 |
|    6 | Scale     | 15.00 |  152 |
|    7 | Sharpener |  3.00 |  122 |
+------+-----------+-------+------+
5 rows in set (0.00 sec)

mysql> CREATE TABLE StudentScores (
    ->  id INT,
    ->  name VARCHAR(100),
    ->  subject VARCHAR(50),
    ->  marks INT
    ->  );
Query OK, 0 rows affected (0.05 sec)

mysql> 
mysql> -- STEP 2: Insert Records
mysql> INSERT INTO StudentScores VALUES
    ->  (1, 'Alice', 'Math', 95),
    ->  (2, 'Bob', 'Math', 76),
    ->  (3, 'Charlie', 'Math', 59),
    ->  (4, 'Diana', 'Math', 88),
    ->  (5, 'Eve', 'Math', 40),
    ->  (6, 'Frank', 'Math', 95),
    ->  (7, 'Grace', 'Science', 67),
    ->  (8, 'Henry', 'Science', 82),
    ->  (9, 'Ivy', 'English', 91),
    ->  (10, 'Jack', 'English', 55),
    ->  (11, 'Kevin', 'Math', 73),
    ->  (12, 'Lily', 'Science', 48),
    ->  (13, 'Mia', 'English', 100),
    ->  (14, 'Noah', 'Math', 64),
    ->  (15, 'Olivia', 'Science', 79);
Query OK, 15 rows affected (0.01 sec)
Records: 15  Duplicates: 0  Warnings: 0

mysql> SELECT * FROM STUDENTSCORES
    -> ;
+------+---------+---------+-------+
| id   | name    | subject | marks |
+------+---------+---------+-------+
|    1 | Alice   | Math    |    95 |
|    2 | Bob     | Math    |    76 |
|    3 | Charlie | Math    |    59 |
|    4 | Diana   | Math    |    88 |
|    5 | Eve     | Math    |    40 |
|    6 | Frank   | Math    |    95 |
|    7 | Grace   | Science |    67 |
|    8 | Henry   | Science |    82 |
|    9 | Ivy     | English |    91 |
|   10 | Jack    | English |    55 |
|   11 | Kevin   | Math    |    73 |
|   12 | Lily    | Science |    48 |
|   13 | Mia     | English |   100 |
|   14 | Noah    | Math    |    64 |
|   15 | Olivia  | Science |    79 |
+------+---------+---------+-------+
15 rows in set (0.00 sec)

mysql> SELECT * FROM STUDENTSCORES WHERE MARKS>80; 
+------+-------+---------+-------+
| id   | name  | subject | marks |
+------+-------+---------+-------+
|    1 | Alice | Math    |    95 |
|    4 | Diana | Math    |    88 |
|    6 | Frank | Math    |    95 |
|    8 | Henry | Science |    82 |
|    9 | Ivy   | English |    91 |
|   13 | Mia   | English |   100 |
+------+-------+---------+-------+
6 rows in set (0.01 sec)

mysql> SELECT * FROM STUDENTSCORES WHERE MARKS>=60; 
+------+--------+---------+-------+
| id   | name   | subject | marks |
+------+--------+---------+-------+
|    1 | Alice  | Math    |    95 |
|    2 | Bob    | Math    |    76 |
|    4 | Diana  | Math    |    88 |
|    6 | Frank  | Math    |    95 |
|    7 | Grace  | Science |    67 |
|    8 | Henry  | Science |    82 |
|    9 | Ivy    | English |    91 |
|   11 | Kevin  | Math    |    73 |
|   13 | Mia    | English |   100 |
|   14 | Noah   | Math    |    64 |
|   15 | Olivia | Science |    79 |
+------+--------+---------+-------+
11 rows in set (0.00 sec)

mysql> SELECT * FROM STUDENTSCORES WHERE MARKS<50; 
+------+------+---------+-------+
| id   | name | subject | marks |
+------+------+---------+-------+
|    5 | Eve  | Math    |    40 |
|   12 | Lily | Science |    48 |
+------+------+---------+-------+
2 rows in set (0.00 sec)

mysql> SELECT * FROM STUDENTSCORES WHERE MARKS=95; 
+------+-------+---------+-------+
| id   | name  | subject | marks |
+------+-------+---------+-------+
|    1 | Alice | Math    |    95 |
|    6 | Frank | Math    |    95 |
+------+-------+---------+-------+
2 rows in set (0.00 sec)

mysql> SELECT * FROM STUDENTSCORES WHERE MARKS!=95; 
+------+---------+---------+-------+
| id   | name    | subject | marks |
+------+---------+---------+-------+
|    2 | Bob     | Math    |    76 |
|    3 | Charlie | Math    |    59 |
|    4 | Diana   | Math    |    88 |
|    5 | Eve     | Math    |    40 |
|    7 | Grace   | Science |    67 |
|    8 | Henry   | Science |    82 |
|    9 | Ivy     | English |    91 |
|   10 | Jack    | English |    55 |
|   11 | Kevin   | Math    |    73 |
|   12 | Lily    | Science |    48 |
|   13 | Mia     | English |   100 |
|   14 | Noah    | Math    |    64 |
|   15 | Olivia  | Science |    79 |
+------+---------+---------+-------+
13 rows in set (0.00 sec)

mysql> SELECT * FROM STUDENTSCORES WHERE MARKS<=60; 
+------+---------+---------+-------+
| id   | name    | subject | marks |
+------+---------+---------+-------+
|    3 | Charlie | Math    |    59 |
|    5 | Eve     | Math    |    40 |
|   10 | Jack    | English |    55 |
|   12 | Lily    | Science |    48 |
+------+---------+---------+-------+
4 rows in set (0.01 sec)

mysql> UPDATE STUDENTSCORES SET MARKS=MARKS+10 WHERE MARKS<50; 
Query OK, 2 rows affected (0.01 sec)
Rows matched: 2  Changed: 2  Warnings: 0

mysql> UPDATE STUDENTSCORES SET MARKS=MARKS+5 WHERE MARKS<=60; 
Query OK, 4 rows affected (0.01 sec)
Rows matched: 4  Changed: 4  Warnings: 0

mysql> UPDATE STUDENTSCORES SET MARKS=MARKS+2 WHERE MARKS>90; 
Query OK, 4 rows affected (0.01 sec)
Rows matched: 4  Changed: 4  Warnings: 0

mysql> UPDATE STUDENTSCORES SET MARKS=MARKS+3 WHERE MARKS>=80; 
Query OK, 6 rows affected (0.01 sec)
Rows matched: 6  Changed: 6  Warnings: 0

mysql> UPDATE STUDENTSCORES SET MARKS=MARKS-1 WHERE MARK!=95; 
ERROR 1054 (42S22): Unknown column 'MARK' in 'where clause'
mysql> UPDATE STUDENTSCORES SET MARKS=MARKS-1 WHERE MARKS!=95; 
Query OK, 15 rows affected (0.01 sec)
Rows matched: 15  Changed: 15  Warnings: 0

mysql> UPDATE STUDENTSCORES SET MARKS=100 WHERE MARKS=95; 
Query OK, 1 row affected (0.01 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql> SELECT * FROM STUDENTSCORES;
+------+---------+---------+-------+
| id   | name    | subject | marks |
+------+---------+---------+-------+
|    1 | Alice   | Math    |    99 |
|    2 | Bob     | Math    |    75 |
|    3 | Charlie | Math    |    63 |
|    4 | Diana   | Math    |    90 |
|    5 | Eve     | Math    |    54 |
|    6 | Frank   | Math    |    99 |
|    7 | Grace   | Science |    66 |
|    8 | Henry   | Science |    84 |
|    9 | Ivy     | English |   100 |
|   10 | Jack    | English |    59 |
|   11 | Kevin   | Math    |    72 |
|   12 | Lily    | Science |    62 |
|   13 | Mia     | English |   104 |
|   14 | Noah    | Math    |    63 |
|   15 | Olivia  | Science |    78 |
+------+---------+---------+-------+
15 rows in set (0.00 sec)

mysql> DELETE FROM STUDENTSCORES WHERE MARKS<50;
Query OK, 0 rows affected (0.01 sec)

mysql> DELETE FROM STUDENTSCORES WHERE MARKS<=60;
Query OK, 2 rows affected (0.01 sec)

mysql> DELETE FROM STUDENTSCORES WHERE MARKS>90;
Query OK, 4 rows affected (0.01 sec)

mysql> DELETE FROM STUDENTSCORES WHERE MARKS>=80;
Query OK, 2 rows affected (0.00 sec)

mysql> DELETE FROM STUDENTSCORES WHERE MARKS!=95;
Query OK, 7 rows affected (0.01 sec)

mysql> DELETE FROM STUDENTSCORES WHERE MARKS=76;
Query OK, 0 rows affected (0.00 sec)

mysql> SELECT * FROM STUDENTSCORES;
Empty set (0.00 sec)

mysql> SHOW TABLES;
+-----------------+
| Tables_in_pfs4  |
+-----------------+
| backupemployees |
| company_staff   |
| employee        |
| employees       |
| product         |
| products        |
| students        |
| studentscores   |
+-----------------+
8 rows in set (0.02 sec)

mysql> DROP TABLE EMPLOYEES;
Query OK, 0 rows affected (0.04 sec)

mysql> CREATE TABLE Employees (
    ->  id INT,
    ->  name VARCHAR(100),
    ->  department VARCHAR(100),
    ->  salary INT,
    ->  isactive BOOLEAN
    ->  );
Query OK, 0 rows affected (0.02 sec)

mysql> 
mysql>  -- STEP 2: Insert Records
mysql> INSERT INTO Employees VALUES
    ->  (1, 'Rahul Sharma', 'IT', 50000, TRUE),
    ->  (2, 'Priya Reddy', 'HR', 30000, TRUE),
    ->  (3, 'Amit Kumar', 'Finance', 45000, FALSE),
    ->  (4, 'Sneha Patel', 'IT', 35000, TRUE),
    ->  (5, 'Vikram Singh', 'Finance', 28000, TRUE),
    ->  (6, 'Anjali Mehta', 'HR', 32000, FALSE),
    ->  (7, 'Kiran Rao', 'IT', 60000, TRUE),
    ->  (8, 'Pooja Verma', 'Marketing', 27000, TRUE),
    ->  (9, 'Ramesh Naidu', 'Sales', 38000, TRUE),
    ->  (10, 'Deepika Joshi', 'Finance', 52000, TRUE),
    ->  (11, 'Suresh Babu', 'Marketing', 29000, FALSE),
    ->  (12, 'Neha Kapoor', 'HR', 41000, TRUE),
    ->  (13, 'Arjun Reddy', 'IT', 55000, FALSE),
    ->  (14, 'Lakshmi Devi', 'Sales', 33000, TRUE),
    ->  (15, 'Nikhil Jain', 'IT', 47000, TRUE);
Query OK, 15 rows affected (0.01 sec)
Records: 15  Duplicates: 0  Warnings: 0

mysql> SELECT*FROM EMPLOYEES
    -> ;
+------+---------------+------------+--------+----------+
| id   | name          | department | salary | isactive |
+------+---------------+------------+--------+----------+
|    1 | Rahul Sharma  | IT         |  50000 |        1 |
|    2 | Priya Reddy   | HR         |  30000 |        1 |
|    3 | Amit Kumar    | Finance    |  45000 |        0 |
|    4 | Sneha Patel   | IT         |  35000 |        1 |
|    5 | Vikram Singh  | Finance    |  28000 |        1 |
|    6 | Anjali Mehta  | HR         |  32000 |        0 |
|    7 | Kiran Rao     | IT         |  60000 |        1 |
|    8 | Pooja Verma   | Marketing  |  27000 |        1 |
|    9 | Ramesh Naidu  | Sales      |  38000 |        1 |
|   10 | Deepika Joshi | Finance    |  52000 |        1 |
|   11 | Suresh Babu   | Marketing  |  29000 |        0 |
|   12 | Neha Kapoor   | HR         |  41000 |        1 |
|   13 | Arjun Reddy   | IT         |  55000 |        0 |
|   14 | Lakshmi Devi  | Sales      |  33000 |        1 |
|   15 | Nikhil Jain   | IT         |  47000 |        1 |
+------+---------------+------------+--------+----------+
15 rows in set (0.00 sec)

mysql> SELECT*FROMEMPLOYES;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'FROMEMPLOYES' at line 1
mysql> SELECT*FROM EMPLOYEES WHERE DEPARTMENT='IT' AND SALARY>40000;
+------+--------------+------------+--------+----------+
| id   | name         | department | salary | isactive |
+------+--------------+------------+--------+----------+
|    1 | Rahul Sharma | IT         |  50000 |        1 |
|    7 | Kiran Rao    | IT         |  60000 |        1 |
|   13 | Arjun Reddy  | IT         |  55000 |        0 |
|   15 | Nikhil Jain  | IT         |  47000 |        1 |
+------+--------------+------------+--------+----------+
4 rows in set (0.01 sec)

mysql> SELECT*FROM EMPLOYEES WHERE DEPARTMENT='HR' OR SALARY<35000;
+------+--------------+------------+--------+----------+
| id   | name         | department | salary | isactive |
+------+--------------+------------+--------+----------+
|    2 | Priya Reddy  | HR         |  30000 |        1 |
|    5 | Vikram Singh | Finance    |  28000 |        1 |
|    6 | Anjali Mehta | HR         |  32000 |        0 |
|    8 | Pooja Verma  | Marketing  |  27000 |        1 |
|   11 | Suresh Babu  | Marketing  |  29000 |        0 |
|   12 | Neha Kapoor  | HR         |  41000 |        1 |
|   14 | Lakshmi Devi | Sales      |  33000 |        1 |
+------+--------------+------------+--------+----------+
7 rows in set (0.00 sec)

mysql> SELECT*FROM EMPLOYEES WHERE NOT(DEPARTMENT='HR');
+------+---------------+------------+--------+----------+
| id   | name          | department | salary | isactive |
+------+---------------+------------+--------+----------+
|    1 | Rahul Sharma  | IT         |  50000 |        1 |
|    3 | Amit Kumar    | Finance    |  45000 |        0 |
|    4 | Sneha Patel   | IT         |  35000 |        1 |
|    5 | Vikram Singh  | Finance    |  28000 |        1 |
|    7 | Kiran Rao     | IT         |  60000 |        1 |
|    8 | Pooja Verma   | Marketing  |  27000 |        1 |
|    9 | Ramesh Naidu  | Sales      |  38000 |        1 |
|   10 | Deepika Joshi | Finance    |  52000 |        1 |
|   11 | Suresh Babu   | Marketing  |  29000 |        0 |
|   13 | Arjun Reddy   | IT         |  55000 |        0 |
|   14 | Lakshmi Devi  | Sales      |  33000 |        1 |
|   15 | Nikhil Jain   | IT         |  47000 |        1 |
+------+---------------+------------+--------+----------+
12 rows in set (0.00 sec)

mysql> SELECT*FROM EMPLOYEES WHERE DEPARTMENT='FINANCE' OR SALARY>30000 AND ISACTIVE=1;
+------+---------------+------------+--------+----------+
| id   | name          | department | salary | isactive |
+------+---------------+------------+--------+----------+
|    1 | Rahul Sharma  | IT         |  50000 |        1 |
|    3 | Amit Kumar    | Finance    |  45000 |        0 |
|    4 | Sneha Patel   | IT         |  35000 |        1 |
|    5 | Vikram Singh  | Finance    |  28000 |        1 |
|    7 | Kiran Rao     | IT         |  60000 |        1 |
|    9 | Ramesh Naidu  | Sales      |  38000 |        1 |
|   10 | Deepika Joshi | Finance    |  52000 |        1 |
|   12 | Neha Kapoor   | HR         |  41000 |        1 |
|   14 | Lakshmi Devi  | Sales      |  33000 |        1 |
|   15 | Nikhil Jain   | IT         |  47000 |        1 |
+------+---------------+------------+--------+----------+
10 rows in set (0.00 sec)

mysql> UPDATE EMPLOYEES SET SALARY=SALARY+2000 WHERE ISACTIVE=1 AND DEPARTMENT='IT' AND SALARY<60000;
Query OK, 3 rows affected (0.01 sec)
Rows matched: 3  Changed: 3  Warnings: 0

mysql> UPDATE EMPLOYEES SET SALARY=SALARY-(SALARY*0.1) WHERE ISACTIVE=0 OR DEPARTMENT='FINANCE';
Query OK, 6 rows affected (0.01 sec)
Rows matched: 6  Changed: 6  Warnings: 0

mysql> UPDATE EMPLOYEES SET ISACTIVE=0 WHERE NOT(DEPARTMENT='IT')
    -> ;
Query OK, 7 rows affected (0.01 sec)
Rows matched: 10  Changed: 7  Warnings: 0

mysql> SELECT*FROM EMPLOYEES
    -> ;
+------+---------------+------------+--------+----------+
| id   | name          | department | salary | isactive |
+------+---------------+------------+--------+----------+
|    1 | Rahul Sharma  | IT         |  52000 |        1 |
|    2 | Priya Reddy   | HR         |  30000 |        0 |
|    3 | Amit Kumar    | Finance    |  40500 |        0 |
|    4 | Sneha Patel   | IT         |  37000 |        1 |
|    5 | Vikram Singh  | Finance    |  25200 |        0 |
|    6 | Anjali Mehta  | HR         |  28800 |        0 |
|    7 | Kiran Rao     | IT         |  60000 |        1 |
|    8 | Pooja Verma   | Marketing  |  27000 |        0 |
|    9 | Ramesh Naidu  | Sales      |  38000 |        0 |
|   10 | Deepika Joshi | Finance    |  46800 |        0 |
|   11 | Suresh Babu   | Marketing  |  26100 |        0 |
|   12 | Neha Kapoor   | HR         |  41000 |        0 |
|   13 | Arjun Reddy   | IT         |  49500 |        0 |
|   14 | Lakshmi Devi  | Sales      |  33000 |        0 |
|   15 | Nikhil Jain   | IT         |  49000 |        1 |
+------+---------------+------------+--------+----------+
15 rows in set (0.00 sec)

