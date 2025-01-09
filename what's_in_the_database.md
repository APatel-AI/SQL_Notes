# What's in the database ?
- Database client
- Entity relationship diagram
# Column constrains
## Data types
- Common
  - Numeric
  - Character
  - Date/Time
  - Boolean
- Special
  - Arrays
  - Monetary
  - Binary
  - Geometric
  - Network Address
  - XML
  - JSON
  - and More!

# Casting with CAST()
format:
`SELECT CAST (value AS new_type)`

`SELECT CAST (3.7 AS integer)`

change the cast of an entire column
`SELECT CAAST (total AS integer)
  FROM price;`

alternative approach
format: 
`SELECT value::new_type;`
