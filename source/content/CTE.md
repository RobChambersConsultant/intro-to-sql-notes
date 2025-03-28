# Overview
CTE stands for Common Table Expression. As far as we're concerned, you can think about this as defining a [[SUBQUERY]] at the start of the SQL notebook and giving it a name so that it can be used again later in your code.

CTEs have 2 main benefits over subqueries:
1. **Readability** - you can separate a CTE from your main query which allows for segmentation of logic. This means someone reading your code (including you) can check the logic for the CTE query separately from the rest of the SQL query logic
2. **Reusability** - Where subqueries need to be repeated (copy and pasted) every time you want to use them, CTEs can be defined a single time, and then called as many times by just using the CTE name 

# Syntax
CTEs are defined by a `WITH` statement, followed by the CTE name, followed by `AS` and then the CTE query logic in brackets (parentheses), `()`.

When creating multiple CTEs, you only need to use a single `WITH` statement, and then separate your CTE definitions with commas.
```sql
WITH cte_1_name AS (
	CTE QUERY LOGIC
),
cte_1_name AS (
	CTE QUERY LOGIC
)
```

# Common use case
The most useful place we will see these is in STRING HANDLING. String handling is a huge pain in SQL and whoever put it in the course must be a sadist because there is no reason you wouldn't just do it in Python. That being said, you may as well make it as easy as you can for yourself by using a CTE.

The following example is from Question 2 of the string handling exercises.

# Example
```sql
USE misc;

WITH RawDataWithIndices AS (

    SELECT

        rawdata

        ,colon_index=CHARINDEX(';', rawdata)

        ,slash_index=CHARINDEX('/', rawdata)

        ,h_index=CHARINDEX('H', rawdata, CHARINDEX('/', rawdata))

        ,w_index=CHARINDEX('W', rawdata, CHARINDEX('/', rawdata))

        ,d_index=CHARINDEX('D', rawdata, CHARINDEX('/', rawdata))

    FROM
        rawdata_furniture
)

SELECT

    SUBSTRING(rawdata, 1, colon_index) AS item

    ,SUBSTRING(rawdata, colon_index+1, slash_index-colon_index-1) AS colour

    ,SUBSTRING(rawdata, h_index+1, w_index-h_index-1) AS height

    ,SUBSTRING(rawdata, w_index+1, d_index-w_index-1) AS width

    ,SUBSTRING(rawdata, d_index+1, 9999999) AS depth

FROM

    RawDataWithIndices

```

Here using a CTE to define a new column for the index of each character you are searching for makes the final query far easier to read - and easier to read SQL is easier to debug SQL so this is always a good thing. For a contrast, see the code below for the solution without using a CTE and compare how readable the final query is:

```sql
SELECT
    SUBSTRING(rawdata, 1, CHARINDEX(';', rawdata)) AS item
    ,SUBSTRING(rawdata, CHARINDEX(';', rawdata)+1, CHARINDEX('/', rawdata)-CHARINDEX(';', rawdata)-1) AS colour
    ,SUBSTRING(rawdata, CHARINDEX('H', rawdata, CHARINDEX('/', rawdata))+1, CHARINDEX('W', rawdata, CHARINDEX('/', rawdata))-CHARINDEX('H', rawdata, CHARINDEX('/', rawdata))-1) AS height
    ,SUBSTRING(rawdata, CHARINDEX('W', rawdata, CHARINDEX('/', rawdata))+1, CHARINDEX('D', rawdata, CHARINDEX('/', rawdata))-CHARINDEX('W', rawdata, CHARINDEX('/', rawdata))-1) AS width
    ,SUBSTRING(rawdata, CHARINDEX('D', rawdata, CHARINDEX('/', rawdata))+1, 9999999) AS depth
FROM
    rawdata_furniture
```
If you think this is a better and more readable solution, allow me to direct you to some [help]([therapy near me - Search](https://www.bing.com/search?q=therapy%20near%20me&qs=n&form=QBRE&sp=-1&ghc=1&lq=0&pq=therapy%20near%20me&sc=12-15&sk=&cvid=5C2C14E1A569481EBE19158D0A935B25&ghsh=0&ghacc=0&ghpl=)).
# Intuition
Think:
 >Is my code readable or is there too much going on?
 >
 >Am I using a subquery multiple times?
 



#kubricksqlnote
