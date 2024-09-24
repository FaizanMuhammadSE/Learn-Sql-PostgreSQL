#### GREATEST

The GREATEST function returns the greatest value in a list of values **_for each row_**
Syntax:
GREATEST (value1, value2, ..., valueN)

Example:
GREATEST (10, 20, 30, 40) returns 40

Example
SELECT GREATEST(30, weight \* 2) FROM phones;

#### LEAST

The LEAST function returns the least value in a list of values **_for each row_**
Syntax:
LEAST (value1, value2, ..., valueN)

Example:
LEAST (10, 20, 30, 40) returns 10

Example
SELECT LEAST(30, weight \* 2) FROM phones;

#### CASE

The CASE function allows you to perform conditional logic in your SQL queries.
Syntax:

```
CASE
WHEN condition THEN result
[WHEN condition THEN result]
...
[ELSE result]
END
```

Example

```
SELECT
    name,
    price,
    CASE
        WHEN price > 100 THEN 'Expensive'
        WHEN price < 50 THEN 'Cheap'
        ELSE 'Average'
    END
FROM products;
```
