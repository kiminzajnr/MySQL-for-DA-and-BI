### The DELETE Statement
- removes records from a database

#### ON DELETE CASCADE
- if a specific value from the parent table's primary key has been deleted, all the records from the child table referring to this value will be removed as well

```
DELETE FROM table_name
WHERE conditions;
```

```
DELETE FROM departments 
WHERE
    dept_no = 'd007';
```