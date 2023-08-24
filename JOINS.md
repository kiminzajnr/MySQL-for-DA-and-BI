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