### MySQL Aggregate functions
- aggregate functions gather data from many rows of a table then aggragate it into a single value

### ```COUNT()```

- How many departments are there in the “employees” database? Use the ‘dept_emp’ table to answer the question.

```
SELECT 
    COUNT(DISTINCT dept_no)
FROM
    dept_emp
```

```COUNT(DISTINCT)``` - Return the number of unique values encountered in a give column

```COUNT(*)``` - Return the number of all rows of the table, ```NULL``` values included

