# African Cities

- Link: https://www.hackerrank.com/challenges/african-cities/
- Difficulty: Easy

## Intuition
Use the country code to join cities to their countries, filter for African countries, and return the matching city names.

## Solution
```sql
SELECT ci.name
FROM city ci
JOIN country co ON ci.countrycode = co.code
WHERE co.continent = 'Africa';
```
