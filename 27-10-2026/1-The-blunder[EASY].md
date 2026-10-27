# The Blunder

- Link: https://www.hackerrank.com/challenges/the-blunder/
- Difficulty: Easy

## Intuition
Remove every zero from each salary to calculate the incorrect average, subtract it from the actual average, and round the difference up.

## Solution
```sql
SELECT CEIL(
    AVG(salary) -
    AVG(CAST(REPLACE(salary, '0', '') AS UNSIGNED))
)
FROM employees;
```
