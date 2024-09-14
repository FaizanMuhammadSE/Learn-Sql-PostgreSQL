- Joins

  - Produces values by merging together rows from different related tables
  - Use a join most times that you're asked to find data that involves multiple tables

- Aggregation

  - Looks at many rows and calculates a single value
  - Words like 'most', 'average', 'least' are a sign that you need to use an aggregation

- Some Insights about Joins
  - Table order between **FROM** and **JOIN** frequently makes a difference
  - We must give context if column names collide
  - Tables can be renamed using the **AS** keyword
  - There are 4 kinds of JOINS
    1. INNER JOIN (just matched)
    2. LEFT OUTER JOIN **_(matched, and all the non-matching in Left Table)_**
    3. RIGHT OUTER JOIN **_(matched, and all the non-matching in Right Table)_**
    4. FULL OUTER JOIN **_(matched, and all the non-matching from both Tables)_**
