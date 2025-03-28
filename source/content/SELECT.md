# Overview
The most common and basic *key word* in SQL. This is used to extract data ([[COLUMN]]) [[FROM]] a [[DATABASE]].

# Syntax
SELECT needs to be followed by the columns names from the (database and) table you want to extract from. It is always followed by the [[FROM]] keyword.

Use `*` to reference every column in a database.

You can also create new columns by specifying a condition, which can be labelled with an [[ALIAS or AS]].

When selecting data from multiple tables (as you do when using a [[JOIN]]), it is best practice to write each column name as `table_name.column_name`.
# Common use case
Every SQL query in DQL will require a SELECT statement.

# Example
```sql
SELECT
	column_name_1
	,column_name_2
	,FUNCTION_NAME(column_name_1, column_name_2) AS new_column_name
FROM
	name_of_database
```

# Intuition
Telling the SQL engine which columns you want to appear in your final dataset.

#kubricksqlnote
