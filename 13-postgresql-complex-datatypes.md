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

### Boolean Types

- `true` `yes` `on` `1` `t` `y` will be considered as `TRUE`
- `false` `no` `off` `0` `f` `n` will be considered as `FALSE`
- `null` will be considered as `NULL`

### DATES and TIMES

- PostgreSQL is very flexible in terms of time
- We can imagine any format of time, postgresql gonna understand it and store in a same manner
- `DATE` type can store date in any format, e.g '1980 November 20', 'Nov 20, 1980'
- `TIME` or `TIME WITHOUT TIME ZONE` type can store time without time zone, it contains hours, minutes, seconds, AM/PM or even 24 hours format e.g '01: 23 AM', '05:23 PM', '20:34'
- `TIME WITH TIME ZONE` type can store time with time-zone, and eventually save it in UTC format e.g '01:23 AM EST' **->** 01:23-05:00 (-5 means 5 hours behind UTC)
- `TIMESTAMP WITH TIME ZONE` type can store everything related time like date, time, timezoen e.g 'NOV-20-1980 1:23 AM PST' **->** 1980-11-20 02:23:00-07

### INTERVAL

- Think of an interval as a duration of time
- `1 day` **->** `1 day`
- `1 D` **->** `1 day`
- `1 D 1 M 1 S` **->** `1 day 1 minute 1 second`
- Even though we can do operation on intervals adding, subtracting etc
- We can also add, subtraction intervals from data as well
