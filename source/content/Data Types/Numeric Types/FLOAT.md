`FLOAT` is a numeric [[TYPE]]. It IEEE 754 floating point representation - ignore this if you're not a nerd, it just means it can be used for science but not by the finance bros.

#### Syntax
```sql
FLOAT
```

You can also specify higher or lower precision:
```sql
FLOAT(24) -- Lower Precision
FLOAT(53) -- Higher Precision
```

If you want to do financial calculations and avoid rounding errors, use [[DECIMAL]] or [[NUMERIC]].