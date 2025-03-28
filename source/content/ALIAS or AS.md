# Overview
Used to rename objects in SQL. Here objects can mean anything: [[TABLE]], [[SUBQUERY]], [[CTE]], [[COLUMN]] etc.

# Syntax
```sql
object_to_be_renamed AS new_object_name
```

# Common use case
The most common use cases for aliasing are naming new columns and naming CTEs. The only time you *need* to use an alias is when creating a [[CTE]].  

It is also commonly used to shorten or abbreviate table names during [[JOIN]]s.

# Example
```sql
SELECT
	t.column_1
	,t.column_2
	,FUNCTION(t.column_1) AS new_column_name
FROM
	very_very_long_table_name as t
```


# Intuition
Renaming data objects for clarity to the *human* reader of the SQL file. 


#kubricksqlnote
