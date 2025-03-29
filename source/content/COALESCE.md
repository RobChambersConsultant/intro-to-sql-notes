Top 5 SQL function right here. It is used for handling `NULL` values - if the value is `NULL`, it is replaced by a default value that you specify - often 0 for numeric data and an empty string for text data but it will depend on context.

# Syntax
```sql
SELECT
	COALESCE(nullable_column, default_value) AS alias
FROM
	target_table
```
Here, `nullable_column` is the column you are checking for `NULL` values. `default_value` is, unsurprisingly, the default value that function will return if `nullable_column` is `NULL`.

# Example

