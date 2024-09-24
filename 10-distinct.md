#### Distinct

- The distinct keyword is used to specify that the result of the query should contain only unique values.

  **For Example**

  ```
  SELECT DISTINCT column_name FROM table_name;
  ```

  This will return all unique values in the specified column.

- We can also count the number of rows

  **For Example**

  ```
  SELECT COUNT(DISTINCT column_name) FROM table_name;
  ```

- Distinct can be applied on more than 1 column as well, to get unique combinations of columns

  **For Example**

  ```
  SELECT DISTINCT column1, column2 FROM table_name;
  ```
