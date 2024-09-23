### Subqueries

- We can use/embed sub queries at various places in a query
- Subqueries can product
  - A single value
  - Set of Rows
  - A single Column
- In Subqueries understanding the shape of returned data is a main thing

### Rules of Subqueries

#### SELECT

- You can just use a subquery in select statement, if query is returning a single value e.g (one row, one column)

#### FROM

- We can write subquery in `FROM` as well
- Subquery must have an alias applied to it, otherwise will get error
- Query can return any type of data structure
- Example

```
SELECT name FROM (SELECT name, price FROM products) AS p
WHERE price > 500
```

```
SELECT max(p.avg_price) AS max_average_price
FROM
(SELECT manufacturer, SUM(price)/COUNT(*) AS avg_price
FROM phones
GROUP BY manufacturer) AS p
```

`OR`

```
SELECT max(p.avg_price) AS max_average_price
FROM
(SELECT manufacturer, AVG(price) AS avg_price
FROM phones
GROUP BY manufacturer) AS p
```

#### JOIN

- We can use subquery in join as well
- Subquery can return any type of data structure but should be be compatible with `ON`
- Example

```
SELECT p.name, c.name AS category_name
FROM products p
JOIN
(SELECT category_id, category_name
FROM categories WHERE category_id = 3) AS c
ON p.category_id = c.category_id
```

#### WHERE

- We can use subquery in `WHERE` clause as well
- Subquery can return any type of data structure but should be be compatible with the **_Operator_** in `WHERE` clause
- Operators Vs Subquery Data-Structure
  - Single Value
    - `<` | `>` | `>=` | `<=` | `=` | `<>` or `!=`
  - Single Column
    - `IN` | `NOT IN` | `> ALL` | `> SOME` | `< ALL` | `< SOME` | `>= ALL`| `>= SOME` | `<= ALL` | `<= SOME` | `= ALL` | `= SOME` | `<> ALL` | `<> SOME`
    - Note: ANY, SOME both keywords can be used for same purpose
    - Write a query that prints the name of all phones that have a price greater than all phones made by Samsung.
    - Solution
      ```
      SELECT name
      FROM phones
      WHERE price > ALL (
          SELECT price FROM phones WHERE manufacturer = 'Samsung'
      );
      ```

### Co-related Subqueries

- A subquery that depends on the outer query
- The term correlated subquery essentially means that we are referring to some row from the outside query in the inner/subquery
- In outside query we give alias, and inside subquery we access that row through alias
- Example: Show the name, department, and price of the most expensive product in each departement
- ```
  SELECT name, department, price
  FROM products AS p1
  WHERE p1.price = (SELECT MAX(price) FROM product AS p2 WHERE p2.department = p1.department)
  ```
- In Correlated SubQuery, subquery runs for each row

### SELECT without FROM

- We can use subquery in select, when subquery is returning a single value
- Example
- ```
  SELECT
   (SELECT MAX(price) FROM phones) AS max_price,
   (SELECT MIN(price) FROM phones) AS min_price,
   (SELECT AVG(price) FROM phones) AS avg_price,
  ```
