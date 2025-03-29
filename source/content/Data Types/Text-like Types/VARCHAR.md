`VARCHAR` is a [[STRING]] type in SQL. It is used to specify a text-like value with a limit to the number of characters that can be held.

`VARCHAR` is a very common type as it is used to store almost all text-based values.

#### Syntax
```sql
VARCHAR(number_of_characters)
```
*NOTE:* Here, `number_of_characters` must be of [[INTEGER]] type. 

You can also use `max` to specify the maximum amount of text - used for large text up to 2Gb:
```sql
VARCHAR(MAX)
```