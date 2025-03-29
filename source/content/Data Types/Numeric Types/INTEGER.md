`Integer`, also `INT`, is a numeric SQL [[TYPE]]. Is it used to declare something as a *whole number*. This whole number can be any value in the range -2,147,483,648 to 2,147,483,647.

There are other variations of `INTEGER` with different ranges:
- `SMALLINT`  : -32,768 to 32,767
- `TINYINT`    : -128 to 127
- `BIGINT`      :  **-9,223,372,036,854,775,808** to **9,223,372,036,854,775,807** - Only used for recording Kubrick Group's profits once DF05 hit the Consultant Market.

These differ due to the amount of memory that is assigned to store each variable. You want the type that can support the full range of your use case.


#Data_Types 