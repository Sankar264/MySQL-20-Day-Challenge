mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| college            |
| company            |
| db4                |
| details            |
| information_schema |
| mysql              |
| performance_schema |
| practice           |
| psf4               |
| school1            |
| student            |
| students           |
| sys                |
| walmartsales       |
| xyz                |
+--------------------+
15 rows in set (0.09 sec)

mysql> use db4;
Database changed
mysql> SHOW TABLES;
+-----------------+
| Tables_in_db4   |
+-----------------+
| backupemp       |
| company_staff   |
| emp             |
| emp2            |
| emp_3           |
| employees       |
| orders          |
| placed_students |
| product_        |
| products        |
| projects        |
| sales           |
| students        |
| studentscores   |
+-----------------+
14 rows in set (0.02 sec)

mysql> -- NUMERIC FUNCTIONS
mysql> SELECT ABS(-100) AS ABSOLUTE_VALUE;
+----------------+
| ABSOLUTE_VALUE |
+----------------+
|            100 |
+----------------+
1 row in set (0.02 sec)

mysql> SELECT CEIL(12.34) AS ROUNDED_DOW;
+-------------+
| ROUNDED_DOW |
+-------------+
|          13 |
+-------------+
1 row in set (0.01 sec)

mysql> SELECT FLOOR(12.34) AS ROUNDED_UP;
+------------+
| ROUNDED_UP |
+------------+
|         12 |
+------------+
1 row in set (0.01 sec)

mysql> SELECT ROUND(12.34567,3) AS ROUNDED_VALUE;
+---------------+
| ROUNDED_VALUE |
+---------------+
|        12.346 |
+---------------+
1 row in set (0.01 sec)

mysql> SELECT MOD(19,4) AS REMINDER;
+----------+
| REMINDER |
+----------+
|        3 |
+----------+
1 row in set (0.00 sec)

mysql> SELECT POW(5,4) AS POWER_VALUE;
+-------------+
| POWER_VALUE |
+-------------+
|         625 |
+-------------+
1 row in set (0.02 sec)

mysql> SELECT SQRT(16) AS SQUARE_ROOT;
+-------------+
| SQUARE_ROOT |
+-------------+
|           4 |
+-------------+
1 row in set (0.00 sec)

mysql> SELECT LOG(10) AS LOG_VALUE;
+-------------------+
| LOG_VALUE         |
+-------------------+
| 2.302585092994046 |
+-------------------+
1 row in set (0.01 sec)

mysql> SELECT LOG(10,100) AS LOG_VALUE;
+-----------+
| LOG_VALUE |
+-----------+
|         2 |
+-----------+
1 row in set (0.00 sec)

mysql> --CONVERTING DEGREE TO RADIANS
    -> SELECT RADIANS(180) AS RADIANS_VALUE;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '--CONVERTING DEGREE TO RADIANS
SELECT RADIANS(180) AS RADIANS_VALUE' at line 1
mysql> SELECT RADIANS(180) AS RADIANS_VALUE;
+-------------------+
| RADIANS_VALUE     |
+-------------------+
| 3.141592653589793 |
+-------------------+
1 row in set (0.01 sec)

mysql> -- RADIANS TO DEGREES
mysql> SELECT DEGREES(PI()) AS DEGREE_VALUE;
+--------------+
| DEGREE_VALUE |
+--------------+
|          180 |
+--------------+
1 row in set (0.01 sec)

mysql> -- SIGN()- RETURNS THE SIGN OF A NUMBER
mysql> -- 1 FOR POSITIVE NUMBER
mysql> -- -1 FOR NEGATIVE NUMBERS
mysql> -- 0 FOR ZERO
mysql> SELECT SIGN(-129) AS SIGN_VALUE;
+------------+
| SIGN_VALUE |
+------------+
|         -1 |
+------------+
1 row in set (0.00 sec)

mysql> SELECT SIGN(34) AS SIGN_VALUE;
+------------+
| SIGN_VALUE |
+------------+
|          1 |
+------------+
1 row in set (0.00 sec)

mysql> SELECT SIGN(0) AS SIGN_VALUE;
+------------+
| SIGN_VALUE |
+------------+
|          0 |
+------------+
1 row in set (0.00 sec)

mysql> -- RAND()- GENERATES A RANDOM NUMBER
mysql> SELECT RAND() AS RANDOM_NUMBER;
+---------------------+
| RANDOM_NUMBER       |
+---------------------+
| 0.11553882166327799 |
+---------------------+
1 row in set (0.01 sec)

mysql> SELECT RAND() AS RANDOM_NUMBER;
+--------------------+
| RANDOM_NUMBER      |
+--------------------+
| 0.6083040867078157 |
+--------------------+
1 row in set (0.00 sec)

mysql> SELECT RAND() AS RANDOM_NUMBER;
+-------------------+
| RANDOM_NUMBER     |
+-------------------+
| 0.694903999282889 |
+-------------------+
1 row in set (0.00 sec)

mysql> -- GREATEST()- FIND THE MAX VALUE
mysql> SELECT GREATEST(3,6,8) AS GREATEST_VALUE;
+----------------+
| GREATEST_VALUE |
+----------------+
|              8 |
+----------------+
1 row in set (0.01 sec)

mysql> -- LEAST() - FINDS SMALL VAL AMONG VALUES
mysql> SELECT LEAST(3,6,8) AS GREATEST_VALUE;
+----------------+
| GREATEST_VALUE |
+----------------+
|              3 |
+----------------+
1 row in set (0.00 sec)

mysql> -- PI()- RETURNS A PI VALUE
mysql> SELECT PI() AS PI_VALUE;
+----------+
| PI_VALUE |
+----------+
| 3.141593 |
+----------+
1 row in set (0.00 sec)

mysql> -- TRUNCATE()
mysql> SELECT TRUNCATE(12.4566,3) AS TRUNCATE_VALUE;
+----------------+
| TRUNCATE_VALUE |
+----------------+
|         12.456 |
+----------------+
1 row in set (0.00 sec)

mysql> SELECT TRUNCATE(12.4566,2) AS TRUNCATE_VALUE;
+----------------+
| TRUNCATE_VALUE |
+----------------+
|          12.45 |
+----------------+
1 row in set (0.00 sec)

mysql> -- LOG2() - RETURNS THE BASE-2 LOG NUM
mysql> SELECT LOG2(8) AS LOG2_VALUE;
+------------+
| LOG2_VALUE |
+------------+
|          3 |
+------------+
1 row in set (0.00 sec)

mysql> SELECT LOG10(8) AS LOG2_VALUE;
+--------------------+
| LOG2_VALUE         |
+--------------------+
| 0.9030899869919435 |
+--------------------+
1 row in set (0.01 sec)

mysql> SELECT LOG10(1000) AS LOG10_VALUE;
+-------------+
| LOG10_VALUE |
+-------------+
|           3 |
+-------------+
1 row in set (0.00 sec)

mysql> -- BIT_COUNT() -- TELLS HOW MANY BITS
mysql> SELECT BIT_COUNT(8) AS BITS_COUNT;
+------------+
| BITS_COUNT |
+------------+
|          1 |
+------------+
1 row in set (0.00 sec)

mysql> SELECT BIT_COUNT(8) AS SET_BITS_COUNT;
+----------------+
| SET_BITS_COUNT |
+----------------+
|              1 |
+----------------+
1 row in set (0.00 sec)

mysql> SELECT BIT_COUNT(15) AS SET_BITS_COUNT;
+----------------+
| SET_BITS_COUNT |
+----------------+
|              4 |
+----------------+
1 row in set (0.00 sec)

mysql> -- OCT()- CONVERT INTO OCTAL NUM
mysql> SELECT OCT(64) AS OCTAL_NUMBER;
+--------------+
| OCTAL_NUMBER |
+--------------+
| 100          |
+--------------+
1 row in set (0.02 sec)

mysql> SELECT BIN(10) AS BINARY_NUMBER;
+---------------+
| BINARY_NUMBER |
+---------------+
| 1010          |
+---------------+
1 row in set (0.01 sec)

mysql> drop table employees;
Query OK, 0 rows affected (0.29 sec)

mysql> CREATE TABLE employees (
    -> 	emp_id INT PRIMARY KEY,
    -> 	first_name VARCHAR(30),
    -> 	last_name VARCHAR(30),
    -> 	email VARCHAR(60),
    -> 	phone_number VARCHAR(20),
    -> 	department VARCHAR(30),
    -> 	city VARCHAR(30),
    -> 	salary DECIMAL(10,2)
    -> );
Query OK, 0 rows affected (0.13 sec)

mysql> 
mysql> 
mysql> INSERT INTO employees VALUES
    -> (101,'Rahul','Kumar','rahul.kumar@gmail.com','987-654-3210','IT','Hyderabad',45000),
    -> (102,'Anita','Sharma','anita.sharma@yahoo.com','912-345-6789','HR','Bangalore',38000),
    -> (103,'Suresh','Verma','suresh.verma@gmail.com','998-123-4567','Sales','Chennai',52000),
    -> (104,'Priya','Singh','priya.singh@outlook.com','900-456-7890','Finance','Pune',47000),
    -> (105,'Rahul','Joshi','rahul.joshi@gmail.com','955-888-1111','Testing','Delhi',41000),
    -> (106,'Kiran','Reddy','kiran.reddy@gmail.com','901-222-3333','IT','Hyderabad',56000),
    -> (107,'Deepika','Naidu','deepika.naidu@yahoo.com','944-111-2222','HR','Vizag',39000),
    -> (108,'Mahesh','Patel','mahesh.patel@gmail.com','933-444-5555','Sales','Mumbai',62000),
    -> (109,'Divya','Gupta','divya.gupta@gmail.com','955-777-8888','Finance','Delhi',49000),
    -> (110,'Arjun','Rao','arjun.rao@gmail.com','988-999-7777','Developer','Hyderabad',68000);
Query OK, 10 rows affected (0.03 sec)
Records: 10  Duplicates: 0  Warnings: 0

mysql> SELECT*FROM EMPLOYEES;
+--------+------------+-----------+-------------------------+--------------+------------+-----------+----------+
| emp_id | first_name | last_name | email                   | phone_number | department | city      | salary   |
+--------+------------+-----------+-------------------------+--------------+------------+-----------+----------+
|    101 | Rahul      | Kumar     | rahul.kumar@gmail.com   | 987-654-3210 | IT         | Hyderabad | 45000.00 |
|    102 | Anita      | Sharma    | anita.sharma@yahoo.com  | 912-345-6789 | HR         | Bangalore | 38000.00 |
|    103 | Suresh     | Verma     | suresh.verma@gmail.com  | 998-123-4567 | Sales      | Chennai   | 52000.00 |
|    104 | Priya      | Singh     | priya.singh@outlook.com | 900-456-7890 | Finance    | Pune      | 47000.00 |
|    105 | Rahul      | Joshi     | rahul.joshi@gmail.com   | 955-888-1111 | Testing    | Delhi     | 41000.00 |
|    106 | Kiran      | Reddy     | kiran.reddy@gmail.com   | 901-222-3333 | IT         | Hyderabad | 56000.00 |
|    107 | Deepika    | Naidu     | deepika.naidu@yahoo.com | 944-111-2222 | HR         | Vizag     | 39000.00 |
|    108 | Mahesh     | Patel     | mahesh.patel@gmail.com  | 933-444-5555 | Sales      | Mumbai    | 62000.00 |
|    109 | Divya      | Gupta     | divya.gupta@gmail.com   | 955-777-8888 | Finance    | Delhi     | 49000.00 |
|    110 | Arjun      | Rao       | arjun.rao@gmail.com     | 988-999-7777 | Developer  | Hyderabad | 68000.00 |
+--------+------------+-----------+-------------------------+--------------+------------+-----------+----------+
10 rows in set (0.00 sec)

mysql> -- DISPLAY FULLNAME BY CONCATINATIONG FIRSTNAME AND LASTNAME
mysql> SELECT FIRST_NAME,LAST_NAME,CONCAT(FIRST_NAME,' ',LAST_NAME) AS FULLNAME FROM EMPLOYEES;
+------------+-----------+---------------+
| FIRST_NAME | LAST_NAME | FULLNAME      |
+------------+-----------+---------------+
| Rahul      | Kumar     | Rahul Kumar   |
| Anita      | Sharma    | Anita Sharma  |
| Suresh     | Verma     | Suresh Verma  |
| Priya      | Singh     | Priya Singh   |
| Rahul      | Joshi     | Rahul Joshi   |
| Kiran      | Reddy     | Kiran Reddy   |
| Deepika    | Naidu     | Deepika Naidu |
| Mahesh     | Patel     | Mahesh Patel  |
| Divya      | Gupta     | Divya Gupta   |
| Arjun      | Rao       | Arjun Rao     |
+------------+-----------+---------------+
10 rows in set (0.01 sec)

mysql> -- CONVERT FIRST_NAME TO UPPERCASE
mysql> SELECT FIRST_NAME,UPPER(FIRST_NAME) AS UPPERCASE_NAME FROM EMPLOYEES;
+------------+----------------+
| FIRST_NAME | UPPERCASE_NAME |
+------------+----------------+
| Rahul      | RAHUL          |
| Anita      | ANITA          |
| Suresh     | SURESH         |
| Priya      | PRIYA          |
| Rahul      | RAHUL          |
| Kiran      | KIRAN          |
| Deepika    | DEEPIKA        |
| Mahesh     | MAHESH         |
| Divya      | DIVYA          |
| Arjun      | ARJUN          |
+------------+----------------+
10 rows in set (0.02 sec)

mysql> SELECT LAST_NAME,LOWER(LAST_NAME) AS LOWERCASE_NAME FROM EMPLOYEES;
+-----------+----------------+
| LAST_NAME | LOWERCASE_NAME |
+-----------+----------------+
| Kumar     | kumar          |
| Sharma    | sharma         |
| Verma     | verma          |
| Singh     | singh          |
| Joshi     | joshi          |
| Reddy     | reddy          |
| Naidu     | naidu          |
| Patel     | patel          |
| Gupta     | gupta          |
| Rao       | rao            |
+-----------+----------------+
10 rows in set (0.01 sec)

mysql> -- EXTRACT THE FIRST 10 CHRACTERS OF EMAIL
mysql> SELECT EMAIL,SUBSTRING(EMAIL,1,10) AS EMAIL_PREFIX FROM EMPLOYEES;
+-------------------------+--------------+
| EMAIL                   | EMAIL_PREFIX |
+-------------------------+--------------+
| rahul.kumar@gmail.com   | rahul.kuma   |
| anita.sharma@yahoo.com  | anita.shar   |
| suresh.verma@gmail.com  | suresh.ver   |
| priya.singh@outlook.com | priya.sing   |
| rahul.joshi@gmail.com   | rahul.josh   |
| kiran.reddy@gmail.com   | kiran.redd   |
| deepika.naidu@yahoo.com | deepika.na   |
| mahesh.patel@gmail.com  | mahesh.pat   |
| divya.gupta@gmail.com   | divya.gupt   |
| arjun.rao@gmail.com     | arjun.rao@   |
+-------------------------+--------------+
10 rows in set (0.01 sec)

mysql> SELECT EMAIL,SUBSTRING(EMAIL,1,11) AS EMAIL_PREFIX FROM EMPLOYEES;
+-------------------------+--------------+
| EMAIL                   | EMAIL_PREFIX |
+-------------------------+--------------+
| rahul.kumar@gmail.com   | rahul.kumar  |
| anita.sharma@yahoo.com  | anita.sharm  |
| suresh.verma@gmail.com  | suresh.verm  |
| priya.singh@outlook.com | priya.singh  |
| rahul.joshi@gmail.com   | rahul.joshi  |
| kiran.reddy@gmail.com   | kiran.reddy  |
| deepika.naidu@yahoo.com | deepika.nai  |
| mahesh.patel@gmail.com  | mahesh.pate  |
| divya.gupta@gmail.com   | divya.gupta  |
| arjun.rao@gmail.com     | arjun.rao@g  |
+-------------------------+--------------+
10 rows in set (0.00 sec)

mysql> -- LENGTH OF FIRSTNAME
mysql> SELECT FIRST_NAME, LENGTH(FIRST_NAME) AS LEN_OF_FIRSTNAME FROM EMPLOYEES;
+------------+------------------+
| FIRST_NAME | LEN_OF_FIRSTNAME |
+------------+------------------+
| Rahul      |                5 |
| Anita      |                5 |
| Suresh     |                6 |
| Priya      |                5 |
| Rahul      |                5 |
| Kiran      |                5 |
| Deepika    |                7 |
| Mahesh     |                6 |
| Divya      |                5 |
| Arjun      |                5 |
+------------+------------------+
10 rows in set (0.01 sec)

mysql> -- REMOVE '-' FROM PHN NUM
mysql> SELECT PHONE_NUMBER, REPLACE(PHONE_NUMBER,'-','') AS PHN_NUM FROM EMPLOYEES;
+--------------+------------+
| PHONE_NUMBER | PHN_NUM    |
+--------------+------------+
| 987-654-3210 | 9876543210 |
| 912-345-6789 | 9123456789 |
| 998-123-4567 | 9981234567 |
| 900-456-7890 | 9004567890 |
| 955-888-1111 | 9558881111 |
| 901-222-3333 | 9012223333 |
| 944-111-2222 | 9441112222 |
| 933-444-5555 | 9334445555 |
| 955-777-8888 | 9557778888 |
| 988-999-7777 | 9889997777 |
+--------------+------------+
10 rows in set (0.01 sec)

mysql> -- REMOVE LEADING AND TRAILING SPACES FROM THE FIRST_NAME
mysql> SELECT TRIM(FIRST_NAME) AS TRIMMED_NAME FROM EMPLOYEES;
+--------------+
| TRIMMED_NAME |
+--------------+
| Rahul        |
| Anita        |
| Suresh       |
| Priya        |
| Rahul        |
| Kiran        |
| Deepika      |
| Mahesh       |
| Divya        |
| Arjun        |
+--------------+
10 rows in set (0.01 sec)

mysql> -- CONCATINATE FIRST_NAME,LAST_NAME,EMAIL SEPERATED BT COMMA(,)
mysql> SELECT CONCAT_WS(',', FIRST_NAME,LAST_NAME,EMAIL)AS EMPLOYEE_INFO FROM EMPLOYEES;
+---------------------------------------+
| EMPLOYEE_INFO                         |
+---------------------------------------+
| Rahul,Kumar,rahul.kumar@gmail.com     |
| Anita,Sharma,anita.sharma@yahoo.com   |
| Suresh,Verma,suresh.verma@gmail.com   |
| Priya,Singh,priya.singh@outlook.com   |
| Rahul,Joshi,rahul.joshi@gmail.com     |
| Kiran,Reddy,kiran.reddy@gmail.com     |
| Deepika,Naidu,deepika.naidu@yahoo.com |
| Mahesh,Patel,mahesh.patel@gmail.com   |
| Divya,Gupta,divya.gupta@gmail.com     |
| Arjun,Rao,arjun.rao@gmail.com         |
+---------------------------------------+
10 rows in set (0.01 sec)

mysql> -- FIND THE POSITION OF THE LETTER IN FIRST_NAME USING POSITION()
mysql> SELECT FIRST_NAME , POSITION('A' IN FIRST_NAME) AS POSITION_OF_A FROM EMPLOYEES;
+------------+---------------+
| FIRST_NAME | POSITION_OF_A |
+------------+---------------+
| Rahul      |             2 |
| Anita      |             1 |
| Suresh     |             0 |
| Priya      |             5 |
| Rahul      |             2 |
| Kiran      |             4 |
| Deepika    |             7 |
| Mahesh     |             2 |
| Divya      |             5 |
| Arjun      |             1 |
+------------+---------------+
10 rows in set (0.01 sec)

mysql> -- DISPLAY THE FIRST 3 CHAR OF FIRST_NAME
mysql> SELECT FIRST_NAME,LEFT(FIRST_NAME,3) AS SHORT_NAME FROM EMPLOYEES;
+------------+------------+
| FIRST_NAME | SHORT_NAME |
+------------+------------+
| Rahul      | Rah        |
| Anita      | Ani        |
| Suresh     | Sur        |
| Priya      | Pri        |
| Rahul      | Rah        |
| Kiran      | Kir        |
| Deepika    | Dee        |
| Mahesh     | Mah        |
| Divya      | Div        |
| Arjun      | Arj        |
+------------+------------+
10 rows in set (0.01 sec)

mysql> SELECT FIRST_NAME,RIGHT(FIRST_NAME,3) AS SHORT_NAME FROM EMPLOYEES;
+------------+------------+
| FIRST_NAME | SHORT_NAME |
+------------+------------+
| Rahul      | hul        |
| Anita      | ita        |
| Suresh     | esh        |
| Priya      | iya        |
| Rahul      | hul        |
| Kiran      | ran        |
| Deepika    | ika        |
| Mahesh     | esh        |
| Divya      | vya        |
| Arjun      | jun        |
+------------+------------+
10 rows in set (0.00 sec)

mysql> -- DISPLAY THE LAST 3 CHAR FROM LAST_NAME 
mysql> SELECT LAST_NAME,RIGHT(LAST_NAME,3) AS SHORT_NAME FROM EMPLOYEES;
+-----------+------------+
| LAST_NAME | SHORT_NAME |
+-----------+------------+
| Kumar     | mar        |
| Sharma    | rma        |
| Verma     | rma        |
| Singh     | ngh        |
| Joshi     | shi        |
| Reddy     | ddy        |
| Naidu     | idu        |
| Patel     | tel        |
| Gupta     | pta        |
| Rao       | Rao        |
+-----------+------------+
10 rows in set (0.00 sec)

mysql> -- REVERSE THE FIRST_NAME
mysql> SELECT FIRST_NAME,REVERSE(FIRST_NAME) AS REV_NAME FROM EMPLOYEES;
+------------+----------+
| FIRST_NAME | REV_NAME |
+------------+----------+
| Rahul      | luhaR    |
| Anita      | atinA    |
| Suresh     | hseruS   |
| Priya      | ayirP    |
| Rahul      | luhaR    |
| Kiran      | nariK    |
| Deepika    | akipeeD  |
| Mahesh     | hsehaM   |
| Divya      | ayviD    |
| Arjun      | nujrA    |
+------------+----------+
10 rows in set (0.01 sec)

mysql> -- PAD FIRSTNAME OF THE LEFT WITH * TO MAKE IT 10 CHARACTERS
mysql> SELECT FIRST_NAME,LPAD(FIRST_NAME,10,'*') AS PADDED_NAME FROM EMPLOEES;
ERROR 1146 (42S02): Table 'db4.emploees' doesn't exist
mysql> 
mysql> ^C
mysql> SELECT FIRST_NAME,LPAD(FIRST_NAME,10,'*') AS PADDED_NAME FROM EMPLOYEES;
+------------+-------------+
| FIRST_NAME | PADDED_NAME |
+------------+-------------+
| Rahul      | *****Rahul  |
| Anita      | *****Anita  |
| Suresh     | ****Suresh  |
| Priya      | *****Priya  |
| Rahul      | *****Rahul  |
| Kiran      | *****Kiran  |
| Deepika    | ***Deepika  |
| Mahesh     | ****Mahesh  |
| Divya      | *****Divya  |
| Arjun      | *****Arjun  |
+------------+-------------+
10 rows in set (0.00 sec)

mysql> SELECT FIRST_NAME,LPAD(FIRST_NAME,10,'') AS PADDED_NAME FROM EMPLOYEES;
+------------+-------------+
| FIRST_NAME | PADDED_NAME |
+------------+-------------+
| Rahul      |             |
| Anita      |             |
| Suresh     |             |
| Priya      |             |
| Rahul      |             |
| Kiran      |             |
| Deepika    |             |
| Mahesh     |             |
| Divya      |             |
| Arjun      |             |
+------------+-------------+
10 rows in set (0.00 sec)

mysql> SELECT FIRST_NAME,LPAD(FIRST_NAME,10) AS PADDED_NAME FROM EMPLOYEES;
ERROR 1582 (42000): Incorrect parameter count in the call to native function 'LPAD'
mysql> SELECT FIRST_NAME,LPAD(FIRST_NAME,10,'@') AS PADDED_NAME FROM EMPLOYEES;
+------------+-------------+
| FIRST_NAME | PADDED_NAME |
+------------+-------------+
| Rahul      | @@@@@Rahul  |
| Anita      | @@@@@Anita  |
| Suresh     | @@@@Suresh  |
| Priya      | @@@@@Priya  |
| Rahul      | @@@@@Rahul  |
| Kiran      | @@@@@Kiran  |
| Deepika    | @@@Deepika  |
| Mahesh     | @@@@Mahesh  |
| Divya      | @@@@@Divya  |
| Arjun      | @@@@@Arjun  |
+------------+-------------+
10 rows in set (0.00 sec)

mysql> SELECT FIRST_NAME,RPAD(FIRST_NAME,10,'@') AS PADDED_NAME FROM EMPLOYEES;
+------------+-------------+
| FIRST_NAME | PADDED_NAME |
+------------+-------------+
| Rahul      | Rahul@@@@@  |
| Anita      | Anita@@@@@  |
| Suresh     | Suresh@@@@  |
| Priya      | Priya@@@@@  |
| Rahul      | Rahul@@@@@  |
| Kiran      | Kiran@@@@@  |
| Deepika    | Deepika@@@  |
| Mahesh     | Mahesh@@@@  |
| Divya      | Divya@@@@@  |
| Arjun      | Arjun@@@@@  |
+------------+-------------+
10 rows in set (0.00 sec)

mysql> -- ASCII CHAR OF A FIRST CHAR IN FIRST_NAME
mysql> SELECT FIRST_NAME,ASCII(FIRST_NAME) AS ASCII_VALUE FROM EMPLOYEES;
+------------+-------------+
| FIRST_NAME | ASCII_VALUE |
+------------+-------------+
| Rahul      |          82 |
| Anita      |          65 |
| Suresh     |          83 |
| Priya      |          80 |
| Rahul      |          82 |
| Kiran      |          75 |
| Deepika    |          68 |
| Mahesh     |          77 |
| Divya      |          68 |
| Arjun      |          65 |
+------------+-------------+
10 rows in set (0.00 sec)

mysql> -- FIND THE CHAR LENGTH OF LASTNAME
mysql> SELECT LAST_NAME , CHAR_LENGTH(LAST_NAME) AS CHAR_NAME FROM EMPLOYEES;
+-----------+-----------+
| LAST_NAME | CHAR_NAME |
+-----------+-----------+
| Kumar     |         5 |
| Sharma    |         6 |
| Verma     |         5 |
| Singh     |         5 |
| Joshi     |         5 |
| Reddy     |         5 |
| Naidu     |         5 |
| Patel     |         5 |
| Gupta     |         5 |
| Rao       |         3 |
+-----------+-----------+
10 rows in set (0.01 sec)

mysql> -- FIND EMPLOYEES WHOSE FIRST NAME STARTS WITH 'R'
mysql> SELECT *FROM EMPLOYEES
    -> WHERE FIRST_NAME LIKE'R%';
+--------+------------+-----------+-----------------------+--------------+------------+-----------+----------+
| emp_id | first_name | last_name | email                 | phone_number | department | city      | salary   |
+--------+------------+-----------+-----------------------+--------------+------------+-----------+----------+
|    101 | Rahul      | Kumar     | rahul.kumar@gmail.com | 987-654-3210 | IT         | Hyderabad | 45000.00 |
|    105 | Rahul      | Joshi     | rahul.joshi@gmail.com | 955-888-1111 | Testing    | Delhi     | 41000.00 |
+--------+------------+-----------+-----------------------+--------------+------------+-----------+----------+
2 rows in set (0.01 sec)

mysql> SELECT * FROM EMPLOYEE 
    -> WHERE POSITION('YAHOO' IN EMAIL);
ERROR 1146 (42S02): Table 'db4.employee' doesn't exist
mysql> SELECT * FROM EMPLOYEES 
    -> WHERE POSITION('YAHOO' IN EMAIL);
+--------+------------+-----------+-------------------------+--------------+------------+-----------+----------+
| emp_id | first_name | last_name | email                   | phone_number | department | city      | salary   |
+--------+------------+-----------+-------------------------+--------------+------------+-----------+----------+
|    102 | Anita      | Sharma    | anita.sharma@yahoo.com  | 912-345-6789 | HR         | Bangalore | 38000.00 |
|    107 | Deepika    | Naidu     | deepika.naidu@yahoo.com | 944-111-2222 | HR         | Vizag     | 39000.00 |
+--------+------------+-----------+-------------------------+--------------+------------+-----------+----------+
2 rows in set (0.00 sec)

mysql> SELECT FIRST_NAME,LAST_NAME,DEPARTMENT,CONCAT(FIRST_NAME,LAST_NAME,DEPARTMENT) AS NEW_STRING FROM EMPLOYEES;
+------------+-----------+------------+-------------------+
| FIRST_NAME | LAST_NAME | DEPARTMENT | NEW_STRING        |
+------------+-----------+------------+-------------------+
| Rahul      | Kumar     | IT         | RahulKumarIT      |
| Anita      | Sharma    | HR         | AnitaSharmaHR     |
| Suresh     | Verma     | Sales      | SureshVermaSales  |
| Priya      | Singh     | Finance    | PriyaSinghFinance |
| Rahul      | Joshi     | Testing    | RahulJoshiTesting |
| Kiran      | Reddy     | IT         | KiranReddyIT      |
| Deepika    | Naidu     | HR         | DeepikaNaiduHR    |
| Mahesh     | Patel     | Sales      | MaheshPatelSales  |
| Divya      | Gupta     | Finance    | DivyaGuptaFinance |
| Arjun      | Rao       | Developer  | ArjunRaoDeveloper |
+------------+-----------+------------+-------------------+
10 rows in set (0.00 sec)

mysql> SELECT EMAIL, LENGTH(EMAIL) AS LEN FROM EMPLOYEES;
+-------------------------+------+
| EMAIL                   | LEN  |
+-------------------------+------+
| rahul.kumar@gmail.com   |   21 |
| anita.sharma@yahoo.com  |   22 |
| suresh.verma@gmail.com  |   22 |
| priya.singh@outlook.com |   23 |
| rahul.joshi@gmail.com   |   21 |
| kiran.reddy@gmail.com   |   21 |
| deepika.naidu@yahoo.com |   23 |
| mahesh.patel@gmail.com  |   22 |
| divya.gupta@gmail.com   |   21 |
| arjun.rao@gmail.com     |   19 |
+-------------------------+------+
10 rows in set (0.00 sec)

mysql> SELECT * FROM EMPLOYEES
    -> WHERE LENGTH(FIRST_NAME)>5;
+--------+------------+-----------+-------------------------+--------------+------------+---------+----------+
| emp_id | first_name | last_name | email                   | phone_number | department | city    | salary   |
+--------+------------+-----------+-------------------------+--------------+------------+---------+----------+
|    103 | Suresh     | Verma     | suresh.verma@gmail.com  | 998-123-4567 | Sales      | Chennai | 52000.00 |
|    107 | Deepika    | Naidu     | deepika.naidu@yahoo.com | 944-111-2222 | HR         | Vizag   | 39000.00 |
|    108 | Mahesh     | Patel     | mahesh.patel@gmail.com  | 933-444-5555 | Sales      | Mumbai  | 62000.00 |
+--------+------------+-----------+-------------------------+--------------+------------+---------+----------+
3 rows in set (0.01 sec)

mysql> SELECT EMAIL,REPLACE(EMAIL,'GMAIL.COM','COMPANY.COM') AS NEW_MAIL FROM EMPLOYEES;
+-------------------------+-------------------------+
| EMAIL                   | NEW_MAIL                |
+-------------------------+-------------------------+
| rahul.kumar@gmail.com   | rahul.kumar@gmail.com   |
| anita.sharma@yahoo.com  | anita.sharma@yahoo.com  |
| suresh.verma@gmail.com  | suresh.verma@gmail.com  |
| priya.singh@outlook.com | priya.singh@outlook.com |
| rahul.joshi@gmail.com   | rahul.joshi@gmail.com   |
| kiran.reddy@gmail.com   | kiran.reddy@gmail.com   |
| deepika.naidu@yahoo.com | deepika.naidu@yahoo.com |
| mahesh.patel@gmail.com  | mahesh.patel@gmail.com  |
| divya.gupta@gmail.com   | divya.gupta@gmail.com   |
| arjun.rao@gmail.com     | arjun.rao@gmail.com     |
+-------------------------+-------------------------+
10 rows in set (0.00 sec)

mysql> SELECT EMAIL,POSITION('@' IN EMAIL) AS POSITION_@ FROM EMPLOYEES;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '@ FROM EMPLOYEES' at line 1
mysql> SELECT EMAIL,POSITION('@' IN EMAIL) AS POSITION FROM EMPLOYEES;
+-------------------------+----------+
| EMAIL                   | POSITION |
+-------------------------+----------+
| rahul.kumar@gmail.com   |       12 |
| anita.sharma@yahoo.com  |       13 |
| suresh.verma@gmail.com  |       13 |
| priya.singh@outlook.com |       12 |
| rahul.joshi@gmail.com   |       12 |
| kiran.reddy@gmail.com   |       12 |
| deepika.naidu@yahoo.com |       14 |
| mahesh.patel@gmail.com  |       13 |
| divya.gupta@gmail.com   |       12 |
| arjun.rao@gmail.com     |       10 |
+-------------------------+----------+
10 rows in set (0.03 sec)

mysql> SELECT email, REPLACE(email, 'gmail.com', 'company.com') AS updated_email
    -> FROM employees;
+-------------------------+--------------------------+
| email                   | updated_email            |
+-------------------------+--------------------------+
| rahul.kumar@gmail.com   | rahul.kumar@company.com  |
| anita.sharma@yahoo.com  | anita.sharma@yahoo.com   |
| suresh.verma@gmail.com  | suresh.verma@company.com |
| priya.singh@outlook.com | priya.singh@outlook.com  |
| rahul.joshi@gmail.com   | rahul.joshi@company.com  |
| kiran.reddy@gmail.com   | kiran.reddy@company.com  |
| deepika.naidu@yahoo.com | deepika.naidu@yahoo.com  |
| mahesh.patel@gmail.com  | mahesh.patel@company.com |
| divya.gupta@gmail.com   | divya.gupta@company.com  |
| arjun.rao@gmail.com     | arjun.rao@company.com    |
+-------------------------+--------------------------+
10 rows in set (0.72 sec)

mysql> SELECT email, SUBSTRING_INDEX(email, '@', 1) AS username
    -> FROM employees;
+-------------------------+---------------+
| email                   | username      |
+-------------------------+---------------+
| rahul.kumar@gmail.com   | rahul.kumar   |
| anita.sharma@yahoo.com  | anita.sharma  |
| suresh.verma@gmail.com  | suresh.verma  |
| priya.singh@outlook.com | priya.singh   |
| rahul.joshi@gmail.com   | rahul.joshi   |
| kiran.reddy@gmail.com   | kiran.reddy   |
| deepika.naidu@yahoo.com | deepika.naidu |
| mahesh.patel@gmail.com  | mahesh.patel  |
| divya.gupta@gmail.com   | divya.gupta   |
| arjun.rao@gmail.com     | arjun.rao     |
+-------------------------+---------------+
10 rows in set (0.19 sec)

mysql> SELECT email, SUBSTRING_INDEX(email, '@', -1) AS username
    -> FROM EMPLOYEES;
+-------------------------+-------------+
| email                   | username    |
+-------------------------+-------------+
| rahul.kumar@gmail.com   | gmail.com   |
| anita.sharma@yahoo.com  | yahoo.com   |
| suresh.verma@gmail.com  | gmail.com   |
| priya.singh@outlook.com | outlook.com |
| rahul.joshi@gmail.com   | gmail.com   |
| kiran.reddy@gmail.com   | gmail.com   |
| deepika.naidu@yahoo.com | yahoo.com   |
| mahesh.patel@gmail.com  | gmail.com   |
| divya.gupta@gmail.com   | gmail.com   |
| arjun.rao@gmail.com     | gmail.com   |
+-------------------------+-------------+
10 rows in set (0.05 sec)

mysql> SELECT LAST_NAME FROM EMPLOYEES
    -> WHERE LAST_NAME LIKE'%A';
+-----------+
| LAST_NAME |
+-----------+
| Sharma    |
| Verma     |
| Gupta     |
+-----------+
3 rows in set (0.07 sec)

mysql> SELECT UPPER(CONCAT(FIRST_NAME,' ',LAST_NAME)) 
    -> FROM EMPLOYEES
    -> WHERE DEPARTMENT IN 'IT';
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ''IT'' at line 3
mysql> SELECT UPPER(CONCAT(FIRST_NAME,' ',LAST_NAME)) AS FULL_NAME
    -> FROM EMPLOYEES
    -> WHERE DEPARTMENT='IT';
+-------------+
| FULL_NAME   |
+-------------+
| RAHUL KUMAR |
| KIRAN REDDY |
+-------------+
2 rows in set (0.04 sec)

mysql> -- FIRST NAMES AMOUNG DUPLICATES
mysql> SELECT FIRST_NAME, COUNT(*) AS OCCURANCES
    -> FROM EMPLOYEES
    -> HAVING COUNT(*)>1;
ERROR 1140 (42000): In aggregated query without GROUP BY, expression #1 of SELECT list contains nonaggregated column 'db4.EMPLOYEES.first_name'; this is incompatible with sql_mode=only_full_group_by
mysql> SELECT FIRST_NAME, COUNT(*) AS OCCURANCES
    -> FROM EMPLOYEES
    -> GROUP BY FIRST_NAME
    -> HAVING COUNT(*)>1;
+------------+------------+
| FIRST_NAME | OCCURANCES |
+------------+------------+
| Rahul      |          2 |
+------------+------------+
1 row in set (0.09 sec)

mysql> SELECT phone_number, REPLACE(phone_number, '-', '') AS formatted_phone
    -> FROM employees;
+--------------+-----------------+
| phone_number | formatted_phone |
+--------------+-----------------+
| 987-654-3210 | 9876543210      |
| 912-345-6789 | 9123456789      |
| 998-123-4567 | 9981234567      |
| 900-456-7890 | 9004567890      |
| 955-888-1111 | 9558881111      |
| 901-222-3333 | 9012223333      |
| 944-111-2222 | 9441112222      |
| 933-444-5555 | 9334445555      |
| 955-777-8888 | 9557778888      |
| 988-999-7777 | 9889997777      |
+--------------+-----------------+
10 rows in set (0.00 sec)

mysql> SELECT FIRST_NAME FROM EMPLOYEES
    -> WHERE FIRST_NAME LIKE '%I%';
+------------+
| FIRST_NAME |
+------------+
| Anita      |
| Priya      |
| Kiran      |
| Deepika    |
| Divya      |
+------------+
5 rows in set (0.00 sec)

mysql> SELECT FIRST_NAME,LENGTH(FIRST_NAME)
    -> FROM EMPLOYEES;
+------------+--------------------+
| FIRST_NAME | LENGTH(FIRST_NAME) |
+------------+--------------------+
| Rahul      |                  5 |
| Anita      |                  5 |
| Suresh     |                  6 |
| Priya      |                  5 |
| Rahul      |                  5 |
| Kiran      |                  5 |
| Deepika    |                  7 |
| Mahesh     |                  6 |
| Divya      |                  5 |
| Arjun      |                  5 |
+------------+--------------------+
10 rows in set (0.03 sec)

mysql> SELECT first_name, LENGTH(first_name) AS name_length
    -> FROM employees
    -> ORDER BY name_length;
+------------+-------------+
| first_name | name_length |
+------------+-------------+
| Rahul      |           5 |
| Anita      |           5 |
| Priya      |           5 |
| Rahul      |           5 |
| Kiran      |           5 |
| Divya      |           5 |
| Arjun      |           5 |
| Suresh     |           6 |
| Mahesh     |           6 |
| Deepika    |           7 |
+------------+-------------+
10 rows in set (0.03 sec)

mysql> SELECT city
    -> FROM employees
    -> WHERE LENGTH(city) > 6;
+-----------+
| city      |
+-----------+
| Hyderabad |
| Bangalore |
| Chennai   |
| Hyderabad |
| Hyderabad |
+-----------+
5 rows in set (0.01 sec)

mysql> SELECT CONCAT(FIRST_NAME,' ',LAST_NAME,'-',DEPARTMENT) AS NAME FROM EMPLOYEES;
+---------------------+
| NAME                |
+---------------------+
| Rahul Kumar-IT      |
| Anita Sharma-HR     |
| Suresh Verma-Sales  |
| Priya Singh-Finance |
| Rahul Joshi-Testing |
| Kiran Reddy-IT      |
| Deepika Naidu-HR    |
| Mahesh Patel-Sales  |
| Divya Gupta-Finance |
| Arjun Rao-Developer |
+---------------------+
10 rows in set (0.00 sec)

mysql> SELECT LEFT(FIRST_NAME,1) FROM EMPLOYEES;
+--------------------+
| LEFT(FIRST_NAME,1) |
+--------------------+
| R                  |
| A                  |
| S                  |
| P                  |
| R                  |
| K                  |
| D                  |
| M                  |
| D                  |
| A                  |
+--------------------+
10 rows in set (0.02 sec)

mysql> SELECT LEFT(LAST_NAME,1) FROM EMPLOYEES;
+-------------------+
| LEFT(LAST_NAME,1) |
+-------------------+
| K                 |
| S                 |
| V                 |
| S                 |
| J                 |
| R                 |
| N                 |
| P                 |
| G                 |
| R                 |
+-------------------+
10 rows in set (0.00 sec)

mysql> SELECT CONCAT(first_name, ' ', last_name, ' - ', department) AS name_dept
    -> FROM employees;
+-----------------------+
| name_dept             |
+-----------------------+
| Rahul Kumar - IT      |
| Anita Sharma - HR     |
| Suresh Verma - Sales  |
| Priya Singh - Finance |
| Rahul Joshi - Testing |
| Kiran Reddy - IT      |
| Deepika Naidu - HR    |
| Mahesh Patel - Sales  |
| Divya Gupta - Finance |
| Arjun Rao - Developer |
+-----------------------+
10 rows in set (0.00 sec)

mysql> 
mysql> SELECT CONCAT(LEFT(first_name, 1), LEFT(last_name, 1)) AS initials
    -> FROM employees;
+----------+
| initials |
+----------+
| RK       |
| AS       |
| SV       |
| PS       |
| RJ       |
| KR       |
| DN       |
| MP       |
| DG       |
| AR       |
+----------+
10 rows in set (0.01 sec)

mysql> SELECT first_name, salary,
    ->    	REPEAT('*', LEAST(FLOOR(salary / 10000), 5)) AS salary_rating
    -> FROM employees;
+------------+----------+---------------+
| first_name | salary   | salary_rating |
+------------+----------+---------------+
| Rahul      | 45000.00 | ****          |
| Anita      | 38000.00 | ***           |
| Suresh     | 52000.00 | *****         |
| Priya      | 47000.00 | ****          |
| Rahul      | 41000.00 | ****          |
| Kiran      | 56000.00 | *****         |
| Deepika    | 39000.00 | ***           |
| Mahesh     | 62000.00 | *****         |
| Divya      | 49000.00 | ****          |
| Arjun      | 68000.00 | *****         |
+------------+----------+---------------+
10 rows in set (0.04 sec)

mysql> SELECT first_name, salary,REPEAT('*', LEAST(FLOOR(SALARY/10000),5)) AS SALARY RATING
    -> FROM EMPLOYEES;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'RATING
FROM EMPLOYEES' at line 1
mysql> SELECT first_name, salary,REPEAT('*', LEAST(FLOOR(SALARY/10000),5)) AS SALARY_RATING
    -> FROM EMPLOYEES;
+------------+----------+---------------+
| first_name | salary   | SALARY_RATING |
+------------+----------+---------------+
| Rahul      | 45000.00 | ****          |
| Anita      | 38000.00 | ***           |
| Suresh     | 52000.00 | *****         |
| Priya      | 47000.00 | ****          |
| Rahul      | 41000.00 | ****          |
| Kiran      | 56000.00 | *****         |
| Deepika    | 39000.00 | ***           |
| Mahesh     | 62000.00 | *****         |
| Divya      | 49000.00 | ****          |
| Arjun      | 68000.00 | *****         |
+------------+----------+---------------+
10 rows in set (0.00 sec)

mysql> FIND_IN_SET(department, 'IT,HR,Sales') AS is_core_dept
    -> FROM employees;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'FIND_IN_SET(department, 'IT,HR,Sales') AS is_core_dept
FROM employees' at line 1
mysql> SELECT FIRST_NAME,DEPARTMENT,
    -> FIND_IN_SET(department, 'IT,HR,Sales') AS is_core_dept
    -> FROM employees;
+------------+------------+--------------+
| FIRST_NAME | DEPARTMENT | is_core_dept |
+------------+------------+--------------+
| Rahul      | IT         |            1 |
| Anita      | HR         |            2 |
| Suresh     | Sales      |            3 |
| Priya      | Finance    |            0 |
| Rahul      | Testing    |            0 |
| Kiran      | IT         |            1 |
| Deepika    | HR         |            2 |
| Mahesh     | Sales      |            3 |
| Divya      | Finance    |            0 |
| Arjun      | Developer  |            0 |
+------------+------------+--------------+
10 rows in set (0.02 sec)

mysql> SELECT email,
    ->    	CONCAT(LEFT(email, 3), '****@', SUBSTRING_INDEX(email, '@', -1)) AS masked_email
    -> FROM employees;
+-------------------------+---------------------+
| email                   | masked_email        |
+-------------------------+---------------------+
| rahul.kumar@gmail.com   | rah****@gmail.com   |
| anita.sharma@yahoo.com  | ani****@yahoo.com   |
| suresh.verma@gmail.com  | sur****@gmail.com   |
| priya.singh@outlook.com | pri****@outlook.com |
| rahul.joshi@gmail.com   | rah****@gmail.com   |
| kiran.reddy@gmail.com   | kir****@gmail.com   |
| deepika.naidu@yahoo.com | dee****@yahoo.com   |
| mahesh.patel@gmail.com  | mah****@gmail.com   |
| divya.gupta@gmail.com   | div****@gmail.com   |
| arjun.rao@gmail.com     | arj****@gmail.com   |
+-------------------------+---------------------+
10 rows in set (0.00 sec)

mysql> SELECT first_name
    -> FROM employees
    -> WHERE LOWER(first_name) = LOWER(REVERSE(first_name));
Empty set (0.02 sec)

mysql> SELECT CONCAT(LOWER(LEFT(first_name, 1)), LOWER(last_name)) AS username
    -> FROM employees;
+----------+
| username |
+----------+
| rkumar   |
| asharma  |
| sverma   |
| psingh   |
| rjoshi   |
| kreddy   |
| dnaidu   |
| mpatel   |
| dgupta   |
| arao     |
+----------+
10 rows in set (0.00 sec)

mysql> SELECT first_name, last_name, STRCMP(first_name, last_name) AS comparison
    -> FROM employees;
+------------+-----------+------------+
| first_name | last_name | comparison |
+------------+-----------+------------+
| Rahul      | Kumar     |          1 |
| Anita      | Sharma    |         -1 |
| Suresh     | Verma     |         -1 |
| Priya      | Singh     |         -1 |
| Rahul      | Joshi     |          1 |
| Kiran      | Reddy     |         -1 |
| Deepika    | Naidu     |         -1 |
| Mahesh     | Patel     |         -1 |
| Divya      | Gupta     |         -1 |
| Arjun      | Rao       |         -1 |
+------------+-----------+------------+
10 rows in set (0.02 sec)

mysql> Terminal close -- exit!
