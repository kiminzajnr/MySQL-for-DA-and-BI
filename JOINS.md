#### INNER JOIN
- selects records with matching values in both tables
- null values, or values appearing in just one of the two tables and not appering in the other are not displayed

```
SELECT 
	table_1.column_names(s), table_2.column_name(s)
FROM
	table_1
JOIN
	table_2 ON table_1.column_name = table_2.column_name;
```

- aliases are a common practice
```
SELECT 
	t1.column_name, t1.column_name, ..., t2.column_name, ...
FROM
	table_1 t1
JOIN
	table_2 t2 ON t1.column_name = t2.column_name;
```

```
SELECT 
    m.dept_no, m.emp_no, d.dept_name
FROM
    dept_manager_dup m
        INNER JOIN
    departments_dup d ON m.dept_no = d.dept_no
ORDER BY m.dept_no;
```

- extract a list containing information about all managers' employee number, first and last name, department number, and hire date
```
SELECT 
    e.emp_no, e.first_name, e.last_name, e.hire_date, m.dept_no
FROM
    employees e
        INNER JOIN
    dept_manager m ON e.emp_no = m.emp_no
ORDER BY e.emp_no;
```

#### LEFT JOIN
- all values from the left table that match no values from the right table + all matching values of the two tables
- order in which you join table matters
- left joins can deliver a list with all records from the left table that do not match any rows from the righ table

```
SELECT 
    m.dept_no, m.emp_no, d.dept_name
FROM
    dept_manager_dup m
        LEFT JOIN
    departments_dup d ON m.dept_no = d.dept_no
-- GROUP BY m.emp_no
ORDER BY m.dept_no;
```

- Join the 'employees' and the 'dept_manager' table to return a subset of all the employees whose last name is Markovitch. See if the output contains a manager with that name

```
SELECT 
    em.emp_no,
    em.first_name,
    em.last_name,
    dm.dept_no,
    dm.from_date
FROM
    employees em
        LEFT JOIN
    dept_manager dm ON em.emp_no = dm.emp_no
WHERE
    em.last_name = 'Markovitch'
ORDER BY dept_no DESC , emp_no;
```

#### RIGHT JOIN
- ```RIGHT JOIN``` = ```RIGHT OUTER JOIN```
- all values from the right table that match no values from the left table + all matching values of the two tables
- all records from the right table will be returned in the result set

#### JOIN AND WHERE USED TOGETHER
- Select the first and last name, the hire date, and the job title of all employees whose first name is “Margareta” and have the last name “Markovitch”

```
SELECT 
    e.emp_no, e.first_name, e.last_name, e.hire_date, t.title
FROM
    employees e
        JOIN
    titles t ON e.emp_no = t.emp_no
WHERE
    first_name = 'Margareta'
        AND last_name = 'Markovitch';
```

#### CROSS JOIN
- takes values from a certain table and connects them with all the values from the tables we want to join it with 
- it connects all the values, not just those that match.
- particularly useful when the tables in a database are not well connected
- Use a CROSS JOIN to return a list with all possible combinations between managers from the dept_manager table and department number d009
```
SELECT 
    dm.*, d.*
FROM
    dept_manager dm
        CROSS JOIN
    departments d
WHERE
    d.dept_no = 'd009';
```

#### Join more that two tables in SQL
```
SELECT 
    e.first_name,
    e.last_name,
    e.hire_date,
    m.from_date,
    d.dept_name
FROM
    employees e
        JOIN
    dept_manager m ON e.emp_no = m.emp_no
        JOIN
    departments d ON m.dept_no = d.dept_no;
```


- How many male and how many female managers do we have in the employees database
```
SELECT 
    e.gender, COUNT(gender)
FROM
    employees e
        JOIN
    dept_manager d ON e.emp_no = d.emp_no
GROUP BY gender;
```

#### UNION vs UNION ALL
- used to combine a few `SELECT` statements in a single output

`UNION ALL` - used to combine a few `SELECT` statements in a single output
```
SELECT
    N columns
FROM
    table_1
UNION ALL SELECT
    N columns
FROM
    table_2;
```
- `UNION` - displays only distinct values in the output
- `UNION ALL` - retrieves the duplicates as well
- if you are looking for better results, use `UNION`
- if you are seeking to optimize performance, use `UNION ALL`