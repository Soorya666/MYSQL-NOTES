# NOTES FOR MY LAZY ASS FUTURE
# some pesky commands that are helpful

- `\! clear` to clear the mysql screen
- `--` for commenting! handy shit to clear out
- `DELETE FROM table_name` akkha table saaf with 0 VALUES (reset)

# mysql commands

 ```sql
  sudo mysql -- to startup the app
```  

- select database():
- SHOW DATABASES; => show all the databases 
- SHOW TABLES ==> self explanatory
- SHOW COLUMNS FROM <table_ka_naam>
or DESC <table_ka_naam>;     ==> dono ka same meaning hai, describing  table   
 
 - DROP TABLE <table_ka_naam>;  

## CREATE [C of Crud] 
 - INSERT INTO <table_ka_naam> fir
      VALUES (table ka attribute 1, table ka attribute 2); 
    > NOTE: if you used varchar then put the value in the damn `" "` quotes

    **for multiple value inserting**: seperate with commas
    ```sql
        insert into people(first_name, last_name, age)
            -> values ('soorya', 'srihari' , 2342)
            -> **,** ('asd', 'adsf', 23423);
    ```
    or else this type of error might come ==> __ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'values ('asodf' , 'as;ldf ', 323)' at line 2__
 
- `PRIMARY KEY` => adds a primary key. THIS SHIT will cause error if same value is given 
this dat error: ``ERROR 1062 (23000): Duplicate entry 'adlfkals' for key 'unique_people.PRIMARY'``

- `AUTO_INCREMENT` => goes well with PRIMARY KEY to make incrments for a number  
(jisko increment karna hai uss field ko hi include mat kar `insert into() && values()` karte time)

- `NOT NULL` => empty values will throw error


---

## READ  [R of cRud] 
- `SELECT` => literally selects the *rows* from tables;

- `WHERE` ==> finetune a search like finding a specific value from a column 
    - its case insensitive. matlab `WHERE name=cats || name=CAts || name=CATS` give the same ass result

- `AS`  ==> literally set another name for a `column name` eg: _cat_id_ or _name_ of a table _cats_ 
eg: 
```sql
select name AS naam, age as TERA_MAIYYAT_KA_AGE from <table_name>;   
```

---

## UPDATE [U of crUd]:

- `UPDATE` ==> simple bc, update a value or *entire column*
eg: table name =`friends` && columns are: `name`, `age`, `status`:

```sql
UPDATE friends SET status='enemies'; -- updates entire `status` column 
```
- `SET` ==> literally sets a value in a col


> good rule of thumb: make sure that before changing values with `WHERE` then first preview it with `SELECT` to see before hand if that selection is indeed correct or not 




## DELETE [D of cruD]
- `DELETE 'FROM' <table_name>` ==> pura table delete ho jayega fir rona mat (use carefully after double check) 
- `DELETE 'FROM' <table_name> WHERE something=something` ==> where ke saath chain karke use karna(for specificity) 


---

## Strings: 
 
- `CONCAT` ==> literally a concat opp
eg: 
```sql
    SELECT CONCAT('helo', 'my', 'baby') from <table_name>; 
    -- output: helomybaby
```

- `CONCAT_WS` ==> WS matlab with-seperator. will split the string and join it with anything
eg: 

```sql
  -- for url slug
  SELECT CONCAT_WS('-', 'title', 'something', 'something');  
  output: `title-something-something` -- notice end mein nahi lagaya hyphen. 
```


- `SUBSTRING` || `SUBSTR` ==> literally selects and gives the sub string
eg: 
```sql
select substring('mehboob', 4, 8)
4 - start from the 4th position (matlab 'm' se)
8 - total length (matlab 'b' is in 8th position)
```
 
```sql
-- aisa bhi likh sakte hain
select substring('mehboob', 4)
4 - start from the 4th position 

```

- `REPLACE` ==> REPLACE(targetToChange, oldValue, newValToReplaceWith)
eg: 

```sql
mysql> select * from books;
+---------+------------------------+--------------+--------------+---------------+----------------+-------+
| book_id | title                  | author_fname | author_lname | released_year | stock_quantity | pages |
+---------+------------------------+--------------+--------------+---------------+----------------+-------+
|       1 | The Great Gatsby       | F. Scott     | Fitzgerald   |          1925 |             12 |   218 |
|       2 | To Kill a Mockingbird  | Harper       | Lee          |          1960 |              8 |   281 |
|       3 | 1984                   | George       | Orwell       |          1949 |             15 |   328 |
|       4 | Pride and Prejudice    | Jane         | Austen       |          1813 |             20 |   279 |
|       5 | The Catcher in the Rye | J.D.         | Salinger     |          1951 |              5 |   277 |
|       6 | Moby-Dick              | Herman       | Melville     |          1851 |              7 |   635 |
|       7 | War and Peace          | Leo          | Tolstoy      |          1869 |              3 |  1225 |
|       8 | The Hobbit             | J.R.R.       | Tolkien      |          1937 |             25 |   310 |
|       9 | Brave New World        | Aldous       | Huxley       |          1932 |             10 |   268 |
|      10 | The Lord of the Rings  | J.R.R.       | Tolkien      |          1954 |             18 |  1178 |
+---------+------------------------+--------------+--------------+---------------+----------------+-------+
10 rows in set (0.00 sec)

mysql> select replace(title, ' ', '_') as titleWithUnderscores from books where title='war and peace' ;
+----------------------+
| titleWithUnderscores |
+----------------------+
| War_and_Peace        |
+----------------------+
1 row in set (0.01 sec)
```

- `REVERSE`: literally reverses
eg;
SELECT REVERSE(<anything_here>) from <table_name>; 
> exceptional case: 
eg; mysql> select reverse(NULl)
```sql
+------------------------------+
| reverse(NULl)                |
+------------------------------+
| NULL                         |
+------------------------------+
1 row in set (0.00 sec)
```
- `CHAR_LENGTH()` ==> 'give the count of the characters'
> NOTE: `LENGTH()` gives the length fo the string **measured in bytes**

- `UPPER()` or  `UCASE` ==> self-explanatory
- `LOWER()` or `LCASE` ==> self-explanatory
- `INSERT()` ==> literally insert kardega bc. 
    - (string, position, length, valueToInsert)
    - if length exceeds total length of string, error
    - if args missing, then error
eg: 
```sql
mysql> select insert('boobeshsingh', 7, 6, 'nigger');
+-----------------------------------------+
| insert('boobeshsingh', 1, 6, 'nigger') |
+-----------------------------------------+
| niggerhsingh 
+-----------------------------------------+
```
- `LEFT` ==> gives all values from the left GIVEN THE COUNT 
eg: 
```sql
mysql> select left('mehboobs', 3);
+---------------------+
| left('mehboobs', 3) |
+---------------------+
| meh                 |
+---------------------+
```
- `RIGHT` ==> same like above but from right
eg: 
```sql
mysql> select right('mehboobs',5);
+---------------------+
| right('mehboobs',5) |
+---------------------+
| boobs               |
+---------------------+
```
- `TRIM()`==> mongoose jesa empty spaces uda dega strings mein aage piche ka
  - `LEADING` ==> left ke side mein jo bhi rahega, usse trim karega
  - `TRAILING` ==> right ke side mein jo bhi rahega, usse trim karega
  - `BOTH` ==> dono ko kar daalega
  - egs: 
```sql
mysql> SELECT TRIM('  bar   ');
        -> 'bar'
mysql> SELECT TRIM(LEADING 'x' FROM 'xxxbarxxx');
        -> 'barxxx'
mysql> SELECT TRIM(BOTH 'x' FROM 'xxxbarxxx');
        -> 'bar'
mysql> SELECT TRIM(TRAILING 'xyz' FROM 'barxxyz');
        -> 'barx'
```
- `REPEAT()`=> repeats a given string. eg: REPEAT('ha', 4); 
output: 'hahahaha'

---

-  `DISTINCT` ==> gives unique values from table; suppose duplicate hoyega, toh ek hi unique value dega usmein se
eg: 

```sql
mysql> select * from books;
+---------+------------------------+--------------+--------------+---------------+----------------+-------+
| book_id | title                  | author_fname | author_lname | released_year | stock_quantity | pages |
+---------+------------------------+--------------+--------------+---------------+----------------+-------+
|       1 | The Great Gatsby       | F. Scott     | Fitzgerald   |          1925 |             12 |   218 |
|       2 | To Kill a Mockingbird  | Harper       | Lee          |          1960 |              8 |   281 |
|       3 | 1984                   | George       | Orwell       |          1949 |             15 |   328 |
|       4 | Pride and Prejudice    | Jane         | Austen       |          1813 |             20 |   279 |
|       5 | The Catcher in the Rye | J.D.         | Salinger     |          1951 |              5 |   277 |
|       6 | Moby-Dick              | Herman       | Melville     |          1851 |              7 |   635 |
|       7 | War and Peace          | Leo          | Tolstoy      |          1869 |              3 |  1225 |
|       8 | The Hobbit             | J.R.R.       | Tolkien      |          1937 |             25 |   310 |
|       9 | Brave New World        | Aldous       | Huxley       |          1932 |             10 |   268 |
|      10 | The Lord of the Rings  | J.R.R.       | Tolkien      |          1954 |             18 |  1178 |
|      11 | NIGGENDAR1             | soorya       | srihari      |          2342 |             33 |   133 |
|      12 | NIGGENDAR2             | soorya       | srihari      |          2342 |             33 |   133 |
|      13 | NIGGENDAR3             | soorya       | srihari      |          2342 |             33 |   133 |
|      14 | NIGGENDAR1             | soorya       | sriharsdfi   |          2342 |             33 | 34123 |
+---------+------------------------+--------------+--------------+---------------+----------------+-------+

mysql> select DISTINCT author_fname, author_lname from books;
+--------------+--------------+
| author_fname | author_lname |
+--------------+--------------+
| F. Scott     | Fitzgerald   |
| Harper       | Lee          |
| George       | Orwell       |
| Jane         | Austen       |
| J.D.         | Salinger     |
| Herman       | Melville     |
| Leo          | Tolstoy      |
| J.R.R.       | Tolkien      |
| Aldous       | Huxley       |
| soorya       | srihari      |
| soorya       | sriharsdfi   |
+--------------+--------------+
```

- `ORDER BY` ==> literally another name given to sort
- you can use `ASC` (default behavior or `DESC` along with it)
- you can target columns using numbers. for eg: `ORDER BY 1` or 2, 3, 4 and so on
eg: `mysql> select author_lname from books order by author_lname DESC;`

```sql
-- before
mysql> select author_lname from books ;
+--------------+
| author_lname |
+--------------+
| Fitzgerald   |
| Lee          |
| Orwell       |
| Austen       |
| Salinger     |
| Melville     |
| Tolstoy      |
| Tolkien      |
| Huxley       |
| Tolkien      |
| srihari      |
| srihari      |
| srihari      |
| sriharsdfi   |
+--------------+


--after

mysql> select author_lname from books order by author_lname ;
+--------------+
| author_lname |
+--------------+
| Austen       |
| Fitzgerald   |
| Huxley       |
| Lee          |
| Melville     |
| Orwell       |
| Salinger     |
| srihari      |
| srihari      |
| srihari      |
| sriharsdfi   |
| Tolkien      |
| Tolkien      |
| Tolstoy      |
+--------------+

```
- `LIMIT` ==> works exactly like the `head` and `tail` cmd in bash
eg: clear hojayega eg dekh ke
syntax: `LIMIT offset, count`
```sql
mysql> select author_lname, released_year, title from books ;
+--------------+---------------+------------------------+
| author_lname | released_year | title                  |
+--------------+---------------+------------------------+
| Fitzgerald   |          1925 | The Great Gatsby       |
| Lee          |          1960 | To Kill a Mockingbird  |
| Orwell       |          1949 | 1984                   |
| Austen       |          1813 | Pride and Prejudice    |
| Salinger     |          1951 | The Catcher in the Rye |
| Melville     |          1851 | Moby-Dick              |
| Tolstoy      |          1869 | War and Peace          |
| Tolkien      |          1937 | The Hobbit             |
| Huxley       |          1932 | Brave New World        |
| Tolkien      |          1954 | The Lord of the Rings  |
| srihari      |          2342 | NIGGENDAR1             |
| srihari      |          2342 | NIGGENDAR2             |
| srihari      |          2342 | NIGGENDAR3             |
| sriharsdfi   |          2342 | NIGGENDAR1             |
+--------------+---------------+------------------------+

mysql> select author_lname from books limit 4;
+--------------+
| author_lname |
+--------------+
| Fitzgerald   |
| Lee          |
| Orwell       |
| Austen       |
+--------------+

mysql> select author_lname from books limit 4,3;
+--------------+
| author_lname |
+--------------+
| Salinger     |
| Melville     |
| Tolstoy      |
+--------------+
-- the 4 means `hey, start from the index 4 of the 'author_lname' column and then give me 3 rows`

```
- `LIKE` ==> use `_`, `%`


## Aggregate functions: 
- `COUNT()`:  gives a single value by condensing values from multiple outputs by just calculating the count
- `GROUP BY`:- will make a single group for similar values in a particular column 
eg:

```sql
mysql> select author_fname from books;
+--------------+
| author_fname |
+--------------+
| F. Scott     |
| Harper       |
| George       |
| Jane         |
| J.D.         |
| Herman       |
| Leo          |
| J.R.R.       |
| Aldous       |
| J.R.R.       |
| soorya       |
| soorya       |
| soorya       |
| soorya       |
+--------------+
-- after group by
mysql> select author_fname, count(*) from books group by author_fname;
+--------------+----------+
| author_fname | count(*) |
+--------------+----------+
| F. Scott     |        1 |
| Harper       |        1 |
| George       |        1 |
| Jane         |        1 |
| J.D.         |        1 |
| Herman       |        1 |
| Leo          |        1 |
| J.R.R.       |        2 |
| Aldous       |        1 |
| soorya       |        4 |
+--------------+----------+
```
- `MIN()` ==> gives a single value in an array in A COLUMN
```sql
mysql> select min(author_fname) from books;
+-------------------+
| min(author_fname) |
+-------------------+
| Aldous            |
+-------------------+
```
- `MAX()` ==> 
```sql
mysql> select max(author_fname) from books;
+-------------------+
| max(author_fname) |
+-------------------+
| soorya            |
+-------------------+
```
---
> NOTE: there is a thing called subqueries that is used to know a value of something which we dont remeber
> like for eg: `select min(column_name) from table_name where (select min(column_name))`
> where ke baad waala brackets ke andar ko `subquery` bulate hai bas.

---

- `SUM()` ==> literally adds the shit and gives back one val or of multiple rows using `GROUP BY`
- ``
- ``
- ``
- ``
- ``
- ``
- ``
















# DATA TYPES: 

| Type | Storage (Bytes) | Minimum value (Signed/Unsigned) | Maximum value (Signed/Unsigned) |
| --- | --- | --- | --- |
| TINYINT | 1 | -128/ 0 | 127/ 255 |
| SMALLINT | 2 | -32768/ 0 | 32767/ 65535 |
| MEDIUMINT | 3 | -8388608/ 0 | 8388607/ 16777215 |
| INT | 4 | -8388607/ 16777215 | 2147483647/ 4294967295 |
| BIGINT | 8 | - 9223372036854775808 / 0 | 9223372036854775807 / 18446744073709551615 |

We have to choose the data types based on the kind (type) of data being stored. If possible, we ne


---

#### int => integer 
#### bigint
#### tinyint =>  can hold values from -128 to 127 for signed TINYINT or 0 to 255 for unsigned TINYINT.
### Syntax
TINYINT(M) [SIGNED | UNSIGNED | ZEROFILL]

egs: 
```sql
mysql> create table tinyint_testing(
    -> colOne tinyint,
    -> colTwo tinyint unsigned,
    -> colThree tinyint zerofill);

mysql> insert into tinyint_testing(colOne, colTwo, colThree) values
    -> (-129, 127, 128)
    -> ;
ERROR 1264 (22003): Out of range value for column 'colOne' at row 1
```

#### DECIMAL/FIXED/NUMERIC/DEC ==>
- DECIMAL(P, D) where `P` is the precision (kitna digits total before decimal) and `D` is the total decimal digits that is allowed 

- The range for this column would be from 99.999 to -99.999.
*Syntax*
```sql
column_name  DECIMAL(P,D);
```
*Example*: 
```sql
mysql> desc product_test;
+-------+--------------+------+-----+---------+-------+
| Field | Type         | Null | Key | Default | Extra |
+-------+--------------+------+-----+---------+-------+
| price | decimal(6,2) | YES  |     | NULL    |       |
+-------+--------------+------+-----+---------+-------+

mysql> insert into product_test(price) values (324422.22) -- wrong hai
ERROR 1264 (22003): Out of range value for column 'price' at row 1
mysql> insert into product_test(price) values (3244.22) -- left and right totalls to six digits
Query OK, 1 row affected (0.03 sec)
```
#### FLOAT 
- its takes 4 bytes but will not be precise in terms of decimal

*Example*
### Example


```sql

mysql> CREATE TABLE datatype_demo(
    ->    ID INT,
    ->    NAME VARCHAR(50),
    ->    HEIGHT FLOAT(20)
    -> );
Query OK, 0 rows affected (0.10 sec)

mysql> insert into datatype_dem^C
mysql> INSERT INTO datatype_demo (ID, NAME, HEIGHT) VALUES
    -> (1, 'Alice', 165.5),
    -> (2, 'Bob', 180.0),
    -> (3, 'Charlie', 172.3);
Query OK, 3 rows affected (0.02 sec)
Records: 3  Duplicates: 0  Warnings: 0

mysql> INSERT INTO datatype_demo (ID, NAME, HEIGHT) VALUES
    -> (4, 'Diana', 12345678901234567890.123456789);
Query OK, 1 row affected (0.02 sec)

mysql> select * from datatype_demo;
+------+---------+------------+
| ID   | NAME    | HEIGHT     |
+------+---------+------------+
|    1 | Alice   |      165.5 |
|    2 | Bob     |        180 |
|    3 | Charlie |      172.3 |
|    4 | Diana   | 1.23457e19 |
+------+---------+------------+
```
Query OK, 0 rows affected (0.03 sec)





#### DOUBLE 
- its very precise but aukaad anusaar, it will take storage space also


### string types 
#### char=> cares about fixed size. 
eg: 
```sql
char(3) -- this will make it fixed
```
#### varchar  ==> cares about maximum size 


