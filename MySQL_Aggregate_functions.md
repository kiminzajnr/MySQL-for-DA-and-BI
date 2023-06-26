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

### ```SUM()```
- What is the total amount of money spent on salaries for all contracts starting after the 1st of January 1997?

```
SELECT 
    COUNT(salary)
FROM
    salaries
WHERE
    from_date > '1997-01-01';
```

### ```MIN()``` and ```MAX()``
- returns the maximum value of a column or minimum value of a column

```
SELECT 
    MAX(salary)
FROM
    salaries;
```

```SELECT 
    MIN(salary)
FROM
    salaries;
```

### ```AVG()```
- extracts the average value of all non-null values in a field
- What is the average annual salary paid to employees who started after the 1st of January 1997?

```
SELECT 
    AVG(salary)
FROM
    salaries
WHERE
    from_date > '1997-01-01';
```

### ```ROUND()```

```
SELECT 
    ROUND(AVG(salary), 2)
FROM
    salaries
WHERE
    from_date > '1997-01-01';
```