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
