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

### ```IFNULL() and COALESCE()```

```IFNULL(expression_1, expression_2)```
- returns the first of the two indicated values if data value found in the table is not null, returns the second value if there is a null value
- can have only two arguments

```COALESCE(expression_1, expression_2 ..., expression_N)```
- allows you to insert more the two arguments in the parentheses as opposed to ```IFNULL``` which allows only two parameters
- can have one, two, or more arguments

- Select the department number and name from the ‘departments_dup’ table and add a third column where you name the department number (‘dept_no’) as ‘dept_info’. If ‘dept_no’ does not have a value, use ‘dept_name’

```
SELECT 
    dept_no, dept_name, IFNULL(dept_no, dept_name) AS dept_info
FROM
    departments_dup;
```
