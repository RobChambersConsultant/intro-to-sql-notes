# Overview
`FROM` is used to tell the SQL engine which [[TABLE]] to extract data from. It is always paired with a [[SELECT]] statement.

When wanting to exact data from multiple different tables in the same query, you can use [[JOIN]]s.

# Syntax
When using `FROM`, you need to know which database you are currently in. For example, for DF05, our default database will be in `datalab_df05`. If you want to extract from a table that is outside of this database, there are 2 options: the [[USE]] keyword, or using the *absolute database reference*.

### USE
See [[USE]].
### Absolute Database Reference
This gives the SQL engine the *exact* path to the table you are looking for. It has the structure of [[DATABASE]].[[SCHEMA]].[[TABLE]]. See below for an example:
```sql
...
FROM
	[database_name].[schema_name].[table_name]
```

# Common use case
As with `SELECT` statements, this will be used with 

# Example
```sql
SELECT
	column_name_1
	,column_name_2
FROM
	name_of_database
```

# Intuition
The intuition is simple for this: you need to tell the SQL engine where to look for the data.

#Query_Design_and_Logic 