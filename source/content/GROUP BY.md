# Overview
`GROUP BY` is used to group rows by a given column(s) or condition - squashes rows down to a single row that all meet that criteria.

If grouping by multiple columns, the grouping will be done in the order that the columns are specified in the query after the `GROUP BY` statement.

Grouping allows [[AGGREGATE FUNCTIONS]] to be used - they cannot be used without using a group by statement.

*NOTE:* Aggregate functions can be used with [[AGGREGATE WINDOW FUNCTIONS]], but used [[PARTITION BY]] instead of group by. See [[GROUP BY Vs  PARTITION BY]].



# Syntax
```sql

```

# Common use case


# Example
```sql

```


# Intuition
*IMPORTANT:* Something to keep in mind is that because GROUP BY 'squashes' many rows down to a single row, you cannot have different values within each 'group' - (because which value would you display?). Hence, if you want to retrieve a specific column when using GROUP BY, that column needs to be added to the group by statement.




#kubricksqlnote
