# Ruby Style Guide

This is Airbnb's Ruby Style Guide.

It was inspired by [Github's guide][github-ruby] and [Bozhidar Batsov's guide][bbatsov-ruby].

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
    
