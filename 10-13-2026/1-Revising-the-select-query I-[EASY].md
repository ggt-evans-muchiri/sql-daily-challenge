# Revising the Select Query I

- Link: https://www.hackerrank.com/challenges/revising-the-select-query/problem
- Difficulty: Easy

## Intuition
We need to return only U.S. cities with a population above 100000, so we filter the city table using a WHERE clause with both conditions: countrycode = 'USA' and population > 100000.

## Solution
```sql
SELECT *
  FROM city
 WHERE countrycode = 'USA' AND population > 100000;
```
