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



# DATA TYPES: 
### numeric types

 - `int` 

### string types
- NOT NULL 
