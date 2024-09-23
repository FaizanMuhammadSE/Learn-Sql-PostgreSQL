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
