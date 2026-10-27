# Population Density Difference

- Link: https://www.hackerrank.com/challenges/population-density-difference
- Difficulty: Easy

## Intuition
Find the difference between the largest and smallest city populations by subtracting the minimum population from the maximum.

## Solution
```sql
SELECT MAX(population) - MIN(population)
FROM city;
```
