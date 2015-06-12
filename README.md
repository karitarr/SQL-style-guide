# SQL Style Guide

This is Airbnb's SQL Style Guide.

Airbnb also maintains a [JavaScript Style Guide][airbnb-javascript].

## Table of Contents
  1.  [Whitespace](#whitespace)
      1. [Indentation](#indentation)
      1. [New Lines](#new-lines)
      1. [Line Breaks](#line-breaks)
  1.  [Line Length](#line-length)
  1.  [Commenting](#commenting)
  1.  [Naming](#naming) 
  1.  [Misc.](#misc.)
      

## Whitespace

### Indentation
* Use soft-tabs with a two space-indent.
* Use spaces before and after operators
* Align all list items following keywords on a new line, indented 2 spaces
```sql
    # good
    SELECT
      *    
    FROM
      reservation2s
    WHERE
      status = 1

    #bad 
    SELECT *    
    FROM reservation2s
    WHERE status = 1
```
* Align  `SELECT` subordinates with each argument on a new line, beginning each line with the comma. Indenting the first argument 4 spaces.
```sql
    # good
    SELECT
        id
      , start_date
      , guest_id
      , host_id      
    FROM
      reservation2s

    #bad 
    SELECT
      id
      , start_date
      , guest_id
      , host_id      
    FROM
      reservation2s

    #bad 
    SELECT
      id, 
      start_date,
      guest_id,
      host_id      
    FROM
      reservation2s

    #bad 
    SELECT id, start_date, guest_id, host_id      
    FROM
      reservation2s
```


### New Lines
* 100 character limit
* For complicated or long calculations put each expression on a new line beginning with the operator

```sql
  SELECT
      total_payout_cents_host_currency
    + reconciled_payout_cents_host_currency
    + liable_payout_cents_host_currency 
    AS 'Host Payout'
```
### Parentheses
* preference??

```sql
    # option 1
    SELECT
      SUM(total_payout_cents_host_currency + liable_payout_cents_host_currency)
    FROM
      host_payout_helpers

    #option 2
    SELECT
      SUM(
          total_payout_cents_host_currency 
        + liable_payout_cents_host_currency
      )
    FROM
      host_payout_helpers  

    #option 3
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
* When using functions with nested layers, align the opening and closing of the block either by putting just the expressions on a new line or the opening paren.
```sql
    # option 1
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
 
### Line Breaks
## Line Length
## Commenting
## Naming
* Use lower case and underscores for field names, tables names
* Avoid excessive abbreviations
* TODO- how to name aliases??

## Capitalization
* The following should be in uppercase 
  - SQL keywords (e.g. SELECT, FROM, WHERE) 
  - Built-in functions (e.g. SUM, AVE, CASE, IF)
  - Data types (e.g. INT, CHAR) 
* Use single quotation for characters, strings, binary and Unicode


 
