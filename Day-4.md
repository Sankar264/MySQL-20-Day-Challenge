Day_04_MySQL
=============


mysql> SHOW DATABASES;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| pfs4               |
| sys                |
+--------------------+
5 rows in set (0.00 sec)

mysql> USE PFS4;
Database changed
mysql> SHOW TABLES;
+----------------+
| Tables_in_pfs4 |
+----------------+
| employees      |
| students       |
+----------------+
2 rows in set (0.00 sec)

mysql> DROP TABLE EMPLOYEES;
Query OK, 0 rows affected (0.26 sec)

mysql> DROP TABLE STUDENTS;
Query OK, 0 rows affected (0.02 sec)

mysql> SHOW TABLES;
Empty set (0.00 sec)

mysql> CREATE TABLE EMPLOYEES(
    -> EMPID CHAR(5),
    -> FNAME VARCHAR(100),
    -> LNAME VARCHAR(60),
    -> AGE INT,
    -> DOJ DATE,
    -> ADDRESS TINYTEXT,
    -> DEPT VARCHAR(50)
    -> );
Query OK, 0 rows affected (0.11 sec)

mysql> DESC EMPLOYEES;
+---------+--------------+------+-----+---------+-------+
| Field   | Type         | Null | Key | Default | Extra |
+---------+--------------+------+-----+---------+-------+
| EMPID   | char(5)      | YES  |     | NULL    |       |
| FNAME   | varchar(100) | YES  |     | NULL    |       |
| LNAME   | varchar(60)  | YES  |     | NULL    |       |
| AGE     | int          | YES  |     | NULL    |       |
| DOJ     | date         | YES  |     | NULL    |       |
| ADDRESS | tinytext     | YES  |     | NULL    |       |
| DEPT    | varchar(50)  | YES  |     | NULL    |       |
+---------+--------------+------+-----+---------+-------+
7 rows in set (0.01 sec)

mysql> SHOW TABLES;
+----------------+
| Tables_in_pfs4 |
+----------------+
| employees      |
+----------------+
1 row in set (0.00 sec)

COMMON USES Of Alter Table
============================
1. ADD a column
2. Modify an existing column(type, size, default..etc)
3. drop column
4. rename a column or table
5. add or remove constraints
6. change column order(in some databases)

syntax - Alter Table table-name <modification>;

adding a new column to the existing table
===========================================
syntax - alter table table-name add column-name datatype(size);mysql> -- add a new column named location data type tinytext to the employees table.
mysql> ALTER TABLE EMPLOYEES ADD LOCATION TINYTEXT;
Query OK, 0 rows affected (0.12 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> DESC EMPLOYEES;
+----------+--------------+------+-----+---------+-------+
| Field    | Type         | Null | Key | Default | Extra |
+----------+--------------+------+-----+---------+-------+
| EMPID    | char(5)      | YES  |     | NULL    |       |
| FNAME    | varchar(100) | YES  |     | NULL    |       |
| LNAME    | varchar(60)  | YES  |     | NULL    |       |
| AGE      | int          | YES  |     | NULL    |       |
| DOJ      | date         | YES  |     | NULL    |       |
| ADDRESS  | tinytext     | YES  |     | NULL    |       |
| DEPT     | varchar(50)  | YES  |     | NULL    |       |
| LOCATION | tinytext     | YES  |     | NULL    |       |
+----------+--------------+------+-----+---------+-------+
8 rows in set (0.00 sec)

mysql> -- add a new column after a particular column.
mysql> -- syntax : alter table table-name add column-name datatype(size) after specified column-name.
mysql> ALTER TABLE EMPLOYEES ADD PFID INT AFTER ADDRESS;
Query OK, 0 rows affected (0.10 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> DESC EMPLOYEES;
+----------+--------------+------+-----+---------+-------+
| Field    | Type         | Null | Key | Default | Extra |
+----------+--------------+------+-----+---------+-------+
| EMPID    | char(5)      | YES  |     | NULL    |       |
| FNAME    | varchar(100) | YES  |     | NULL    |       |
| LNAME    | varchar(60)  | YES  |     | NULL    |       |
| AGE      | int          | YES  |     | NULL    |       |
| DOJ      | date         | YES  |     | NULL    |       |
| ADDRESS  | tinytext     | YES  |     | NULL    |       |
| PFID     | int          | YES  |     | NULL    |       |
| DEPT     | varchar(50)  | YES  |     | NULL    |       |
| LOCATION | tinytext     | YES  |     | NULL    |       |
+----------+--------------+------+-----+---------+-------+
9 rows in set (0.00 sec)

mysql> -- MODIFY THE FNAME COLUMN IN EMPLOYEES TABLE TO VARCHAR(50).
mysql> ALTER TABLE EMPLOYEES MODIFY FNAME VARCHAR(50);
Query OK, 0 rows affected (0.14 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> DESC EMPLOYEES;
+----------+-------------+------+-----+---------+-------+
| Field    | Type        | Null | Key | Default | Extra |
+----------+-------------+------+-----+---------+-------+
| EMPID    | char(5)     | YES  |     | NULL    |       |
| FNAME    | varchar(50) | YES  |     | NULL    |       |
| LNAME    | varchar(60) | YES  |     | NULL    |       |
| AGE      | int         | YES  |     | NULL    |       |
| DOJ      | date        | YES  |     | NULL    |       |
| ADDRESS  | tinytext    | YES  |     | NULL    |       |
| PFID     | int         | YES  |     | NULL    |       |
| DEPT     | varchar(50) | YES  |     | NULL    |       |
| LOCATION | tinytext    | YES  |     | NULL    |       |
+----------+-------------+------+-----+---------+-------+
9 rows in set (0.00 sec)

mysql> ALTER TABLE EMPLOYEES MODIFY LNAME VARCHAR(100);
Query OK, 0 rows affected (0.05 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> DESC EMPLOYEES;
+----------+--------------+------+-----+---------+-------+
| Field    | Type         | Null | Key | Default | Extra |
+----------+--------------+------+-----+---------+-------+
| EMPID    | char(5)      | YES  |     | NULL    |       |
| FNAME    | varchar(50)  | YES  |     | NULL    |       |
| LNAME    | varchar(100) | YES  |     | NULL    |       |
| AGE      | int          | YES  |     | NULL    |       |
| DOJ      | date         | YES  |     | NULL    |       |
| ADDRESS  | tinytext     | YES  |     | NULL    |       |
| PFID     | int          | YES  |     | NULL    |       |
| DEPT     | varchar(50)  | YES  |     | NULL    |       |
| LOCATION | tinytext     | YES  |     | NULL    |       |
+----------+--------------+------+-----+---------+-------+
9 rows in set (0.00 sec)

mysql> -- CHANGE COULMN NAME
mysql> -- ALTER TABLE TABLE-NAME CHNAGE EXISTING-COLUMN-NAME NEW-COLUMN-NAME DATATYPE(SIZE). 
mysql> ALTER TABLE EMPLOYEES CHANGE FNAME FIRSTNAME VARCHAR(30);
Query OK, 0 rows affected (0.06 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> DESC EMPLOYEES;
+-----------+--------------+------+-----+---------+-------+
| Field     | Type         | Null | Key | Default | Extra |
+-----------+--------------+------+-----+---------+-------+
| EMPID     | char(5)      | YES  |     | NULL    |       |
| FIRSTNAME | varchar(30)  | YES  |     | NULL    |       |
| LNAME     | varchar(100) | YES  |     | NULL    |       |
| AGE       | int          | YES  |     | NULL    |       |
| DOJ       | date         | YES  |     | NULL    |       |
| ADDRESS   | tinytext     | YES  |     | NULL    |       |
| PFID      | int          | YES  |     | NULL    |       |
| DEPT      | varchar(50)  | YES  |     | NULL    |       |
| LOCATION  | tinytext     | YES  |     | NULL    |       |
+-----------+--------------+------+-----+---------+-------+
9 rows in set (0.00 sec)

mysql> ALTER TABLE EMPLOYEES CHANGE LNAME LASTNAME VARCHAR(30);
Query OK, 0 rows affected (0.05 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> DESC EMPLOYEES;
+-----------+-------------+------+-----+---------+-------+
| Field     | Type        | Null | Key | Default | Extra |
+-----------+-------------+------+-----+---------+-------+
| EMPID     | char(5)     | YES  |     | NULL    |       |
| FIRSTNAME | varchar(30) | YES  |     | NULL    |       |
| LASTNAME  | varchar(30) | YES  |     | NULL    |       |
| AGE       | int         | YES  |     | NULL    |       |
| DOJ       | date        | YES  |     | NULL    |       |
| ADDRESS   | tinytext    | YES  |     | NULL    |       |
| PFID      | int         | YES  |     | NULL    |       |
| DEPT      | varchar(50) | YES  |     | NULL    |       |
| LOCATION  | tinytext    | YES  |     | NULL    |       |
+-----------+-------------+------+-----+---------+-------+
9 rows in set (0.00 sec)

mysql> -- TO DROP A COLUMN.
mysql> -- ALTER TABLE TABLE-NAME DROP COLUMN COLUMN-NAME.
mysql> ALTER TABLE EMPLOYEES DROP COLUMN PFID;
Query OK, 0 rows affected (0.04 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> DESC EMPLOYEES;
+-----------+-------------+------+-----+---------+-------+
| Field     | Type        | Null | Key | Default | Extra |
+-----------+-------------+------+-----+---------+-------+
| EMPID     | char(5)     | YES  |     | NULL    |       |
| FIRSTNAME | varchar(30) | YES  |     | NULL    |       |
| LASTNAME  | varchar(30) | YES  |     | NULL    |       |
| AGE       | int         | YES  |     | NULL    |       |
| DOJ       | date        | YES  |     | NULL    |       |
| ADDRESS   | tinytext    | YES  |     | NULL    |       |
| DEPT      | varchar(50) | YES  |     | NULL    |       |
| LOCATION  | tinytext    | YES  |     | NULL    |       |
+-----------+-------------+------+-----+---------+-------+
8 rows in set (0.00 sec)

mysql> ALTER TABLE EMPLOYEES DROP COLUMN LOCATION;
Query OK, 0 rows affected (0.05 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> DESC EMPLOYEES;
+-----------+-------------+------+-----+---------+-------+
| Field     | Type        | Null | Key | Default | Extra |
+-----------+-------------+------+-----+---------+-------+
| EMPID     | char(5)     | YES  |     | NULL    |       |
| FIRSTNAME | varchar(30) | YES  |     | NULL    |       |
| LASTNAME  | varchar(30) | YES  |     | NULL    |       |
| AGE       | int         | YES  |     | NULL    |       |
| DOJ       | date        | YES  |     | NULL    |       |
| ADDRESS   | tinytext    | YES  |     | NULL    |       |
| DEPT      | varchar(50) | YES  |     | NULL    |       |
+-----------+-------------+------+-----+---------+-------+
7 rows in set (0.00 sec)

mysql> -- CHANGE THE TABLE NAME.
mysql> -- SYNTAX : ALTER TABLE EXISTING-TABLE-NAME RENAME TO NEW-TABLE-NAME.
mysql> ALTER TABLE EMPLOYEES RENAME TO CODEGNAN_EMP;
Query OK, 0 rows affected (0.04 sec)

mysql> SHOW TABLES;
+----------------+
| Tables_in_pfs4 |
+----------------+
| codegnan_emp   |
+----------------+
1 row in set (0.00 sec)

mysql> DESC CODEGNAN_EMP;
+-----------+-------------+------+-----+---------+-------+
| Field     | Type        | Null | Key | Default | Extra |
+-----------+-------------+------+-----+---------+-------+
| EMPID     | char(5)     | YES  |     | NULL    |       |
| FIRSTNAME | varchar(30) | YES  |     | NULL    |       |
| LASTNAME  | varchar(30) | YES  |     | NULL    |       |
| AGE       | int         | YES  |     | NULL    |       |
| DOJ       | date        | YES  |     | NULL    |       |
| ADDRESS   | tinytext    | YES  |     | NULL    |       |
| DEPT      | varchar(50) | YES  |     | NULL    |       |
+-----------+-------------+------+-----+---------+-------+
7 rows in set (0.00 sec)

mysql> ALTER TABLE CODEGNAN_EMP RENAME TO EMPLOYEES;
Query OK, 0 rows affected (0.04 sec)

mysql> SHOW TABLES;
+----------------+
| Tables_in_pfs4 |
+----------------+
| employees      |
+----------------+
1 row in set (0.00 sec)

mysql> DESC EMPLOYEES;
+-----------+-------------+------+-----+---------+-------+
| Field     | Type        | Null | Key | Default | Extra |
+-----------+-------------+------+-----+---------+-------+
| EMPID     | char(5)     | YES  |     | NULL    |       |
| FIRSTNAME | varchar(30) | YES  |     | NULL    |       |
| LASTNAME  | varchar(30) | YES  |     | NULL    |       |
| AGE       | int         | YES  |     | NULL    |       |
| DOJ       | date        | YES  |     | NULL    |       |
| ADDRESS   | tinytext    | YES  |     | NULL    |       |
| DEPT      | varchar(50) | YES  |     | NULL    |       |
+-----------+-------------+------+-----+---------+-------+
7 rows in set (0.00 sec)

mysql> SHOW TABLES;
+----------------+
| Tables_in_pfs4 |
+----------------+
| employees      |
+----------------+
1 row in set (0.00 sec)

mysql> CREATE TABLE COMPANY_STAFF(
    -> EMP_ID INT,
    -> AGE TINYINT,
    -> EXPERIENCE SMALLINT,
    -> GENDER CHAR(1),
    -> EMP_NAME VARCHAR(50),
    -> ADDRESS TINYTEXT,
    -> SALARY DECIMAL(10,2),
    -> DEPARTMENT ENUM('HR','IT','Sales','Finance','Support'),
    -> SKILLS SET('Java','Python','SQL','Excel','Communication'),
    -> JOINING_DATE DATE
    -> );
Query OK, 0 rows affected (0.02 sec)

mysql> DESC COMPANY_STAFF;
+--------------+----------------------------------------------------+------+-----+---------+-------+
| Field        | Type                                               | Null | Key | Default | Extra |
+--------------+----------------------------------------------------+------+-----+---------+-------+
| EMP_ID       | int                                                | YES  |     | NULL    |       |
| AGE          | tinyint                                            | YES  |     | NULL    |       |
| EXPERIENCE   | smallint                                           | YES  |     | NULL    |       |
| GENDER       | char(1)                                            | YES  |     | NULL    |       |
| EMP_NAME     | varchar(50)                                        | YES  |     | NULL    |       |
| ADDRESS      | tinytext                                           | YES  |     | NULL    |       |
| SALARY       | decimal(10,2)                                      | YES  |     | NULL    |       |
| DEPARTMENT   | enum('HR','IT','Sales','Finance','Support')        | YES  |     | NULL    |       |
| SKILLS       | set('Java','Python','SQL','Excel','Communication') | YES  |     | NULL    |       |
| JOINING_DATE | date                                               | YES  |     | NULL    |       |
+--------------+----------------------------------------------------+------+-----+---------+-------+
10 rows in set (0.04 sec)

mysql> SHOW TABLES;
+----------------+
| Tables_in_pfs4 |
+----------------+
| company_staff  |
| employees      |
+----------------+
2 rows in set (0.00 sec)

mysql> ALTER TABLE COMPANY_STAFF ADD EMAIL VARCHAR(30);
Query OK, 0 rows affected (0.07 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> ALTER TABLE COMPANY_STAFF ADD PHONE_NUMBER INT;
Query OK, 0 rows affected (0.04 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> DESC COMPANY_STAFF;
+--------------+----------------------------------------------------+------+-----+---------+-------+
| Field        | Type                                               | Null | Key | Default | Extra |
+--------------+----------------------------------------------------+------+-----+---------+-------+
| EMP_ID       | int                                                | YES  |     | NULL    |       |
| AGE          | tinyint                                            | YES  |     | NULL    |       |
| EXPERIENCE   | smallint                                           | YES  |     | NULL    |       |
| GENDER       | char(1)                                            | YES  |     | NULL    |       |
| EMP_NAME     | varchar(50)                                        | YES  |     | NULL    |       |
| ADDRESS      | tinytext                                           | YES  |     | NULL    |       |
| SALARY       | decimal(10,2)                                      | YES  |     | NULL    |       |
| DEPARTMENT   | enum('HR','IT','Sales','Finance','Support')        | YES  |     | NULL    |       |
| SKILLS       | set('Java','Python','SQL','Excel','Communication') | YES  |     | NULL    |       |
| JOINING_DATE | date                                               | YES  |     | NULL    |       |
| EMAIL        | varchar(30)                                        | YES  |     | NULL    |       |
| PHONE_NUMBER | int                                                | YES  |     | NULL    |       |
+--------------+----------------------------------------------------+------+-----+---------+-------+
12 rows in set (0.00 sec)

mysql> ALTER TABLE COMPANY_STAFF CHANGE PHONE_NUMBER PHONE_NUMBER VARCHAR(30);
Query OK, 0 rows affected (0.05 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> DESC COMPANY_STAFF;
+--------------+----------------------------------------------------+------+-----+---------+-------+
| Field        | Type                                               | Null | Key | Default | Extra |
+--------------+----------------------------------------------------+------+-----+---------+-------+
| EMP_ID       | int                                                | YES  |     | NULL    |       |
| AGE          | tinyint                                            | YES  |     | NULL    |       |
| EXPERIENCE   | smallint                                           | YES  |     | NULL    |       |
| GENDER       | char(1)                                            | YES  |     | NULL    |       |
| EMP_NAME     | varchar(50)                                        | YES  |     | NULL    |       |
| ADDRESS      | tinytext                                           | YES  |     | NULL    |       |
| SALARY       | decimal(10,2)                                      | YES  |     | NULL    |       |
| DEPARTMENT   | enum('HR','IT','Sales','Finance','Support')        | YES  |     | NULL    |       |
| SKILLS       | set('Java','Python','SQL','Excel','Communication') | YES  |     | NULL    |       |
| JOINING_DATE | date                                               | YES  |     | NULL    |       |
| EMAIL        | varchar(30)                                        | YES  |     | NULL    |       |
| PHONE_NUMBER | varchar(30)                                        | YES  |     | NULL    |       |
+--------------+----------------------------------------------------+------+-----+---------+-------+
12 rows in set (0.00 sec)

mysql> ALTER TABLE COMPANY_STAFF ADD BONUS AFTER SALARY;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'AFTER SALARY' at line 1
mysql> ALTER TABLE COMPANY_STAFF ADD BONUS INT AFTER SALARY;
Query OK, 0 rows affected (0.09 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> DESC COMPANY_STAFF;
+--------------+----------------------------------------------------+------+-----+---------+-------+
| Field        | Type                                               | Null | Key | Default | Extra |
+--------------+----------------------------------------------------+------+-----+---------+-------+
| EMP_ID       | int                                                | YES  |     | NULL    |       |
| AGE          | tinyint                                            | YES  |     | NULL    |       |
| EXPERIENCE   | smallint                                           | YES  |     | NULL    |       |
| GENDER       | char(1)                                            | YES  |     | NULL    |       |
| EMP_NAME     | varchar(50)                                        | YES  |     | NULL    |       |
| ADDRESS      | tinytext                                           | YES  |     | NULL    |       |
| SALARY       | decimal(10,2)                                      | YES  |     | NULL    |       |
| BONUS        | int                                                | YES  |     | NULL    |       |
| DEPARTMENT   | enum('HR','IT','Sales','Finance','Support')        | YES  |     | NULL    |       |
| SKILLS       | set('Java','Python','SQL','Excel','Communication') | YES  |     | NULL    |       |
| JOINING_DATE | date                                               | YES  |     | NULL    |       |
| EMAIL        | varchar(30)                                        | YES  |     | NULL    |       |
| PHONE_NUMBER | varchar(30)                                        | YES  |     | NULL    |       |
+--------------+----------------------------------------------------+------+-----+---------+-------+
13 rows in set (0.00 sec)

mysql> ALTER TABLE COMPANY_STAFF ADD STATUS VARCHAR(30) AFTER DEPARTMENT;
Query OK, 0 rows affected (0.09 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> DESC COMPANY_STAFF;
+--------------+----------------------------------------------------+------+-----+---------+-------+
| Field        | Type                                               | Null | Key | Default | Extra |
+--------------+----------------------------------------------------+------+-----+---------+-------+
| EMP_ID       | int                                                | YES  |     | NULL    |       |
| AGE          | tinyint                                            | YES  |     | NULL    |       |
| EXPERIENCE   | smallint                                           | YES  |     | NULL    |       |
| GENDER       | char(1)                                            | YES  |     | NULL    |       |
| EMP_NAME     | varchar(50)                                        | YES  |     | NULL    |       |
| ADDRESS      | tinytext                                           | YES  |     | NULL    |       |
| SALARY       | decimal(10,2)                                      | YES  |     | NULL    |       |
| BONUS        | int                                                | YES  |     | NULL    |       |
| DEPARTMENT   | enum('HR','IT','Sales','Finance','Support')        | YES  |     | NULL    |       |
| STATUS       | varchar(30)                                        | YES  |     | NULL    |       |
| SKILLS       | set('Java','Python','SQL','Excel','Communication') | YES  |     | NULL    |       |
| JOINING_DATE | date                                               | YES  |     | NULL    |       |
| EMAIL        | varchar(30)                                        | YES  |     | NULL    |       |
| PHONE_NUMBER | varchar(30)                                        | YES  |     | NULL    |       |
+--------------+----------------------------------------------------+------+-----+---------+-------+
14 rows in set (0.00 sec)

mysql> ALTER TABLE COMPANY_STAFF ADD COMPANY_NAME VARCHAR(30) FIRST;
Query OK, 0 rows affected (0.09 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> DESC COMPANY_STAFF;
+--------------+----------------------------------------------------+------+-----+---------+-------+
| Field        | Type                                               | Null | Key | Default | Extra |
+--------------+----------------------------------------------------+------+-----+---------+-------+
| COMPANY_NAME | varchar(30)                                        | YES  |     | NULL    |       |
| EMP_ID       | int                                                | YES  |     | NULL    |       |
| AGE          | tinyint                                            | YES  |     | NULL    |       |
| EXPERIENCE   | smallint                                           | YES  |     | NULL    |       |
| GENDER       | char(1)                                            | YES  |     | NULL    |       |
| EMP_NAME     | varchar(50)                                        | YES  |     | NULL    |       |
| ADDRESS      | tinytext                                           | YES  |     | NULL    |       |
| SALARY       | decimal(10,2)                                      | YES  |     | NULL    |       |
| BONUS        | int                                                | YES  |     | NULL    |       |
| DEPARTMENT   | enum('HR','IT','Sales','Finance','Support')        | YES  |     | NULL    |       |
| STATUS       | varchar(30)                                        | YES  |     | NULL    |       |
| SKILLS       | set('Java','Python','SQL','Excel','Communication') | YES  |     | NULL    |       |
| JOINING_DATE | date                                               | YES  |     | NULL    |       |
| EMAIL        | varchar(30)                                        | YES  |     | NULL    |       |
| PHONE_NUMBER | varchar(30)                                        | YES  |     | NULL    |       |
+--------------+----------------------------------------------------+------+-----+---------+-------+
15 rows in set (0.00 sec)

mysql> ALTER TABLE COMPANY_STAFF ADD QUALIFICATION VARCHAR(30) AFTER EMP_NAME;
Query OK, 0 rows affected (0.05 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> DESC COMPANY_STAFF;
+---------------+----------------------------------------------------+------+-----+---------+-------+
| Field         | Type                                               | Null | Key | Default | Extra |
+---------------+----------------------------------------------------+------+-----+---------+-------+
| COMPANY_NAME  | varchar(30)                                        | YES  |     | NULL    |       |
| EMP_ID        | int                                                | YES  |     | NULL    |       |
| AGE           | tinyint                                            | YES  |     | NULL    |       |
| EXPERIENCE    | smallint                                           | YES  |     | NULL    |       |
| GENDER        | char(1)                                            | YES  |     | NULL    |       |
| EMP_NAME      | varchar(50)                                        | YES  |     | NULL    |       |
| QUALIFICATION | varchar(30)                                        | YES  |     | NULL    |       |
| ADDRESS       | tinytext                                           | YES  |     | NULL    |       |
| SALARY        | decimal(10,2)                                      | YES  |     | NULL    |       |
| BONUS         | int                                                | YES  |     | NULL    |       |
| DEPARTMENT    | enum('HR','IT','Sales','Finance','Support')        | YES  |     | NULL    |       |
| STATUS        | varchar(30)                                        | YES  |     | NULL    |       |
| SKILLS        | set('Java','Python','SQL','Excel','Communication') | YES  |     | NULL    |       |
| JOINING_DATE  | date                                               | YES  |     | NULL    |       |
| EMAIL         | varchar(30)                                        | YES  |     | NULL    |       |
| PHONE_NUMBER  | varchar(30)                                        | YES  |     | NULL    |       |
+---------------+----------------------------------------------------+------+-----+---------+-------+
16 rows in set (0.00 sec)

mysql> ALTER TABLE COMPANY_STAFF MODIFY EMP_NAME VARCHAR(100
    -> );
Query OK, 0 rows affected (0.06 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> DESC COMPANY_STAFF;
+---------------+----------------------------------------------------+------+-----+---------+-------+
| Field         | Type                                               | Null | Key | Default | Extra |
+---------------+----------------------------------------------------+------+-----+---------+-------+
| COMPANY_NAME  | varchar(30)                                        | YES  |     | NULL    |       |
| EMP_ID        | int                                                | YES  |     | NULL    |       |
| AGE           | tinyint                                            | YES  |     | NULL    |       |
| EXPERIENCE    | smallint                                           | YES  |     | NULL    |       |
| GENDER        | char(1)                                            | YES  |     | NULL    |       |
| EMP_NAME      | varchar(100)                                       | YES  |     | NULL    |       |
| QUALIFICATION | varchar(30)                                        | YES  |     | NULL    |       |
| ADDRESS       | tinytext                                           | YES  |     | NULL    |       |
| SALARY        | decimal(10,2)                                      | YES  |     | NULL    |       |
| BONUS         | int                                                | YES  |     | NULL    |       |
| DEPARTMENT    | enum('HR','IT','Sales','Finance','Support')        | YES  |     | NULL    |       |
| STATUS        | varchar(30)                                        | YES  |     | NULL    |       |
| SKILLS        | set('Java','Python','SQL','Excel','Communication') | YES  |     | NULL    |       |
| JOINING_DATE  | date                                               | YES  |     | NULL    |       |
| EMAIL         | varchar(30)                                        | YES  |     | NULL    |       |
| PHONE_NUMBER  | varchar(30)                                        | YES  |     | NULL    |       |
+---------------+----------------------------------------------------+------+-----+---------+-------+
16 rows in set (0.00 sec)

mysql> ALTER TABLE COMPANY_STAFF MODIFY SALARY DECIMAL(20,3);
Query OK, 0 rows affected (0.04 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> DESC COMPANY_STAFF;
+---------------+----------------------------------------------------+------+-----+---------+-------+
| Field         | Type                                               | Null | Key | Default | Extra |
+---------------+----------------------------------------------------+------+-----+---------+-------+
| COMPANY_NAME  | varchar(30)                                        | YES  |     | NULL    |       |
| EMP_ID        | int                                                | YES  |     | NULL    |       |
| AGE           | tinyint                                            | YES  |     | NULL    |       |
| EXPERIENCE    | smallint                                           | YES  |     | NULL    |       |
| GENDER        | char(1)                                            | YES  |     | NULL    |       |
| EMP_NAME      | varchar(100)                                       | YES  |     | NULL    |       |
| QUALIFICATION | varchar(30)                                        | YES  |     | NULL    |       |
| ADDRESS       | tinytext                                           | YES  |     | NULL    |       |
| SALARY        | decimal(20,3)                                      | YES  |     | NULL    |       |
| BONUS         | int                                                | YES  |     | NULL    |       |
| DEPARTMENT    | enum('HR','IT','Sales','Finance','Support')        | YES  |     | NULL    |       |
| STATUS        | varchar(30)                                        | YES  |     | NULL    |       |
| SKILLS        | set('Java','Python','SQL','Excel','Communication') | YES  |     | NULL    |       |
| JOINING_DATE  | date                                               | YES  |     | NULL    |       |
| EMAIL         | varchar(30)                                        | YES  |     | NULL    |       |
| PHONE_NUMBER  | varchar(30)                                        | YES  |     | NULL    |       |
+---------------+----------------------------------------------------+------+-----+---------+-------+
16 rows in set (0.00 sec)

mysql> ALTER TABLE COMPANY_STAFF CHANGE EMP_NAME EMPLOYEE_NAME VARCHAR(30);
Query OK, 0 rows affected (0.04 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> DESC COMPANY_STAFF;
+---------------+----------------------------------------------------+------+-----+---------+-------+
| Field         | Type                                               | Null | Key | Default | Extra |
+---------------+----------------------------------------------------+------+-----+---------+-------+
| COMPANY_NAME  | varchar(30)                                        | YES  |     | NULL    |       |
| EMP_ID        | int                                                | YES  |     | NULL    |       |
| AGE           | tinyint                                            | YES  |     | NULL    |       |
| EXPERIENCE    | smallint                                           | YES  |     | NULL    |       |
| GENDER        | char(1)                                            | YES  |     | NULL    |       |
| EMPLOYEE_NAME | varchar(30)                                        | YES  |     | NULL    |       |
| QUALIFICATION | varchar(30)                                        | YES  |     | NULL    |       |
| ADDRESS       | tinytext                                           | YES  |     | NULL    |       |
| SALARY        | decimal(20,3)                                      | YES  |     | NULL    |       |
| BONUS         | int                                                | YES  |     | NULL    |       |
| DEPARTMENT    | enum('HR','IT','Sales','Finance','Support')        | YES  |     | NULL    |       |
| STATUS        | varchar(30)                                        | YES  |     | NULL    |       |
| SKILLS        | set('Java','Python','SQL','Excel','Communication') | YES  |     | NULL    |       |
| JOINING_DATE  | date                                               | YES  |     | NULL    |       |
| EMAIL         | varchar(30)                                        | YES  |     | NULL    |       |
| PHONE_NUMBER  | varchar(30)                                        | YES  |     | NULL    |       |
+---------------+----------------------------------------------------+------+-----+---------+-------+
16 rows in set (0.00 sec)

mysql> ALTER TABLE COMPANY_STAFF CHANGE JOINING_DATE DATE_OF_JOINING DATE;
Query OK, 0 rows affected (0.02 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> DESC COMPANY_STAFF;
+-----------------+----------------------------------------------------+------+-----+---------+-------+
| Field           | Type                                               | Null | Key | Default | Extra |
+-----------------+----------------------------------------------------+------+-----+---------+-------+
| COMPANY_NAME    | varchar(30)                                        | YES  |     | NULL    |       |
| EMP_ID          | int                                                | YES  |     | NULL    |       |
| AGE             | tinyint                                            | YES  |     | NULL    |       |
| EXPERIENCE      | smallint                                           | YES  |     | NULL    |       |
| GENDER          | char(1)                                            | YES  |     | NULL    |       |
| EMPLOYEE_NAME   | varchar(30)                                        | YES  |     | NULL    |       |
| QUALIFICATION   | varchar(30)                                        | YES  |     | NULL    |       |
| ADDRESS         | tinytext                                           | YES  |     | NULL    |       |
| SALARY          | decimal(20,3)                                      | YES  |     | NULL    |       |
| BONUS           | int                                                | YES  |     | NULL    |       |
| DEPARTMENT      | enum('HR','IT','Sales','Finance','Support')        | YES  |     | NULL    |       |
| STATUS          | varchar(30)                                        | YES  |     | NULL    |       |
| SKILLS          | set('Java','Python','SQL','Excel','Communication') | YES  |     | NULL    |       |
| DATE_OF_JOINING | date                                               | YES  |     | NULL    |       |
| EMAIL           | varchar(30)                                        | YES  |     | NULL    |       |
| PHONE_NUMBER    | varchar(30)                                        | YES  |     | NULL    |       |
+-----------------+----------------------------------------------------+------+-----+---------+-------+
16 rows in set (0.00 sec)

mysql> ALTER TABLE COMPANY_STAFF DROP COLUMN BONUS;
Query OK, 0 rows affected (0.11 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> ALTER TABLE COMPANY_STAFF DROP COLUMN PHONE_NUMBER;
Query OK, 0 rows affected (0.07 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> DESC COMPANY_STAFF;
+-----------------+----------------------------------------------------+------+-----+---------+-------+
| Field           | Type                                               | Null | Key | Default | Extra |
+-----------------+----------------------------------------------------+------+-----+---------+-------+
| COMPANY_NAME    | varchar(30)                                        | YES  |     | NULL    |       |
| EMP_ID          | int                                                | YES  |     | NULL    |       |
| AGE             | tinyint                                            | YES  |     | NULL    |       |
| EXPERIENCE      | smallint                                           | YES  |     | NULL    |       |
| GENDER          | char(1)                                            | YES  |     | NULL    |       |
| EMPLOYEE_NAME   | varchar(30)                                        | YES  |     | NULL    |       |
| QUALIFICATION   | varchar(30)                                        | YES  |     | NULL    |       |
| ADDRESS         | tinytext                                           | YES  |     | NULL    |       |
| SALARY          | decimal(20,3)                                      | YES  |     | NULL    |       |
| DEPARTMENT      | enum('HR','IT','Sales','Finance','Support')        | YES  |     | NULL    |       |
| STATUS          | varchar(30)                                        | YES  |     | NULL    |       |
| SKILLS          | set('Java','Python','SQL','Excel','Communication') | YES  |     | NULL    |       |
| DATE_OF_JOINING | date                                               | YES  |     | NULL    |       |
| EMAIL           | varchar(30)                                        | YES  |     | NULL    |       |
+-----------------+----------------------------------------------------+------+-----+---------+-------+
14 rows in set (0.00 sec)

mysql> ALTER TABLE COMPANY_STAFF RENAME TO STAFF_RECORDS;
Query OK, 0 rows affected (0.07 sec)

mysql> SHOW TABLES;
+----------------+
| Tables_in_pfs4 |
+----------------+
| employees      |
| staff_records  |
+----------------+
2 rows in set (0.00 sec)

mysql> ALTER TABLE STAFF_RECORDS RENAME TO COMPANY_STAFF;
Query OK, 0 rows affected (0.02 sec)

mysql> SHOW TABLES;
+----------------+
| Tables_in_pfs4 |
+----------------+
| company_staff  |
| employees      |
+----------------+
2 rows in set (0.00 sec)

mysql> DESC COMPANY_STAFF;
+-----------------+----------------------------------------------------+------+-----+---------+-------+
| Field           | Type                                               | Null | Key | Default | Extra |
+-----------------+----------------------------------------------------+------+-----+---------+-------+
| COMPANY_NAME    | varchar(30)                                        | YES  |     | NULL    |       |
| EMP_ID          | int                                                | YES  |     | NULL    |       |
| AGE             | tinyint                                            | YES  |     | NULL    |       |
| EXPERIENCE      | smallint                                           | YES  |     | NULL    |       |
| GENDER          | char(1)                                            | YES  |     | NULL    |       |
| EMPLOYEE_NAME   | varchar(30)                                        | YES  |     | NULL    |       |
| QUALIFICATION   | varchar(30)                                        | YES  |     | NULL    |       |
| ADDRESS         | tinytext                                           | YES  |     | NULL    |       |
| SALARY          | decimal(20,3)                                      | YES  |     | NULL    |       |
| DEPARTMENT      | enum('HR','IT','Sales','Finance','Support')        | YES  |     | NULL    |       |
| STATUS          | varchar(30)                                        | YES  |     | NULL    |       |
| SKILLS          | set('Java','Python','SQL','Excel','Communication') | YES  |     | NULL    |       |
| DATE_OF_JOINING | date                                               | YES  |     | NULL    |       |
| EMAIL           | varchar(30)                                        | YES  |     | NULL    |       |
+-----------------+----------------------------------------------------+------+-----+---------+-------+
14 rows in set (0.00 sec)

mysql> ALTER TABLE COMPANY_STAFF ADD LAST_UPDATED VARCHAR(30) BEFORE DATE_OF_JOINING;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'BEFORE DATE_OF_JOINING' at line 1
mysql> ALTER TABLE COMPANY_STAFF ADD LAST_UPDATED VARCHAR(30) AFTER SKILLS;
Query OK, 0 rows affected (0.04 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> DESC COMPANY_STAFF;
+-----------------+----------------------------------------------------+------+-----+---------+-------+
| Field           | Type                                               | Null | Key | Default | Extra |
+-----------------+----------------------------------------------------+------+-----+---------+-------+
| COMPANY_NAME    | varchar(30)                                        | YES  |     | NULL    |       |
| EMP_ID          | int                                                | YES  |     | NULL    |       |
| AGE             | tinyint                                            | YES  |     | NULL    |       |
| EXPERIENCE      | smallint                                           | YES  |     | NULL    |       |
| GENDER          | char(1)                                            | YES  |     | NULL    |       |
| EMPLOYEE_NAME   | varchar(30)                                        | YES  |     | NULL    |       |
| QUALIFICATION   | varchar(30)                                        | YES  |     | NULL    |       |
| ADDRESS         | tinytext                                           | YES  |     | NULL    |       |
| SALARY          | decimal(20,3)                                      | YES  |     | NULL    |       |
| DEPARTMENT      | enum('HR','IT','Sales','Finance','Support')        | YES  |     | NULL    |       |
| STATUS          | varchar(30)                                        | YES  |     | NULL    |       |
| SKILLS          | set('Java','Python','SQL','Excel','Communication') | YES  |     | NULL    |       |
| LAST_UPDATED    | varchar(30)                                        | YES  |     | NULL    |       |
| DATE_OF_JOINING | date                                               | YES  |     | NULL    |       |
| EMAIL           | varchar(30)                                        | YES  |     | NULL    |       |
+-----------------+----------------------------------------------------+------+-----+---------+-------+
15 rows in set (0.00 sec)

