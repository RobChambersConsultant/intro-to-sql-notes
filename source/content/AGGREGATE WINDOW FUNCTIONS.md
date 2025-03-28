# Overview
Aggregate window functions are used to perform [[AGGREGATE FUNCTIONS]] on column(s) without collapsing the rows as you would when using [[GROUP BY]]. 

# Syntax
```sql
SELECT
	AGGREGATE_FUNCTION(target_column) OVER (PARTITION BY partition_column ORDER BY order_column) AS column_alias
FROM
	target_table
```
Explanation of syntax:
- `AGGREGATE_FUNCTION` refers to any of the functions found in [[AGGREGATE FUNCTIONS]]
- `target_column` refers to the column you want to perform the aggregate function on
- `OVER` is a keyword used to show that the aggregate function is being performed as a window function rather than using a `GROUP BY`
- `PARTITION BY` is the window function equivalent of `GROUP BY` - it tells the SQL engine how to group your rows before performing the aggregate function.
- `ORDER BY` is used to add an order to the results in each group.
# Common use case
Common use cases include:
- Calculating a running average or cumulative sum
- Calculating a total `SUM` or `COUNT` without collapsing rows
- Calculating in-line percentages

# Example
#### Total Sum and Cumulative Sum
See example in [[GROUP BY Vs  PARTITION BY]].

#### Calculating In-line Percentage
```sql
SELECT
	category_id
	,name AS category_name
	,COUNT(name) AS category_frequency
	,COUNT(*) * 1.0 / SUM(COUNT(*)) over() AS category_percentage
FROM
	category
GROUP BY
	category_id
	,name
```
Explanation:
`COUNT(*)` counts all rows for each `category_id` and category name. This is called `category_frequency` - the number of times a given category appears in the table.

`SUM(COUNT(*)) OVER ()` sums each `COUNT` value in the table - this is because there is no `PARTITION BY` criteria in `OVER ()` so it just counts the whole table as one big group. 

Something to note that is not clear at first is that the `COUNT()` functions are using the `GROUP BY` columns as their grouping conditions, whereas the `SUM` function is using the condition in the `OVER ()` statement as its grouping condition.

If this seems confusing to you, **don't stress** - it will make sense eventually, and in the meantime (and the exam) you can just copy and paste `COUNT(*) * 1.0 / SUM(COUNT(*)) over()` whenever you want to calculate a percentage.

# Intuition
This is probably one of the topics that is hardest to get a good intuition for. I'll give you a couple of loose rules of thumb to help you think through when and how you might want to use them:
1. Do I want to perform a function from [[AGGREGATE FUNCTIONS]] but keep all my rows?
2. Do I want to calculate a percentage, or another statistic that is different for each row but depends on the whole table. Some more examples of these are:
	1. Differences from the mean
	2. Percentage difference  
	3. Percentage of the Total
3. Am I using `GROUP BY` already? If so, what will the groups look like after this grouping is done (run an example query to see). It is this example table that your window function will run on. 


#kubricksqlnote
