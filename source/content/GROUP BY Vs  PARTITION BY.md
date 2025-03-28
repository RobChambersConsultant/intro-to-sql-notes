When to use `GROUP BY` versus `OVER ()` and `PARTITION BY` can sometimes cause some confusion.

`GROUP BY` and `PARTITION BY` are almost the exact same, except `PARTITION BY` keeps every row, whereas `GROUP BY` 'squashes' them down to a single row.

Therefore, as a rule of thumb, if you want to perform an [[AGGREGATE FUNCTIONS]] like `SUM` or `COUNT`, think to yourself:

>"Do I want to keep all the rows of this table, or do I want to compress them into a fewer number of rows?"

To answer the above question, have a look at the table you are trying to generate and look for repeated and/or incrementing values. Have a look at the following example:
#### Window Function
**How it is called:**
```sql
SELECT 
    person, 
    date, 
    km_ran, 
    SUM(km_ran) OVER (PARTITION BY person) AS total_km_ran
FROM Runs;
```
**What it returns:**

| person | date       | km_ran | total_km_ran |
| ------ | ---------- | ------ | ------------ |
| Alice  | 2024-03-24 | 5      | 16           |
| Alice  | 2024-03-25 | 7      | 16           |
| Alice  | 2024-03-26 | 4      | 16           |
| Bob    | 2024-03-24 | 3      | 11           |
| Bob    | 2024-03-25 | 6      | 11           |
| Bob    | 2024-03-26 | 2      | 11           |
*NOTE:*
- There is repetition in the `person` column
- The `total_km_ran` column is also repeating 
- There are unique values in the `date` and `km_ran` columns 

#### Incrementing Window Function
**How it is called:**
```sql
SELECT 
    person, 
    date, 
    km_ran, 
    SUM(km_ran) OVER (PARTITION BY person ORDER BY date) AS cumulative_km_ran
FROM Runs;
```
**What it returns:**

| person | date       | km_ran | cumulative_km_ran |
| ------ | ---------- | ------ | ----------------- |
| Alice  | 2024-03-24 | 5      | 5                 |
| Alice  | 2024-03-25 | 7      | 12                |
| Alice  | 2024-03-26 | 4      | 16                |
| Bob    | 2024-03-24 | 3      | 3                 |
| Bob    | 2024-03-25 | 6      | 9                 |
| Bob    | 2024-03-26 | 2      | 11                |
*NOTE:*
- There is repetition in the `person` column
- The `cumulative_km_ran` column is incrementing 
- There are unique values in the `date` and `km_ran` columns 
#### Group By
**How it is called:**
```sql
SELECT 
    person, 
    SUM(km_ran) AS total_km_ran
FROM Runs
GROUP BY person;
```
**What it returns:**

| person | total_km_ran |
| ------ | ------------ |
| Alice  | 16           |
| Bob    | 11           |
*NOTE:*
- There no repetition in the `person` column
- The `total_km_ran` column has the same value as the maximum values in the window function table
- There are no `date` and `km_ran` columns - which of the 3 different values would you put for each group 




#Query_Design_and_Logic 
#Problem_Solving_Strategy 
