# SQL Style Guide


This is Airbnb's SQL Style Guide.

## Table of Contents
  1. [Structure](#structure)
  1. [Lists](#lists)
  1. [Joins](#joins)
  1. [Operators](#operators)
  1. [Expressions](#expressions) 
      1. [Parentheses](#parentheses)
      1. [Nested Functions](#nested-functions)
      1. [Nested Functions](#nested-functions)
  1.  [Naming Convensions](#naming-conventions)
  2.  [Commenting](#commenting)

      

## Structure
* Use soft-tabs with a two space-indent
* Place each keyword on a new line
* Clearly separate union queries by adding a line break before and after the ```UNION``` keyword

## Lists
* Wrap SELECT statements longer than 30 characters in the following way:

#### Style 1
The first value is placed on a new line, indented 4 spaces. The subsequent values are placed on new lines, beginning with commas. The value names are aligned. 
```sql
    SELECT
        id
      , start_date
      , guest_id
      , host_id      
    FROM
      reservation2s
```

#### Style 2
The first value is placed on a new line, indented 2 spaces. The subsequent values are placed on new lines, beginning with commas. The commas align with the first value. 
```sql
    SELECT
      id
      , start_date
      , guest_id
      , host_id      
    FROM
      reservation2s
```
#### Style 3
The first value is placed on a new line, indented 2 spaces. The subsequent values are placed on new lines, ending with commas.
```sql
    SELECT
      id, 
      start_date,
      guest_id,
      host_id,      
    FROM
      reservation2s
```

## Joins
####Style 1
 ```JOIN``` keyword is placed on a new line. The ```ON``` and ```AND``` keywords are moved to a new line and indented 2 spaces: 
```sql 
SELECT *
FROM reservation2s 
LEFT JOIN payment2s 
  ON reservation2s.id = payment2s.ref_model_id 
  AND payment2s.charge_successful
LEFT JOIN line_items 
  ON reservation2s.id = line_items.item_id 
  AND line_items.reconciled 
```
####Style 2
  The ```JOIN``` keyword is placed on a new line.The argument is placed on a new line and intended 2 spaces.The ```ON``` keyword is NOT placed on a new line. The arguments following ```ON``` are placed on a new line, indented 2 spaces and aligned.
```sql 
SELECT *
FROM 
  reservation2s 
LEFT JOIN 
  payment2s 
ON 
  reservation2s.id = payment2s.ref_model_id 
  AND payment2s.charge_successful
LEFT JOIN 
  line_items 
ON 
  reservation2s.id = line_items.item_id 
  AND line_items.reconciled
```

## Operators
* Use 1 space before and after operators

```base_price + extras_price - host_fee / nights```
```sql 
WHERE i.i = i2.max
```

## Expressions
* For complicated or long calculations put each expression on a new line beginning with the operator

```sql
  SELECT
      total_payout_cents_host_currency
    + reconciled_payout_cents_host_currency
    + liable_payout_cents_host_currency 
    AS 'Host Payout'
```

### Parentheses
#### Style 1
 Keep opening paren inline with the function. Place expressions on a new line and indent 2 spaces. Place closing paren on a new line and align with the function to close the block: 
```sql    
    SELECT
      SUM(
          total_payout_cents_host_currency 
        + liable_payout_cents_host_currency
      )
    FROM
      host_payout_helpers  
```
#### Style 2
 Place opening paren on a new line and indent 2 spaces  Place expressions on a new line and indent 2 spaces. Place closing paren on a new line and align with the function to close the block:
```sql
    SELECT
      SUM
        (
          total_payout_cents_host_currency 
        + liable_payout_cents_host_currency
        )
    FROM
      host_payout_helpers 
```
### Nested Functions
* When using functions with nested layers, align the opening and closing of the block either by putting just the expressions on a new line or the opening paren:
```sql
    SELECT
      SUM(
        ROUND(
            total_payout_cents_host_currency
            - GREATEST(
                liable_payout_cents_host_currency - reconciled_payout_cents_host_currency,
                0
              )
          ) / fx.rate
        )
      ) / 100 AS 'Host Payout'
 ```

### Subqueries
* For subqueries, place an open paren on a new line and intent 4 spaces. Place the SELECT statement on a new line and indent 2 spaces. Place the closing paren on a new line and align with opening paren. Place the alias on a new line and indent 2 spaces:
```sql
    SELECT *
    FROM 
      reservation2s
    JOIN
        (
          SELECT * 
          FROM reservation2s
          WHERE status = 1
        ) 
          inner_table
    ON innter_table.id = reservation2s.id
 ```

## Commenting
* Comments should begin with a hash followed by 2 spaces
* Comments should lie above the code, not inline
* Things that should have comments in SQL:
  - High level explanation in files with multiple queries
  - Complicated IF-THEN-ELSE or CASE WHEN statements
  - Derived tables that don't have an explanatory alias

## Naming Conventions
* The following should be in uppercase 
  - SQL keywords (e.g. ```SELECT```, ```FROM```, ```WHERE```) 
  - Built-in functions (e.g. ```SUM```, ```AVE```, ```CASE```, ````IF```)
  - Data types (e.g. ```INT```, ```CHAR```) 
* Use single quotation for characters, strings, binary and Unicode
* Use lower case and underscores for field names and tables names
* for currency fields follow the name with the denomination + currency + rate/timing:
```sql
revenue_cents_usd_at_booking
```
