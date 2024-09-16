- **Sorting is very easy in SQL**

  - Use `SORT BY` keyword to sort on any column
  - By default sort is `ASC` (ascending)
  - For descending, mention explicitly in query using `DESC` keyword
  - Can use multiple column_names comma separated for a fallback sorting, when 2 or more rows are same
  - Example of `SORT BY` with more than one column:

  ```sql
  SELECT *
  FROM employees
  ORDER BY department, salary DESC;
  ```

- **LIMIT Vs OFFSET**

  - `LIMIT`:

    - The `LIMIT` clause is used to specify the maximum number of records to return.
    - It is useful for pagination, where you want to display a subset of results.
    - Example: `SELECT * FROM table_name LIMIT 10;` will return the first 10 records from the table.

  - `OFFSET`:

    - The `OFFSET` clause is used to _skip_ a specific number of starting rows before return the rows.
    - It is often used in conjunction with `LIMIT` for pagination.
    - Example: `SELECT * FROM table_name LIMIT 10 OFFSET 20;` will skip the first 20 records and then return the next 10 records.
    - Example: `SELECT * FROM table_name SORT BY column_name DESC LIMIT 1 OFFSET 1;` it will return second largets record

  - As a best practice while use LIMIT before OFFSET, while using both at a same time in query, ALTHOUGH order won't effect the result
