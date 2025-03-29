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

As previously stated, grouping is very useful when performed alongside [[AGGREGATE FUNCTIONS]] so check these out for some more examples.
# Example
```sql
SELECT
	employee_name
	,week_commencing
	,SUM(hours_worked) AS hours_worked_per_week
	,COUNT(*) AS days_worked_per_week
FROM
	employees
GROUP BY
	employee_id
	,employee_name
	,week_commencing
```
*NOTE:* Things to note about this query:
1. We group on each non-aggregate column that we want to return i.e. on `employee_id`, `employee_name`, and `week_commencing`.
2. Even though we group by `employee_id`, `employee_name` is more useful to the human reader of the result so we don't need to include it in the `SELECT` statement.
3. Even though grouping by`employee_name` won't change the groupings (because it will already be unique for each `employee_id`), we still need to group on this column so that it can appear in the results

# Intuition
*IMPORTANT:* Something to keep in mind is that because GROUP BY 'squashes' many rows down to a single row, you cannot have different values within each 'group' - (because which value would you display?). Hence, if you want to retrieve a specific column when using GROUP BY, that column needs to be added to the group by statement.




#Query_Design_and_Logic 