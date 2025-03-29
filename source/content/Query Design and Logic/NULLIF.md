Another useful expression for handling `NULL`s, similar to [[COALESCE]].

`NULLIF` takes two inputs and compares if they are equal to each other. If they are equal, it returns `NULL`. This can be useful for avoiding things like divide-by-zero errors.

# Example
```sql
SELECT
	1 / NULLIF(numerical_column, 0) AS inverse_numerical_column
FROM
	target_table
```
`NULLIF` is used here to avoid a divide by zero error if the value of `numerical_column` is 0.