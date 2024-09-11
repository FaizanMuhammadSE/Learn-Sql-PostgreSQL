- SQL Statement Execution Pattern

  1. FROM (TABLE SELECTION)
  2. WHERE (FILTERING ROWS)
  3. SELECT (SELECTING SPECIFIC COLS)

- [Operations] Below is a list of operators used in PostgreSQL for filtering records:

  - `=`: Equal to.

  ```sql
  SELECT * FROM employees WHERE department = 'Sales';
  ```

  - `<>` or `!=`: Not equal to.

  ```sql
  SELECT * FROM employees WHERE department <> 'Sales';
  ```

  - `<`: Less than.

  ```sql
  SELECT * FROM employees WHERE salary < 50000;
  ```

  - `<=`: Less than or equal to.

  ```sql
  SELECT * FROM employees WHERE salary <= 50000;
  ```

  - `>`: Greater than.

  ```sql
  SELECT * FROM employees WHERE salary > 50000;
  ```

  - `>=`: Greater than or equal to.

  ```sql
  SELECT * FROM employees WHERE salary >= 50000;
  ```

  - `AND`: Logical AND.

  ```sql
  SELECT * FROM employees WHERE department = 'Sales' AND salary > 50000;
  ```

  - `OR`: Logical OR.

  ```sql
  SELECT * FROM employees WHERE department = 'Sales' OR department = 'Marketing';
  ```

  - `NOT`: Logical NOT.

  ```sql
  SELECT * FROM employees WHERE NOT department = 'Sales';
  ```

  - `BETWEEN`: Within a range (inclusive).

  ```sql
  SELECT * FROM employees WHERE salary BETWEEN 50000 AND 100000;
  ```

  - `LIKE`: Pattern matching using wildcards.

  ```sql
  SELECT * FROM employees WHERE name LIKE 'J%';
  ```

  - `ILIKE`: Case-insensitive pattern matching using wildcards.

  ```sql
  SELECT * FROM employees WHERE name ILIKE 'j%';
  ```

  - `IN`: Matches any value in a list.

  ```sql
  SELECT * FROM employees WHERE department IN ('Sales', 'Marketing');
  ```

  - `IS NULL`: Checks for null values.

  ```sql
  SELECT * FROM employees WHERE manager_id IS NULL;
  ```

  - `IS NOT NULL`: Checks for non-null values.

  ```sql
  SELECT * FROM employees WHERE manager_id IS NOT NULL;
  ```

  - `EXISTS`: Checks for the existence of rows in a subquery.

  ```sql
  SELECT * FROM employees WHERE EXISTS (SELECT 1 FROM departments WHERE departments.id = employees.department_id);
  ```

  - `ANY`: Compares a value to any value in a list or subquery.

  ```sql
  SELECT * FROM employees WHERE salary = ANY (SELECT salary FROM employees WHERE department = 'Sales');
  ```

  - `ALL`: Compares a value to all values in a list or subquery.

  ```sql
  SELECT * FROM employees WHERE salary > ALL (SELECT salary FROM employees WHERE department = 'Sales');
  ```

- Compound Where Clause
  - Various conditions can be applied in Where clause
