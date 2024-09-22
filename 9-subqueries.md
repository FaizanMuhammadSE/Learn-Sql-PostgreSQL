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
