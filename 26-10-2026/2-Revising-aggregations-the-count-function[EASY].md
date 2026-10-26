# Revising Aggregations - The Count Function

- Link: https://www.hackerrank.com/challenges/revising-aggregations-the-count-function
- Difficulty: Easy

## Intuition
Filter the `CITY` rows to cities with a population greater than 100,000, then count the remaining rows.

## Solution
```sql
SELECT COUNT(*)
FROM city
WHERE population > 100000;
```
