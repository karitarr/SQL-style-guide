# SQL Style Guide

This is Airbnb's SQL Style Guide.

Airbnb also maintains a [JavaScript Style Guide][airbnb-javascript].

## Table of Contents
  1.  [Whitespace](#whitespace)
      1. [Indentation](#indentation)
      1. [Inline](#inline)
      1. [Newlines](#newlines)
  1.  [Line Length](#line-length)
  1.  [Commenting](#commenting)
  1.  [Misc.](#misc.)
      

## Whitespace

### Indentation

* Use soft-tabs with a two space-indent.
* Alight `SELECT` statements beginning with a comma or have all on the same line.

* Use spaces before and after operators
* Align parameters following keywords on a new line and indent 2 spaces

    ```sql
    SELECT
      *
    FROM
      reservation2s
    WHERE
      status = 1
    ```

### Inline

* 100 character limit
* For calculated strings(?) put each parameter on a new line beginning with the operator

```sql

    # good 
    SELECT
      SUM(
        ROUND(
          (
            total_payout_cents_host_currency
            - reconciled_payout_cents_host_currency
            - GREATEST(
                liable_payout_cents_host_currency - reconciled_payout_cents_host_currency,
                0
              )
          ) / fx.rate
        )
      ) / 100 AS 'Future Host Payout (2620)'
     
      # bad
    ```



### Newlines

## Line Length
## Commenting
## Misc
* Keywords should be in all caps


