### The SQL SELECT statement
- Allows you to extract a fraction of the entire data set
- used to retrieve data from database objects, like tables 
    *(query from database)*

```
SELECT column_1, column_2,... column_n
FROM table_name;
```

```
SELECT 
    first_name, last_name
FROM
    employees;
SELECT 
    *
FROM
    employees;
```

#### WHERE

- the WHERE clause will allow us to set a condition upon which we will specify what part of the data we want to retrieve from the database  
```
SELECT column_1, ... column_n
FROM table_name
WHERE condition;
```

```
SELECT 
    *
FROM
    employees
WHERE
    first_name = 'Elvis';
```

#### AND

- allows you to logically combine two statements in the condition code block hence narrowing the output we would like to extract from our data

```
SELECT column_1, ... column_n
FROM table_name
WHERE condition_1 and condition_2;
```

```
SELECT 
    *
FROM
    employees
WHERE
    first_name = 'Elvis' AND gender = 'M';
```
- binds SQL to meet both conditions enlisted in the WHERE clause simultaneously

#### OR

```
SELECT column_1, ... column_n
FROM table_name
WHERE condition_1 OR condition_2;
``` 
- Either condition_1 or condition_2 is met

```
SELECT 
    *
FROM
    employees
WHERE
    first_name = 'Elvis' OR first_name = 'Aruna';
```

#### Operator Precedence

- an SQL rule stating that in the execution of the query, the operator AND is applied first, while the operator OR is applied second regardles of the order in which you use these operators

##### Exercise
- Retrieve a list with all female employees whose first name is either Kellie or Aruna

```
SELECT 
    *
FROM
    employees
WHERE
    (first_name = 'Kellie'
        OR first_name = 'Aruna')
        AND gender = 'F';
```

#### NOT IN
- use the not in operator to select all individuals from the 'employees' table, whose first name is either "Denis" or "Elvis"

```
SELECT 
    *
FROM
    employees
WHERE
    first_name IN ('Denis' , 'Elvis');
```
- could also be done as
```
SELECT 
    *
FROM
    employees
WHERE
    first_name = 'Denis' or first_name = 'Elvis';
```

*the second option is slow*

- Extract all records from the 'employees' table, aside from those with employees John, Mark or Jacob
```
SELECT 
    *
FROM
    employees
WHERE
    first_name NOT IN ('John', 'Mark', 'Jacob');
```

#### LIKE - NOT LIKE
- % - a substitute for a **sequence** of characters
- helps you match a **single** character

*to match all names starting with 'Mar'*
```
SELECT 
    *
FROM
    employees
WHERE
    first_name LIKE ('Mar%');
```  
*to match all names ending with 'Mar'*
```
SELECT 
    *
FROM
    employees
WHERE
    first_name LIKE ('%Mar');
```  
*to match all names  with 'Mar' in between*
```
SELECT 
    *
FROM
    employees
WHERE
    first_name LIKE ('%Mar%');
```  
*to match all names starting with 'Mar' followed by a single character*
```
SELECT 
    *
FROM
    employees
WHERE
    first_name LIKE ('Mar_');
```  
*to match all names not containing sequence 'Mar'*
```
SELECT 
    *
FROM
    employees
WHERE
    first_name NOT LIKE ('%Mar%');
```

#### Wildcard Characters
1. `%` - a substitute for a *sequence* of characters
2. `_` - helps you match a *single* character
3. `*` - Will deliver a list of *all* columns in a table. it can also be used to count *all* rows of a table

#### BETWEEN... AND...
- designate the interval to which a given value belongs

```
SELECT 
    *
FROM
    employees
WHERE
    hire_date BETWEEN '1990-01-01' AND '2000-01-01';
```
- `1990-01-01` and `2000-01-01` will be included in the retrieved list of records

#### NOT BETWEEN... AND...
- will refer to an interval below the first value and above the second value

```
SELECT 
    *
FROM
    employees
WHERE
    hire_date NOT BETWEEN '1990-01-01' AND '2000-01-01';
```

*can also be applied to strings other than dates only*

#### IS NOT NULL / IS NULL
- extract values that are not null / are null
```
SELECT column_1,... column_n
FROM table_name
WHERE column_name IS NOT NULL;
```

```
SELECT column_1,... column_n
FROM table_name
WHERE column_name IS NULL;
```

- Select the names of all departments whos department number value is not null
```
SELECT 
    *
FROM
    departments
WHERE
    dept_no IS NOT NULL;
```

#### More comparison operators - Exercise

- Retrieve list with data about all female employees who were hired in the year 2000 or after

```
SELECT 
    *
FROM
    employees
WHERE
    hire_date >= '2000-01-01'
        AND gender = 'F';
```

- Retrieve a list with all employees' salaries higher than $150,000

```
SELECT 
    *
FROM
    salaries
WHERE
    salary > 150000;
```

#### SELECT DISTINCT
- selects all *distinct, different* data values
```
SELECT DISTINCT column_1,... column_n
FROM table_name;
```

- Obtain a list with all different 'hire dates' from table 'employees'

```
SELECT DISTINCT
    hire_date
FROM
    employees;
```

#### Aggregate Functions

- `COUNT()` - counts the number of non-null records in a field
```
SELECT COUNT(column_name)
FROM table_name;
```

`COUNT(DISTINCT)`

```
SELECT COUNT(DISTINCT column_name)
FROM table_name;
```

- How many annual contracts with a value higher than or equal to $100,000 have been registered in the salaries table?

```
SELECT 
    COUNT(*)
FROM
    salaries
WHERE
    salary >= 100000;
```

- `SUM()` - sums all the non-null values in a column
- `MIN()` - returns the minimum value from the entire list
- `MAX()` - returns the maximum value from the entire list
- `AVG()` - calculates the average of all non-null values       belonging to a certain column of a table

*aggregate functions ignore null values unless told not to*

#### ORDER BY

```
SELECT 
    *
FROM
    employees
ORDER BY first_name;
```

- default is ASC, to order in DESC

```
SELECT 
    *
FROM
    employees
ORDER BY first_name DESC;
```

#### GROUP BY

- to group results according to a specific field or fields
- `GROUP BY` is placed immediately after the `WHERE` conditions if any and just before the `ORDER BY` clause

```
SELECT column_name(s)
FROM table_name
WHERE conditions
GROUP BY column_name(s)
```

```
SELECT 
    first_name, COUNT(first_name) AS
FROM
    employees
GROUP BY first_name
ORDER BY first_name DESC;
```

#### Alias (AS)
- used to rename a selection from your query

```
SELECT 
    first_name, COUNT(first_name) AS names_count
FROM
    employees
GROUP BY first_name
ORDER BY first_name DESC;
```

- Write a query that obtains two columns. The first column must contain annual salaries higher than 80,000 dollars. The second column, renamed to “emps_with_same_salary”, must show the number of employees contracted to that salary. Lastly, sort the output by the first column.

```
SELECT 
    salary, COUNT(salary) AS emps_with_same_salary
FROM
    salaries
WHERE
    salary > 80000
GROUP BY salary
ORDER BY salary;
```

#### HAVING
- refine the output from records that do not satisfy a certain condition. mostly implemented with `GROUP BY`

```
SELECT colum_name(s)
FROM table_name
WHERE conditions
GROUP BY column_names(s)
HAVING conditions
ORDER BY column_name(s);
```

- `WHERE` vs `HAVING`
- after `HAVING`, you can have a condition with an aggregate function, while `WHERE` cannot use aggregate functions within its conditions

- select the employee numbers of all individuals who have signed more that 1 contract after the 1st of January 2000

```
SELECT 
    emp_no, COUNT(emp_no) AS contra_sighned
FROM
    dept_emp
WHERE
    from_date > '2000-01-01'
GROUP BY emp_no
HAVING COUNT(emp_no) > 1
ORDER BY emp_no;
```

OR

```
SELECT 
    emp_no
FROM
    dept_emp
WHERE
    from_date > '2000-01-01'
GROUP BY emp_no
HAVING COUNT(from_date) > 1
ORDER BY emp_no;
```