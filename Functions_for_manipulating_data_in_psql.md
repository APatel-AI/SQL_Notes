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

