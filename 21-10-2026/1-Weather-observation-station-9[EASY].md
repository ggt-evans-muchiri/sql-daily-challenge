# Weather Observation Station 9

- Link: https://www.hackerrank.com/challenges/weather-observation-station-9
- Difficulty: Easy

## Intuition
We need the distinct city names that do not start with a vowel. Each `NOT LIKE 'vowel%'` condition excludes names starting with that vowel. Combining the conditions with `AND` ensures the name starts with none of the five vowels, and `DISTINCT` removes duplicates.

## Solution
```sql
SELECT DISTINCT city 
FROM station
WHERE city NOT LIKE 'a%'
AND city NOT LIKE 'e%'
AND city NOT LIKE 'i%'
AND city NOT LIKE 'o%'
AND city NOT LIKE 'u%';
```
