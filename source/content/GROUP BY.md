# Overview
`GROUP BY` is used to group rows by a given column(s) or condition - squashes rows down to a single row that all meet that criteria.

If grouping by multiple columns, the grouping will be done in the order that the columns are specified in the query after the `GROUP BY` statement.

Grouping allows [[AGGREGATE FUNCTIONS]] to be used - they cannot be used without using a group by statement.

*NOTE:* Aggregate functions can be used with [[AGGREGATE WINDOW FUNCTIONS]], but used [[PARTITION BY]] instead of group by. See [[GROUP BY Vs  PARTITION BY]].



# Syntax
```sql
SELECT
	*
FROM
	table_name
GROUP BY
	column_1, column_2
```

# Common use case
`GROUP BY` is used when you want to extract properties of groups of data. Common groups might be:
- Grouping by `employee_id` to get information about each employee
- Grouping by date to get information on everything that happened on a given day
- Grouping by country, and then city name to get information on each city within a country

# Example
```sql

```


# Intuition
*IMPORTANT:* Something to keep in mind is that because GROUP BY 'squashes' many rows down to a single row, you cannot have different values within each 'group' - (because which value would you display?). Hence, if you want to retrieve a specific column when using GROUP BY, that column needs to be added to the group by statement.




#kubricksqlnote
