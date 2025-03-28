# Overview
Aggregate functions are used to perform functions on groups of rows at a time. 

Each function will perform differently and can take different [[TYPE]]s as input. For example, `COUNT()` acts on the number of rows so it can take any value, whereas `SUM()` performs addition so you must pass numerical types ([[FLOAT]], [[INTEGER]], [[DECIMAL]] etc.).

The most important thing to understand about aggregate functions is what group the function is going to act on. This has been covered in [[GROUP BY]]. The best way to visualize this is just to make a query with some example data first so you know what your grouping is currently returning. 

**NOTE:** Aggregate functions will ignore `NULL` values - i.e. if you are counting over `column_name` and there is a `NULL` value for the `column_name` entry, `COUNT` will ignore it and not increase the count. If you want to make sure values aren't skipped, use a `NULL` handling function like [[COALESCE]] or [[NULLIF]].
# Syntax
### GROUP BY Syntax
```sql
SELECT
	AGGREGATE_FUNCTION(target_column) AS alias
FROM
	target_table
GROUP BY
	grouping_column
```

### Window Function Syntax
```sql
SELECT
	AGGREGATE_FUNCTION(target_column) OVER (PARTITION BY grouping_column ORDER BY ordering_column) AS alias
	,some_other_column
FROM
	target_table
```
# Common Aggregate Functions
- [[COUNT]]
- [[SUM]]
- [[AVG]]
- [[MIN]]
- [[MAX]]

# Example
```sql

```


# Intuition



#kubricksqlnote
