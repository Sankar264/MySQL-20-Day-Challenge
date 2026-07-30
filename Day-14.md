Day_14_MySQL
=============

Date and Time Functions
========================
CURDATE(): Returns the current date;
CURTIME(): Returns the current time;
NOW() Returns the current date and time
DATE(): Extract date part
TIME(): Extract time part
YEAR(): Extract year
MONTH(): Extract month
DAY()/ dayofmonth(): Extract day of month
WEEK(): Extract week number
DAYOFWEEK: Extract the day of the week

mysql> use pfs4;
Database changed
mysql> select curdate() as current_date;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'current_date' at line 1
mysql> select curdate() as current__date;
+---------------+
| current__date |
+---------------+
| 2026-07-29    |
+---------------+
1 row in set (0.00 sec)

mysql> select curtime() as current__time;
+---------------+
| current__time |
+---------------+
| 11:14:25      |
+---------------+
1 row in set (0.00 sec)

mysql> select now() as current_date_time;
+---------------------+
| current_date_time   |
+---------------------+
| 2026-07-29 11:14:40 |
+---------------------+
1 row in set (0.00 sec)

mysql> select date(now()) as extracted_date;
+----------------+
| extracted_date |
+----------------+
| 2026-07-29     |
+----------------+
1 row in set (0.00 sec)

mysql> select time(now()) as extracted_time;
+----------------+
| extracted_time |
+----------------+
| 11:15:24       |
+----------------+
1 row in set (0.00 sec)

mysql> SELECT TIME('2024-04-03 14:32:10') AS EXTRATED_TIME;
+---------------+
| EXTRATED_TIME |
+---------------+
| 14:32:10      |
+---------------+
1 row in set (0.00 sec)

mysql> SELECT YEAR(NOW()) AS YEAR_PART;
+-----------+
| YEAR_PART |
+-----------+
|      2026 |
+-----------+
1 row in set (0.00 sec)

mysql> SELECT MONTH(NOW()) AS MONTH_PART;
+------------+
| MONTH_PART |
+------------+
|          7 |
+------------+
1 row in set (0.00 sec)

mysql> SELECT DAY(NOW()) AS DAY_PART;
+----------+
| DAY_PART |
+----------+
|       29 |
+----------+
1 row in set (0.01 sec)

mysql> SELECT WEEK(NOW()) AS WEEK_NUMBER;
+-------------+
| WEEK_NUMBER |
+-------------+
|          30 |
+-------------+
1 row in set (0.00 sec)

mysql> SELECT DAYOFWEEK(NOW()) AS DAY_OF_WEEK;
+-------------+
| DAY_OF_WEEK |
+-------------+
|           4 |
+-------------+
1 row in set (0.00 sec)

mysql> SELECT DATE_ADD(NOW(),INTERVAL 20 DAY) AS NEW_DATE;
+---------------------+
| NEW_DATE            |
+---------------------+
| 2026-08-18 11:21:27 |
+---------------------+
1 row in set (0.00 sec)

mysql> SELECT DATE_sub(NOW(),INTERVAL 20 DAY) AS NEW_DATE;
+---------------------+
| NEW_DATE            |
+---------------------+
| 2026-07-09 11:22:30 |
+---------------------+
1 row in set (0.00 sec)

mysql> SELECT DATEdiff(NOW(),'2005-04-12') AS days_diff;
+-----------+
| days_diff |
+-----------+
|      7778 |
+-----------+
1 row in set (0.00 sec)

mysql> SELECT DATE_FORMAT(NOW(),'%w,%M,%D,%Y') AS FORMATED_DATE;
+------------------+
| FORMATED_DATE    |
+------------------+
| 3,July,29th,2026 |
+------------------+
1 row in set (0.00 sec)

mysql> SELECT DATE_FORMAT(NOW(),'%W,%M,%D,%Y') AS FORMATED_DATE;
+--------------------------+
| FORMATED_DATE            |
+--------------------------+
| Wednesday,July,29th,2026 |
+--------------------------+
1 row in set (0.00 sec)

mysql> SELECT LAST_DAY(NOW()) AS LAST__DAY;
+------------+
| LAST__DAY  |
+------------+
| 2026-07-31 |
+------------+
1 row in set (0.00 sec)

mysql> SELECT MONTHNAME(NOW()) AS MONTH_NAME;
+------------+
| MONTH_NAME |
+------------+
| July       |
+------------+
1 row in set (0.00 sec)

mysql> SELECT DAYNAME(NOW()) AS DAY_NAME;
+-----------+
| DAY_NAME  |
+-----------+
| Wednesday |
+-----------+
1 row in set (0.00 sec)

mysql> SELECT QUARTER(NOW()) AS MONTH_QUARTER;
+---------------+
| MONTH_QUARTER |
+---------------+
|             3 |
+---------------+
1 row in set (0.00 sec)

mysql> SELECT TIME_TO_SEC('01:01:01') AS TOTAL_SECONDS;
+---------------+
| TOTAL_SECONDS |
+---------------+
|          3661 |
+---------------+
1 row in set (0.00 sec)

mysql> SELECT SEC_TO_TIME(3661) AS TOTAL_TIME;
+------------+
| TOTAL_TIME |
+------------+
| 01:01:01   |
+------------+
1 row in set (0.00 sec)

mysql> SELECT SYSDATE() AS SYSTEM_DATE_TIME;
+---------------------+
| SYSTEM_DATE_TIME    |
+---------------------+
| 2026-07-29 11:34:38 |
+---------------------+
1 row in set (0.00 sec)

mysql> CREATE TABLE employee_attendance
    -> (
    -> 	emp_id INT PRIMARY KEY AUTO_INCREMENT,
    -> 	emp_name VARCHAR(100),
    -> 	department VARCHAR(50),
    -> 	joining_date DATE,
    -> 	birth_date DATE,
    -> 	login_time DATETIME,
    -> 	logout_time DATETIME,
    -> 	salary DECIMAL(10,2)
    -> );
Query OK, 0 rows affected (0.14 sec)

mysql> 
mysql> INSERT INTO employee_attendance
    -> (emp_name, department, joining_date, birth_date, login_time, logout_time, salary)
    -> VALUES
    -> ('Rahul','IT','2021-06-15','1998-05-10','2024-11-20 09:05:10','2024-11-20 18:15:30',55000),
    -> ('Sneha','HR','2020-03-21','1996-11-18','2024-11-21 08:55:20','2024-11-21 17:45:50',48000),
    -> ('Arjun','Finance','2019-08-10','1994-07-30','2024-11-22 09:15:45','2024-11-22 18:35:20',62000),
    -> ('Priya','IT','2022-01-05','2000-01-25','2024-11-23 09:00:00','2024-11-23 17:55:40',51000),
    -> ('Kiran','Admin','2018-12-11','1992-09-15','2024-11-24 08:40:30','2024-11-24 17:30:00',45000),
    -> ('Anjali','Testing','2023-04-17','1999-12-20','2024-11-25 09:12:10','2024-11-25 18:05:00',47000),
    -> ('Vijay','IT','2021-09-14','1997-04-08','2024-11-26 09:08:15','2024-11-26 18:20:40',59000),
    -> ('Divya','HR','2019-10-19','1995-06-11','2024-11-27 08:50:30','2024-11-27 17:42:15',50000),
    -> ('Ramesh','Finance','2017-07-01','1991-08-14','2024-11-28 09:03:00','2024-11-28 18:12:00',70000),
    -> ('Pooja','Testing','2022-05-09','2001-03-19','2024-11-29 09:18:50','2024-11-29 18:25:10',53000);
Query OK, 10 rows affected (0.01 sec)
Records: 10  Duplicates: 0  Warnings: 0

mysql> 
mysql> 
mysql> select*from  employee_attendance;
+--------+----------+------------+--------------+------------+---------------------+---------------------+----------+
| emp_id | emp_name | department | joining_date | birth_date | login_time          | logout_time         | salary   |
+--------+----------+------------+--------------+------------+---------------------+---------------------+----------+
|      1 | Rahul    | IT         | 2021-06-15   | 1998-05-10 | 2024-11-20 09:05:10 | 2024-11-20 18:15:30 | 55000.00 |
|      2 | Sneha    | HR         | 2020-03-21   | 1996-11-18 | 2024-11-21 08:55:20 | 2024-11-21 17:45:50 | 48000.00 |
|      3 | Arjun    | Finance    | 2019-08-10   | 1994-07-30 | 2024-11-22 09:15:45 | 2024-11-22 18:35:20 | 62000.00 |
|      4 | Priya    | IT         | 2022-01-05   | 2000-01-25 | 2024-11-23 09:00:00 | 2024-11-23 17:55:40 | 51000.00 |
|      5 | Kiran    | Admin      | 2018-12-11   | 1992-09-15 | 2024-11-24 08:40:30 | 2024-11-24 17:30:00 | 45000.00 |
|      6 | Anjali   | Testing    | 2023-04-17   | 1999-12-20 | 2024-11-25 09:12:10 | 2024-11-25 18:05:00 | 47000.00 |
|      7 | Vijay    | IT         | 2021-09-14   | 1997-04-08 | 2024-11-26 09:08:15 | 2024-11-26 18:20:40 | 59000.00 |
|      8 | Divya    | HR         | 2019-10-19   | 1995-06-11 | 2024-11-27 08:50:30 | 2024-11-27 17:42:15 | 50000.00 |
|      9 | Ramesh   | Finance    | 2017-07-01   | 1991-08-14 | 2024-11-28 09:03:00 | 2024-11-28 18:12:00 | 70000.00 |
|     10 | Pooja    | Testing    | 2022-05-09   | 2001-03-19 | 2024-11-29 09:18:50 | 2024-11-29 18:25:10 | 53000.00 |
+--------+----------+------------+--------------+------------+---------------------+---------------------+----------+
10 rows in set (0.01 sec)

mysql> SELECT LOGIN_TIME,DATE(LOGIN_TIME) AS EXTRACTED_DATE FROM EMPLOYEE_ATTENDANCE;
+---------------------+----------------+
| LOGIN_TIME          | EXTRACTED_DATE |
+---------------------+----------------+
| 2024-11-20 09:05:10 | 2024-11-20     |
| 2024-11-21 08:55:20 | 2024-11-21     |
| 2024-11-22 09:15:45 | 2024-11-22     |
| 2024-11-23 09:00:00 | 2024-11-23     |
| 2024-11-24 08:40:30 | 2024-11-24     |
| 2024-11-25 09:12:10 | 2024-11-25     |
| 2024-11-26 09:08:15 | 2024-11-26     |
| 2024-11-27 08:50:30 | 2024-11-27     |
| 2024-11-28 09:03:00 | 2024-11-28     |
| 2024-11-29 09:18:50 | 2024-11-29     |
+---------------------+----------------+
10 rows in set (0.00 sec)

mysql> SELECT LOGIN_TIME,TIME(LOGIN_TIME) AS EXTRACTED_TIME FROM EMPLOYEE_ATTENDANCE;
+---------------------+----------------+
| LOGIN_TIME          | EXTRACTED_TIME |
+---------------------+----------------+
| 2024-11-20 09:05:10 | 09:05:10       |
| 2024-11-21 08:55:20 | 08:55:20       |
| 2024-11-22 09:15:45 | 09:15:45       |
| 2024-11-23 09:00:00 | 09:00:00       |
| 2024-11-24 08:40:30 | 08:40:30       |
| 2024-11-25 09:12:10 | 09:12:10       |
| 2024-11-26 09:08:15 | 09:08:15       |
| 2024-11-27 08:50:30 | 08:50:30       |
| 2024-11-28 09:03:00 | 09:03:00       |
| 2024-11-29 09:18:50 | 09:18:50       |
+---------------------+----------------+
10 rows in set (0.00 sec)

mysql> SELECT EMP_NAME,YEAR(JOINING_DATE) AS JOINING_YEAR FROM EMPLOYEE_ATTENDANCE;
+----------+--------------+
| EMP_NAME | JOINING_YEAR |
+----------+--------------+
| Rahul    |         2021 |
| Sneha    |         2020 |
| Arjun    |         2019 |
| Priya    |         2022 |
| Kiran    |         2018 |
| Anjali   |         2023 |
| Vijay    |         2021 |
| Divya    |         2019 |
| Ramesh   |         2017 |
| Pooja    |         2022 |
+----------+--------------+
10 rows in set (0.00 sec)

mysql> SELECT EMP_NAME,MONTH(BIRTH_DATE) AS BIRTH_MONTH FROM EMPLOYEE_ATTENDANCE;
+----------+-------------+
| EMP_NAME | BIRTH_MONTH |
+----------+-------------+
| Rahul    |           5 |
| Sneha    |          11 |
| Arjun    |           7 |
| Priya    |           1 |
| Kiran    |           9 |
| Anjali   |          12 |
| Vijay    |           4 |
| Divya    |           6 |
| Ramesh   |           8 |
| Pooja    |           3 |
+----------+-------------+
10 rows in set (0.00 sec)

mysql> SELECT EMP_NAME,DAY(BIRTH_DATE) AS BIRTH_DAY FROM EMPLOYEE_ATTENDANCE;
+----------+-----------+
| EMP_NAME | BIRTH_DAY |
+----------+-----------+
| Rahul    |        10 |
| Sneha    |        18 |
| Arjun    |        30 |
| Priya    |        25 |
| Kiran    |        15 |
| Anjali   |        20 |
| Vijay    |         8 |
| Divya    |        11 |
| Ramesh   |        14 |
| Pooja    |        19 |
+----------+-----------+
10 rows in set (0.00 sec)

mysql> SELECT EMP_NAME,WEEK(JOINING_DATE) AS BIRTH_DAY FROM EMPLOYEE_ATTENDANCE;
+----------+-----------+
| EMP_NAME | BIRTH_DAY |
+----------+-----------+
| Rahul    |        24 |
| Sneha    |        11 |
| Arjun    |        31 |
| Priya    |         1 |
| Kiran    |        49 |
| Anjali   |        16 |
| Vijay    |        37 |
| Divya    |        41 |
| Ramesh   |        26 |
| Pooja    |        19 |
+----------+-----------+
10 rows in set (0.00 sec)

mysql> SELECT EMP_NAME,DAYOFWEEK(JOINING_DATE) AS BIRTH_DAY FROM EMPLOYEE_ATTENDANCE;
+----------+-----------+
| EMP_NAME | BIRTH_DAY |
+----------+-----------+
| Rahul    |         3 |
| Sneha    |         7 |
| Arjun    |         7 |
| Priya    |         4 |
| Kiran    |         3 |
| Anjali   |         2 |
| Vijay    |         3 |
| Divya    |         7 |
| Ramesh   |         7 |
| Pooja    |         2 |
+----------+-----------+
10 rows in set (0.00 sec)

mysql> SELECT EMP_NAME,DATE_ADD(JOINING_DATE,INTERVAL 30 DAY) AS BIRTH_DAY FROM EMPLOYEE_ATTENDANCE;
+----------+------------+
| EMP_NAME | BIRTH_DAY  |
+----------+------------+
| Rahul    | 2021-07-15 |
| Sneha    | 2020-04-20 |
| Arjun    | 2019-09-09 |
| Priya    | 2022-02-04 |
| Kiran    | 2019-01-10 |
| Anjali   | 2023-05-17 |
| Vijay    | 2021-10-14 |
| Divya    | 2019-11-18 |
| Ramesh   | 2017-07-31 |
| Pooja    | 2022-06-08 |
+----------+------------+
10 rows in set (0.00 sec)

mysql> SELECT EMP_NAME,DATEDIFF(JOINING_DATE,NOW()) AS BIRTH_DAY FROM EMPLOYEE_ATTENDANCE;
+----------+-----------+
| EMP_NAME | BIRTH_DAY |
+----------+-----------+
| Rahul    |     -1870 |
| Sneha    |     -2321 |
| Arjun    |     -2545 |
| Priya    |     -1666 |
| Kiran    |     -2787 |
| Anjali   |     -1199 |
| Vijay    |     -1779 |
| Divya    |     -2475 |
| Ramesh   |     -3315 |
| Pooja    |     -1542 |
+----------+-----------+
10 rows in set (0.00 sec)

mysql> SELECT EMP_NAME,DATEDIFF(NOW(),JOINING_DATE) AS BIRTH_DAY FROM EMPLOYEE_ATTENDANCE;
+----------+-----------+
| EMP_NAME | BIRTH_DAY |
+----------+-----------+
| Rahul    |      1870 |
| Sneha    |      2321 |
| Arjun    |      2545 |
| Priya    |      1666 |
| Kiran    |      2787 |
| Anjali   |      1199 |
| Vijay    |      1779 |
| Divya    |      2475 |
| Ramesh   |      3315 |
| Pooja    |      1542 |
+----------+-----------+
10 rows in set (0.00 sec)

mysql> SELECT EMP_NAME,DATEDIFF(LOGIN_TIME,LOGOUT_TIME) AS TIME_DIFF FROM EMPLOYEE_ATTENDANCE;
+----------+-----------+
| EMP_NAME | TIME_DIFF |
+----------+-----------+
| Rahul    |         0 |
| Sneha    |         0 |
| Arjun    |         0 |
| Priya    |         0 |
| Kiran    |         0 |
| Anjali   |         0 |
| Vijay    |         0 |
| Divya    |         0 |
| Ramesh   |         0 |
| Pooja    |         0 |
+----------+-----------+
10 rows in set (0.00 sec)

mysql> SELECT EMP_NAME,DATEDIFF(LOGIN_TIME,LOGOUT_TIME) AS TIME_DIFF FROM EMPLOYEE_ATTENDANCE;
+----------+-----------+
| EMP_NAME | TIME_DIFF |
+----------+-----------+
| Rahul    |         0 |
| Sneha    |         0 |
| Arjun    |         0 |
| Priya    |         0 |
| Kiran    |         0 |
| Anjali   |         0 |
| Vijay    |         0 |
| Divya    |         0 |
| Ramesh   |         0 |
| Pooja    |         0 |
+----------+-----------+
10 rows in set (0.00 sec)

mysql> SELECT EMP_NAME,LAST_DAY(JOINING_DATE) AS TIME_DIFF FROM EMPLOYEE_ATTENDANCE;
+----------+------------+
| EMP_NAME | TIME_DIFF  |
+----------+------------+
| Rahul    | 2021-06-30 |
| Sneha    | 2020-03-31 |
| Arjun    | 2019-08-31 |
| Priya    | 2022-01-31 |
| Kiran    | 2018-12-31 |
| Anjali   | 2023-04-30 |
| Vijay    | 2021-09-30 |
| Divya    | 2019-10-31 |
| Ramesh   | 2017-07-31 |
| Pooja    | 2022-05-31 |
+----------+------------+
10 rows in set (0.00 sec)

mysql> SELECT EMP_NAME,DATE_FORMAT(BIRTH_DATE,'%M,%D') AS MONTH_DAY_FORMAT FROM EMPLOYEE_ATTENDANCE;
+----------+------------------+
| EMP_NAME | MONTH_DAY_FORMAT |
+----------+------------------+
| Rahul    | May,10th         |
| Sneha    | November,18th    |
| Arjun    | July,30th        |
| Priya    | January,25th     |
| Kiran    | September,15th   |
| Anjali   | December,20th    |
| Vijay    | April,8th        |
| Divya    | June,11th        |
| Ramesh   | August,14th      |
| Pooja    | March,19th       |
+----------+------------------+
10 rows in set (0.00 sec)

mysql> SELECT * FROM EMPLOYEE_ATTENDANCE WHERE YEAR(JOINING_DATE) = CURYEAR;
ERROR 1054 (42S22): Unknown column 'CURYEAR' in 'where clause'
mysql> SELECT * FROM EMPLOYEE_ATTENDANCE WHERE YEAR(JOINING_DATE) = YEAR(NOW())
    -> ;
Empty set (0.01 sec)

mysql> SELECT * FROM EMPLOYEE_ATTENDANCE WHERE MONTH(BIRTH_DATE) = 11;
+--------+----------+------------+--------------+------------+---------------------+---------------------+----------+
| emp_id | emp_name | department | joining_date | birth_date | login_time          | logout_time         | salary   |
+--------+----------+------------+--------------+------------+---------------------+---------------------+----------+
|      2 | Sneha    | HR         | 2020-03-21   | 1996-11-18 | 2024-11-21 08:55:20 | 2024-11-21 17:45:50 | 48000.00 |
+--------+----------+------------+--------------+------------+---------------------+---------------------+----------+
1 row in set (0.00 sec)

mysql> SELECT * FROM EMPLOYEE_ATTENDANCE WHERE MONTH(JONING_DATE) = 6;
ERROR 1054 (42S22): Unknown column 'JONING_DATE' in 'where clause'
mysql> SELECT * FROM EMPLOYEE_ATTENDANCE WHERE MONTH(JOINING_DATE) = 6;
+--------+----------+------------+--------------+------------+---------------------+---------------------+----------+
| emp_id | emp_name | department | joining_date | birth_date | login_time          | logout_time         | salary   |
+--------+----------+------------+--------------+------------+---------------------+---------------------+----------+
|      1 | Rahul    | IT         | 2021-06-15   | 1998-05-10 | 2024-11-20 09:05:10 | 2024-11-20 18:15:30 | 55000.00 |
+--------+----------+------------+--------------+------------+---------------------+---------------------+----------+
1 row in set (0.00 sec)

mysql> SELECT * FROM EMPLOYEE_ATTENDANCE WHERE DAY(BIRTH_DATE) = 10;
+--------+----------+------------+--------------+------------+---------------------+---------------------+----------+
| emp_id | emp_name | department | joining_date | birth_date | login_time          | logout_time         | salary   |
+--------+----------+------------+--------------+------------+---------------------+---------------------+----------+
|      1 | Rahul    | IT         | 2021-06-15   | 1998-05-10 | 2024-11-20 09:05:10 | 2024-11-20 18:15:30 | 55000.00 |
+--------+----------+------------+--------------+------------+---------------------+---------------------+----------+
1 row in set (0.00 sec)

mysql> SELECT * FROM EMPLOYEE_ATTENDANCE WHERE QUARTER(JOINING_DATE) = 2;
+--------+----------+------------+--------------+------------+---------------------+---------------------+----------+
| emp_id | emp_name | department | joining_date | birth_date | login_time          | logout_time         | salary   |
+--------+----------+------------+--------------+------------+---------------------+---------------------+----------+
|      1 | Rahul    | IT         | 2021-06-15   | 1998-05-10 | 2024-11-20 09:05:10 | 2024-11-20 18:15:30 | 55000.00 |
|      6 | Anjali   | Testing    | 2023-04-17   | 1999-12-20 | 2024-11-25 09:12:10 | 2024-11-25 18:05:00 | 47000.00 |
|     10 | Pooja    | Testing    | 2022-05-09   | 2001-03-19 | 2024-11-29 09:18:50 | 2024-11-29 18:25:10 | 53000.00 |
+--------+----------+------------+--------------+------------+---------------------+---------------------+----------+
3 rows in set (0.00 sec)

mysql> SELECT * FROM EMPLOYEE_ATTENDANCE WHERE DATEDIFF(JOINING_DATE,NOW())>3;
Empty set (0.00 sec)

mysql> SELECT * FROM EMPLOYEE_ATTENDANCE WHERE DATEDIFF(NOW(),JOINING_DATE)>3;
+--------+----------+------------+--------------+------------+---------------------+---------------------+----------+
| emp_id | emp_name | department | joining_date | birth_date | login_time          | logout_time         | salary   |
+--------+----------+------------+--------------+------------+---------------------+---------------------+----------+
|      1 | Rahul    | IT         | 2021-06-15   | 1998-05-10 | 2024-11-20 09:05:10 | 2024-11-20 18:15:30 | 55000.00 |
|      2 | Sneha    | HR         | 2020-03-21   | 1996-11-18 | 2024-11-21 08:55:20 | 2024-11-21 17:45:50 | 48000.00 |
|      3 | Arjun    | Finance    | 2019-08-10   | 1994-07-30 | 2024-11-22 09:15:45 | 2024-11-22 18:35:20 | 62000.00 |
|      4 | Priya    | IT         | 2022-01-05   | 2000-01-25 | 2024-11-23 09:00:00 | 2024-11-23 17:55:40 | 51000.00 |
|      5 | Kiran    | Admin      | 2018-12-11   | 1992-09-15 | 2024-11-24 08:40:30 | 2024-11-24 17:30:00 | 45000.00 |
|      6 | Anjali   | Testing    | 2023-04-17   | 1999-12-20 | 2024-11-25 09:12:10 | 2024-11-25 18:05:00 | 47000.00 |
|      7 | Vijay    | IT         | 2021-09-14   | 1997-04-08 | 2024-11-26 09:08:15 | 2024-11-26 18:20:40 | 59000.00 |
|      8 | Divya    | HR         | 2019-10-19   | 1995-06-11 | 2024-11-27 08:50:30 | 2024-11-27 17:42:15 | 50000.00 |
|      9 | Ramesh   | Finance    | 2017-07-01   | 1991-08-14 | 2024-11-28 09:03:00 | 2024-11-28 18:12:00 | 70000.00 |
|     10 | Pooja    | Testing    | 2022-05-09   | 2001-03-19 | 2024-11-29 09:18:50 | 2024-11-29 18:25:10 | 53000.00 |
+--------+----------+------------+--------------+------------+---------------------+---------------------+----------+
10 rows in set (0.00 sec)

mysql> SELECT * FROM EMPLOYEE_ATTENDANCE WHERE TIMESTAMPDIFF(YEAR,JOINING_DATE,CUR_DATE)>3;
ERROR 1054 (42S22): Unknown column 'CUR_DATE' in 'where clause'
mysql> SELECT * FROM EMPLOYEE_ATTENDANCE WHERE TIMESTAMPDIFF(YEAR,JOINING_DATE,CURDATE)>3;
ERROR 1054 (42S22): Unknown column 'CURDATE' in 'where clause'
mysql> SELECT * FROM EMPLOYEE_ATTENDANCE WHERE TIMESTAMPDIFF(YEAR,JOINING_DATE,CURDATE())>3;
+--------+----------+------------+--------------+------------+---------------------+---------------------+----------+
| emp_id | emp_name | department | joining_date | birth_date | login_time          | logout_time         | salary   |
+--------+----------+------------+--------------+------------+---------------------+---------------------+----------+
|      1 | Rahul    | IT         | 2021-06-15   | 1998-05-10 | 2024-11-20 09:05:10 | 2024-11-20 18:15:30 | 55000.00 |
|      2 | Sneha    | HR         | 2020-03-21   | 1996-11-18 | 2024-11-21 08:55:20 | 2024-11-21 17:45:50 | 48000.00 |
|      3 | Arjun    | Finance    | 2019-08-10   | 1994-07-30 | 2024-11-22 09:15:45 | 2024-11-22 18:35:20 | 62000.00 |
|      4 | Priya    | IT         | 2022-01-05   | 2000-01-25 | 2024-11-23 09:00:00 | 2024-11-23 17:55:40 | 51000.00 |
|      5 | Kiran    | Admin      | 2018-12-11   | 1992-09-15 | 2024-11-24 08:40:30 | 2024-11-24 17:30:00 | 45000.00 |
|      7 | Vijay    | IT         | 2021-09-14   | 1997-04-08 | 2024-11-26 09:08:15 | 2024-11-26 18:20:40 | 59000.00 |
|      8 | Divya    | HR         | 2019-10-19   | 1995-06-11 | 2024-11-27 08:50:30 | 2024-11-27 17:42:15 | 50000.00 |
|      9 | Ramesh   | Finance    | 2017-07-01   | 1991-08-14 | 2024-11-28 09:03:00 | 2024-11-28 18:12:00 | 70000.00 |
|     10 | Pooja    | Testing    | 2022-05-09   | 2001-03-19 | 2024-11-29 09:18:50 | 2024-11-29 18:25:10 | 53000.00 |
+--------+----------+------------+--------------+------------+---------------------+---------------------+----------+
9 rows in set (0.00 sec)

mysql> SELECT EMP_NAME,TIMESTAMPDIFF(HOUR,LOGIN_TIME,LOGOUT_TIME) AS WORKING_HOURS FROM EMPLOYEE_ATTENDANCE;
+----------+---------------+
| EMP_NAME | WORKING_HOURS |
+----------+---------------+
| Rahul    |             9 |
| Sneha    |             8 |
| Arjun    |             9 |
| Priya    |             8 |
| Kiran    |             8 |
| Anjali   |             8 |
| Vijay    |             9 |
| Divya    |             8 |
| Ramesh   |             9 |
| Pooja    |             9 |
+----------+---------------+
10 rows in set (0.00 sec)

mysql> SELECT EMP_NAME,TIMESTAMPDIFF(MINUTE,LOGIN_TIME,LOGOUT_TIME) AS WORKING_MINUTES FROM EMPLOYEE_ATTENDANCE;
+----------+-----------------+
| EMP_NAME | WORKING_MINUTES |
+----------+-----------------+
| Rahul    |             550 |
| Sneha    |             530 |
| Arjun    |             559 |
| Priya    |             535 |
| Kiran    |             529 |
| Anjali   |             532 |
| Vijay    |             552 |
| Divya    |             531 |
| Ramesh   |             549 |
| Pooja    |             546 |
+----------+-----------------+
10 rows in set (0.00 sec)

mysql> SELECT EMP_NAME,LOGIN_TIME FROM EMPLOYEE_ATTENDANCE WHERE TIME(LOGIN_TIME) <'9:00:00';
+----------+---------------------+
| EMP_NAME | LOGIN_TIME          |
+----------+---------------------+
| Rahul    | 2024-11-20 09:05:10 |
| Sneha    | 2024-11-21 08:55:20 |
| Arjun    | 2024-11-22 09:15:45 |
| Priya    | 2024-11-23 09:00:00 |
| Kiran    | 2024-11-24 08:40:30 |
| Anjali   | 2024-11-25 09:12:10 |
| Vijay    | 2024-11-26 09:08:15 |
| Divya    | 2024-11-27 08:50:30 |
| Ramesh   | 2024-11-28 09:03:00 |
| Pooja    | 2024-11-29 09:18:50 |
+----------+---------------------+
10 rows in set (0.01 sec)

mysql> SELECT EMP_NAME,LOGIN_TIME FROM EMPLOYEE_ATTENDANCE WHERE TIME(LOGIN_TIME) >'9:10:00';
Empty set (0.00 sec)

mysql> SELECT EMP_NAME,LOGIN_TIME FROM EMPLOYEE_ATTENDANCE WHERE TIME(LOGIN_TIME) <'09:00:00';
+----------+---------------------+
| EMP_NAME | LOGIN_TIME          |
+----------+---------------------+
| Sneha    | 2024-11-21 08:55:20 |
| Kiran    | 2024-11-24 08:40:30 |
| Divya    | 2024-11-27 08:50:30 |
+----------+---------------------+
3 rows in set (0.00 sec)

mysql> SELECT EMP_NAME,LOGIN_TIME FROM EMPLOYEE_ATTENDANCE WHERE TIME(LOGIN_TIME) <'09:10:00';
+----------+---------------------+
| EMP_NAME | LOGIN_TIME          |
+----------+---------------------+
| Rahul    | 2024-11-20 09:05:10 |
| Sneha    | 2024-11-21 08:55:20 |
| Priya    | 2024-11-23 09:00:00 |
| Kiran    | 2024-11-24 08:40:30 |
| Vijay    | 2024-11-26 09:08:15 |
| Divya    | 2024-11-27 08:50:30 |
| Ramesh   | 2024-11-28 09:03:00 |
+----------+---------------------+
7 rows in set (0.00 sec)

mysql> SELECT EMP_NAME,LOGIN_TIME FROM EMPLOYEE_ATTENDANCE WHERE TIME(LOGIN_TIME) >'09:10:00';
+----------+---------------------+
| EMP_NAME | LOGIN_TIME          |
+----------+---------------------+
| Arjun    | 2024-11-22 09:15:45 |
| Anjali   | 2024-11-25 09:12:10 |
| Pooja    | 2024-11-29 09:18:50 |
+----------+---------------------+
3 rows in set (0.00 sec)

mysql> SELECT EMP_NAME,JOINING_DATE FROM EMPLOYEE_ATTENDANCE WHERE WEEKNAME(JOINING_DATE) = 'MONDAY';
ERROR 1305 (42000): FUNCTION pfs4.WEEKNAME does not exist
mysql> SELECT EMP_NAME,JOINING_DATE FROM EMPLOYEE_ATTENDANCE WHERE WEEK(JOINING_DATE) = 2;
Empty set (0.00 sec)

mysql> SELECT EMP_NAME,JOINING_DATE FROM EMPLOYEE_ATTENDANCE WHERE DAYOFWEEK(JOINING_DATE) = 2;
+----------+--------------+
| EMP_NAME | JOINING_DATE |
+----------+--------------+
| Anjali   | 2023-04-17   |
| Pooja    | 2022-05-09   |
+----------+--------------+
2 rows in set (0.00 sec)

mysql> SELECT EMP_NAME,BIRTH_DATE FROM EMPLOYEE_ATTENDANCE WHERE MONTHNAME(BIRTH_DATE) LIKE 'J%';
+----------+------------+
| EMP_NAME | BIRTH_DATE |
+----------+------------+
| Arjun    | 1994-07-30 |
| Priya    | 2000-01-25 |
| Divya    | 1995-06-11 |
+----------+------------+
3 rows in set (0.00 sec)

mysql> SELECT EMP_NAME,JOINING_DATE FROM EMPLOYEE_ATTENDANCE WHERE WEEK(JOINING_DATE) = 25;
Empty set (0.00 sec)

mysql> SELECT EMP_NAME,LAST_DAY(BIRTH_DATE) AS LAST_DAY_BDAY FROM EMPLOYEE_ATTENDANCE;
+----------+---------------+
| EMP_NAME | LAST_DAY_BDAY |
+----------+---------------+
| Rahul    | 1998-05-31    |
| Sneha    | 1996-11-30    |
| Arjun    | 1994-07-31    |
| Priya    | 2000-01-31    |
| Kiran    | 1992-09-30    |
| Anjali   | 1999-12-31    |
| Vijay    | 1997-04-30    |
| Divya    | 1995-06-30    |
| Ramesh   | 1991-08-31    |
| Pooja    | 2001-03-31    |
+----------+---------------+
10 rows in set (0.00 sec)

JOINS
======
A join in MySQL is used to combine rows from two or more tables based on related columns.

example:
========
employee-table ---> employee details
department-table --> department details
if you want to see which employee belongings to which department you need to join these two tables.

why do we need joins?
=====================
1. to fetch data from multiple tables in a single query.
2. to reduce data duplication(instead of keeping everything one table.)
3. to implement relationships like (one-to-one, one-to-many, many-to-many,many-to-one) in databases
4. to generate reports and analytics combing different datasets.mysql> Terminal close -- exit!
