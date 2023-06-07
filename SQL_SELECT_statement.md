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