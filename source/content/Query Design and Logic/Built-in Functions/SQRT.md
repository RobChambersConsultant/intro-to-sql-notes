Calculates the mathematical square root of a column/value.

# Example
```sql
SELECT
	numeric_column
	,SQRT(numeric_column) AS sqrt_numeric_column
FROM
	target_table
```