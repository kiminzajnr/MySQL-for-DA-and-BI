### The INSERT Statement
```
INSERT INTO table_name (column_1, ..., column_n)
VALUES (value_1, ..., value_n)
```

```
INSERT INTO employees
(
    emp_no,
    birth_date,
    first_name,
    last_name,
    gender,
    hire_date
) VALUES
(
    9999901,
    '1986-04-21',
    'John',
    'Smith',
    'M',
    '2011-01-01'
);
```

OR
```
INSERT INTO employees
VALUES
(
    9999902,
    '1986-04-21',
    'John',
    'Smith',
    'M',
    '2011-01-01'
);
```

#### Inserting data into a new table

#### INSERT INTO SELECT

```
INSERT INTO table_2 (column_1, ..., column_n)
SELECT column_1, ..., column_n
FROM table_1
WHERE condition;
```

- create a new table and insert all data as from *departments* table

```
CREATE TABLE departments_dup (
    dept_no CHAR(4) NOT NULL,
    dept_name VARCHAR(40) NOT NULL
);

INSERT INTO departments_dup
SELECT * FROM departments;
```