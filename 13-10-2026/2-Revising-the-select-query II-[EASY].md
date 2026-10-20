# Revising the Select Query II

- Link: https://www.hackerrank.com/challenges/revising-the-select-query-2
- Difficulty: Easy

## Intuition
We need to return just the name of the city records where the country code is `USA` and the population is greater than `100000`. The simplest approach is to filter the table with a `WHERE` clause using both conditions together.

## Solution
```sql
SELECT name
  FROM city
 WHERE countrycode = 'USA' AND population > 120000;
```
