# Top Earners

- Link: https://www.hackerrank.com/challenges/earnings-of-employees/
- Difficulty: Easy

## Intuition
Find the maximum total earnings (`months * salary`), then count how many employees share that maximum.

## Solution
```sql
SELECT CONCAT(MAX(months * salary), ' ', COUNT(*))
FROM employee
WHERE (months * salary) = (
    SELECT MAX(months * salary)
    FROM employee
);
```
