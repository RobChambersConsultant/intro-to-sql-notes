A numerical data [[TYPE]] used to specify the precision of non-integer numbers.
### Syntax
```sql
DECIMAL(total_digits, digits_after_decimal_point)
```

### Example
To specify a number that has 5 total digits, with 3 before the decimal point and 2 after, you would write:
```sql
DECIMAL(5,2)
```
This would allow numbers that look like `xxx.xx` e.g. `121.33`. This is a useful number for monetary value that are less than £1000.