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
      1. [File/class-level comments](#fileclass-level-comments)
      1. [Function comments](#function-comments)
      1. [Block and inline comments](#block-and-inline-comments)
      1. [Punctuation, spelling, and grammar](#punctuation-spelling-and-grammar)
      1. [TODO comments](#todo-comments)
      1. [Commented-out code](#commented-out-code)
  1.  [Methods](#methods)
      1. [Method definitions](#method-definitions)
      1. [Method calls](#method-calls)
  1.  [Conditional Expressions](#conditional-expressions)
      1. [Conditional keywords](#conditional-keywords)
      1. [Ternary operator](#ternary-operator)
  1.  [Syntax](#syntax)
  1.  [Naming](#naming)
  1.  [Classes](#classes)
  1.  [Exceptions](#exceptions)
  1.  [Collections](#collections)
  1. [Strings](#strings)
  1. [Regular Expressions](#regular-expressions)
  1. [Percent Literals](#percent-literals)
  1. [Rails Specific](#rails)
  1. [Be Consistent](#be-consistent)

## Whitespace

### Indentation

* Use soft-tabs with a two space-indent.

* Indent `when` as deep as `case`.

    ```sql
    case
    when song.name == 'Misty'
      puts 'Not again!'
    when song.duration > 120
      puts 'Too long!'
    when Time.now.hour > 21
      puts "It's too late"
    else
      song.play
    end

    kind = case year
           when 1850..1889 then 'Blues'
           when 1890..1909 then 'Ragtime'
           when 1910..1929 then 'New Orleans Jazz'
           when 1930..1939 then 'Swing'
           when 1940..1950 then 'Bebop'
           else 'Jazz'
           end
    ```

* Align function parameters either all on the same line or one per line.

    ```ruby
    # good
    def self.create_translation(phrase_id,
                                phrase_key,
                                target_locale,
                                value,
                                user_id,
                                do_xss_check,
                                allow_verification)
      ...
    end

    # bad
    def self.create_translation(phrase_id, phrase_key, target_locale,
                                value, user_id, do_xss_check, allow_verification)
      ...
    end
    ```
