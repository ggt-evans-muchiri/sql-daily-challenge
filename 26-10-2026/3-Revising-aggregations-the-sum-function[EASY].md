# Revising Aggregations - The Sum Function

- Link: https://www.hackerrank.com/challenges/revising-aggregations-sum
- Difficulty: Easy

## Intuition
Filter cities to California, then sum the population values for the matching rows.

## Solution
```sql
SELECT SUM(population)
FROM city 
WHERE district = 'California';
```
