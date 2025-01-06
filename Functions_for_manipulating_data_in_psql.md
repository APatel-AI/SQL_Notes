# Common data types
## TEXT data types
  - CHAR, VARCHAR, and TEXT
- Numeric data types
  - INT and DECIMAL
- Date / time data types
  - DATE, TIME, TIMESTAMP, INTERVAL
- Arrays
      
# Date and time data types
## TIMESTAMP data types
- timestamps in sql use the ISO 8601 format: yyyy-mm-dd
- contain both daate and time values

## DATE and TIME data types (better option)
- DATE data types use an yyyy-mm-dd format
## INTERVAL data types
- INTERVAL types are representations of period of time

## EXAMPLE OF USING INTERVAL (SQL)
```
SELECT
 	-- Select the rental and return dates
	rental_date,
	return_date,
 	-- Calculate the expected_return_date
	rental_date + INTERVAL '3 days' AS expected_return_date
FROM rental;
```

# Working with ARRAYs
## CREATE TABLE example
```
CREATE TABLE my_first_table (
  first_column,
  second_column integer
);
```



## Inserting into the table created above
```
INSERT INTO my_first_table
  (first_column, second_column) VALUES ('text value', 12);
```


## Searching an ARRAY with ANY
- PostgreSQL also provides the ability to filter results by searching for values in an ARRAY. The ANY function allows you to search for a value in any index position of an ARRAY. Here's an example.
```
WHERE 'search text' = ANY(array_name)
```
When using the ANY function, the value you are filtering on appears on the left side of the equation with the name of the ARRAY column as the parameter in the ANY function.

### Excercise example
- Match 'Trailers' in any index of the special_features ARRAY regardless of position.

```
SELECT
  title, 
  special_features 
FROM film 
-- Modify the query to use the ANY function 
WHERE 'Trailers' = ANY (special_features);
```

## ARRAY a special type
- creating a simple table with 2 array columns
```
CREATE TABLE grades(
	student_id int,
	email text[][],
	test_scores int []
};
```

## Searching an ARRAY with @>
- The contains operator @> operator is alternative syntax to the ANY function and matches data in an ARRAY using the following syntax.
```
WHERE array_name @> ARRAY['search text'] :: type[]
```
### Excercise Example
- Use the contains operator to match the text Deleted Scenes in the special_features column.

```
SELECT 
  title, 
  special_features 
FROM film 
-- Filter where special_features contains 'Deleted Scenes'
WHERE special_features @> ARRAY['Deleted Scenes'];
```

# Adding & Subtracting date / time data
- subtracting date
  ```
  SELECT date '2005-09-11' - date '2005-09-10';
  ```

  The query above will result in an integer type of 1.

- adding date
  ```
  SELECT date '2005-09-11' + integer '3'; 
  ```
  The query above will result in a date value of '2005-09-14'

- subtracting time stamp data

  ```
  SELECT date '2005-09-11 00:00:00' - date '2005-09-09 12:00:00';

  ```
  The output of the query above is an interval, '1 day 12:00:00'

- Adding Date / time arthmetic using INTERVALs
  ```
  SELECT timestamp '2019-05-01' + 21 * INTERVAL '1 day';

  ```

# The String Concatenation operator
### Example
```
SELECT
	first_name,
	last_name,
	first_name || ' ' || last_name AS full_name
FROM customer

```
You can also use CONCAT() in psql

### Example
```
SELECT
	CONCAT(first_name, ' ', last_name) AS full_name
FROM customer;
```

### String concatenation with non-string input
```
SELECT
	customer_id || ': '
	|| first_name || ' '
	|| last_name AS full_name
FROM customer;
```

### Changing the case of string

```
SELECT
	UPPER(email)
FROM customer;
```
or 

``` 
SELECT
	LOWER(email)
FROM customer;
```

or

``` 
SELECT
	INITCAP(email)
FROM customer;
```

### Replacing characters in a string

use the replace function 'REPLACE()'
```
SELECT
	REPLACE(description, 'A Astounding', 'An Astounding') as description
FROM film;
```


## Determining the length of a string
use the function CHAR_LENGTH(): accepts a string as the input and returns the number of characters in the string as an integer for the output.
```
SELECT
	title,
	CHAR_LENGTH(title)
FROM film;
```

## Finding the position of a character in a string
use the function STRPOS(var, '' ): takes in 2 parameters the location and the thing you are looking for
```
SELECT
	email,
	STRPOS(email, '@')
FROM customer;
```

## Parsing string data
```
SELECT
	LEFT(description, 50)
FROM film;

```

## Extracting substrings of character data
use the SUBSTRING() function: it takes 3 parameters, 1: the source string or column, 2:integer value representing the start of the string, 3:the length of the substring you want to extract.
```
SELECT
	SUBSTRING(description, 10, 50)
FROM
	film AS f;
```

## Extracting substrings of character data
```
SELECT
	SUBSTRING(email FROM POSITION('@' IN email)+1 FOR CHAR_LENGTH(email))
FROM
	customer;
```



