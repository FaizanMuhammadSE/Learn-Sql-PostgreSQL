- SQL is used to interact with various databases e.g

  - Oracle
  - MS SQL Server
  - MySQL
  - Postgres

- Challenges of Databases

  - Writing efficient queries to retrieve information
  - Designing schema, or structure, of the database
  - Understanding when to use advanced features
  - Managing the database in a production environment
    - Scaling, Backup etc

- During Database desing we will ask following questions from ourselves

  - What kind of thing are we storing? (Probably it will be a table)
  - What properties does this thing have?
  - What type of data does each of these properties contain? (string, number)

- Keywords

  - Tell database that we want to do something.
  - Always written out in **_capital_** letters

- Identifiers

  - Tell the database what thing we want to act on.
  - Always written out in **_small_** letters

- Column Data Types

  - VARCHAR: it is variable lenght character we can assume it like string, can mention maximum length as well, will get error if tried to exceed limit while entering record in DB
  - INTEGER: it stores integer from negative 2 billion to positive 2 billion

- Creating Table

  - `CREATE TABLE cities (name VARCHAR(50), population INTEGER);`

- Inserting Data in Table

  - `INSERT INTO cities (name, population) values ('Delhi', 234567), ('Lahore', '1000000');`
  - Just make sure insert data in the **_same order_** in which you mention column names

- Transforming

  - SQL isn't just about pulling raw data out of a table
  - We can write SQL to transform or process data before we receive it

- Retrieving
  - `SELECT * FROM table_name;`
  - `SELECT col_1, col_2 FROM table_name;`
  - ```SELECT col_1, col_2 * col_3 AS calculated_column
    FROM table_name;
    ```
- String Operators And Functions
  - || join two strings
  - CONCAT join strings
  - LOWER gives a lowecase string
  - LENGTH gives length of string
  - UPPER gives an uppercase string
