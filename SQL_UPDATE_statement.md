#### Transaction Control Language

##### the COMMIT statement
- saves the transaction in the database
- changes cannot be undone

##### the ROLLBACK statement
- allows you to take a step back
- the last change(s) made will not count
- reverts to the last non-committed state

### The SQL UPDATE Statement
- used to update the values of existing records in a table

```
UPDATE table_name
SET column_1 = value_1, ... column_n = value_n
WHERE conditions;
```
*all rows will be updated if you don't provide a WHERE condition*

```
SET 
    first_name = 'Stella',
    last_name = 'Parkinson',
    birth_date = '1990-12-31',
    gender = 'F'
WHERE
    emp_no = 9999901;
```