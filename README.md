1.Name:Hrishika Verma 
2.Company:CodTech
3.ID:CT4SQL4338
4.Domain:SQL 
5.Duration:july to August 
6.Overview Of the project 
a.PROJECT:LIBRARY MANAGEMENT SYSTEM
b. OBJECTIVE:
Create a database for managing a library's book inventory, members, and 
borrow/return transactions. This project helps you learn basic SQL commands 
and database design. Design tables for books, members, and transactions. 
Write SQL queries to insert, update, delete, and retrieve data.
KEY ACTIVITIES:
Some key features in SQL include:

1. Data Manipulation Language (DML): SQL allows you to retrieve, insert, update, and delete data from databases using commands like SELECT, INSERT, UPDATE, and DELETE.
2. Data Definition Language (DDL): SQL provides commands for defining the structure of a database such as creating tables (CREATE TABLE), modifying tables (ALTER TABLE), and deleting tables (DROP TABLE).
3. Querying and Filtering: SQL allows you to write complex queries to retrieve specific data from one or multiple tables using the SELECT statement. You can also use WHERE clause to filter results based on specific conditions.
4. Joins: SQL supports different types of joins like INNER JOIN, LEFT JOIN, RIGHT JOIN, and FULL JOIN to combine data from multiple tables based on related columns.
5. Aggregation Functions: SQL offers various aggregation functions like SUM(), AVG(), COUNT(), MAX(), MIN() that allow you to perform calculations on groups of data rows.
These are just some key features in SQL; there are many more advanced capabilities depending on the specific database management system being used.
Implementation:
Hrishika verma CA 1 MITM, [7/15/2024 10:43 AM]
mysql> describe books;
+----------------+--------------+------+-----+---------+-------+
| Field          | Type         | Null | Key | Default | Extra |
+----------------+--------------+------+-----+---------+-------+
| book_id        | int(11)      | NO   | PRI | NULL    |       |
| title          | varchar(100) | YES  |     | NULL    |       |
| author         | varchar(100) | YES  |     | NULL    |       |
| genre          | varchar(50)  | YES  |     | NULL    |       |
| published_date | date         | YES  |     | NULL    |       |
+----------------+--------------+------+-----+---------+-------+
5 rows in set (0.05 sec)

mysql> CREATE TABLE Members (
    ->   member_id INT PRIMARY KEY,
    ->   name VARCHAR(100),
    ->   address VARCHAR(200),
    ->   contact_number VARCHAR(20)
    -> );
Query OK, 0 rows affected (0.08 sec)

mysql> describe members;
+----------------+--------------+------+-----+---------+-------+
| Field          | Type         | Null | Key | Default | Extra |
+----------------+--------------+------+-----+---------+-------+
| member_id      | int(11)      | NO   | PRI | NULL    |       |
| name           | varchar(100) | YES  |     | NULL    |       |
| address        | varchar(200) | YES  |     | NULL    |       |
| contact_number | varchar(20)  | YES  |     | NULL    |       |
+----------------+--------------+------+-----+---------+-------+
4 rows in set (0.02 sec)

mysql> CREATE TABLE Transactions (
    ->  transaction_id int(50) PRIMARY KEY,
    ->  member_id INT(50),
    ->  book_id INT(50),
    ->  transaction_date DATE,
    ->  return_date DATE
    -> );
Query OK, 0 rows affected (0.06 sec)

mysql> INSERT INTO Transactions (transaction_id, member_id, book_id, transaction_date, return_date)
    -> VALUES (1, 101, 201, '2022-01-15', '2022-02-15');
Query OK, 1 row affected (0.02 sec)

mysql> INSERT INTO Transactions (transaction_id, member_id, book_id, transaction_date, return_date)
    -> values(2,102,'2022-01-18','2022-02-20');
ERROR 1136 (21S01): Column count doesn't match value count at row 1
mysql> INSERT INTO Transactions (transaction_id, member_id, book_id, transaction_date, return_date) values(2,102,202,'2022-02-17','2022-05-20');
Query OK, 1 row affected (0.01 sec)

mysql> INSERT INTO Transactions (transaction_id, member_id, book_id, transaction_date, return_date) values(3,103,203,'2022-05-24','2022-08-20');
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO Transactions (transaction_id, member_id, book_id, transaction_date, return_date) values(4,104,204,'2022-02-05','2022-03-20');
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO Transactions (transaction_id, member_id, book_id, transaction_date, return_date) values(5,105,205,'2022-03-05','2022-04-25');
Query OK, 1 row affected (0.00 sec)

mysql> select  * from transactions;
+----------------+-----------+---------+------------------+-------------+
| transaction_id | member_id | book_id | transaction_date | return_date |
+----------------+-----------+---------+------------------+-------------+
|              1 |       101 |     201 | 2022-01-15       | 2022-02-15  |
|              2 |       102 |     202 | 2022-02-17       | 2022-05-20  |
|              3 |       103 |     203 | 2022-05-24       | 2022-08-20  |
|              4 |       104 |     204 | 2022-02-05       | 2022-03-20  |
|              5 |       105 |     205 | 2022-03-05       | 2022-04-25  |
+----------------+-----------+---------+------------------+-------------+
5 rows in set (0.00 sec)

mysql> UPDATE Transactions
    -> SET return_date = '2022-03-01'
    -> WHERE transaction_id = 1;
Query OK, 1 row affected (0.00 sec)
Rows matched: 1  Changed: 1  Warnings: 0

Hrishika verma CA 1 MITM, [7/15/2024 10:43 AM]
mysql> select  * from transactions;
+----------------+-----------+---------+------------------+-------------+
| transaction_id | member_id | book_id | transaction_date | return_date |
+----------------+-----------+---------+------------------+-------------+
|              1 |       101 |     201 | 2022-01-15       | 2022-03-01  |
|              2 |       102 |     202 | 2022-02-17       | 2022-05-20  |
|              3 |       103 |     203 | 2022-05-24       | 2022-08-20  |
|              4 |       104 |     204 | 2022-02-05       | 2022-03-20  |
|              5 |       105 |     205 | 2022-03-05       | 2022-04-25  |
+----------------+-----------+---------+------------------+-------------+
5 rows in set (0.00 sec)

mysql> DELETE FROM Transactions
    -> WHERE transaction_id = 1;
Query OK, 1 row affected (0.00 sec)

mysql> select  * from transactions;
+----------------+-----------+---------+------------------+-------------+
| transaction_id | member_id | book_id | transaction_date | return_date |
+----------------+-----------+---------+------------------+-------------+
|              2 |       102 |     202 | 2022-02-17       | 2022-05-20  |
|              3 |       103 |     203 | 2022-05-24       | 2022-08-20  |
|              4 |       104 |     204 | 2022-02-05       | 2022-03-20  |
|              5 |       105 |     205 | 2022-03-05       | 2022-04-25  |
+----------------+-----------+---------+------------------+-------------+
4 rows in set (0.00 sec)

mysql> INSERT INTO Books (book_id, title, author, genre)
    -> VALUES (301, 'To Kill a Mockingbird', 'Harper Lee', 'Fiction');
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO Books (book_id, title, author, genre) values(302,"science","josh","scientific");
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO Books (book_id, title, author, genre) values(303,"roamntic","piyush bhagat","romance");
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO Books (book_id, title, author, genre) values(304,"dhamal","rohit dhetty","comedy");
Query OK, 1 row affected (0.00 sec)

mysql> UPDATE Books
    -> SET genre = 'Literary Fiction'
    -> WHERE book_id = 301;
Query OK, 1 row affected (0.00 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql> select  * from books;
+---------+-----------------------+---------------+------------------+----------------+
| book_id | title                 | author        | genre            | published_date |
+---------+-----------------------+---------------+------------------+----------------+
|     301 | To Kill a Mockingbird | Harper Lee    | Literary Fiction | NULL           |
|     302 | science               | josh          | scientific       | NULL           |
|     303 | roamntic              | piyush bhagat | romance          | NULL           |
|     304 | dhamal                | rohit dhetty  | comedy           | NULL           |
+---------+-----------------------+---------------+------------------+----------------+
4 rows in set (0.00 sec)

mysql> DELETE FROM Books
    -> WHERE book_id = 303;
Query OK, 1 row affected (0.00 sec)

mysql> select  * from books;
+---------+-----------------------+--------------+------------------+----------------+
| book_id | title                 | author       | genre            | published_date |
+---------+-----------------------+--------------+------------------+----------------+
|     301 | To Kill a Mockingbird | Harper Lee   | Literary Fiction | NULL           |
|     302 | science               | josh         | scientific       | NULL           |
|     304 | dhamal                | rohit dhetty | comedy           | NULL           |
+---------+-----------------------+--------------+------------------+----------------+
3 rows in set (0.00 sec)

Hrishika verma CA 1 MITM, [7/15/2024 10:43 AM]
mysql> INSERT INTO members (member_id, member_name, membership_type)
    -> VALUES (1, 'Alice', 'Gold');
ERROR 1054 (42S22): Unknown column 'member_name' in 'field list'
mysql> describe members;
+----------------+--------------+------+-----+---------+-------+
| Field          | Type         | Null | Key | Default | Extra |
+----------------+--------------+------+-----+---------+-------+
| member_id      | int(11)      | NO   | PRI | NULL    |       |
| name           | varchar(100) | YES  |     | NULL    |       |
| address        | varchar(200) | YES  |     | NULL    |       |
| contact_number | varchar(20)  | YES  |     | NULL    |       |
+----------------+--------------+------+-----+---------+-------+
4 rows in set (0.00 sec)

mysql> INSERT INTO members (member_id, name, address, contact_number)
    -> VALUES (1, 'Alice', '123 Main Street', '555-1234');
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO members (member_id, name, address, contact_number) values(2,"hrishi","tirupati",683889293);
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO members (member_id, name, address, contact_number) values(3,"parinay","lal gate",364863467);
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO members (member_id, name, address, contact_number) values(4,"pari","sati gate",364893467);
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO members (member_id, name, address, contact_number) values(5,"paritiksha","sati gate",987693467);
Query OK, 1 row affected (0.00 sec)

mysql> select * from members;
+-----------+------------+-----------------+----------------+
| member_id | name       | address         | contact_number |
+-----------+------------+-----------------+----------------+
|         1 | Alice      | 123 Main Street | 555-1234       |
|         2 | hrishi     | tirupati        | 683889293      |
|         3 | parinay    | lal gate        | 364863467      |
|         4 | pari       | sati gate       | 364893467      |
|         5 | paritiksha | sati gate       | 987693467      |
+-----------+------------+-----------------+----------------+
5 rows in set (0.00 sec)

mysql> UPDATE members
    -> SET address = '456 Elm Street'
    -> WHERE member_id = 1;
Query OK, 1 row affected (0.00 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql> DELETE FROM members WHERE member_id = 1;
Query OK, 1 row affected (0.00 sec)

mysql> select * from members;
+-----------+------------+-----------+----------------+
| member_id | name       | address   | contact_number |
+-----------+------------+-----------+----------------+
|         2 | hrishi     | tirupati  | 683889293      |
|         3 | parinay    | lal gate  | 364863467      |
|         4 | pari       | sati gate | 364893467      |
|         5 | paritiksha | sati gate | 987693467      |
+-----------+------------+-----------+----------------+
4 rows in set (0.00 sec)

mysql>
