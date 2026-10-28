# Average Population of Each Continent

- Link: https://www.hackerrank.com/challenges/average-population-of-each-continent/
- Difficulty: Easy

## Intuition
Join each city to its country's continent, group the cities by continent, and apply FLOOR to the average city population in each group.

## Solution
```sql
SELECT co.continent, FLOOR(AVG(ci.population))
FROM country co
JOIN city ci ON co.code = ci.countrycode
GROUP BY co.continent;
```