# Unions , Intersections And Except in PostgreSQL

## UNION

The `UNION` operator is used to combine the result sets of two or more `SELECT` statements. It removes duplicate rows between the various `SELECT` statements.

### Syntax

```sql
SELECT column1, column2, ...
FROM table1
UNION
SELECT column1, column2, ...
FROM table2;
```

### Key Points

- Each `SELECT` statement within the `UNION` must have the same number of columns.
- The columns must also have similar data types.
- The columns in each `SELECT` statement must be in the same order.

### Example

```sql
SELECT city FROM customers
UNION
SELECT city FROM suppliers;
```

## UNION ALL

The `UNION ALL` operator is similar to `UNION`, but it includes duplicate rows in the result set.

### Syntax

```sql
SELECT column1, column2, ...
FROM table1
UNION ALL
SELECT column1, column2, ...
FROM table2;
```

### Example

```sql
SELECT city FROM customers
UNION ALL
SELECT city FROM suppliers;
```

## INTERSECT

The `INTERSECT` operator is used to return the result set of two or more `SELECT` statements that have matching rows.

### Syntax

```sql
SELECT column1, column2, ...
FROM table1
INTERSECT
SELECT column1, column2, ...
FROM table2;
```

### Key Points

- Each `SELECT` statement within the `INTERSECT` must have the same number of columns.
- The columns must also have similar data types.
- The columns in each `SELECT` statement must be in the same order.

### Example

```sql
SELECT city FROM customers
INTERSECT
SELECT city FROM suppliers;
```

## INTERSECT ALL

The `INTERSECT ALL` operator returns all rows that are common between the `SELECT` statements, including duplicates.

### Syntax

```sql
SELECT column1, column2, ...
FROM table1
INTERSECT ALL
SELECT column1, column2, ...
FROM table2;
```

### Example

```sql
SELECT city FROM customers
INTERSECT ALL
SELECT city FROM suppliers;
```

## EXCEPT

The `EXCEPT` operator is used to return the result set of one `SELECT` statement that does not appear in the result set of another `SELECT` statement.

### Syntax

```sql
SELECT column1, column2, ...
FROM table1
EXCEPT
SELECT column1, column2, ...
FROM table2;
```

### Key Points

- Each `SELECT` statement within the `EXCEPT` must have the same number of columns.
- The columns must also have similar data types.
- The columns in each `SELECT` statement must be in the same order.
- Result will be `diff` if queries position changed around Except

### Example

```sql
SELECT city FROM customers
EXCEPT
SELECT city FROM suppliers;
```

## EXCEPT ALL

The `EXCEPT ALL` operator returns all rows from the first `SELECT` statement that are not in the second `SELECT` statement, including duplicates.

### Syntax

```sql
SELECT column1, column2, ...
FROM table1
EXCEPT ALL
SELECT column1, column2, ...
FROM table2;
```

### Example

```sql
SELECT city FROM customers
EXCEPT ALL
SELECT city FROM suppliers;
```
