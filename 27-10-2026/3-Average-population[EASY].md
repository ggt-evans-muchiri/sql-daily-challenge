# Average Population

- Link: https://www.hackerrank.com/challenges/average-population/
- Difficulty: Easy

## Intuition
Round the average population across all cities to the nearest whole number.

## Solution
```sql
SELECT ROUND(AVG(population))
FROM city;
```
