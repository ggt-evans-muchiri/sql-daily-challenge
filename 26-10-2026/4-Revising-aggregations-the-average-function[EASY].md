# Revising Aggregations - The Average Function

- Link: https://www.hackerrank.com/challenges/revising-aggregations-the-average-function
- Difficulty: Easy

## Intuition
Filter cities to California, then calculate the average population of the matching rows.

## Solution
```sql
SELECT AVG(population)
FROM city
WHERE district = 'California';
```
