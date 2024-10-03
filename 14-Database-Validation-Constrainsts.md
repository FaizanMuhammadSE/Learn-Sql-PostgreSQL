- In Row level validation we check
  - Is a given value defined
  - Is a value unique in its column
  - Is a value <, >, <=, >=, = to some value
- We can set `NOT NULL` constraint on any column
  - Either at Table creation level
    ```
    CREATE TABLE products (
        id SERIAL PRIMARY KEY,
        name VARCHAR(40),
        price INTEGER NOT NULL,
        weight INTEGER
    )
    ```
  - Or After Table creation
    ```
    ALTER TABLE products
    ALTER COLUMN price SET NOT NULL;
    ```
  - But here is a gotcha, we can apply constraints on columns, if any value inside it is voilating rule, so either we have to delete that row, or change value of that specific cell, after that we can apply constraint
- We can provide default value for a column, if we won't provide its value, then instead of SAVING null, that default value will be considered
- We can set `UNIQUE` constraint on any column
  - Either at table creation level or after table creation, but got error if any previous value is not meeting constraint, have to resolved that first
    ```
    ALTER TABLE products
    ADD UNIQUE (name); // brackets are mandatory, it help in applying multi-column uniqueness
    ```
  - We can apply multi-level column uniquess constraints, means combination of that columns should be unique
    ```
    ALTER TABLE products
    ADD UNIQUE (name, department); // brackets are mandatory, it help in applying multi-column uniqueness
    ```
- We can add validation check, either at Table creation level or after creation
  - At Table Creation
    ```
    CREATE TABLE products (
        id SERIAL PRIMARY KEY,
        name VARCHAR(40),
        price INTEGER CHECK (price > 0),
        weight INTEGER
    )
    ```
  - After table creation
    ```
    ALTER TABLE products
    ADD CHECK (price > 0)
    ```
  - Even we can apply check over **muliple-columns**
    ```
    CREATE TABLE orders (
        id SERIAL PRIMARY KEY,
        productId FOREIGN KEY,
        creation_time NOT NULL,
        estimated_delivery_time NOT NULL,
        CHECK (estimated_delivery_time > creation_time)
    )
    ```
- We can set `PRIMARY KEY` constraint on any column
- We can set `FOREIGN KEY` constraint on any column
- Logically speaking we should apply validation on both levels, on server level or DB level, mostly critical validations on DB level and rest on server
  | WEB SERVER | DATABASE LEVEL |
  |------------|----------|
  | Easier to express more complex validation | Validation still applied if you event connect with a diff client/server |
  | Far easier to apply new validation rules | Guaranteed that validation will always applied |
  | Many libraries to handle validation automatically | Can only apply new validation rules if existing data satisfies it |
