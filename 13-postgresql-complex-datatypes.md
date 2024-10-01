- There are various Categories of types
- Each category has further lot of types from which we can decide
- Categories like Number, Boolean, Character etc
- Categories like number have various types e.g SERIAL, BIGSERIAL, INTEGER, FLOAT, DOUBLE etc

### Numbers

- We will learn some fast rules for Numeric Types
  1. ID column of any Table **->** Mark the column as `serial` or `smallserial` or `bigserial`
  2. Need to store a number without decimal **->** Mark the column as `integer`
  3. Need to store a number with a decimal and this data need to be very accurate **->** Mark the column as `numeric` or `decimal`
     - Bank Balance, grams of gold, scientific calculations
  4. Need to store a number with a decimal and the decimal doesn't make a big difference **->** Mark the column as `double precision` or `float` or `real`
     - Kilograms of trash in a landfill, liters of water in a lake, air pressure in a tire

### CHARACTERS

- `CHAR(5)` **->** Store some characters, length will always be 5 even postgres has to insert spaces
- `VARCHAR` **->** Store any length of string
- `VARCHAR(40)` **->** Store any string up to 40 characters, automatically remove extra characters
- `TEXT` Store any length of string
