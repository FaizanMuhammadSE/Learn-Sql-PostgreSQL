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
  - For Foreign Key Setting in PostgreSQL
  ```
  CREATE TABLE boat_crew (id INTEGER SERIAL PRIMAY KEY, username VARCHAR, boat_id REFERENCES boats(id))
  ```
