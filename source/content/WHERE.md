# Overview
`WHERE` is one of the more straightforward keywords in SQL. It is used to provide a filter on the data that is extracted. You write a *condition* that can return True or False, and only results that match this criteria (i.e. the condition is True) are returned.

To negate this, and return rows where the condition is False, put `NOT` in front the condition.

Multiple conditions can be used simultaneously by linking them together with the [[AND]] and [[OR]] keywords.
# Syntax
```sql
SELECT
	*
FROM
	table_name
WHERE
	(condition_1)
	AND (condition_2)
	OR NOT (condition_3)
```

# Common use case
When you only want to extract data that match a given criteria e.g. querying for all employees who's timecards show less than 40 hours of work for a given week.
# Example
```sql
SELECT
	*
FROM
	employee_table
WHERE
	hours_logged < 40.0
	AND
	week_commencing = '2025-03-24'
```



#kubricksqlnote
