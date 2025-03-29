# Overview
If a [[COLUMN]] is `NULLABLE`, it means it is allowed to not have a value. When this is the call, the 'value' will be `NULL`.

# Syntax
```sql
NULL
or
NOT NULL
```

# Common use case
`NULL` is most commonly seen when performing a join (but not `INNER JOIN`) when matches cannot be found between the tables.

`NULL` is often seen when using a [[CREATE]] table statement in the definition of the columns to dictate whether or not that column can have empty values.


#Data_Types 
