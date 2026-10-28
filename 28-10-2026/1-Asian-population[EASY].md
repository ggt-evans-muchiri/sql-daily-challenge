# Asian Population

- Link: https://www.hackerrank.com/challenges/asian-population
- Difficulty: Easy

## Intuition
Match each city to its country using the country code, keep only countries in Asia, and sum the populations of their cities.

## Solution
```sql
SELECT SUM(ci.population)
FROM city ci
JOIN country co ON co.code = ci.countrycode
WHERE co.continent = 'Asia';
```