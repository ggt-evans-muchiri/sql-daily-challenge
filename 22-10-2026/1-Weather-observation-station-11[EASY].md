# Weather Observation Station 11

- Link: https://www.hackerrank.com/challenges/weather-observation-station-11
- Difficulty: Easy

## Intuition
We need distinct city names that either do not start with a vowel or do not end with a vowel. Check each condition independently, then combine them with `OR`: a city is excluded only when it both starts and ends with a vowel.

## Solution
```sql
SELECT DISTINCT city
FROM station
WHERE (
    LOWER(city) NOT LIKE 'a%'
    AND LOWER(city) NOT LIKE 'e%'
    AND LOWER(city) NOT LIKE 'i%'
    AND LOWER(city) NOT LIKE 'o%'
    AND LOWER(city) NOT LIKE 'u%'
)
OR (
    LOWER(city) NOT LIKE '%a'
    AND LOWER(city) NOT LIKE '%e'
    AND LOWER(city) NOT LIKE '%i'
    AND LOWER(city) NOT LIKE '%o'
    AND LOWER(city) NOT LIKE '%u'
);
```
