- Database designing is a critical step
- Normally there are multiple tables in a single database
- Each table represent entities
- Tables have relations with each other
  1. one-to-one
  2. one-to-many
  3. many-to-one
  4. many-to-many
- These relationships represented through Primary Key & Foreign Key
  - Primary Key is a unique identifier for each row in a table
  - Foreign Key is a reference to other table row
  - The **_Many_** side of the relationship gets the Foreign Key column
- Primary Key and Foreign Key should set while creating Tables

  - For Primary Key Setting in PostgreSQL
  - **_SERIAL_** keywords serves the purpose of auto generation of key

  ```
  CREATE TABLE boats (id INTEGER SERIAL PRIMARY KEY, name VARCHAR);
  ```

  - Foreign Key can't have Non-Existing PK value
  - Foreign Key can have Null or duplicated PK value
  - For Foreign Key Setting in PostgreSQL

  ```
  CREATE TABLE boat_crew (id INTEGER SERIAL PRIMAY KEY, username VARCHAR, boat_id REFERENCES boats(id))
  ```

  - Primary Key Delete Constraints (when we try to delete a row in table, but its Foreign Key exists in related tabel)
  - We normally set these constraints while setting foreing key in a table

    - **ON DELETE CASCADE**: Automatically deletes the rows in the child_table / foreign_key_rows when the corresponding row in the parent table is deleted.
    - **ON DELETE SET NULL**: Sets the Foreign Key column to NULL when the corresponding row in the parent table is deleted.
    - **ON DELETE RESTRICT**: Prevents the deletion of a row in the parent table if there are matching rows in the child table.
    - **ON DELETE NO ACTION**: Similar to RESTRICT, but the check is done after attempting to delete the row.
    - **ON DELETE SET DEFAULT**: Sets the Foreign Key column to its default value when the corresponding row in the parent table is deleted.
  - Example

  ```
    CREATE TABLE boat_crew (
      id INTEGER SERIAL PRIMAY KEY, username VARCHAR, boat_id REFERENCES boats(id) ON DELETE CASCADE
    );
  ```
