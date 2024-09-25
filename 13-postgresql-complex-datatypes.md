- There are various Categories of types
- Each category has further lot of options to decide
- Categories like Number, Boolean, Character etc

### Numbers

- We will learn some fast rules for Numeric Types
  1. ID column of any Table **->** Mark the column as `serial` or `smallserial` or `bigserial`
  2. Need to store a number without decimal **->** Mark the column as `integer`
  3. Need to store a number with a decimal and this data need to be very accurate **->** Mark the column as `numeric` or `decimal`
     - Bank Balance, grams of gold, scientific calculations
  4. Need to store a number with a decimal and the decimal doesn't make a big difference **->** Mark the column as `double precision` or `float` or `real`
     - Kilograms of trash in a landfill, liters of water in a lake, air pressure in a tire
