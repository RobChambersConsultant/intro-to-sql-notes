# Overview
`CONSTRAINT`s are limits or rules for relationships or values in SQL. This is done when creating tables to see [[CREATE]] first if you are unsure on how to do this.

They are most commonly seen when defining [[TABLE]]s.

For example, if you wanted to make sure that the `age` column in a table is between 0 and 120, you would use a `CHECK` constraint in the column definition. See below for the syntax for this example. 

Another type of constraint is [[FOREIGN KEY]] definition. 
# Syntax
#### `CHECK` constraints.
```sql
CREATE TABLE table_name (
    id INT PRIMARY KEY AUTO_INCREMENT, -- Primary key definition key can change
    column_1 TYPE CHECK (constraint_condition)
);
```
#### Foreign Key Syntax
```sql
CREATE TABLE Orders (
    primary_key_name INT PRIMARY KEY AUTO_INCREMENT,
    foreign_key_name INT, -- The foreign key name in this table
    CONSTRAINT constraint_error_name FOREIGN KEY (foreign_key_name) REFERENCES ForeignTableName(primary_key_in_other_table) ON DELETE CASCADE
);
```

*NOTE:* `ON DELETE CASCADE` here means that if the row being referenced in the other table is deleted, delete all rows in this table that reference that row.

# Example
#### Check Constraints
```sql
CREATE TABLE persons (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100) NOT NULL,
    age INT CHECK (age BETWEEN 0 AND 120)
);
```

#### Foreign Key Constraints
```sql
CREATE TABLE Customers (
    customer_id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100) NOT NULL
);

CREATE TABLE Orders (
    order_id INT PRIMARY KEY AUTO_INCREMENT,
    customer_id INT,
    order_date DATE NOT NULL,
    CONSTRAINT fk_customer FOREIGN KEY (customer_id) REFERENCES Customers(customer_id) ON DELETE CASCADE
);
```

# Intuition
The reason check constraints exist is to limit the amount of checks that need to be done at query time. You don't want to have to check whether a number is within a given range or of the correct type every single time you write or make a query. It is a lot easier to do this check a single time when writing to the database, and then you can be sure of the data integrity when reading.

The reason foreign key constraints exist is to make sure that table dependencies are reliable. If you table is dependent on another table, you want to make sure that you aren't referencing a row in a database that doesn't exist (anymore, if its been deleted).



#kubricksqlnote
