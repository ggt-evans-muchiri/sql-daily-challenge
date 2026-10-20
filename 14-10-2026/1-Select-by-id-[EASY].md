# Select By ID

- Link: https://www.hackerrank.com/challenges/select-by-id
- Difficulty: Easy

## Intuition
We need to return the row from the city table where the id matches 1661. The simplest approach is to filter the table using a WHERE clause with the exact id value.

## Solution
```sql
SELECT *
  FROM city
 WHERE id = 1661;
```
