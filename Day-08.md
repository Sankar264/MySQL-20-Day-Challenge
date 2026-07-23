Constraints
==============
Constrains are rules applied to the table columns in MYSQL to ensure that only valid and accurate and accurate data os stored in the database.
in simple words:
Constrains= Rules that control the data entered into a table
Why do we use Constraints
maintain data integrity
prevent invalid data entry 
Avoid duplicate records
ensure relationships between tables.
make the database reliable and consistent
TYPES OF CONSTRAINTS :-
NOT NULL :- DOES'NT ALLOW NULL VALUES.
UNIQUE :- DOES'NT ALLOW DUBLICATE VALUES. 
PRIMARY KEY:- COMBINTION OF UNIQUE PLUS NOT NULL.
COMPOSITE KEY:- 
FOREGIN KEY :- A foreign key is a key used to link two tables together.
A foreign key is a FIELD(OR COLLECTION OF FIELDS) in one table that refers to the primary key in another table.
The table containing the foreign key is called the child table. and table containing the candidate key is called as referenced table or parent table .
CHECK :- 
DEFAULT :-
WHAT ARE REFERENTIAL ACTIONS
----------------------------
REFERENTIAL ACTION DEFINES WHAT HAPPENS TO CHILD TABLE DATA WHEN PARENT TABLE DATA IS DELETED OR UPDTED
ON DELETE CASCADE
ON UPDATE CASCADE

ON DELETE SET NULL;
ON UPDATE SET NULL;
