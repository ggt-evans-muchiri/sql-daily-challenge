# Japan Population

- Link: https://www.hackerrank.com/challenges/japan-population/
- Difficulty: Easy

## Intuition
Select cities in Japan using the country code `JPN`, then sum their populations.

## Solution
```sql
SELECT SUM(population)
FROM city
WHERE countrycode = 'JPN';
```
