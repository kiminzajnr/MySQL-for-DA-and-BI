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

Select the names of all departments whos department number value is not null
```
SELECT 
    *
FROM
    departments
WHERE
    dept_no IS NOT NULL;
```