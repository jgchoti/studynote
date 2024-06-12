# SQL Commands

## SELECT

Retrieve data from a table.

```sql
SELECT * FROM employee;
Selects all columns from the employee table.
```

```sql
SELECT column1, column2 FROM table;
```

> Selects specific columns.

```sql
SELECT COUNT(name_column) FROM table;
```

> Counts non-null values in a column.

```sql
SELECT name AS n, countrycode AS c FROM city;
```

> Use `AS` to rename columns.

## ORDER BY

Sort results by specified columns.

```sql
ORDER BY name DESC;
```

> Sorts results by name in **descending** order.

```sql
ORDER BY name ASC, age DESC;
```

> Sorts results by name in **ascending** order, and by age in **descending** order if names are the same.

## WHERE

Filter records based on conditions.

```sql
WHERE field = 'value' OR field2 = 'value2';
```

### Operators

| Operator            | Description                                |
|---------------------|--------------------------------------------|
| =                   | Equal to                                   |
| <> or !=            | Not equal to                               |
| >                   | Greater than                               |
| <                   | Less than                                  |
| >=                  | Greater than or equal to                   |
| <=                  | Less than or equal to                      |
| BETWEEN ... AND ... | Checks if a value is within a range        |
| IN (...)            | Checks if a value is in a list             |
| NOT IN (...)        | Checks if a value is not in a list         |

```sql
col_name BETWEEN 1.5 AND 10.5;
```

```sql
col_name IN (2, 4, 6);
```

### IS NULL and IS NOT NULL  

| Operator         | Description                                |
|------------------|--------------------------------------------|
| IS NULL          | Checks for null values                     |
| IS NOT NULL      | Checks for non-null values                 |

```sql
WHERE field IS NULL;
WHERE field IS NOT NULL;
```

## DISTINCT

Removes duplicate rows.

```sql
SELECT DISTINCT countrycode FROM city;
```

## LIKE

Pattern matching.

```sql
SELECT * FROM city WHERE name LIKE 'Ansh_n';
```

| Operator         | Description                                |
|------------------|--------------------------------------------|
| LIKE 'Ansh_n'   | Matches patterns with wildcard characters |
| LIKE '%'        | Wildcard character for any number of characters |

## LIMIT

Limits the number of rows returned.

```sql
LIMIT 10;  -- Returns the first 10 rows
LIMIT 10 OFFSET 5;  -- Skips the first 5 rows and then returns the next 10
```

## JOIN

Combines rows from two or more tables based on a related column.

### INNER JOIN:

```sql
SELECT * FROM city 
INNER JOIN country 
ON city.countrycode = country.code;
```

> Use table_name.column_name for unambiguous column references.

```sql
SELECT column, another_table_column, …
FROM mytable
INNER JOIN another_table 
ON mytable.id = another_table.id;
```

## GROUP BY
Groups rows that have the same values in specified columns into aggregated data.
Commonly used with aggregate functions like COUNT, MAX, MIN, SUM, AVG.

```sql
SELECT department, COUNT(*)
FROM employee
GROUP BY department;
```

> This query counts the number of employees in each department.

```sql
SELECT department, AVG(salary)
FROM employee
GROUP BY department;
```

> This query calculates the average salary for each department.

## HAVING

Filters groups created by the GROUP BY clause. Used instead of WHERE with aggregate functions.

```sql
SELECT department, COUNT(*)
FROM employee
GROUP BY department
HAVING COUNT(*) > 10;
```

> This query only shows departments with more than 10 employees.