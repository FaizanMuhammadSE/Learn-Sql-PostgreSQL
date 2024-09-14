- **_Group By_**

  - Reduces many rows down to fewer rows
  - It actually segregates rows in the form of groups, each row belong to a group
  - _Can't select ungrouped columns, just that columns can be accessed which are part of group-by clause_
  - _Ungrouped columns can just be accessed when using aggregate \_functions_

- **_Aggregates_**
  - Reduces many values down to one value
  - Can be used with group by to reduce many rows down to fewer rows
  - Some aggregate functions are
    - **Count():** returns the number of values in a group of values
    - **Sum():** finds the sum of group of numbers
    - **AVG():** Finds the average of a group of numbers
    - **Min():** returns the minimum value from a group of numbers
    - **Max():** returns the maximum value from a group of numbers
- Aggregate functions can be used with or without group by clause
- When using aggregates functions, we can't select non-aggregated columns, until we use group-by on non-aggregated column

  - **Incorrect Query**

  ```
   SELECT product, SUM(quantity)
   FROM sales;
  ```

  - **Correct Query**

  ```
   SELECT product, SUM(quantity)
     FROM sales
     GROUP BY product;
  ```

- **_Key Points About Count_**

  - Use `COUNT(*)` when you need the total number of rows.
  - Use `COUNT(column_name)` when you need the count of non-`NULL` values in a specific column.
  - Use `Count(*)` with `GROUP BY` to get number of rows for each group

- **_WHERE VS HAVING_**
  - **WHERE Clause:**
    - Used to filter rows before any groupings are made.
    - Cannot be used with aggregate functions.
    - Example:
      ```sql
      SELECT product, quantity
      FROM sales
      WHERE quantity > 10;
      ```
  - **HAVING Clause:**
    - Used to filter groups after the `GROUP BY` clause has been applied.
    - Can be used with aggregate functions.
    - Example:
      ```sql
      SELECT product, SUM(quantity)
      FROM sales
      GROUP BY product
      HAVING SUM(quantity) > 100;
      ```
