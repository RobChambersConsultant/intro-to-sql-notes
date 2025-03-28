A foreign key is just the primary key of another database that is used to 'link' two databases together. This 'link' defines the relationship between 2 tables. 

Foreign keys can be both *duplicate* and [[NULL]] depending on the relationship between the tables:
- If the table has one to many relationship - e.g. many employees having the same manager - there may be *duplicate* foreign keys.
- If there can be no instances of a foreign key in a database - e.g. the CEO does not have a manager therefore no foreign key is appropriate - then the column will be `NULLABLE`.